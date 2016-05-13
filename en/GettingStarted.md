# Getting Started
Hotload is a cloud service that enables Cordova and React Native developers to deploy mobile app updates directly to their users’ devices. It works by acting as a central repository that developers can publish certain updates to (e.g. JS, HTML, CSS and image changes), and that apps can query for updates from (using our provided client SDKs). This allows you to have a more deterministic and direct engagement model with your end-users, while addressing bugs and/or adding small features that don’t require you to re-build a binary and/or re-distribute it through any public app stores.

## 1. Install the Hotload CLI

You manage your Hotload account using our NodeJS-based CLI. To install it, open a command prompt or terminal, and type npm 

**install -g hotload-cli**

**Note:** On OSX and Linux, you may need to prefix this command with sudo

## 2. Create a Hotload account

Before you can release any updates, you first need to create a Hotload account. To do this, simply type the following command via the CLI and authenticate with your GitHub

**hotlaod register**

## 3. Register your app with the service

In order to let the service know about your app, simply register it using a recognizable name. For example,

**hotlaod app add MyApp**

## 4. Hotload-ify your app
Add the appropriate Hotload client SDKs to your app, and configure them to query for updates against the app deployment created above. The following provide details on how to do this for each unique app type:

* React Native


## 5. Release an app update
After making changes to your app’s code or assets, push the update to your staging environment by using the CLI command which corresponds to the app type you are building for React Native, and specifies the name of your Hotload app and the platform that your update is targetting (iOS or Android).

### React Native
Run the release-react comand in the Hotload CLI, which will handle bundling your JavaScript and asset files and releasing the update to the Hotload server. As follow:

**Hotload release-react MyApp ios**

## 6. Run your app
And that’s it! All users running your app will receive the update using the experience you configured in step #4. For more details, refer to the CLI and client SDK documentation for React Native .

