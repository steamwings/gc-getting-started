# Getting Started: Front-end Development #

We provide three front-end clients using [NativeScript with Angular](https://docs.nativescript.org/angular):
* Single-page application (SPA) Website
* Android 
* iOS

## Environment Setup ##
<a name="setup"></a>

*I'm considering a standardized development environment availble with [Vagrant](vagrantup.com). If you're interested in helping, say something.*

### Clone gc-ns ###

* Start with [VSCode](https://code.visualstudio.com/).
* Clone the `gc-ns` repo. Note that you'll want to execute most commands from the `green-curtain` directory, where the Angular/NS app is actually located.
* Once Node.js is installed, run `npm install`. (If you don't have Node.js, see the next step.)

### Follow the official setup ###

You may want to reference [the NativeScript Angular setup guide](https://docs.nativescript.org/angular/start/quick-setup). It includes:
* Installing Node.js
* `npm install -g nativescript`
*  Install NativeScript Playground _and_ NativeScript Preview on any iOS or Android device you want to use for testing. 

We've had issues with [their setup for Windows](https://docs.nativescript.org/angular/start/ns-setup-win). See [Android emulator](#android-emulator).

Run `tns doctor` to verify your configuration.

### Preview the app ##
<a name="preview-app"></a>

At this point, you can try `tns preview` in the `green-curtain` directory. Scan the barcode from the NativeScript Playground app. The Preview app will act like the app and can be even closed and resumed the same way. Code changes should prompt a reload.

### Android Emulator ### 
<a name="android-emulator"></a>

Having an emulator provides some advantages over the preview app. The easiest way to install is to just install Android Studio, but you may want to reference [the {N} guide](https://docs.nativescript.org/angular/tooling/android-virtual-devices).

The command `avdmanager list avd` should list your android virtual devices, including the names you need to start them.

You can start one with `emulator -avd <name> -gpu host`. The `-gpu` argument is recommended, but not required. I recommend configuring [emulator acceleration](https://developer.android.com/studio/run/emulator-acceleration), but note that the process is different for Intel and AMD processors.

If you've read the platform-specific details below and `emulator` still won't work for you, you can always manually launch from Android Studio:
1. Find AVD Manager. (From the "Welcome to Android Studio" launcher, you can hit the arrow by **Configure**.)
2. Find the green play button to launch a virtual device.

Once an android virtual device is running, try `tns run` from the `green-curtain` directory and the app be launched in the emulator.

#### On Windows ####
The [NativeScript setup](https://docs.nativescript.org/angular/start/ns-setup-win#setup-steps) doesn't seem to configure the Android CLI tools completely. (Also note that if you use it and also Android Studio, you'll probably also end up with two JDKs.)

The difficult part seems to be configuring the Android CLI path variables. If the emulator command isn't working for you, try these steps:
1. Search "path" in Windows search. (Just hit the Windows key and start typing.) Hit **Edit the system environment variables**.
2. Go to **Environment Variables**.
3. Under **System variables**, make sure that `ANDROID_HOME` is set to your SDK location (mine is `C:\Android\android-sdk`). 
4. Find `Path` and hit **Edit...**.
5. Make sure you have entries in the following order:
- `<your-sdk-path>\emulator`
- `<your-sdk-path>\tools`
- `<your-sdk-path>\platform-tools`
- `<your-sdk-path>\tools\bin`

### Issues ###
<a name="issues"></a>

You may need to follow one of the advanced setups if NativeScript's magic install script didn't work. I know I had issues on Windows, possibly because I already had Android Studio and a JDK installed.

If you run into a problem with `tns preview` or `tns run` not pushing changes or something, kill the process (Ctrl+C on Windows/Linux) and restart.

## Workflow ##
<a name="workflow"></a>

You can run `ng serve` for web, `tns run` for emulators, and `tns preview` for test devices and watch code changes update on everything at the same time.

### Debug ###

VSCode's debug option works for web and I don't know if I've tried for an emulator. I don't think it will work (out of the box) with preview.

### VSCode tasks ###
See [description in the main readme](readme.md#tasks).

Sample `tasks.json`:
```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "serve",
            "type": "shell",
            "command": "cd green-curtain; ng serve",
            "presentation": {
                "reveal": "always",
                "panel": "new",
            },
            "runOptions": {
                "runOn": "folderOpen"
            }
        },
        {
            "label": "Android emulator",
            "type": "shell",
            "command": "emulator -avd Nexus_5X_API_29_x86 -gpu host",
            "presentation": {
                "reveal": "always",
                "panel": "new",
            },
            "runOptions": {
                "runOn": "folderOpen"
            }
        }
    ]
}
```

### Unit Tests ###

*crickets chirp judgmentally*