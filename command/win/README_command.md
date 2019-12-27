# 查找匹配字符串
findstr /s /i "match str" "*.java"

## [Win 10] VT-x is not available, but is enabled in BIOS
There are three common culprits for the type of error the user is seeing:

    VT-x is not enabled in the BIOS
    The CPU doesn't support VT-x
    Hyper-V virtualization is enabled in Windows

Since the user already eliminated the first two possible culprits, the next step is to open a command prompt as administrator and run the following command:

```shell
    dism.exe /Online /Disable-Feature:Microsoft-Hyper-V
```

Afterwards, reboot the PC and try VirtualBox again.



