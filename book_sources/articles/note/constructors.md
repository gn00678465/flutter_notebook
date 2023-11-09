# Dart - Constructors
> 在 Dart 中類的建構子使用的技巧

```dart
/// Default Constructor
class User {
  String name = 'John doe';
  User();
}


/// Constructor with parameters
class User {
  final String name;
  User(this.name);
}

/// Constructor with the initial method
class User {
  final String name;
  late int age;
  
  User(this.name, int age) {
    this.age = age;
  }
}

/// Constructor with assertion
class User {
  String name;
  User(this.name) : assert(name.length > 3);
}

/// Constructor with initializer
class User {
  static String uppercase(String str) => str.toUpperCase();
  String name;
  User(name) : name = uppercase(name);
}

/// Constructor with super()
/// override variable
class Person {
  String id;
  Person(this.id);
}
class User extends Person {
  String name;
  User(this.name, String id) : super(id);
}

/// Constructor with this()
/// Named constructor
class User {
  String name;
  int salary;
  User(this.name, this.salary);
  User.worker(String name) : this(name, 10);
  User.boss(String name) : this(name, 100);
}
```

## Private Constructor
> 通常用於實現單例模式或限制該類的實例化。

```dart
void main() {
  ServiceSDK(); // error: Couldn't find constructor 'ServiceSDK'.

  ServiceSDK.fetch();
}

class ServiceSDK {
  ServiceSDK._();
  
  static const String _apiKey = '123213123';
  
  static Future<void> fetch() async {
    print(_apiKey);
  }
}
```

## Private Named Constructor

## Factory Constructor
> Factory 無法訪問 `this`