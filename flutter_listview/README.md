# flutter_listview

Implementation of ListView in Flutter

## Getting Started
<p>We’ll start by creating an empty project. Click on File -> New Flutter Project, and create a flutter application.</p>
<p>You’ll notice some code in the main.dart file, delete all of it. We’ll be creating a new app from scratch.</p>
<p>Let’s start by adding an external package that we will be using in the project. Expand the project folder in the left-hand project pane. You’ll find a file named pubspec.yaml, think of this as the gradle file for flutter. This is where you add your dependencies for flutter projects.</p>

<p>We’ll be adding a library to generate random words to display in our listview. Copy and paste the code below.</p>

<pre>
english_words: ^3.1.0
</pre>

<h2>Adding a stateless widget</h2>
<p>I hope you’ve deleted all the code in main.dart file as we would be starting from scratch. First, we need to add a stateless widget, which can be thought of as the container of our app. This is the container that would never change. All the widgets added henceforth will be its children or grand-children and so on.</p>

<p>Import the material library and the library to generate random words.</p>

<pre>
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';
</pre>

<p>Let’s initiate the app launch in the main method:</p>
<pre>
void main() => runApp(new MyApp());
</pre>
<p>Finally, we create the stateless widget MyApp as below:</p>
<pre>
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: "List in Flutter",
      home: new Scaffold(
        appBar: new AppBar(
          title: Text("List"),
        ),
        body: RandomWords(),
      ),
    );
  }
}
</pre>

<p>To create a Stateless widget all you need to do is extend the StatelessWidget class and override build method. Build returns a Widget, in our case which is MaterialApp, as we are using material design.<p>

<p>Next, come the properties of the MaterialApp such as the title, it’s content (home), theme, locales etc., in our case we will be changing the title and adding a body to our material app.</p>

<p>For the home property, we return a Scaffold which is a container that lets us add material design elements such as Snackbars, sliding drawer, ActionBar etc. Using Scaffold, we will add an action bar to our app as shown above.</p>

<p>Next step is to build the body of the <b>Scaffold.</b></p>

<h2>Building the body</h2>
<p>For the body of our app, we will be adding a ListView which will be a stateless widget. Although we won’t be interacting with the listview items right now, it is a good idea to make them stateful as in most use cases you would associate a click action on the list items.</p>

<p>Creating a stateful widget is as simple as extending the StatefulWidget class:</p>

<pre>
class RandomWords extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return new RandomWordsState();
  }
}
</pre>
