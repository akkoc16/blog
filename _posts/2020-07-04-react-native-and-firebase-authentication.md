---
date: 2020-07-04
layout: code
title: React-Native and Firebase Authentication
subtitle: 'Firebase Authentication'
description: >-
image: >-
  https://miro.medium.com/max/1400/1*SzrSsS1stZQ7ipYObndbAw.png
optimized_image: >-
  https://miro.medium.com/max/1400/1*SzrSsS1stZQ7ipYObndbAw.png
category: tech
tags:
  - react-native
  - software development
  - firebase authentication
author: mehmetenverakkoc
paginate: true
---
<strong>React-Native and Firebase Authentication</strong>

Hi, I’m Enver. In this article, I will talk about general steps on how to do user authentication with firebase while developing a mobile application in React-Native.

Firebase is one of the free platforms that Google offers to users. As an example of its general-purpose, you have developed applications on any platform. You can create a database for your application with Firebase or you can perform user authentication operations. In addition to these, it provides many services such as Cloud Firestore, Hosting, and Cloud Storage. We will perform authentication steps using email and password.

<strong>Create a Project and Connect with Your App</strong>

First, we need to create a project after logging into the Google Firebase Console. After creating a project, we choose a platform (iOS / Android / Web) for the application that we will develop from the application adding screen. After choosing the platform, you will see a page to connect your application to Firebase. On this page, it will be asking us to enter our Android package name first (Since I created the project as Android, this step may proceed differently for iOS.). You can find your Android package name in the AndroidManifest.xml file in the app/src/main directory. Then, you can give a nickname for your app. Finally, some Google services need to generate a key for your app. Therefore, you need to enter your special SHA-1 signing certificate. <a href="https://developers.google.com/android/guides/client-auth">You can examine the information about how to get your certificate here.</a>

You can examine all of these steps here.

<img src="https://miro.medium.com/max/1248/1*9bJaSDLItgh4oQxUUWkxnA.jpeg"/>

<img src="https://miro.medium.com/max/1400/1*toei_GXDjM4yWyrWs-XQ3Q.jpeg"/>

<img src="https://miro.medium.com/max/1400/1*sC_0QMEEKy8NkHGnBuLW4w.jpeg"/>

<img src="https://miro.medium.com/max/1400/1*FuaMNyxqN3IdeClUf4Hz_g.jpeg"/>

After all these steps, we save the application and place the google-services.json file in the android/app directory to connect the firebase with our application.

<img src="https://miro.medium.com/max/1230/1*wXIcskSm-RPwa5dqYnsKnw.jpeg"/>

Here are some pieces of code that we need to add to our application.

In the project directory, we added “classpath‘ com.google.gms: google-services: 4.2.0 “ under dependencies in the android/build.gradle file.

```yaml
dependicies {
  classpath('com.google.gms:google-services:4.2.0')
  classpath('com.android.tools.build:gradle:3.5.2')}
```

Finally, we added apply plugin: ‘com.google.gms.google-services’ to the last line of the build.gradle file in the android/app directory. With these steps, we activated google services in our application.

```yaml
apply plugin: 'com.google.gms.google-services'
```

*<strong>Note:</strong> After all these steps, once you run your application while connected to the internet, it must be connected to Firebase. If you have any problems, perform the above steps correctly again.*

<strong>React-Native Packages</strong>

To use Firebase features, we need to download some packages and import them into our code.

First, we should <a href="https://rnfirebase.io">install the React Native Firebase “app” module to the root of your React Native project with NPM or Yarn:</a>

*Using npm*
<strong>npm install --save @react-native-firebase/app</strong>

*Using Yarn*
<strong>yarn add @react-native-firebase/app</strong>

Next, we have to install the packages below so that we can use the authentication module.

*Install the authentication module*
<strong>yarn add @react-native-firebase/auth</strong>

*If you're developing your app using iOS, run this command*
<strong>cd ios/ && pod install</strong>

Finally, before we start writing code, let’s go to the Google Firebase Console and enable Sign-In method from the authentication section as Email/Password.

<img src="https://miro.medium.com/max/1400/1*EHa3Wh_JQhN5VEWCIrIEvw.jpeg"/>

<img src="https://miro.medium.com/max/1400/1*RfdW2CpQZAuOMs8rWQqLhg.jpeg"/>

<strong>Login and Sign-Up Pages</strong>

Now we can use Firebase Authentication in our application. For this, I share the Login and Sign-up pages that I created earlier.

<strong>Login Page</strong>

Here we imported the firebase authentication module and enabled an existing user to login to the application with the signInWithEmailAndPassword method. We have done this in the onLoginClick structure to make this process happen when the user presses the login button.


<script src="https://gist.github.com/akkoc16/166eba34c726c3b4bf045d772b31767d.js"></script>

<img src="https://miro.medium.com/max/664/1*vE1cFdwSeDD5Tm2TLjLnJQ.jpeg"/>

<strong>SignUp Page</strong>

Here we imported the firebase authentication module and enabled a new user to sign-up to the application with the createUserWithEmailAndPassword method. We have done this in the saveUser structure to make this process happen when the user presses the save button.

<script src="https://gist.github.com/akkoc16/1c650d038f2f66951a5209b74cf94b40.js"></script>

<img src="https://miro.medium.com/max/666/1*6ZZWLsYGXOHuv3YywY0wKQ.jpeg"/>

In general, we perform user authentication with Firebase in this way. You can examine the above code structures in detail and make changes.

*There are different packages that I use in the sample code pieces. Don’t be confused by these!*

Thanks for reading!