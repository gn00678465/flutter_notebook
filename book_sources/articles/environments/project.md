# Flutter 建立專案

## 建立專案

```bash
flutter create my_app
```
> Flutter 預設將專案資料夾名字用於 **BundleID** 和 **ApplicationID** > **BundleID** 為 `com.example.my_app` > **ApplicationID** 為 `com.example.myApp`

```bash
flutter create --project-name my_app --org dev.flutter my_app
```

> `org` 與 `project-name` 兩個參數組合成 **BundleID** 和 **ApplicationID**，需要留意參數是否合乎他們的規格。
> 建立專案時建議加上 `org` 與 `project-name` 兩個參數

- --platform: 專案可支援的平台，預設全部

## 新增 platform 在已存在專案

```bash
flutter create --platforms=web,macos .
```

## Reference

- [Flutter ‘create’ 了什麼？](https://kendevlog.wordpress.com/2020/09/26/flutter-create/)
- [修改 applicationId](https://www.eeaseries.com/2021/01/applicationid.html)
- BundleID: [CFBundleIdentifier](https://developer.apple.com/documentation/bundleresources/information_property_list/cfbundleidentifier)
- ApplicationID: [設定應用程式模組](https://developer.android.com/studio/build/configure-app-module?hl=zh-tw)
