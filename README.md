# Cloud Deployment with Heroku Study

## What is the Cloud Deployment with Heroku Study?
The Cloud Deployment with Heroku Study examines the relatively painless deployment of an application to Heroku (and by extension AWS). Although there are a few cons associated with using Heroku such as scaling costs and slow loads if the app is inactive, Heroku is a powerful tool for app deployment.

Here are some questions covered in this study:

* [Any interesting takeaways from the Cloud Deployment with Heroku Study?](#Any-interesting-takeaways-from-the-Cloud-Deployment-with-Heroku-Study)
* [What is Heroku?](#What-is-Heroku)
* [How do you deploy an app to Heroku?](#How-do-you-deploy-an-app-to-Heroku)

<br>

## Any interesting takeaways from the Cloud Deployment with Heroku Study?

<dl>

### Heroku runs on Amazon Web Services (AWS).

<dd>

AWS is an Infrastructure as a Serice (IaaS) provider, which is responsible for managing large shared data centers. Those data centers are what we call the "cloud". Although there a few other cloud service providers like Azure and Google, Heroku seems to be the best for developers in terms of ease and use. Technically, you could bypass Heroku and use AWS directly, but it seems like there is a LOT of high level knowledge required. There are alternatives such as Nanobox, Back4App, Firebase, etc. but Heroku is a great place to start.

</dd>

### Using Heroku can get VERY expensive.

<dd>

Initially, Heroku is cheap and they include free dynos for development at 1000 free hours per month. However, as you scale your application (add more RAM, CPU's, etc.) to meet growing demand and create more dynos, the costs can increase signifigantly. And since Heroku runs on AWS infrastructure, the prices can only be so low.

</dd>

### Heroku apps "sleep".

<dd>

Using free dynos will most likely "sleep" when there are larger periods of inactivity. This isnt necessarily a bad thing, but expect inactive Heroku apps to take at least 20 seconds to "wake up" before you make any call to the server.

</dd>

### You need to have a package.json file.

<dd>

Heroku expects your project to include a *package.json*. As a brief refresher, the *poackage.json* file defines all of the dependencies your application uses and need to be installed with the application. Functionally, the Heroku Node.js buildpack is employed only after the application it detects it in the root directory. 

So if you try to run the ```git push heroku master``` at the command line and you recieve an error to the effect of the push being rejected, it most likely because the *package.json* is NOT in the root directory.

</dd>

</dl>

<br>

## What is Heroku?

Heroku is a container-based cloud platform as a servive (PaaS) that developers use to deploy, manage, and scale modern applications. In other words, it is a deployment tool meant to make life easier for developers.

Heroku runs apps in dynos, which are essentially virtual computers that can scale the power required to run those apps. This means that as your demand for your app grows, you can scale horizontally or vertically (for a price of course). Important to note that Heroku does not host your app as it is deployed to Amazon Web Services (AWS).

<br>

## How do you deploy an app to Heroku?

<dl>
<dd>

### STEP 1: Create an app on Heroku:
------
Assuming you have created an account on Heroku, the first step to deploy your app to Heroku is to move into your project folder containing your node app and run the command ```heroku create```. When you do this, Heroku will create an app on Heroku and prepare Heroku to recieve your source code. Then a random project name for you while also setting up a subdomain at herokuapp.com. Note that before this step you should have a package.json file as Heroku expects that your project will have this file included.

```
    heroku create
```
After you end this command, you should seea confirmation of the application creation on Heroku, the identifcation of the Heroku app created, and two associated URL's. The first URL is the direct heroku app. The second is git remote.
```
    heroku create
    Creating app... done, fast-badlands-55259
    https://fast-badlands-55259.herokuapp.com/ | https://git.heroku.com/fast-badlands-55259.git
```

<br>

### STEP 2: Push App to Heroku:
------
When you are ready to deploy your app to Heroku, run ```git push heroku master```.
```
    git push heroku master
```
When you run this command, you should see a build process confirming the successful installation of your app to Heroku:
```
    $ git push heroku master
    Counting objects: 497, done.
    Delta compression using up to 8 threads.
    Compressing objects: 100% (379/379), done.
    Writing objects: 100% (497/497), 234.92 KiB | 23.49 MiB/s, done.
    Total 497 (delta 83), reused 497 (delta 83)
    remote: Compressing source files... done.
    remote: Building source:
    remote:
    remote: -----> Node.js app detected
    remote:
    remote: -----> Creating runtime environment
    remote:
    remote:        NPM_CONFIG_LOGLEVEL=error
    remote:        NODE_ENV=production
    remote:        NODE_MODULES_CACHE=true
    remote:        NODE_VERBOSE=false
    remote:
    remote: -----> Installing binaries
    remote:        engines.node (package.json):  10.x
    remote:        engines.npm (package.json):   unspecified (use default)
    remote:
    remote:        Resolving node version 10.x...
    remote:        Downloading and installing node 10.17.0...
    remote:        Using default npm version: 6.11.3
    remote:
    remote: -----> Installing dependencies
    remote:        Installing node modules (package.json)
    remote:        added 130 packages from 100 contributors and audited 248 packages in 4.801s
    remote:        found 0 vulnerabilities
    remote:
    remote:
    remote: -----> Build
    remote:
    remote: -----> Pruning devDependencies
    remote:        removed 79 packages and audited 127 packages in 1.324s
    remote:        found 0 vulnerabilities
    remote:
    remote:
    remote: -----> Caching build
    remote:        - node_modules
    remote:
    remote: -----> Build succeeded!
    remote: -----> Discovering process types
    remote:        Procfile declares types -> web
    remote:
    remote: -----> Compressing...
    remote:        Done: 19.8M
    remote: -----> Launching...
    remote:        Released v3
    remote:        https://fast-badlands-55259.herokuapp.com/ deployed to Heroku
    remote:
    remote: Verifying deploy... done.
    To https://git.heroku.com/fast-badlands-55259.git
    * [new branch]      master -> master

```

<br>

## STEP 3: Check to see if you have a dyno and give it a test run!
To do this, you simply need to run the following at the command line:
```
    heroku ps:scale web=1
```
When you run that command, you should see the following:
```
    heroku ps:scale web=1
    Scaling dynos... done, now running web at 1:Free
```
And then to see the app live, simply open the app (which will be automatically pointed to your app on the Heroku servers):
```
    heroku open
```

</dd>
</dl>