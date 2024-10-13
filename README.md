# Holbegram (or Atlasgram) Final Flutter Project

Task Link: https://intranet.atlasschool.com/projects/2918

### Introduction

Developing a mobile application using the technology of Flutter and Dart frameworks. Traditionally, Android relies on Java, while iOS uses Objective-C or Swift, requiring developers to manage two codebases if they wish to support both platforms. 

Enter **Flutter**: a powerful and streamlined framework that utilizes Dart. Flutter simplifies the process by allowing us to write a single codebase for both platforms, rendering directly onto the OS's canvas for high performance and smooth user experience.

### Getting Started

Before diving into the code, I recommend checking out the following resources to set a solid foundation and enhance your understanding of Flutter and its ecosystem:

- [Dart - Cheatsheet](https://dart.dev/resources/dart-cheatsheet)
- [FlutterFire Overview](https://firebase.flutter.dev/docs/overview/)
- [Getting Started with Firebase on Flutter](https://www.youtube.com/watch?v=EXp0gq9kGxI&t=780s&ab_channel=Firebase)
- [Get Started with Firebase Authentication on Flutter](https://firebase.flutter.dev/docs/auth/start/)
- [Cloud Storage on Flutter](https://firebase.google.com/docs/storage/flutter/start)
- [Layouts in Flutter](https://docs.flutter.dev/ui/layout)
- [Introduction to Widgets](https://docs.flutter.dev/ui)
- [Firebase Storage Load and Display Images | Flutter](https://www.youtube.com/watch?v=AQQJJw3zOqs&ab_channel=dbestech)
- [Every Flutter Widget Explained](https://www.youtube.com/watch?v=kj_tldMmu4w)

#### Dependencies

Ensure these dependencies are included in your project:

- [Firebase Database Plugin for Flutter](https://pub.dev/packages/firebase_database)
- [Firebase Auth for Flutter](https://pub.dev/packages/firebase_auth)
- [Cloud Firestore Plugin for Flutter](https://pub.dev/packages/cloud_firestore)
- [Cloud Storage for Flutter](https://pub.dev/packages/firebase_storage)
- [Cupertino Icons](https://pub.dev/packages/cupertino_icons)
- [Image Picker plugin for Flutter](https://pub.dev/packages/image_picker)
- [BottomNavyBar](https://pub.dev/packages/bottom_navy_bar)
- [provider](https://pub.dev/packages/provider)
- [Uuid](https://pub.dev/packages/uuid)
- [Cached network image](https://pub.dev/packages/flutter_staggered_grid_view)
- [Flutter Pull To Refresh](https://pub.dev/packages/pull_to_refresh#flutter_pulltorefresh)

### Project Setup

To kick off your project, follow these steps in your command-line tool:

```bash
flutter create holbegram
cd holbegram
flutter run
```

### Setting Up Firebase

For the backend, we will utilize Firebase—a comprehensive BaaS platform that supports features like a real-time database, cloud storage, authentication, and much more.

#### Steps to Integrate Firebase:

1. Visit [Firebase's website](https://firebase.google.com/) and create an account.
2. Navigate to the [Firebase Console](https://console.firebase.google.com/) and click 'Add Project'.
3. Follow the on-screen instructions to set up a new project called `holbegram`.

### Let’s Embark on This Journey

First, we are going to build a fire_base app called `holbegram`:

![image](https://github.com/user-attachments/assets/dba78964-8d42-4ac8-b5a1-1a4d61a3e9dd)

Second Disable Google Analytics for this project:

![image](https://github.com/user-attachments/assets/a332bdf7-b2d1-4fb3-a161-66459bc09ac3)

### Authentication

Click on Enable the Authentication: Enable the Email/Password:

![image](https://github.com/user-attachments/assets/cf466243-d5ac-487b-868b-3387a289562c)

![image](https://github.com/user-attachments/assets/c79ce4d9-a32c-4beb-8c27-6b584516c41e)

![image](https://github.com/user-attachments/assets/bf2dd149-412e-42d2-b6ad-31b9b30547f3)

### Database

Now you are going to move to the next task which is creating a database.

To do that follow the following steps:

1- Go to Firestore Database then click on Create Database.

2- Choose “start in text mode”

![image](https://github.com/user-attachments/assets/3ad75a88-1430-48f4-b9c4-0d3d82722780)

3- choose the location that is close to you.

![image](https://github.com/user-attachments/assets/f291fbed-bb27-49b3-a9aa-5d28edab994c)

4- Go to rules:

![image](https://github.com/user-attachments/assets/a5c59f94-befc-48fa-88bd-332f21446808)

5- Delete the rules so anyone can read and write to a database:

![image](https://github.com/user-attachments/assets/b6143f43-9100-4780-82f2-d6ed3c3f5e7e)

Finally, press Publish

### Adding Firebase to our App

#### So now let’s add Firebase to our app:

#### If you want to use Android Follow the Android Support

#### If you want to work with iOS follow the iOS Support

# Adding Android support

Registering the App

In order to add Android support to our Flutter application, select the Android logo from the dashboard. This brings us to the following screen:

![image](https://github.com/user-attachments/assets/0a9b6053-7553-4517-8fb9-b19015a51868)

The most important thing here is to match up the Android package name that you choose here with the one inside of our application.

The structure consists of at least two segments. A common pattern is to use a domain name, a company name, and the application name:

`com.example.holbegram`

Once you’ve decided on a name, open `android/app/build.gradle` in your code editor and update the applicationId to match the `Android package name`:

Example of File `android/app/build.gradle`

`...
defaultConfig {
    // TODO: Specify your own unique Application ID (https://developer.android.com/studio/build/application-id.html).
    applicationId 'com.example.holbegram'
    ...
}
...`

You can skip the app nickname and debug signing keys at this stage. Select Register app to continue.

### Downloading the Config File

The next step is to add the `Firebase configuration` file into our Flutter project. This is important as it contains the API keys and other critical information for Firebase to use.

Select Download `google-services.json` from this page:

![image](https://github.com/user-attachments/assets/d2ea26d9-ead1-485b-bad7-3ce2a5286481)

Next, move the `google-services.json` file to the `android/app` directory within the Flutter project.

### Adding the Firebase SDK

We’ll now need to update our Gradle configuration to include the Google Services plugin.

Open `android/build.gradle` in your code editor and modify it to include the following:

```gradle
buildscript {
  repositories {
    // Ensure Google's Maven repository is included
    google()  // Google's Maven repository
  }
  dependencies {
    ...
    // Include the Google Services classpath
    classpath 'com.google.gms:google-services:4.3.13'  // Check for the latest version
  }
}

allprojects {
  repositories {
    // Make sure Google's Maven repository is here
    google()  
    ...
  }
}
```

### Step 2: Update App-level `build.gradle`

Open the `build.gradle` file located at `android/app/build.gradle` and make the following updates:

```gradle
apply plugin: 'com.android.application'
// Apply the Google Services plugin
apply plugin: 'com.google.gms.google-services'

dependencies {
  // Import the Firebase Bill of Materials (BoM)
  implementation platform('com.google.firebase:firebase-bom:30.2.0')

  // Optionally, add the dependencies for any other desired Firebase products
  // See: https://firebase.google.com/docs/android/setup#available-libraries
}
```

### Step 3: Sync and Run Your Project

- **Sync Your Project with Gradle**: Ensure all dependencies are properly downloaded and integrated by syncing your project with Gradle files in your IDE.
- **Run Your Application**: Launch your app on an Android device or emulator to verify the integration. Check your Firebase console for any logs or data to confirm that the setup was successful.

### Additional Resources

For further details on Firebase features and additional library integrations, refer to the official Firebase documentation:
- [Firebase Android Setup](https://firebase.google.com/docs/android/setup)
- [Available Firebase Libraries](https://firebase.google.com/docs/android/setup#available-libraries)

From here, run your application on an Android device or simulator. If everything has worked correctly, you should get the following message in the dashboard:

![image](https://github.com/user-attachments/assets/41f4c350-c6df-482b-9cdf-54cf73a90daf)

### Adding iOS support


In order to add Firebase support for iOS, we have to follow a similar set of instructions.

Head back over to the dashboard and select Add app and then iOS icon to be navigated to the setup process.

Registering an App

You Should have `Xcode` installed in your PC:

Once again, we’ll need to add an “iOS Bundle ID”. It is possible to use the “Android package name” for consistency:


![image](https://github.com/user-attachments/assets/8ab32827-0a09-4e6f-af3b-29e243f273b2)

You’ll then need to make sure this matches up by opening the iOS folder up in `Xcode`

![image](https://github.com/user-attachments/assets/31734d60-5127-46ca-99c4-ef84bc0d622b)

- #### General

![image](https://github.com/user-attachments/assets/dc8c8642-d54c-4c48-baa1-80ee8524f40f)

Now go back to your firebase and add the iOS Bundle ID
after that Download the configuration file.

#### Downloading the Config File

Drag and Drop the file `GoogleService-Info.plist` and move this into the root of your `Xcode` project within `Runner`:

![image](https://github.com/user-attachments/assets/7d84782e-f010-4813-9fd1-45297686815a)

![image](https://github.com/user-attachments/assets/9384bf98-e727-456b-8206-c49571becf34)

#### Be sure to move this file within Xcode to create the proper file references.


Task Link: https://intranet.atlasschool.com/projects/2918





