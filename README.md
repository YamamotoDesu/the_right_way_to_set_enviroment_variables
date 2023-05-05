# the_right_way_to_set_enviroment_variables
https://itnext.io/secure-your-flutter-project-the-right-way-to-set-environment-variables-with-compile-time-variables-67c3163ff9f4

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

# ☑️ Dart define
```
flutter run --dart-define=baseUrl=https://github.com/mastersam07
```

# ✅ Dart define from file
```
flutter run --dart-define-from-file=config.json
```

## Android
config.json
```json
{
 "APP_NAME": "batcave",
 "APP_SUFFIX": ".dev",
 "MAPS_API_KEY": "someKeyString"
}
```

AndroidManifest.xml
```xml
android:label="@string/app_name"
<meta-data android:name="com.google.android.geo.API_KEY"
            android:value="@string/googleMapApiKey"/>
```

build.grale
```gradle
def envVariables = [
    APP_NAME: project.hasProperty('APP_NAME')
            ? APP_NAME
            : 'batcave',
    APP_SUFFIX: project.hasProperty('APP_SUFFIX')
            ? APP_SUFFIX
            : null,
    MAPS_API_KEY: project.hasProperty('MAPS_API_KEY')
            ? MAPS_API_KEY
            : "someString",
];

    defaultConfig {
          applicationIdSuffix envVariables.APP_SUFFIX
          resValue "string", "app_name", envVariables.APP_NAME
          resValue "string", "googleMapAqpiKey", envVariables.MAPS_API_KEY
    }
```


## iOS
info.plist
```
	<key>CFBundleIdentifier</key>
	<string>$(PRODUCT_BUNDLE_IDENTIFIER)$(APP_SUFFIX)</string>
 <key>CFBundleName</key>
	<string>$(APP_NAME)</string>
```

