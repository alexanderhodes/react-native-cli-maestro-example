# Example for using maestro with React Native (CLI)

In this repository we want to show how to use Maestro with React Native apps built with Expo. You can read the full article on our [blog at dev.to](). If you want check out maestro with a React Native Expo app, you can have a look at [this repository](https://github.com/alexanderhodes/react-native-expo-maestro-example), because there are some differences when launching the app with Expo.

The application is a simple sign in interface where username and password can be entered. After clicking the sign in button a success message will be displayed below the button.

<div style="display:flex;flex-direction:row">
<img src="https://raw.githubusercontent.com/alexanderhodes/react-native-cli-maestro-example/main/res/example-screenshot.png" alt="Screenshot Sign In" height="400" width="auto" style="marginRight: 16px">
<img src="https://raw.githubusercontent.com/alexanderhodes/react-native-cli-maestro-example/main/res/example-success-screenshot.png" alt="Screenshot Sign In Success" height="400" width="auto">
</div>

## Running the app

Preparing the app and installing the dependencies.

```bash
# Install dependencies
$ npm install
# Install ios pods
$ npm run ios:pods
# Start app
$ npm start
# Start ios app
$ npm run ios
# Start android app
$ npm run android
```

## Maestro tests

The tests located in `.maestro` directory are developed for running locally in your iOS simulator or Android emulator.

You can run the tests as well in the cloud. For running the tests in the cloud.

For creating new workflows you can check out the [Maestro docs](https://maestro.mobile.dev) and [Maestro studio](https://maestro.mobile.dev/getting-started/maestro-studio).

![Maestro studio](https://raw.githubusercontent.com/alexanderhodes/react-native-cli-maestro-example/main/res/maestro-studio-2.png)

### Install maestro

Before running the tests, you need to setup Maestro on your machine. On MacOS and Linux you can follow these steps. 

```bash
# install and upgrade maestro
$ curl -Ls "https://get.maestro.mobile.dev" | bash
```

Running flows on iOS Simulator requires installation of [Facebook IDB](https://fbidb.io).

```bash
$ brew tap facebook/fb
$ brew install facebook/fb/idb-companion
```

On windows you need to do further steps. A complete instruction can be found in the [Maestro docs](https://maestro.mobile.dev/getting-started/installing-maestro).

You can check if maestro is installed by checking the version. It should print the version number, e.g. 1.17.

```bash
$ maestro -v
```

### Running workflows

The workflows can be started with the Maestro CLI. Below you can find some commands for starting a single or multiple tests.

```bash
# run single test
$ maestro test .maestro/sign-in-flow.yaml
# run single test with external parameters
$ maestro test -e USERNAME="Test User" -e PASSWORD=Test123456 .maestro/sign-in-flow-external-parameters.yaml
# running every test in directory
$ maestro test -e USERNAME="Test User" -e PASSWORD=Test123456 .maestro
```

Furthermore, it's possible to create test reports like this:

```xml
<?xml version='1.0' encoding='UTF-8'?>
<testsuites>
  <testsuite name="Test Suite" device="iPhone 14 Plus - iOS 16.1 - E7F8022E-939F-4165-B887-F342740BFCE6" tests="5" failures="0">
    <testcase id="sign-in-flow" name="sign-in-flow"/>
    <testcase id="sign-in-flow-with-subflow" name="sign-in-flow-with-subflow"/>
    <testcase id="sign-in-flow-constants" name="sign-in-flow-constants"/>
    <testcase id="sign-in-flow-testid" name="sign-in-flow-testid"/>
    <testcase id="sign-in-flow-external-parameters" name="sign-in-flow-external-parameters"/>
  </testsuite>
</testsuites>
```

You can run these tests with this command:

```bash
$ maestro test --format junit --output results.xml -e USERNAME="Test User" -e PASSWORD="Test123456" .maestro
```

### Creating video records

In addition to running tests, you can record them for getting a screen record.

```bash
# start video recording
$ maestro record .maestro/sign-in-flow-testid.yaml
```

![Maestro record](https://raw.githubusercontent.com/alexanderhodes/react-native-cli-maestro-example/main/res/maestro-record.png)

## Tips and tricks

In our article we described some tips and tricks, like usage of `testID`, parameters and constants, recording workflows and nested flows. 

## Further resources

- [Maestro Documentation](https://maestro.mobile.dev)
- [Maestro GitHub Repository](https://github.com/mobile-dev-inc/maestro)
- [Maestro Cloud Documentation](https://cloud.mobile.dev)
- [Example Repository for React Native Expo App](https://github.com/alexanderhodes/react-native-expo-maestro-example)
