# Management CLI


## Installation

### Install Node.js
### Install the Hotload CLI: 

> npm install -g hotload-cli

## Getting Started

1. Create a CodePush account push using the CodePush CLI
2. Register your app with CodePush, and optionally share it with other developers on your team
3. CodePush-ify your app and point it at the deployment you wish to use (Cordova and React Native)
4. Release an update for your app
5. Live long and prosper! (details)



## Account creation

### Register
Before you can begin releasing app updates, you need to create a CodePush account. You can do this by simply running the following command once you’ve installed the CLI:

> hotload register

### Login
Most commands within the CodePush CLI require authentication, and therefore, before you can begin managing your account, you need to login using the GitHub or Microsoft account you used when registering. You can do this by running the following command:

> hotload login

### Logout
When you login from the CLI, your access key is persisted to disk for the duration of your session so that you don’t have to login every time you attempt to access your account. In order to end your session and delete this access key, simply run the following command:

> hotload logout

## App Management
Before you can deploy any updates, you need to register an app with the CodePush service using the following command:

> hotload app add <appName>


If your app targets both iOS and Android, we recommend creating separate apps with CodePush. One for each platform. This way, you can manage and release updates to them separately, which in the long run, tends to make things simpler. The naming convention that most folks use is to suffix the app name with -iOS and -Android. For example:

> hotload app add MyApp-Android

> hotload app add MyApp-iOS

All new apps automatically come with two deployments (Staging and Production) so that you can begin distributing updates to multiple channels without needing to do anything extra (see deployment instructions below). After you create an app, the CLI will output the deployment keys for the Staging and Production deployments, which you can begin using to configure your mobile clients via their respective SDKs (details for Cordova and React Native).

If you decide that you don’t like the name you gave to an app, you can rename it at any time using the following command:

> hotload app rename <appName> <newAppName>

The app’s name is only meant to be recognizable from the management side, and therefore, you can feel free to rename it as necessary. It won’t actually impact the running app, since update queries are made via deployment keys.

If at some point you no longer need an app, you can remove it from the server using the following command:

> hotload app rm <appName>

Do this with caution since any apps that have been configured to use it will obviously stop receiving updates.

Finally, if you want to list all apps that you’ve registered with the CodePush server, you can run the following command:

> hotload app ls


## Deployment Management
If having a staging and production version of your app is enough to meet your needs, then you don’t need to do anything else. However, if you want an alpha, dev, etc. deployment, you can easily create them using the following command:

> hotload deployment add <appName> <deploymentName>

Just like with apps, you can remove and rename deployments as well, using the following commands respectively:

> hotload deployment rm <appName> <deploymentName>

> hotload deployment rename <appName> <deploymentName> <newDeploymentName>

If at any time you’d like to view the list of deployments that a specific app includes, you can simply run the following command:

> hotload deployment ls <appName> [--displayKeys|-k]

You can view a history of the 50 most recent releases for a specific app deployment using the following command:

>hotload deployment history <appName> <deploymentName>

## Releasing Updates
## Promoting Updates
## Rolling Back Updates


