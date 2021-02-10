This is sample project that demonstracts how to connect to a Firebase auth emulator.

# Running
Before you will be able to run the emulator, you will first need to install it.

## Install the Auth Emulator

First you will need to install the [Firebase CLI](https://firebase.google.com/docs/cli).  

> Complete documenation for how to install the emulators locally refer to the [Firebase Guides](https://firebase.google.com/docs/emulator-suite/install_and_configure).


## Start the Auth Emulator (with UI)
Once you have the emulator installed you will need to start it using this command. 
```
%> firebase emulators:start --project test
```

If you just want to run a suite a tests you can also just run it like this ...
```
%> firebase emulators:exec --project test
```

**NOTE** The `--project test` can be any value but it is important to remember what you used because you will need it later.

## Setup your connection login in your code ...

```javascript
// import the firebase-admin module
const admin = require('firebase-admin')

// initialize using the same `--project` value used when starting the emulator
admin.initializeApp({ projectId: "test" })
```


Now you are free to use the `admin.auth()` api however you'd like!