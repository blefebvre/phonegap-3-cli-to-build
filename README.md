phonegap-3-cli-to-build
=======================

An app detailing the steps I took to create an app via the CLI and build it on PhoneGap build. I followed [these instructions](http://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html#The%20Command-line%20Interface).

## Environment

Install PhoneGap via npm:

	npm install cordova -g

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



