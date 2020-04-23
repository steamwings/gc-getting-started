# Getting Started: Front-end Development #

We provide three front-end clients using [NativeScript with Angular](https://docs.nativescript.org/angular):
* Single-page application (SPA) Website
* Android 
* iOS

## Environment Setup ##

*I'm considering a standardized development environment availble with [Vagrant](vagrantup.com). If you're interested in helping, say something.*

### Clone gc-ns ###

* Start with [VSCode](https://code.visualstudio.com/).
* Clone the `gc-ns` repo. You'll want to execute most command from the `green-curtain` directory.
* Once Node.js is installed, run `npm install`. (If you don't have Node.js, there are instructions at the link in the next step.)

### Follow the official setup ###

[The NativeScript Angular setup guide](https://docs.nativescript.org/angular/start/quick-setup) is pretty thorough. Follow the quick and full guide, including:
* Installing Node.js
* `npm install -g nativescript`
*  Install NativeScript Playground _and_ NativeScript Preview on any test iOS or Android devices. 

### Preview the app ##

At this point, you can try `tns preview` in the `green-curtain` directory. Scan the barcode from the NativeScript Playground app. The Preview app will act like the app and can be even closed and resumed the same way. Code changes should prompt a reload.

### Android Emulator ###

Having an emulator provides some advantages over the preview app. Follow [the {N} guide](https://docs.nativescript.org/angular/tooling/android-virtual-devices) and create an emulator for yourself.

Once one is running, try `tns run` and make sure the app starts in your emulator.

I'm not sure if the `avdmanager` CLI tool exists on Windows. I've been opening Android Studio to start the AVD Manager and start my emulator. Android Studio can be closed as soon as the play button is hit for the emulator. After the emulator starts, `tns run` is very reliable for me.

### Issues ###

You may need to follow one of the advanced setups if NativeScript's magic install script didn't work. I know I had issues on Windows, possibly because I already had Android Studio and a JDK installed.

If you run into a problem with `tns preview` or `tns run` not pushing changes or something, kill the process (Ctrl+C on Windows/Linux) and restart.

## Workflow ##

You can run `ng serve` for web, `tns run` for emulators, and `tns preview` for test devices and watch code changes update on everything at the same time.

### Debug ###

VSCode's debug option works for web and I don't know if I've tried for an emulator. I don't think it will work (out of the box) with preview.

### Unit Tests ###

*crickets chirp judgmentally*