# uas_pemograman_mobile
## Aplikasi Flutter Dengan API: Booking KAI


| #               | Biodata            |
| --------------- | -----------------  |
| **Nama**        | Modesta Liunesi    |
| **NIM**         | 312110142          |
| **Kelas**       | TI.21.A1           |
| **Mata Kuliah** | Pemrograman Mobile |

<br>



## Hasil
(asset/hasil_1.png)
<br>

(asset/hasil_2.png)

## Isi dari program

* main.dart
```dart
import 'dart:convert';
import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'API Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  List<dynamic> stations = [];

  Future<void> fetchData() async {
    Uri url = Uri.parse('https://booking.kai.id/api/stations2');
    http.Response response = await http.get(url);

    if (response.statusCode == 200) {
      setState(() {
        stations = jsonDecode(response.body);
      });
    } else {
      print('Request failed with status: ${response.statusCode}.');
    }
  }

  @override
  void initState() {
    super.initState();
    fetchData();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('312110142-Modesta Liunesi'),
      ),
      body: ListView.builder(
        itemCount: stations.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(stations[index]['name']),
            subtitle: Text(stations[index]['city']),
          );
        },
      ),
    );
  }
}

```
<br>

* widget_test.dart
```dart
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';
import 'package:uas_flutter/main.dart';

void main() {
  testWidgets('Counter increments smoke test', (WidgetTester tester) async {
    // Build our app and trigger a frame.
    await tester.pumpWidget(MyApp());

    // Verify that our counter starts at 0.
    expect(find.text('0'), findsOneWidget);
    expect(find.text('1'), findsNothing);

    // Tap the '+' icon and trigger a frame.
    await tester.tap(find.byIcon(Icons.add));
    await tester.pump();

    // Verify that our counter has incremented.
    expect(find.text('0'), findsNothing);
    expect(find.text('1'), findsOneWidget);
  });
}

<br>

* pubspec.yaml
```yaml
dependencies:
  flutter:
    sdk: flutter
  http: ^0.13.4
```

##Thank You!
