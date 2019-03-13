# Awesome_Flutter_App

<img src="https://cdn-images-1.medium.com/max/1200/1*wKCxZurgsSr94Ozr4aXLNQ.png" width="100%" height="auto">
<h1>What is Flutter?</h1>
<p>Flutter is google’s mobile app SDK (software development kit) for making native interfaces for both Android and iOS devices using a single code base. So we write code once and then we can deploy on both the different software devices.</p>

<p>The whole flutter UI and UX features are in correspondence to the Google’s Material Design Concept. Each UI element on the app will be categorised as widget’s.</p>
<ul>
  <li>Multi Platform - Android & IOS</li>
  <li><b>High performance & low latency</b></li>
  <li>DART as main language</li>
  <li>open-source / github</li>
  <li>"flutter" frame render / rapid variation of signal paramenters</li>
  <li>not a monolith structure - (access to,all control over,all layers of the system)</li>
  <li>Custom ui rendering engine</li>
</ul>

<h2>Installation on MACOS</h2>
<p>If you don’t have Git installed in your system, then please do before downloading the Flutter Bundle from flutter SDK and make sure you have Xcode and Android Studio installed as well.</p>
<ul>
  <li>Now we can download the flutter SDK and unzip in any location you prefer.</li>
  <li>Now we need to add the flutters path in the terminal. First change directory (cd “your flutter path”) and then type - export PATH=/”your flutter folder path”/bin:$PATH. To verify the location of path type - echo $PATH.</li>
  <li>To check if you are all set or need to download or update any dependancy, type - flutter doctor. This will give you a summary on which software/dependency needs to be downloaded. If anything needs to be downloaded or setup, the flutter doctor will give you a detailed instruction on how to setup. Once all the software/dependencies have been setup, rerun - flutter doctor and if all the dependencies are configured, we can move to the next step.</li>
  <li>Now we can open Android Studio (make sure you have the latest IDE installed or 3.0>) and the welcome window pops up and on the right bottom click on Configure -> Plugin ->Search and Install Dart and Flutter plugin. If you don’t find the welcome window then you can download the plugin from Android Studio -> preferences ->plugin. Restart Android Studio and now you will be able to see an option called start flutter project.</li>
  <li>Click on start flutter project and then select Flutter Application from the first window and click next. Give a project name and then for the flutter SDK path give the git repo path and click next.</li>
  <li>Now choose a company domain and check the checkboxes if you need any Kotlin or Swift support and click finish. Now a dummy project will be setup and to run this project in both Android and iOS simulator, go to devices and open an iOS simulator. If you don’t have an Android Simulator then go to Tools -> AVD Manager -> Create Virtual Device -> Select a device -> Select a API level -> Finish.</li>
  <li>Now you can select any of the device and run this dummy program.</li>
<li>To run both the emulators at the same time you can use the Terminal. First go to the project location (cd /project location) and then type - flutter run -d all. Now you can hot reload your app on the fly, press “r” or to restart the app entirely on both simulators, press “R”.</li>
</ul>
