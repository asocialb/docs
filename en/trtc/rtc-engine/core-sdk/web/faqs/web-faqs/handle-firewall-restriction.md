# Handle Firewall Restriction

This tutorial mainly introduces the best practices for dealing with firewall restrictions. For example, in a network environment with a firewall such as an enterprise intranet, TRTC Web SDK cannot be used normally due to firewall restrictions. In this case, there are two solutions:

- **Solution 1**: Listen for SDK errors and guide users to change networks or configure firewall whitelists.
- **Solution 2**: Use the Nginx + coturn proxy solution.

> **Note**The TRTC Web SDK uses UDP to transfer media data to the TRTC server by default, and has a built-in Turn Server that supports relaying media data through UDP or TCP.In the public network, users do not need to set up any proxies, as the SDK will attempt to establish media connections in the order of direct connection, Turn Server UDP, and Turn Server TCP.If it is known that the user will be using the SDK within an internal network firewall, it may not be possible to establish a media connection, and a proxy will need to be set up.

## Solution 1

This solution is suitable for that you cannot confirm whether the user's network will be restricted by the firewall. At this time, you can listen for SDK errors, guide users to change networks or check firewalls.

When you call APIs such as startLocalVideo, startLocalAudio, startRemoteVideo, etc., the SDK will establish a media connection channel internally for transfering media data. When encountering firewall restrictions, the SDK may fail to establish a connection, and the SDK will throw a firewall-restricted error and continue to retry.

You can refer to the following code example to listen for this error and guide users to change networks or check network firewalls and whitelist the domains and ports used by TRTC Web SDK.

```
trtc.on(TRTC.EVENT.ERROR, error => {  // User network firewall restrictions may cause audio and video calls to fail.  // At this time, guide users to change networks or check network firewall settings.  if (error.code === TRTC.ERROR_CODE.OPERATION_FAILED && error.extraCode === 5501) {      }});
```

### What ports and domain names should I add to the allowlist of my firewall for WebRTC?

Add the following ports to the allowlist

| WebRTC (H5) | Ports |
| --- | --- |
| TCP | 443 |
| UDP | 8000, 8080, 8800, 843, 443, 16285 |

Add the following domain names to the allowlist

```
apisgp.my-imcloud.com# version after v5.5.0*.rtc-web.com*.rtc-web.io# version before v5.5.0signailing.rtc.tencentcloud.comschedule.rtc.tencentcloud.com*.rtc.tencentcloud.com
```

## Solution 2

This solution is suitable for that you confirm that the user's network is restricted by the firewall, and you need to set up a proxy server to solve the problem.

This solution requires the deployment of two servers, Nginx + Turn Server. You can contact your company's operations and maintenance colleagues to assist in building. The Nginx proxy server is used to proxy the Websocket signaling data packets of TRTC Web SDK. The Turn Server is used to relay media data.

| Solution | Applicable scenarios | Network requirements |
| --- | --- | --- |
| A | Users can access a specific external proxy server on the network | The proxy server is deployed on the external network, and the internal network firewall needs to open a whitelist to allow internal network users to access the external proxy server. |
| B | Users can only access an internal proxy server on the network | The proxy server is deployed on the internal network, and the internal network firewall needs to open a whitelist to allow the internal proxy server to access the external network. |

![Figure 2-A](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/086a8647e5bc11ee9ca3525400bb593a.png)

![Figure 2-B](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/0b8f19bfe5bc11eeb1eb525400b5f95f.png)

### Solution 2-A

#### Setting up Nginx server

1. Deploy Nginx server

Refer to the Nginx server deployment tutorial found on the Internet for deployment. If the enterprise has already deployed the Nginx service, it can be configured directly.

2. Configure Nginx server.

```
vi /etc/nginx/nginx.conf
```

```
http {  server {     # The access domain name of the Nginx server    server_name proxy.example.com;     # The access port of the Nginx server    listen 443;     ssl on;     location /ws/ { # Corresponding to the websocketProxy parameter in setProxyServer      proxy_pass https://signaling.rtc.qq.com/; # TRTC server      proxy_http_version 1.1;       proxy_set_header Upgrade $http_upgrade;       proxy_set_header Connection "upgrade";     }    location /logger/ { # Corresponding to the loggerProxy parameter in setProxyServer      proxy_pass https://yun.tim.qq.com/;    }    # SSL certificate corresponding to the domain name, used for HTTPS, users need to apply for it themselves    ssl_certificate ./crt/1_proxy.trtcapi.com_bundle.crt;     ssl_certificate_key ./crt/2_proxy.trtcapi.com.key;   }}
```

3. Reload Nginx.

```
sudo nginx -s reload
```

4. Confirm that the company's firewall allows access to the Nginx server IP and port.

#### Setting up Turn server

You can search for turn server setup tutorials on the Internet for setup, or you can use the following script to set up a turn server in **CentOS**.

1. Create a script file **turn.sh** in the Linux server, and the script content is as follows.

```
#!/usr/bin/env bash# current file name is turn.sh# ref:# https://gabrieltanner.org/blog/turn-server    STEP 3 testing turn server# https://medium.com/av-transcode/what-is-webrtc-and-how-to-setup-stun-turn-server-for-webrtc-communication-63314728b9d0# as super-user# usage:  current_program <external-ip>set -xset -eip apwdwhoamidisplay_usage() {        echo "This script must be run with super-user privileges."        echo -e "\\nUsage: $0 <external-ip> \\ne.g. $0 154.8.246.205"}# if less than two arguments supplied, display usageif [ $# -lt 1 ]then        display_usage        exit 1fiif [[ $1 =~ ^[0-9]+\\.[0-9]+\\.[0-9]+\\.[0-9]+$ ]]; then  echo "get external ip $1"else  echo "wrong external ip $1 , must not have whitespace, tab and other char"  exit 2fiyum install -y coturn# $1 is <external-ip>cat <<EOF > /etc/coturn/turnserver.confexternal-ip=$1listening-port=3478lt-cred-mechmax-port=65535min-port=20000no-dtlsno-tlsrealm=tencentuser=turn:turnverboseEOF
```

2. Add executable permission.

```
chmod +x turn.sh
```

3. Execute the script as root, for example:

```
sudo ./turn.sh <server public IP>
```

4. Start the turn server.

```
systemctl start coturn# Check if turn is started successfullyps aux | grep coturn# If you want to restart the service, executeservice coturn restartÂ
```

5. Configure the firewall for the turn server, open inbound port 3478 (TCP & UDP), and outbound ports (UDP) between min and max ports in the configuration above.
6. Configure the company's internal network firewall to allow access to the turn server's IP and open outbound port 3478 (TCP & UDP).
7. Test the turn server

Use this [test page](https://webrtc.github.io/samples/src/content/peerconnection/trickle-ice/) to test whether the turn server is accessible. If the result shows "done" as shown in the screenshot below, the turn server is working properly.

![turn-test](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/70df0db4e5be11ee9f745254008eb8a8.png)

### Solution 2-B

Solution 2-B builds the Nginx proxy in the same way as Solution 2-A.

There are two main differences:

1. When building a turn server, the external-ip field in the configuration file must be filled in with the address of the server on your corporate intranet.

```
# The start script in Solution 2-A is the server's external address, e.g. 14.3.3.3sudo . /turn.sh 14.3.3.3# In Solution 2-B, the start script fills in the server's intranet address, # e.g. 10.0.0.4 for the intranetsudo . /turn.sh 10.0.0.4
```

2. Firewall configuration:
- For the Nginx server, the domain name whitelist needs to be configured in the company's intranet firewall to allow the Nginx server to access TRTC's related domain names. Refer to [Whitelist](#what-ports-and-domain-names-should-i-add-to-the-allowlist-of-my-firewall-for-webrtc.3F).
- For the Turn Server, allow the Turn Server to access the external network.

### Setting Up Proxy Server to TRTC Web SDK

After you have set up Nginx and Turn server, you can refer to the following example to set up a proxy server.

```
const trtc = TRTC.create(); await trtc.enterRoom({  ...,  proxy: {    // Set up a Websocket proxy to relay signaling data packets between the SDK and the TRTC backend.    websocketProxy: 'wss://proxy.example.com/ws/',    // Set up a turn server to relay media data packets between the SDK and the TRTC backend. 14.3.3.3:3478 is the IP address and port of the turn server.    turnServer: { url: '14.3.3.3:3478', username: 'turn', credential: 'turn', credentialType: 'password' },    // By default, the SDK will connect to trtc server directly, if connection failed, then SDK will try to connect the TURN server to relay the media data. You can set 'relay' to force the connection through the TURN server.    iceTransportPolicy: 'all',     // By default, the SDK reports logs to the yun.tim.qq.com domain name. If this domain name cannot be accessed in your internal network, you need to whitelist the domain name or configure the following log proxy.    // Set up a log reporting proxy. Logs are key data for troubleshooting, so be sure to set up this proxy.    loggerProxy: 'https://proxy.example.com/logger/',  }})
```


---
*Source: [https://trtc.io/document/59667](https://trtc.io/document/59667)*
