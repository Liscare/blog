---
title: "7 steps to deploy your Symfony site using Oracle 11g on Microsoft IIS"
date: 2020-08-24
draft: false
author: "liscare"
tags: ["Symfony", "IIS", "Oracle", "English"]
categories: ["Web"]
featuredImagePreview: "/posts/not_found.png"
summaryStyle:
    hiddenImage: false
    hiddenDescription: false
    hiddenTitle: true
    tags:
      theme: "image"
      color: "white"
      background: "black"
      transparency: 0.7
page:
    theme: full
lightgallery: true
toc:
  auto: false
---

At work, I deployed a web app on IIS, nothing new until now. But, weeks ago, I chose the framework Symfony to help me on translations, ORM, routing, templating etc. Deploy your pure PHP web site on IIS is easy, with a web site made with Symfony is definitifely not commun. Most of tutoriels on Internet (like [StackOverFlow](https://stackoverflow.com/)) are about Symfony 2 and answers are (too) short (and/or too specified). So, I decide to write this article explaining how to deploy your Symfony web site on the Microsoft IIS with an Oracle dababase (based on my experience).

> This tutorial has been written to help you in your deployment, take what you want but do not follow it like a "StackOverFlow copy/paste developer".

Let’s start with version:
- Microsoft IIS 2019
- Symfony 4
- Oracle 11g
- PHP CLI 7.4.7

{{< image src="/posts/meme/meme_lapin_depart.gif" alt="Bugs Bunny ready to start">}}

## Step 1 : Composer & PHP

Install Composer via this link: https://getcomposer.org/download/ and, to check the installation, run composer with the command line (cmd) `composer -V` on your server (where IIS is).
Install PHP CGI (I think it works with PHP 8, try it and go back with PHP 7 if it doesn’t work) and then run `php --version`. This command line should work. With this command, you can notice what kind of PHP you have, it will be important for the installation of Oracle database.

## Step 2 : Import your web site

Copy your web site in an empty repository except `vendor` and `var` folders and `env.local` file. To finish, create a new Web site through IIS with the physical path to the public repository in your web site sources (recently copied).

## Step 3: Install your dependencies with Composer

If your company uses a firewall to be connected on internet, you should first connect to your company’s firewall on your server (to have internet access). Execute the following command where your `composer.json` is: `composer install --no-dev --optimize-autoloader`. It will download and install dependencies of your project.

## Step 4: Global configuration

First, create a new file in the root folder called `env.prod` for the production configuration. In this file, add and modify this line ccording to yout database configuration `DATABASE_URL=oci8://login:password@databaseUrl:port/databaseName` (for example `oci8://admin:1234@127.0.0.1:3000/DEV`). Then, add `APP_ENV=prod` and `APP_DEBUG=0`. Compile the file by using `composer dump-env prod`, now, you have a `env.prod.php` file.

{{< image src="/posts/meme/meme_chien_ok.gif" caption="Your boss waiting the app deployment" alt="A dog with cute eyes watching the photographer">}}

## Step 5: Route your web site

Symfony manages all routes for your website, you need a new IIS component to do that. Firstly, install the IIS component called Rewrite URL: download it from [here](https://www.iis.net/downloads/microsoft/url-rewrite) and launch the .exe. You can also download this module with the button "get New Web Platform Component" in your IIS manager. Check if this module is correctly installed by finding it on the Feature View. Then create a file called `web.config` in the public repository and insert the code available [below](https://gist.github.com/Liscare/820f622fa8ca1d866e8dfcec038551f0). Now, all routes are managed by Symfony!

## Step 6: Configure your PHP

Download the DLL for Oracle 11g [here](https://pecl.php.net/package/oci8). Choose DLL of the last version and, according to your PHP version, choose "Non Thread Safe" (NTS) or "Thread Safe" (TS) (use `php -v` to see if your current PHP is NTS or TS). Extract the content and move php_oci8_11g.dll into the folder ext of your PHP CLI (do not rename this file). Enable, at least, extensions (uncomment by deleting the semicolon) that you need and add the line `extension=oci8_11g`. Of course, adapt those steps if you have a different version of Oracle.

A 404 error means that Symfony doesn't work.

## Step 7: Enable Oracle 11g
### In your project

Before this step, you should only have a database error in your web site logs (see it in the var folder). You know, Oracle is particular for Symfony, you must add some lines in `config/services.yaml` and create 2 classes in `App\EventListener` (see [below](https://gist.github.com/Liscare/820f622fa8ca1d866e8dfcec038551f0), fork from [phpfour’s gist](https://gist.github.com/phpfour/4290cc1f0892dda4ef94a492d6b3f81e)).

### For PHP
If you execute the following command: `php -v`, you will get an error about the oci8 extension. Until now, your Oracle database cannot be use by your Symfony project yet. You have to install on your server Oracle Instant Client. This step seems easy but can get hard. Download the Instant Client from [here](https://www.oracle.com/database/technologies/instant-client/winx64-64-downloads.html) (link from Windows 64 bits). Choose the Basic one with the same or upper version of your database. Unzip the archive and copy it somewhere on your IIS server. Add to the PHP's PATH the path to this folder, the PHP user should be able to read the entire folder of Instant Client. Now, execute the command `php -v`, you should not have an error about oci8.

### Event listeners for Oracle database

{{< gist Liscare 820f622fa8ca1d866e8dfcec038551f0 >}}

## Troubleshooting

- **If `composer install --no-dev --optimize-autoloader` doesn’t work**, delete composer.lock and try again. If the problem persists, copy the vendor folder from your development environment into the root folder of your web site (not recommended in production environment).
- **If you want to debug routes of IIS**, add a logging rule for 500 error (or another one) by clicking on Failed Request Tracing Rules in your IIS manager. Find the location by double clicking the module (Failed Request Tracing Rules) on Feature View and then click on View Trace Log (It was C:\inetpub\logs\FailedReqLogFiles for me). Other IIS’ logs are in C:\inetpub\logs\LogFiles.
- **More logs with Symfony and PHP:** symfony logs are located in var/log/prod.log. If you are using the package [monolog-bundle](https://symfony.com/doc/current/logging.html), add SHELL_VERBOSITY=3 in .env file to activate full log. For php logs, turn on full logs by changing display_errors=On and display_startup_errors=On in your php.ini. Those manipulations should be reverted after resolving your bug!!!

## Tips & Info

- OCI means Oracle Call Interface, it is the interface (coded in native C) between your code and your Oracle Database
- Define a global route (`@Route("/",name="default"`)) redirecting to a login page
- Some PL/SQL functions are not available in Doctrine, you can use [Doctrine Extensions](https://github.com/beberlei/DoctrineExtensions) for that
- Do not store password in your CVS, use the file `.env.local` and untrack it. You can also use [Symfony Secret](https://symfony.com/doc/current/configuration/secrets.html) to encrypt them.
- Do not forget to use an user with the strict necessary access on your database. For example, you can create your tables by coping the PL/SQL result from this command: `php bin/console doctrine:schema:create --dump-sql` to delete the CREATE and ALTER access to your database user.
- Avoid enabling useless PHP extensions in your php.ini