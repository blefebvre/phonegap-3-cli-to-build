phonegap-3-cli-to-build
=======================

An app detailing the steps I took to create an app via the CLI and build it on PhoneGap build. I followed [these instructions](http://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html#The%20Command-line%20Interface).

## Environment

Install PhoneGap via npm:

	npm install -g cordova

Install ios-sim via homebrew:

	brew install ios-sim

## App creation

Create the app:

	cordova create kick-the-tires "com.brucelefebvre" "kick the tires"

Install the Xcode command line tools to build for iOS (see [these docs](http://docs.phonegap.com/en/3.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide)).

Add the iOS platform:

	cd kick-the-tires/
	cordova platform add ios

Sanity check:

	cordova platforms ls

... should output: [ 'ios' ]

## Build

Build your app for iOS:

	cordova build ios

And open it up in the simulator:

	cordova emulate ios

## Add a plugin

I'll add the File plugin:

	cordova plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-file.git

Check:

	cordova plugin ls

... should output: [ 'org.apache.cordova.core.file' ]

## Build remotely with PhoneGap build

You will need the PhoneGap CLI for this (details on its usage were [found here](https://github.com/mwbrooks/phonegap-cli)):
	
	npm install -g phonegap

Login using your [PhoneGap build](https://build.phonegap.com) credentials:

	phonegap remote login

Build and run:

	phonegap remote run ios

Note: You need to upload a certificate and provisioning profile to PhoneGap build to run the app on a device.

Scan the QRcode with your device to install.

