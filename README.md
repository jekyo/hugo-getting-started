# Tutorial: Deploying a basic Hugo app on Jekyo

Demo app [here](https://hugo-demo.jekyo.app/)

### Prerequisites

Make sure you have [NodeJS](https://nodejs.org/en/download/), [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) and [git](https://github.com/git-guides/install-git) installed.

If it's your first time using **Jekyo**, you can **install** it by running the following command in your terminal:

`npm install -g jekyo`

### Sign in to Jekyo

You can sign in to Jekyo by running `jekyo user:signin`

```
➜  ~ jekyo user:signin 
Your email?: **************
Your password?: **********
You have successfully signed in!
```
If you don't have a Jekyo account, you can create one in the terminal by running `jekyo user:signup`. 

## 1. Create a basic Hugo app

You can start your Hugo project by using `jekyo create`

Using the **arrows** on your keyboard, select **hugo** and press **enter**.  
```
? Select template
  None Creates only the application
  expressjs A basic app skeleton using [Express](https://expressjs.com/)     
  nuxt-js A boilerplate SSR application using [Nuxt.js](https://nuxtjs.org/) 
❯ hugo A basic starter app using [Hugo](https://gohugo.io/)
```
When prompted, enter the desired name for your Hugo app. 

`Application name?: hugo-tutorial`

This will create a basic Hugo app in the current directory by cloning this [Hugo starter app](https://github.com/jekyo/hugo-getting-started) repository.

```
Cloning source code... OK
Application created!
```

### Deploy the Hugo app on Jekyo

To deploy the app, first navigate to the newly created directory:

`cd hugo-tutorial`

Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://hugo-tutorial.jekyo.app ... OK
```

You can now browse to your Hugo app on https://hugo-tutorial.jekyo.app (replace 'hugo-tutorial' with your app name)

## 2. Deploying an existing Hugo app

Navigate to your local Hugo app directory

`cd my-hugo-app`

Initialize a git repository if you haven't already done so by running `git init`. 

### Edit package.json

Make sure to include `$PORT` and `$HOST` variables in your **package.json**:

```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "hugo",
    "start": "hugo server --port $PORT --bind $HOST"
  },
```

### Edit config.toml

Include the theme you are using in your **config.toml** file:

```
title = 'My New Hugo Site'
theme = "ananke"
```

### Create an empty Jekyo app:

`jekyo create` 

Select 'none' using the **arrows** on your keyboard and press **enter**. This will create an app using your current directory. 

```
? Select template (Use arrow keys)
❯ None Creates an application from your current directory
```

Name your app: 

`Application name?: my-hugo-app`

Run `jekyo link` to link your local app to the remote Jekyo app. Select 'my-hugo-app' using the **arrows** on your keyboard and press **enter**.

```
? Select application (Use arrow keys)
❯ my-hugo-app
```
### Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://my-hugo-app.jekyo.app ... OK
```

You can now browse to your Hugo app on https://my-hugo-app.jekyo.app (replace 'my-hugo-app' with your app name)

## Pushing local changes to Jekyo 

Add the newly modified file(s) to the git index by using [git add](https://www.atlassian.com/git/tutorials/saving-changes)

`git add filename`

Create a [git commit](https://github.com/git-guides/git-commit)

`git commit -m "your commit message"`

Now, simply deploy your app again:

`jekyo deploy`

You will see your changes on your live app after a short while. 





