# Step 1: Install Chat SDK

This document describes how to quickly integrate the Chat SDK into your Windows project.

## Environment Requirements

- Operating system: Windows 7 or later.
- Development environment: Visual Studio 2010 or later. Visual Studio 2019 is recommended.

## Integrating Chat SDK

The following describes how to integrate the SDK into a Visual Studio 2019 project by creating a simple MFC project.

### Step 1. Download Chat SDK

Download the Chat SDK for Windows [here](https://github.com/TencentCloud/TIMSDK/tree/master/Windows/IMSDK), and decompress it. You can rename it "ImSDK" for convenience. It contains the following parts:

| Directory Name | Description |
| --- | --- |
| c_include | C API header files |
| cpp_include | C++ API header files |
| shared_lib\\Win32 | **32-bit Release mode**, which uses the /MT option to link library files. |
| shared_lib\\Win64 | **64-bit Release mode**, which uses the /MT option to link library files. |

### Step 2. Create a project

Open Visual Studio and create an MFC application named "IMDemo". If the MFC application is not one of the first options, you can search for it through the search template at the top.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ada8dbd247d811ef9b7d525400fdb830.png)

For quick integration, select the relatively simple **Dialog based** type on the **Application Type** page of the wizard. For other configuration items, keep them as default.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/ca6f6ee947d811ef92e952540055f650.png)

### Step 3. Copy the files

Copy the SDK folder generated after decompression (the "ImSDK" folder obtained in [step 1](https://www.tencentcloud.com/document/product/1047/34310#step-1.-download-the-im-sdk)) to the directory where `IMDemo.vcxproj` is located.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/894b6993499411ef9bf1525400a9236a.png)

### Step 4. Modify the project configuration

The SDK provides 32-bit and 64-bit static libraries in **Release** mode, which require some special configurations. Open the IMDemo attribute page, select **Solution Explorer**, right-click `IMDemo`, and select **Properties**.

The following takes the **32-bit Release mode** as an example:

1. Add the include directory.
 Go to **C/C++** > **General** > **Additional Include Directories** and add the SDK C header file directory `$(ProjectDir)ImSDK\\c_include`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/90d2e6f8499411ef998b525400f69702.png)

2. Add the library directory.
 Go to **Linker** > **General** > **Additional Library Directories** and add the SDK library directory `$(ProjectDir)ImSDK\\shared_lib\\Win32`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/c6970319499411ef8357525400bdab9d.png)

3. Add the library file.
 Go to **Linker** > **Input** > **Additional Dependencies** and add the SDK library file `ImSDK.lib`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/a7eca1e7499411efbaba525400d5f8ef.png)

4. Copy the DLL file to the execution directory.
 Go to **Build Events** > **Pre-Build Event** > **Command Line**, enter `xcopy /E /Y "$(ProjectDir)ImSDK\\shared_lib\\Win32" "$(OutDir)"`, and copy the `ImSDK.dll` dynamic library file to the output directory of the project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5f65d4fd47d911ef8866525400bdab9d.png)

5. Specify the encoding format of the source file.
The SDK header file uses the UTF-8 encoding format, whereas some compilers compile source files in the default system encoding format. This may lead to compilation failure. Set this parameter to instruct compilers to compile source files using UTF-8 encoding.
Go to **C/C++** > **Command Line** > **Additional Options** and enter `/source-charset:.65001`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/6db9620247d911ef8f89525400d5f8ef.png)

Most of the settings for the **64-bit Release** are similar to those for the **32-bit Release**. The difference lies in the SDK library directory as follows:

1. Add the library directory.
- Go to **Linker** > **General** > **Additional Library Directories** and add the SDK library directory `$(ProjectDir)ImSDK\\shared_lib\\Win64`.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7e53500347d911ef8866525400bdab9d.png)

2. Copy the DLL file to the execution directory.
- In **Release mode**, go to **Build Events** > **Pre-Build Event** > **Command Line**, enter `xcopy /E /Y "$(ProjectDir)ImSDK\\shared_lib\\Win64" "$(OutDir)"`, and copy the `ImSDK.dll` dynamic library file to the output directory of the project.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/8fcea99347d911ef91895254002693fd.png)

### Step 5. Print Chat SDK version number

- In the `IMDemoDlg.cpp` file, add the header file inclusion:

```
#include "TIMCloud.h"
```

- In the `IMDemoDlg.cpp` file, find the `CIMDemoDlg::OnInitDialog` function and add the following test code before `return`:

```
SetWindowText(L"IMDemo");CString szText;szText.Format(L"SDK version: %hs", TIMGetSDKVersion());CWnd* pStatic = GetDlgItem(IDC_STATIC);pStatic->SetWindowTextW(szText);
```

- Press **F5** to run the code and print the SDK version number.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7111425447da11ef92e952540055f650.png)

## FAQs

- If the following error occurs, check whether the directory of the SDK header file has been correctly added according to the preceding project configuration:

```
fatal error C1083: unable to open the header file: "TIMCloud.h": No such file or directory
```

- If the following error occurs, check whether the SDK library directory and library file have been correctly added according to the preceding project configuration:

```
LINK : fatal error LNK1104: Unable to open the `ImSDK.lib` file.
```

```
error LNK2019: Unresolved external symbol `__imp__TIMGetSDKVersion`, referenced in the `"protected: virtual int __thiscall CIMDemoDlg::OnInitDialog(void)" (?OnInitDialog@CIMDemoDlg@@MAEHXZ)` function
```

- If an error occurs, check whether the SDK's DLL has been copied to the execution directory as described in the project configuration step above.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/fc0d4df2222011ee909c525400cea498.png)


---
*Source: [https://trtc.io/document/34310](https://trtc.io/document/34310)*
