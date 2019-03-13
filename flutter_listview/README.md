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
