# Firebase-App-Indexing

1. Connect your app to firebase
2. Add app indexing library to your app

project level build.gradle
```
classpath 'com.google.gms:google-services:3.1.1'
```

and

```
implementation 'com.google.firebase:firebase-appindexing:11.8.0'
```
in your app level build.gradle;

3. Support links to your app content
Now that you've added firebase and the app indexing library to your app,generate intent filter for HTTP URL

```<intent-filter android:autoVerify="true">
      <action android:name="android.intent.action.VIEW" />

      <category android:name="android.intent.category.DEFAULT" />
      <category android:name="android.intent.category.BROWSABLE" />

      <data
          android:scheme="http"
          android:host="akamahesh.github.io"
          android:pathPattern="/Memoria-web" />
   </intent-filter>
```

4. Add logic to handle opening URL in your app (main Activity)
```
    Intent appLinkIntent = getIntent();
    String appLinkAction = appLinkIntent.getAction();
    Uri appLinkData = appLinkIntent.getData();
    Toast.makeTe    xt(this,"Uri "+appLinkData,Toast.LENGTH_SHORT).show();
```
> Now your app can handle your Http URL

5. Enable public content indexing
Associate your site with your app using https://developers.google.com/digital-asset-links/v1/getting-started?utm_source=studio
and build your app against API level 23 or higher for the android platform. If you don’t use HTTPS or are building against anything below API level 23, use the Google Search Console https://support.google.com/webmasters/answer/6178088?utm_source=studio to associate your site with your app.

After Google indexes your public app content, your users will be able to find it in the search results.

6. Enable personal content indexing
Create a class that extends IntentService and then add, update, or remove personal content from the on-device index. See our code samples .

7. Log user actions
Build the Action object with the title and URL of the content and the Action type. Then call both the start() and end() methods to log the action.
Insert code to log user Actions

Now Google Search can take into account the actions your users take on public and personal app content to provide improved ranking for your search results and suggestions.


> how to test it ?
1. Installing this app in your phone.
2. open http://akamahesh.herokuapp.com/app-indexing.html url in browser of your app.
3. Click on Contact Us link
4. It should open app and show url as a toast in your phone