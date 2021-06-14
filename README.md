# simpleAppOpener
This is a sample project of an android apps that can open another apps within its local storage. Make sure you input your app package name instead of app name. This app will only work if user input the apps package name (somethings like com.tinder, com.instagram.android , etc) and not the app name (something like Tinder, Instagram wont work)

## Deep Dive
Take a look at `startNewActivity()` methods. It is the backbone of this app. 

```

        String packageName = txtPackage.getText().toString();
        Intent intent = context.getPackageManager().getLaunchIntentForPackage(packageName);
        if (intent != null) {
            intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
            context.startActivity(intent);
        } else {
            intent = new Intent(Intent.ACTION_VIEW);
            intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
            intent.setData(Uri.parse("market://details?id=" + packageName));
            context.startActivity(intent);
        }
    
```

First i try to get app package name which is inputted at textbox. Then i will create an `Intent` based on package name. After the intent created and not null, I will launch the apps using `context.StartActivity(intent)`. Otherwise, i will launch play store with predefined url set at `intent.setData(Uri.parse("market://details?id=" + packageName))`
