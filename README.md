# Cloud Deployment with Heroku Study

## What is the Cloud Deployment with Heroku Study?
The Cloud Deployment with Heroku Study examines

Here are some questions covered in this study:

* [What is Heroku?](#What-is-Heroku)
* [How do you deploy an app to Heroku?](#How-do-you-deploy-an-app-to-Heroku)
* [](#)
* [](#)
* [](#)

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

<br>

### STEP 2: Push app to Heroku:
------
To push your app to heroku, run ```heroku create``` at the command line.
```
    heroku create
```
After you end this command, you should seea confirmation of the application creation on Heroku, the identifcation of the Heroku app created, and associated URL's.
```
    $ heroku create
    Creating app... done, fast-badlands-55259
    https://fast-badlands-55259.herokuapp.com/ | https://git.heroku.com/fast-badlands-55259.git

```



</dd>
</dl>