## ANDROID Intent

### 通过Intent 广播消息,BroadcastReceiver进行接受

AndroidManifest.xml
```xml
<!--define permission-->
<permission android:name="com.xxx.permission.MY_INTENT" />
...
<!--use customer permission-->
<uses-permission android:name="com.xxx.permission.MY_INTENT" />
...
<intent-filter>
    <action android:name="android.intent.action.BOOT_COMPLETED" />
    <action android:name="com.xxx.app.MY_ACTION" />
</intent-filter>
<receiver
    android:name=".MyReceiver"
    android:enabled="true"
    android:exported="true"
    android:permission="com.xxx.permission.MY_INTENT"
    >
    <!-- filter actions -->
    <intent-filter>
        <action android:name="com.xxx.app.MY_ACTION" />
    </intent-filter>
</receiver>
```
MyReceiver.java
```java
public class MyReceiver extends BroadcastReceiver {
    @Override
    public void onReceive(Context context, Intent intent) {
        Toast.makeText(context, "test", Toast.LENGTH_LONG).show();
    }
}
```

### 说明

    android8.0 上 对隐试广播进行了限制

### 解决方案
    发送广播的时候携带intent.addFlags(0x01000000); 即能让广播突破隐式广播限制    

    