# Flutter - Dark Mode
> 在 Material/Cupertino 兩種風格中設定 Dark Mode

## Material

```dart
MaterialApp(
  themeMode: isDarkTheme ? ThemeMode.dark : ThemeMode.light, // 可以設定為 ThemeMode.system
  theme: ThemeData.light(), // 當 theme mode 為 light 時套用
  darkTheme: ThemeData.dark(), // 當 theme mode 為 dark 時套用
  //...
);
```

## Cupertino
>  Cupertino 提供了 CupertinoDynamicColors 用於建立動態顏色

```dart
CupertinoApp(
  theme: CupertinoThemeData(
    brightness: isDarkTheme ? Brightness.dark : Brightness.light,
    barBackgroundColor: const CupertinoDynamicColor.withBrightness(
      color: CupertinoColors.white,  // 當 brightness 為 light 時套用此顏色
      darkColor: CupertinoColors.black,  // 當 brightness 為 dark 時套用此顏色
    ),
  ),
  // ...
);
```