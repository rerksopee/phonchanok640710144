import 'dart:math';

import 'package:flutter/material.dart';


void main() {
  runApp(const FunnyQuotesApp());
}

class FunnyQuotesApp extends StatelessWidget {
  const FunnyQuotesApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home:  HomePage(),
    );
  }
}
class HomePage extends StatefulWidget {
  HomePage({super.key}) ;

  @override
  State<HomePage> createState() => _HomePageState();
}


class _HomePageState extends State<HomePage> {


  static const List<String>_quoteList = [
    'การมีแฟนที่ดี คือการที่มีแฟนเป็นเรา',
    'ไม่มีหรอก "เราชนะ" มีแต่ "เราชอบนะ" เธอชอบไหม!',
    'ถ้าเขาจะรัก ตัวจริงไม่เหมือนในรูปเขาก็รัก',
    'จงเลือกอยู่กับคนที่ใช่ ใช่เลยควรอยู่คนเดียว',
    'เหมาะกับการอยู่ในวงเหล้า มากกว่าการเข้าไปอยู่ในใจใคร',
  ];

  static const List<MaterialColor> _colorsList = [
    Colors.purple,
    Colors.pink,
    Colors.cyan,
    Colors.lightGreen,
    Colors.yellow
  ];
  var _quote = _quoteList[0];
  var _color = _colorsList[0];

  void _handleClikGo (){
    var rand = Random();

    String newQuote;
    do{
      var randomIndex = rand.nextInt(_quoteList.length);
      newQuote = _quoteList[randomIndex];
    } while(newQuote == _quote);
    MaterialColor newColor;
    do{
      var randomIndex = rand.nextInt(_colorsList.length);
      newColor = _colorsList[randomIndex];
    }while(newColor == _color);

  setState(() {
    _quote = newQuote;
    _color = newColor;
  });
}

  @override

  Widget build(BuildContext context) {

    return Scaffold(
      appBar: AppBar (
          title:Text("คำคม/แคปชั่นกวนๆ"),
          backgroundColor: Colors.pink.shade100
      ),

      floatingActionButton : FloatingActionButton(

          child: Text('สุ่ม'),
          onPressed:_handleClikGo,
          backgroundColor: Colors.pink.shade200

      ),

      body: Center(

        child:  Text(

          _quote,
          style : TextStyle(
          color : _color,

            fontSize: 40,
            fontStyle: FontStyle.italic,
            fontWeight: FontWeight.bold,

          ),

        ),
      ),

    );

  }

}
