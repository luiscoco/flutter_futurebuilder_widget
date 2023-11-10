# Flutter Futurebuilder Widget


```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('FutureBuilder Example'),
        ),
        body: MyFutureBuilderWidget(),
      ),
    );
  }
}

class MyFutureBuilderWidget extends StatelessWidget {
  Future<String> fetchData() async {
    // Simulating an asynchronous operation, e.g., fetching data from an API
    await Future.delayed(Duration(seconds: 2));
    return "Hello, FutureBuilder!";
  }

  @override
  Widget build(BuildContext context) {
    return FutureBuilder<String>(
      future: fetchData(),
      builder: (context, snapshot) {
        switch (snapshot.connectionState) {
          case ConnectionState.none:
            return Text('Press button to start.');
          case ConnectionState.active:
          case ConnectionState.waiting:
            return Text('Awaiting result...');
          case ConnectionState.done:
            if (snapshot.hasError)
              return Text('Error: ${snapshot.error}');
            return Text('Result: ${snapshot.data}');
        }
      },
    );
  }
}
```

