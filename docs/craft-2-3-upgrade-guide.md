---

template:         article
reviewed:         2018-05-07
title:            Upgrade from Craft CMS 2 to Craft CMS 3
naviTitle:        Upgrade from Craft 2
lead:             Learn how to update your Craft 2 installation to Craft 3. 
group:            craft
stack:            uni 

websiteLink:      https://craftcms.com/
websiteLinkText:  craftcms.com
category:         CMS
image:            craft-cms-logo.png

keywords:
  - craft
  - craftCMS2
  - craftCMS3
  - upgrade

---

You already have Craft 2 CMS installed and you are now looking to upgrade it to version 3? Here is what you need to know. First of all, please read the official upgrade guide:

* [docs.craftcms.com/v3/upgrade.html](https://docs.craftcms.com/v3/upgrade.html)

Craft 2 was way more simple. So we have recommended to use SFTP deployment. With Craft 3 many things are different, modern and more powerful. Just the way we like it:

* configuration with `dotenv` files
* new directory structure
* Composer based workflow
* Git support

Now you have two options to upgrade from Craft 2 to Craft 3:

#### 1. Quick update

The above linked guide offer you a way to upgrade with as little intervention as possible. Go that route if you are looking a quick way to upgrade. Keep your current directory structure and continue the SFTP workflow. 

#### 2. Full update

So you want to make use Git and Composer and resemble the new Craft 3 directory structure? Then you best: Start a new Craft 3 project from scratch, import your templates, configs and contents. See the [official Craft guide](https://docs.craftcms.com/v3/upgrade.html#if-you-want-your-directory-structure-to-resemble-a-new-craft-3-project) for more on this.

On the fortrabbit side you better start a new App additional App as well. When your local development version is running the new Craft 3 version with all your contents, [deploy it with Git and rsync](craft-3-deploy-with-git-uni) to your new fortrabbit App. Once it is also running on fortrabbit, remove the [domain](/domains) from the old App running on Craft 2 and add it to the new App running on Craft 3. Once the domain switch is done, delete the now not needed Craft 2 fortrabbit App. Also check out our general [migration guide](/migrating) on how to switch seamlessly and without downtime.