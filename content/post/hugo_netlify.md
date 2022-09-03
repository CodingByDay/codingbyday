---
title: "Publish a website for free using Hugo and Netlify"
date: 2022-09-03T15:04:58+02:00
draft: false
---

**The time necessary: An hour!**

In this post, I will explain how you can publish an amazing website completely for free using serverless technology called Hugo. 
Here is the video of me going through it if you are more of a visual learner.


So what is Hugo?
Hugo is the fastest growing serverless tech stack for creating amazing websites, it is written in Go,
and it makes obvious the fact that for most of the websites you don't actually need SQL and that is a huge blessing if you are concerned about the cost of the hosting services, which can amount to more than we are willing to pay, especially if your website does not have a huge amount of traffic. If you follow this guide you will be able to create a website completely for free and therefore I think this post could be beneficial for you. 

If you want to follow along the link to the GitHub repository will be below. You need to have git installed on your machine for hosting to work, so If you do not have it. Just head over to this URL and download it
https://git-scm.com/download/win
First of all, you need to install Hugo. Hugo is available on all operating systems and depending on the one you are using you will find instructions on how to install it on the Hugos website.
I will presume that most of you are on Windows and therefore here I will post the code necessary for Windows but once you have Hugo installed the process is the same.

``` html
# Run Powershell as admin
# Copy Paste this

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

```

Now, when the installation is complete you can then run this command inside CMD to install Hugo

``` html
choco install hugo -confirm
```
After we install Hugo we are ready to go.
Create a folder somewhere, this folder will be the home of your project. Open a cmd and navigate to that folder or open git bash with a right click inside of the folder.
Then we create a new Hugo website by running this command, change the example with the name of your site.

``` html
hugo new site example
cd example
```
You will get a message saying that the site has been successfully created, and that is it for the boilerplate site. Now we will initialize a git repository so that we can use it to publish our site.

``` html
Git init
Git add .
Git commit –m “Initial commit”
```

After we do this we need to choose a theme for our website because by default Hugo does not come with a theme. You can go to the Hugo website and see all of the available themes there, but I would suggest that you first try „anubis“ and then choose another one, there are almost identical to set up, but if you want to see how it works first then there is nothing wrong with this one.
We will add the theme as a submodule to our project. To do this you need to run the next command.

``` html
git submodule add https://github.com/mitrichius/hugo-theme-anubis.git themes/anubis
```

Then we will want to open the folder inside of a text editor, for non C# languages I use Visual Studio Code, and I think you would like it too, but feel free to use whichever one you want.
Inside of the text editor open the config.toml and it should like like this

``` html
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
```

At the end of the file we need to add the next line telling Hugo which theme we want to use

``` html
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
theme = "anubis"
```

That's it. We have created Hugo powered website! Congratulations. To see our website inside of the CMD we can run.

``` html
hugo serve
```

And then in your browser you can navigate to http://localhost:1313/ to see it. Your website should appear there.
To add a new post to our site we can run the next command.

``` html
hugo new post/hello-world.md
```

A new file will be created inside of content/post called hello-world.md. Since Hugo does not use a database those files are our our posts and so by changing them we make changes to the posts themselves
The post file should look like this.

``` html
title: "Hello World"
date: 2022-09-03T13:35:37+02:00
draft: true
```

Change the draft to false and then say something after the  closing „---„
Mine looks like this
``` html
---
title: "Hello World"
date: 2022-09-03T13:35:37+02:00
draft: false
---

**Hello world**

This is our first post!
``` 

Then after we save the file and had back to http://localhost:1313/ we can see our post there.
Run this command afterward.

``` html
Hugo -D
```

This is just a basic blog, you can of course make your site look and function much better by changing the config.toml and finding more information online on how to add pages, change the design add additional javascript, manage subscriptions, and so on, but for now, let us say that we have done all of that and we want to publish the site for free.

**PUBLISHING THE SITE**

In order to publish the site, we need to create a GitHub repository. I believe you know how to do this so once you do create it, copy the link to your repository and come back to the cmd and add it to your project folder.

``` html
git remote add example <url>
```    

Now we you add a .gitignore file so that our public folder does not get published to GitHub. From your editor of choice create a new file called .gitignore and add the following line there.

``` html
public/
```

  To publish the project to GitHub  ran the following commands:

``` html
Git init
Git add .
Git commit –m “First commit”
Git push example
And you are done. The only thing left to be done is to publish the site using Netlify which takes just a few more minutes.
Register an account on Netlify and click on create a new site from an existing project. Choose the GitHub repository and then click publish, and voila, your site is successfully published. If the build fails then you need to add a file to your project folder called netlify.toml. Inside of this file  specify the Hugo version installed on our machine, to find out the version you have type: 

``` html
Hugo version
```

Mine is 0.102.3, yours might be different, so change the contents of netlify.toml accordingly.

``` html
 [context.production.environment]
          HUGO_VERSION = "0.102.3"  
```
Also now that the site is active we need to change the baseURL inside of the config.toml to the address of the Netlify app.
Change example.com to the address of the app

``` html
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
theme = "anubis"
And commit the changes again.

``` html
Git init
Git add .
Git commit –m “second commit”
Git push example
```

Every time we change the GitHub repository the site will rebuild. So you can then add posts, set up a domain, and customize your site however you want.
I hope you found this useful. If you need some help you can contact me using the social links at the front page. See you in another post.


