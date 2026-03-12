# API List for Webhooks Configuration

## Callback Information Configuration

| Feature Overview | API |
| --- | --- |
| Create Callback | [v1/callback/set](https://www.tencentcloud.com/document/product/647/60111#) |
| Query Callback | [v1/callback/get](https://www.tencentcloud.com/document/product/647/60112#) |
| Update Callback | [v1/callback/update](https://www.tencentcloud.com/document/product/647/60113#) |
| Deleting callback | [v1/callback/delete](https://www.tencentcloud.com/document/product/647/60114#) |

## Callback Command Word List

| Call Status Callback | Call Event Callback |
| --- | --- |
| `cancel` Cancel: Caller cancels the call before it is answered`reject` Declined: The callee rejects the call`not_answer` Missed call: The callee does not answer within the timeout period`normal_end` Complete: The call is connected and ends normally`call_busy` Busy Line: The call is on a busy line`interrupt` Interruption: The call is interrupted due to network or other reasons | `caller_start_call` Originator Initiates Call`caller_call_accepted` Originator Answers Call`caller_call_missed` Originator Misses Call`caller_call_rejected` Caller Rejects Call`caller_call_busy` Caller Line is Busy`caller_cancel_call` Caller Cancels Call`caller_call_failed `Caller Fails to Initiate Call`caller_call_end` Caller Ends Call Normally`caller_call_interrupted` Caller's Call Interrupted`callee_receive_call` Callee Receives Call`callee_accept_call` Callee Answers Call`callee_not_answer_call` Callee Does Not Answer`callee_reject_call` Callee Rejects Call`callee_ignore_call` Callee Ignores Call`callee_call_canceled` Callee Cancels Call`callee_call_end` Callee Ends Call Normally`callee_call_interrupted` Callee's Call Interrupted`invite_user` Midway invite user`join_in_group_call` Join the call midway |


---
*Source: [https://trtc.io/document/60135](https://trtc.io/document/60135)*
