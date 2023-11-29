# Flutter - Extension methods
> Extension methods 可以在既有的 class 或 libraries 上擴充新的功能

## 限制
1. 不能對 dynamic 型別調用 extension methods
2. API conflicts
    - 當與 interface 或其他的 extension member 發生衝突的情況下，有幾種解決方式
    1. 使用 `show` 或 `hide` 限制 export api
    2. 使用 `as` prefix import

## 語法
```dart
extension <extension name>? on <type> {
  (<member definition>)*
}
```

```dart
/// example
extension StringExt on String {
  void log() {
    debugPrint(this);
  }
}
```

## Reference
- [Extension methods](https://dart.dev/language/extension-methods)