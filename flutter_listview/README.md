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

<p>Now, we need to create a class which would manage the state of the stateful widget. I’ll be calling it RandomWordsState.</p>
<pre>
class RandomWordsState extends State<RandomWords> {
  final _suggestions = <WordPair>[];

  final _biggerFont = const TextStyle(fontSize: 18.0);

  @override
  Widget build(BuildContext context) {
    return Scaffold (
      appBar: AppBar(
        title: Text('Startup Name Generator'),
      ),
      body: _buildSuggestions(),
    );
  }
}
</pre>

<p>The build method will be returning the actual widget which will be rendered on the screen. Instead of adding the scaffold in the main stateless widget, we can add it here as well and just return the entire widget as one.</p>

<p>Note, that we have added two field items, _suggestions, and _biggerFont. Adding an Underscore is just a DART convention to denote private methods and properties. We will be storing our random words to display in _suggestions and _biggerFont will be used to add styling to our text.</p>

<p>Now, we’ll create the _buildSuggestions method and add it to RandomWordsState class:</p>
<pre>
Widget _buildSuggestions() {
  return new ListView.builder(
    padding: const EdgeInsets.all(10.0),
    itemBuilder: (context, i) {
      if (i.isOdd) return Divider();

      final index = i ~/ 2;
      // If you've reached at the end of the available word pairs...
      if (index >= _suggestions.length) {
        // ...then generate 10 more and add them to the suggestions list.
        _suggestions.addAll(generateWordPairs().take(10));
      }
      return _buildRow(_suggestions[index]);
    },
  );
}
</pre>

<p>This method returns the ListView widget which will then be added to the body of the Scaffold we created earlier.

Notice that we return a divider in case “i” is odd, this is because even the dividers are treated as items in ListView, and since dividers start after the first Item (whose index is 0), the index of dividers will be odd always.

Next, we check whether more words need to be added to the list and if so, then add 10 at a time.

Now we have initialized the ListView, but how do we tell flutter the layout of the list Items.</p>

<h2>Building ListItem</h2>
<p>Now, we will create the _buildRow method which will return a widget, which is essentially a layout describing how the list items must look. You can do all sorts of things with it, but for this example, we will simply be adding a text to the row item:</p>
<pre>
Widget _buildRow(WordPair pair) {
  return new ListTile(
    title: new Text(pair.asPascalCase, style: _biggerFont),
  );
}
</pre>

<p>Here’s how your main.dart should look like at the end:</p>
<pre>
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';



void main() => runApp(MainApp());

class MainApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'My Flutter App'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {

  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
        home: new Scaffold(
          appBar: new AppBar(
            title: Text("Home"),
            textTheme: Theme.of(context).textTheme.apply(
                bodyColor: Colors.black
            ),
            backgroundColor: Colors.white,
          ),
          body: RandomWords(),
        )
    );
  }
}


class RandomWords extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return new RandomWordsState();
  }
}

class RandomWordsState extends State<RandomWords> {
  final _suggestions = <WordPair>[];

  final _biggerFont = const TextStyle(fontSize: 18.0);

  @override
  Widget build(BuildContext context) {
    return Scaffold (
      body: _buildSuggestions(),
    );
  }

  Widget _buildSuggestions() {
    return new ListView.builder(
      padding: const EdgeInsets.all(10.0),
      itemBuilder: (context, i) {
        if (i.isOdd) return Divider();

        final index = i ~/ 2;
        // If you've reached the end of the available word pairings...
        if (index >= _suggestions.length) {
          // ...then generate 10 more and add them to the suggestions list.
          _suggestions.addAll(generateWordPairs().take(10));
        }
        return _buildRow(_suggestions[index]);
      },
    );
  }

  Widget _buildRow(WordPair pair) {
    return new ListTile(
      title: new Text(pair.asPascalCase, style: _biggerFont),
    );
  }
}

</pre>
