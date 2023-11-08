# Flutter - Singleton
> 在 Dart/Flutter 中建立單例模式的不同方式

## Factory constructor

```dart
class Singleton {
  static final Singleton _instance = Singleton._internal();

  factory Singleton() {
    return _instance;
  }

  Singleton._internal();
}

void main() {
  Singleton s1 = Singleton();
  Singleton s2 = Singleton();
  
  print(identical(s1, s2)); // true
  print(s1 == s2); // true
}
```

## Static field with getter

```dart
class Singleton {
  Singleton._privateConstructor();
  
  static final Singleton _instance = Singleton._privateConstructor();
  
  static Singleton get instance => _instance;

}

void main() {
  Singleton s1 = Singleton.instance;
  Singleton s2 = Singleton.instance;

  print(identical(s1, s2));
  print(s1 == s2);
}
```

## Static field

```dart
class Singleton {
  Singleton._privateConstructor();
  static final Singleton instance = Singleton._privateConstructor();
}

void main() {
  Singleton s1 = Singleton.instance;
  Singleton s2 = Singleton.instance;

  print(identical(s1, s2));
  print(s1 == s2);
}
```

## Reference
  - [How do you build a Singleton in Dart?](https://stackoverflow.com/questions/12649573/how-do-you-build-a-singleton-in-dart)