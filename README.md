PhoneGap 3.0 - CLI to build
===========================

This repo details the steps I took to create an app via the CLI, add a plugin, and build it remotely on PhoneGap build. I followed a post from [@cfjedimaster](http://www.raymondcamden.com/index.cfm/2013/7/19/PhoneGap-30-Released--Things-You-Should-Know) and the PhoneGap CLI help/readme. I avoided [these cordova docs](http://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html#The%20Command-line%20Interface).

## Environment

Install PhoneGap via npm:

	npm install -g phonegap

Install ios-sim via homebrew:

	brew install ios-sim

## App creation

Create the app:

	phonegap create kick-the-tires --id "com.brucelefebvre.kick-the-tires" --name "kick-the-tires"

Install the Xcode command line tools in order to build for iOS (see [these docs](http://docs.phonegap.com/en/3.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide)).

Add the File plugin:

	phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-file.git

Sanity check:

	phonegap local plugin list

... should output: [phonegap] org.apache.cordova.core.file

## Build

Build and run your app in the iOS sim:

	phonegap run ios

Your app should appear in the iOS sim, with "DEVICE IS READY" in green.

## Plugin use

Ensure the plugin is functional. Replace the onDeviceReady (in www/js/index.js) function with:

	onDeviceReady: function() {
		app.receivedEvent('deviceready');
		// Try out the File API
		window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, 
			function(fileSystem) {
				// File success
				alert(fileSystem.root.name);
			},
			function(evt) {
				// File fail
				alert(evt.target.error.code);
			}
		);
	},

## Build remotely with PhoneGap build

Login using your [PhoneGap build](https://build.phonegap.com) credentials:

	phonegap remote login

Build and run:

	phonegap remote run ios

Note: You need to upload a certificate and provisioning profile to PhoneGap build to build & run the app on a device.

Scan the QR code with your device to install.

The QR code printed to the console did not work for me, but the [online version](https://build.phonegap.com/apps) did.

## Resources

[PhoneGap 3.0 Released - Things You Should Know](http://www.raymondcamden.com/index.cfm/2013/7/19/PhoneGap-30-Released--Things-You-Should-Know) - Raymond Camden
[PhoneGap and PhoneGap/Build command-line interface](https://github.com/mwbrooks/phonegap-cli) - Github