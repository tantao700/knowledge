# How to preset the app in Android System?

- there are two kinds to preset:
    - preset APK
    - preset APP with sources

## Preset APK

1.Sample with Shadowsocks.apk

- Create the Shadowsocks file in folder AOSP/packages/apps
- Put the Shadowsocks.apk and create a new Android.mk
```mk
    #Android.mk
    LOCAL_PATH := $(call my-dir)
    
    include $(CLEAR_VARS)
    
    LOCAL_MODULE_TAGS := optional
    
    LOCAL_MODULE := < your app folder name >
    
    # 签名
    LOCAL_CERTIFICATE := < desired key >
    
    # 指定 src 目录 
    LOCAL_SRC_FILES := < app apk filename >
    
    LOCAL_MODULE_CLASS := APPS
    
    # 该模块的后缀，不用定义
    #LOCAL_MODULE_SUFFIX := $(COMMON_ANDROID_PACKAGE_SUFFIX)
    
    include $(BUILD_PREBUILT)
```