---

template:         article
reviewed:         2019-02-25
title:            Install Kirby on fortrabbit
naviTitle:        Kirby 3
lead:             Kirby is a popular, file based CMS originated from Germany (YEAH!). Learn here how to install and tune Kirby on fortrabbit.
group:            Install_guides
stack:            uni
dontList:         yes
workInProgress:   yes

websiteLink:      https://getkirby.com/
websiteLinkText:  getkirby.com
category:         CMS
image:            kirby-mark.png
version:          3.0.2

keywords:
    - getkirby
    - starterkit

---

## Get ready

Make sure you to have completed all steps in the [get ready guide](/get-ready).


### Choose your deployment work-flow

There are two main ways to deploy code here on fortrabbit: [Git](/git-deployment) and [SFTP](/sftp-uni). The general rule of thumb is, that content driven legacy applications, like [WordPress](/install-wordpress), are better uploaded in classical manner with SFTP. Modern PHP web frameworks that are based on [Composer](/composer) are mostly deployed with Git. 

Now, Kirby is a bit in between. Kirby is, like [Grav](/install-grav), file based. So there is no database, the actual contents are text files written on the file system.

[Our architecture graphic here](/deployment-methods-uni#toc-understanding-the-architecture) shows you that the files, you can access via SFTP or SSH (Universal App) are not the ones, that are in Git. The Git repo is a separated thing. So, deploying with Git is a one way street that only goes up, not down. In other words: You can NOT `git pull` any changes you have made on the Apps file system. In an ideal world, code and content are maybe separated. With a file based CMS this is all together.


## SFTP upload

There is not much to say on that topic. Just make sure to upload all contents of your local Kirby folder, including the hidden `.htaccess` file into the `htdocs` folder within your App. 

## Deploy with Git and Composer

Make sure to read the [Kirby meets Composer](https://getkirby.com/docs/cookbook/installation/composer) article from official Kirby docs. Here is a basic rundown: 

1. Initialize Kirby with Composer on your local machine
2. Deploy to fortrabbit using Git and Composer
3. Synchronize contents with rsync


### Install Kirby locally with Composer

```
# 1. Create a local (on your own computer) kirby project folder with Composer:
$ composer create-project getkirby/plainkit {{app-name}}
```

Note that Kirby offers a "starterkit" (with some demo contents and a theme with some templates) and a "plainkit" with no contents at all (which is used here). Maybe you also have a project running locally and are just looking for ways to deploy that. Continue with the next steps.

### Configure Kirby for Git deployment

Open your local Kirby project folder with your text editor or IDE. Within there open the (hidden) `.gitignore` file on top level to tell Git to ignore some folders. Add those two lines:

```
…
# Kirby itself
/kirby

# Composer dependencies
/vendor

# Stuff you are creating
/content
…
```

PLEASE NOTE: The setting above will also keep the `/content` folder out of Git. This is our opinionated way to do it. It will help keeping your repo tidy and separating code from content. But you will need to run dedicated rsync commands to deploy and update the "contents" (see below). You can also decide to exclude the `/content` with the `.gitignore` so that you can deploy everything with Git all together. Keep in mind that you can not pull in new contents from the fortrabbit App this way.

At that point you should be able to run the project in your local development environment already. We highly recommend to develop the site locally, use fortrabbit for staging and production.


### Deploy Kirby with Git

```
# 1. Initialize Git
$ git init .

# 2. Add your Apps Git remote to your local repo
$ git remote add fortrabbit {{ssh-user}}@deploy.{{region}}.frbit.com:{{app-name}}.git

# 4. Add changes to Git
$ git add -A

# 5. Commit changes
$ git commit -m 'My first commit'

# 6. Initial push and upstream
$ git push -u fortrabbit master

# From there on only
$ git push
```

### Synchronize your contents

As mentioned above, deployment of your code base (templates and configuration) and dependencies (Kirby and Composer) is done via Git deployment. Deploying the content is a separated step. We recommend to use rsync to up- or down-load new contents to and from your remote fortrabbit App (see also our [rsync article](/rsync)). On your local computer in the Terminal in the kirby project folder execute:

```
# SYNC UP: from local to remote
$ rsync -av ./content {{app-name}}@deploy.{{region}}.frbit.com:~/content
```

It works also the other way around. For example in a case, where you have done some edits online and want those changes to be reflected in your local development environment:

```
# SYNC DOWN: from remote to local
$ rsync -av {{app-name}}@deploy.{{region}}.frbit.com:~/content ./content
```

You can also use [SFTP](/sftp) to synchronize the `content` folder.

<div class="alert p-m"> 
    HERE IT SHOULD ACTUALLY WORK. The local files are working fine in local dev, but on remote I get a simple "Not found" output. nothing in logs. When uploading the "plainkit" via SFTP, it works. <br>
    With fortrabbit: When you Git push > Composer will be triggered. The "vendor" folder is in place. The "kirby" folder is also in place.  <br><br>
    A difference I have noticed between the "downloaded SFTP version" and the "composer version" is that with SFTP the vendor folder inside the kirby folder, with the Composer version it's top level.
</div>

<!--

## Tuning

Let's get deeper:


### Sending mails

fortrabbit does not support `sendmail`, so sending mails out of the box might not work. Kirby provides config for transactional mail providers, or you can use a plugin to send e-mail over your own SMTP account.


### Setting the panel option

When initially setting up the `panel`, you might gonna see an error about the server name. You can add this configuration line to the file: `site/config/config.php`:

```
c::set('panel.install', true);
```

### Get a license

Remember that Kirby is not a free software. Get a license, support the authors!

## Disclaimer

Kirby is a mighty system with lot's of options. I might have missed some good stuff. Don't hesitate to contribute here.

-->