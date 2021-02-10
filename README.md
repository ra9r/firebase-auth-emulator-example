This is sample project that demonstracts how to connect to a Firebase auth emulator.

# Setup
Before you will be able to run you will need to install the [Firebase CLI](https://firebase.google.com/docs/cli).  

```
%> npm install -g firebase-tools
```

Next download the dependencies

```
%> npm install
```

# Running
Now here is how to run this project.  All it does is connect to the auth emulator and creates a new user.

## Running your tests as part of a CI

If you just want to run `npm test` you can start the emulator and run the tests with a single command ...
```
%> firebase emulators:exec --project test
```

**NOTE** The `--project test` can be any value but it is important to remember what you used because you will need it later.

## Running with the emulator UI
If you prefer to start the emulator and leave it running so you can also use the UI, then first run the start command like this ...
```
%> firebase emulators:start --project test
```

Then run your tests like this ...

```
%> npm test
```

If you want to use the UI simply go to http://localhost:8088/ in a browser.




# Using the emulator from your code ...
As you can see in `index.js` this is how you connect to the emulator from your code ...

```javascript
// import the firebase-admin module
const admin = require('firebase-admin')

// initialize using the same `--project` value used when starting the emulator
admin.initializeApp({ projectId: "test" })
```


Now you are free to use the `admin.auth()` api however you'd like!

# Additional Notes
The ports are very important for getting this all working.  Emulator ports are configured in the `firebase.json` file and looks like this:

```json
{
  "emulators": {
    "auth": {
      "port": 9099
    },
    "ui": {
      "enabled": true,
      "port": 8088
    }
  }
}
```

When running you need to make sure that the following environment variable is also set:

```
FIREBASE_AUTH_EMULATOR_HOST="localhost:9099"
```

**NOTE** the port used in the env variable must match the port defined in the json `emulators.auth.port` value.

**NOTE** If you run this project using `npm test` the `FIREBASE_AUTH_EMULATOR_HOST` property is already set for you.