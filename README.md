# Expo SDK38 is broken on iOS (works on Android and Web) - tested on snack

Using the simple [drawer example](https://reactnavigation.org/docs/drawer-based-navigation/). Running the app on iOS returns the following error (works on Android and Web):

```
Device: (914:881) Tried to register two views with the same name RNCSafeAreaProvider
  Evaluating module://react-native-safe-area-context.js
  Evaluating module://@react-navigation/drawer.js
  Evaluating module://App.js.js
  Loading module://App.js
```

Appears related to this bug <https://github.com/th3rdwave/react-native-safe-area-context/issues/110>

Try code on Snack: <https://snack.expo.io/@ikakara/github.com-ikakara-expo-sdk38-bug>

**Reported issue:**

<https://github.com/expo/expo/issues/9095>

## Tested with SDK37 which I'm not sure gives much insight

For SDK37, the last working version of react-native-safe-area-context is 1.0.2.

```
  "dependencies": {
    "@react-navigation/drawer": "^5.8.4",
    "@react-navigation/native": "^5.6.1",
    "logkitty": "^0.7.1",
    "expo": "37.0.8",
    "react": "^16.13.1",
    "react-dom": "^16.13.1",
    "react-native": "https://github.com/expo/react-native/archive/sdk-37.0.1.tar.gz",
    "react-native-reanimated": "~1.9.0",
    "react-native-safe-area-context": "1.0.2",
    "react-native-screens": "~2.9.0",
    "react-native-web": "~0.13.1"
  },
```

Versions more recent than 1.0.2 return the following:

```
Device: (38:287) View config not found for name RNCSafeAreaProvider.
```

Which may just be a version incompatibility.

## Expo SDK38 depends on react-native-safe-area-context@3.0.7

So I'm not sure if there's a viable workaround for SDK38 because v1.0.2 and 3.0.7 seem incompatible. Anyway, the following seems to work for the trivial example.

```
  "resolutions": {
    "logkitty": "^0.7.1",
    "react-native-safe-area-context": "1.0.2"
  },
  "dependencies": {
    "@react-navigation/drawer": "^5.8.4",
    "@react-navigation/native": "^5.6.1",
    "logkitty": "^0.7.1",
    "expo": "~38.0.8",
    "react": "^16.13.1",
    "react-dom": "^16.13.1",
    "react-native": "https://github.com/expo/react-native/archive/sdk-38.0.1.tar.gz",
    "react-native-reanimated": "~1.9.0",
    "react-native-screens": "~2.9.0",
    "react-native-web": "~0.13.1"
  },
```
