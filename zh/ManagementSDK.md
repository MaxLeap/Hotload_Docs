

# Management SDK


A JavaScript library for programmatically managing your CodePush account (e.g. creating apps, promoting releases), which allows authoring Node.js-based build and/or deployment scripts, without needing to shell out to the [CLI](https://github.com/Microsoft/code-push/blob/master/cli/README.md).



## Getting Started[](#getting-started)

1.  Create an access key to authenticate with the CodePush server using the following CodePush CLI command:



    ```
    code-push access-key add "DESCRIPTION_OF_THE_KEY"

    ```

  

    If you already created a key that you want to use here, then you can retrieve it by running `code-push access-key ls` and using the value of the `Key` column for the key you wish to use.

2.  Install the management SDK by running `npm install code-push --save`

3.  Import it using the following statement (using ES6 syntax as applicable):

 
    ```
    var CodePush = require("code-push");    

    ```

   
4.  Create an instance of the `CodePush` class, passing it the access key you created or retrieved in step #1:

  

    ```
    var codePush = new CodePush("YOUR_ACCESS_KEY");

    ```

 

5.  Begin automating the management of your account! For more details on what you can do with this `codePush` object, refer to the API reference section below.


## API Reference[](#api-reference)

The `code-push` module exports a single class (typically referred to as `CodePush`), which represents a proxy to the CodePush account management REST API. This class has a single constructor for authenticating with the CodePush service, and a collection of instance methods that correspond to the commands in the management [CLI](https://github.com/Microsoft/code-push/blob/master/cli/README.md), which allow you to programmatically control every aspect of your CodePush account.

### Constructors[](#constructors)

*   **CodePush(accessKey: string)** - Creates a new instance of the CodePush management SDK, using the specified access key to authenticated with the server.

### Methods[](#methods)

*   **addAccessKey(description: string): Promise<AccessKey>** - Creates a new access key with the specified description (e.g. “VSTS CI”).

*   **addApp(appName: string): Promise<App>** - Creates a new CodePush app with the specified name.

*   **addCollaborator(appName: string, email: string): Promise<void>** - Adds the specified CodePush user as a collaborator to the specified CodePush app.

*   **addDeployment(appName: string, deploymentName: string): Promise<Deployment>** - Creates a new deployment with the specified name, and associated with the specified app.

*   **clearDeploymentHistory(appName: string, deploymentName: string): Promise<void>** - Clears the release history associated with the specified app deployment.

*   **getAccessKey(accessKey: string): Promise<AccessKey>** - Retrieves the metadata about the specific access key.

*   **getAccessKeys(): Promise<AccessKey[]>** - Retrieves the list of access keys associated with your CodePush account.

*   **getApp(appName: string): Promise<App>** - Retrieves the metadata about the specified app.

*   **getApps(): Promise<App[]>** - Retrieves the list of apps associated with your CodePush account.

*   **getCollaborators(appName: string): Promise<CollaboratorMap>** - Retrieves the list of collaborators associated with the specified app.

*   **getDeployment(appName: string, deploymentName: string): Promise<Deployment>** - Retrieves the metadata for the specified app deployment.

*   **getDeploymentHistory(appName: string, deploymentName: string): Promise<Package[]>** - Retrieves the list of releases that have been made to the specified app deployment.

*   **getDeploymentMetrics(appName: string, deploymentName): Promise<DeploymentMetrics>** - Retrieves the installation metrics for the specified app deployment.

*   **getDeployments(appName: string): Promose<Deployment[]>** - Retrieves the list of deployments associated with the specified app.

*   **promote(appName: string, sourceDeploymentName: string, destDeploymentName: string): Promise<void>** - Promotes the latest release from one deployment to another for the specified app.

*   **release(appName: string, deploymentName: string, updateContentsPath: string, targetBinaryVersion: string, description?: string, isMandatory: boolean = false): Promise<void>** - Releases a new update to the specified deployment.

*   **removeAccessKey(accessKey: string): Promise<void>** - Removes the specified access key from your CodePush account.

*   **removeApp(appName: string): Promise<void>** - Deletes the specified CodePush app from your account.

*   **removeCollaborator(appName: string, email: string): Promise<void>** - Removes the specified account as a collaborator from the specified app.

*   **removeDeployment(appName: string, deploymentName: string): Promise<void>** - Removes the specified deployment from the specified app.

*   **renameApp(oldAppName: string, newAppName: string): Promise<void>** - Renames an existing app.

*   **renameDeployment(appName: string, oldDeploymentName: string, newDeploymentName: string): Promise<void>** - Renames an existing deployment within the specified app.

*   **rollback(appName: string, deploymentName: string, targetRelease?: string): Promise<void>** - Rolls back the latest release within the specified deployment. Optionally allows you to target a specific release in the deployment’s history, as opposed to rolling to the previous release.

*   **transferApp(appName: string, email: string): Promise<void>** - Transfers the ownership of the specified app to the specified account.

