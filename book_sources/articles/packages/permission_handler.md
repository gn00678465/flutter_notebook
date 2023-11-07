# Flutter package - permission_handler
> permission_handler 只支援 ANDROID、IOS、WINDOWS
> 主要為 ANDROID、IOS 系統，會要跟使用者要求權限

## install
```bash
flutter pub add permission_handler
```

## Setup

### Android
1. 在 **gradle.properties** 檔案中加入
    ```properties
    android.useAndroidX=true
    android.enableJetifier=true
    ```
2. 確認 **android/app/build.gradle** 中的 `compileSdkVersion`
    ```gradle
    android {
      compileSdkVersion 33
      ...
    }
    ```

**加入權限**

設定檔路徑: **android/app/src/main/AndroidManifest.xml**

```xml
<manifest>
    ...
    
    <!--
    Internet permissions do not affect the `permission_handler` plugin, but are required if your app needs access to
    the internet.
    -->
    <uses-permission android:name="android.permission.INTERNET"/>

    <!-- Permissions options for the `contacts` group -->
    <uses-permission android:name="android.permission.READ_CONTACTS"/>
    <uses-permission android:name="android.permission.WRITE_CONTACTS"/>
    <uses-permission android:name="android.permission.GET_ACCOUNTS"/>

    <!-- Permissions options for the `storage` group -->
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />
    <uses-permission android:name="android.permission.READ_MEDIA_VIDEO" />
    <uses-permission android:name="android.permission.READ_MEDIA_AUDIO" />

    <!-- Permissions options for the `camera` group -->
    <uses-permission android:name="android.permission.CAMERA"/>

    <!-- Permissions options for the `sms` group -->
    <uses-permission android:name="android.permission.SEND_SMS"/>
    <uses-permission android:name="android.permission.RECEIVE_SMS"/>
    <uses-permission android:name="android.permission.READ_SMS"/>
    <uses-permission android:name="android.permission.RECEIVE_WAP_PUSH"/>
    <uses-permission android:name="android.permission.RECEIVE_MMS"/>

    <!-- Permissions options for the `phone` group -->
    <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
    <uses-permission android:name="android.permission.CALL_PHONE"/>
    <uses-permission android:name="android.permission.ADD_VOICEMAIL"/>
    <uses-permission android:name="android.permission.USE_SIP"/>
    <uses-permission android:name="android.permission.READ_CALL_LOG"/>
    <uses-permission android:name="android.permission.WRITE_CALL_LOG"/>

    <!-- Permissions options for the `calendar` group -->
    <uses-permission android:name="android.permission.READ_CALENDAR" />
    <uses-permission android:name="android.permission.WRITE_CALENDAR" />

    <!-- Permissions options for the `location` group -->
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />

    <!-- Permissions options for the `microphone` or `speech` group -->
    <uses-permission android:name="android.permission.RECORD_AUDIO" />

    <!-- Permissions options for the `sensors` group -->
    <uses-permission android:name="android.permission.BODY_SENSORS" />
    <uses-permission android:name="android.permission.BODY_SENSORS_BACKGROUND" />

    <!-- Permissions options for the `accessMediaLocation` group -->
    <uses-permission android:name="android.permission.ACCESS_MEDIA_LOCATION" />

    <!-- Permissions options for the `activityRecognition` group -->
    <uses-permission android:name="android.permission.ACTIVITY_RECOGNITION" />

    <!-- Permissions options for the `ignoreBatteryOptimizations` group -->
    <uses-permission android:name="android.permission.REQUEST_IGNORE_BATTERY_OPTIMIZATIONS" />

    <!-- Permissions options for the `nearby devices` group -->
    <uses-permission android:name="android.permission.BLUETOOTH" />
    <uses-permission android:name="android.permission.BLUETOOTH_SCAN" />
    <uses-permission android:name="android.permission.BLUETOOTH_ADVERTISE" />
    <uses-permission android:name="android.permission.BLUETOOTH_CONNECT" />
    <uses-permission android:name="android.permission.NEARBY_WIFI_DEVICES" />

    <!-- Permissions options for the `manage external storage` group -->
    <uses-permission android:name="android.permission.MANAGE_EXTERNAL_STORAGE" />

    <!-- Permissions options for the `system alert windows` group -->
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />

    <!-- Permissions options for the `request install packages` group -->
    <uses-permission android:name="android.permission.REQUEST_INSTALL_PACKAGES" />

    <!-- Permissions options for the `access notification policy` group -->
    <uses-permission android:name="android.permission.ACCESS_NOTIFICATION_POLICY"/>

    <!-- Permissions options for the `notification` group -->
    <uses-permission android:name="android.permission.POST_NOTIFICATIONS"/>

    <!-- Permissions options for the `alarm` group -->
    <uses-permission android:name="android.permission.SCHEDULE_EXACT_ALARM" />
    
    <application>
    ...
    </application>
</manifest>
```

### iOS
1. 在 **Podfile** 中加入以下程式碼
    ```
    post_install do |installer|
      installer.pods_project.targets.each do |target|
        ... # Here are some configurations automatically generated by flutter

        # Start of the permission_handler configuration
        target.build_configurations.each do |config|

          # You can enable the permissions needed here. For example to enable camera
          # permission, just remove the `#` character in front so it looks like this:
          #
          # ## dart: PermissionGroup.camera
          # 'PERMISSION_CAMERA=1'
          #
          #  Preprocessor definitions can be found in: https://github.com/Baseflow/flutter-permission-handler/blob/master/permission_handler_apple/ios/Classes/PermissionHandlerEnums.h
          config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [
            '$(inherited)',

            ## dart: PermissionGroup.calendar
            # 'PERMISSION_EVENTS=1',

            ## dart: PermissionGroup.reminders
            # 'PERMISSION_REMINDERS=1',

            ## dart: PermissionGroup.contacts
            # 'PERMISSION_CONTACTS=1',

            ## dart: PermissionGroup.camera
            # 'PERMISSION_CAMERA=1',

            ## dart: PermissionGroup.microphone
            # 'PERMISSION_MICROPHONE=1',

            ## dart: PermissionGroup.speech
            # 'PERMISSION_SPEECH_RECOGNIZER=1',

            ## dart: PermissionGroup.photos
            # 'PERMISSION_PHOTOS=1',

            ## dart: [PermissionGroup.location, PermissionGroup.locationAlways, PermissionGroup.locationWhenInUse]
            # 'PERMISSION_LOCATION=1',

            ## dart: PermissionGroup.notification
            # 'PERMISSION_NOTIFICATIONS=1',

            ## dart: PermissionGroup.mediaLibrary
            # 'PERMISSION_MEDIA_LIBRARY=1',

            ## dart: PermissionGroup.sensors
            # 'PERMISSION_SENSORS=1',   

            ## dart: PermissionGroup.bluetooth
            # 'PERMISSION_BLUETOOTH=1',

            ## dart: PermissionGroup.appTrackingTransparency
            # 'PERMISSION_APP_TRACKING_TRANSPARENCY=1',

            ## dart: PermissionGroup.criticalAlerts
            # 'PERMISSION_CRITICAL_ALERTS=1'
          ]

        end 
        # End of the permission_handler configuration
      end
    end
    ```
2. 將所需要的權限前的 **#** 移除
    
**加入權限**

格式
  - <key>權限的 key</key>
  - <string>請求權限的提示文字</string> 

設定檔路徑: **ios/Runner/Info.plist**

```plist
<dict>
...

    <!-- Permission options for the `location` group -->
    <key>NSLocationWhenInUseUsageDescription</key>
    <string>Need location when in use</string>
    <key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
    <string>Always and when in use!</string>
    <key>NSLocationUsageDescription</key>
    <string>Older devices need location.</string>
    <key>NSLocationAlwaysUsageDescription</key>
    <string>Can I have location always?</string>

    <!-- Permission options for the `mediaLibrary` group -->
    <key>NSAppleMusicUsageDescription</key>
    <string>Music!</string>
    <key>kTCCServiceMediaLibrary</key>
    <string>media</string>

    <!-- Permission options for the `calendar` group -->
    <key>NSCalendarsUsageDescription</key>
    <string>Calendars</string>

    <!-- Permission options for the `camera` group -->
    <key>NSCameraUsageDescription</key>
    <string>camera</string>

    <!-- Permission options for the `contacts` group -->
    <key>NSContactsUsageDescription</key>
    <string>contacts</string>

    <!-- Permission options for the `microphone` group -->
    <key>NSMicrophoneUsageDescription</key>
    <string>microphone</string>

    <!-- Permission options for the `speech` group -->
    <key>NSSpeechRecognitionUsageDescription</key>
    <string>speech</string>

    <!-- Permission options for the `sensors` group -->
    <key>NSMotionUsageDescription</key>
    <string>motion</string>

    <!-- Permission options for read the `photos` group -->
    <key>NSPhotoLibraryUsageDescription</key>
    <string>photos</string>

    <!-- Permission options for write access `photos` group -->
    <key>NSPhotoLibraryAddUsageDescription</key>
    <string>photos</string>

    <!-- Permission options for the `reminder` group -->
    <key>NSRemindersUsageDescription</key>
    <string>reminders</string>

    <!-- Permission options for the `bluetooth` -->
    <key>NSBluetoothAlwaysUsageDescription</key>
    <string>bluetooth</string>
    <key>NSBluetoothPeripheralUsageDescription</key>
    <string>bluetooth</string>

    <!-- Permission options for the `appTrackingTransparency` -->
    <key>NSUserTrackingUsageDescription</key>
    <string>appTrackingTransparency</string>

</dict>
```

## Usage
- [How to use](https://pub.dev/packages/permission_handler#how-to-use)

## Reference
  - [pub.dev - permission_handler](https://pub.dev/packages/permission_handler)
  - [flutter-permission-handler-demo](https://github.com/Baseflow/flutter-permission-handler/tree/main)