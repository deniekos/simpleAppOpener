# simpleAppOpener
This is a sample project of an android apps that can open another apps within its local storage. Make sure you input your app package name instead of app name.
The main method of the apps is startNewActivity(Context). It will attach the app package name into intent using getPackageManager and launch the intent which
attached to inputted package name.
