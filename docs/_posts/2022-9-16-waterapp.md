---
title: "WaterApp - A Simple Cross-Platform App"
author: "Samuel Kriikkula"
tags: waterapp
---
Hello there, guys and gals! I really wanted to develop my own app from scratch this time. 
I decided to do thing simple and not shoot too high. This app will remind the user to drink water at
intervals decided.

## Flutter

![Flutter](https://flutter-sy.com/wp-content/uploads/2021/04/right-chev.png)

Which framework to choose is a difficult choise. My friend Rodde introduced me to Flutter.
A cross-platform UI library which is powered by Dart, the language the folks at Google developed.
I did some testing with Flutter and I gotta say I really like it!

## Getting Started
Install VSCode if not already and install The Flutter plugin.
Once installed, click Ctrl + Shirt + P and select "Flutter: New Project"

![New Project](https://i.imgur.com/yiUhSXt.png)

## Main
The starting point can be found in *lib/main.dart*
Empty the file and copy the following:
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const WaterApp());
}

class WaterApp extends StatelessWidget {
  const WaterApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text("WaterApp"),
        ),
      ),
    );
  }
}

```

Open the VSCode terminal and type `flutter run`. You should se a white background and a blue topbar with the title "WaterApp".

## Next up
Click [here](https://kriikkula.com/waterapp) for all parts.