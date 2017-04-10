---

template:      article
reviewed:      2016-12-30
title:         Companies on fortrabbit
naviTitle:     Company
excerpt:       How to work with Companies on fortrabbit
group:         platform
stack:         all

keywords:
    - beginner
    - platform
    - teamwork
    - sharing
    - roles
    - organization
    - access
    - tenant
    - client
    - epmloyees

---


Your fortrabbit Account represents YOU and is your personal login and path to access Apps. A Company on fortrabbit helps you to structure and manage team and billing aspects of your Apps.

```nohighlight
┌─────────────────────────────────────────────────────┐
│                       Company                       │
│                                                     │
│    Apps           Accounts        Billing Contacts  │
│  ┌─────────────┐ ┌──────────────┐ ┌──────────────┐  │
│  │ {{app-one}} │ │  {{owner1}}  │ │ {{Billing1}} │  │
│  ├─────────────┤ ├──────────────┤ ├──────────────┤  │
│  │ {{app-two}} │ │  {{owner2}}  │ │ {{Billing1}} │  │
│  ├─────────────┤ ├──────────────┤ └──────────────┘  │
│  │{{app-three}}│ │  {{admin2}}  │                   │
│  └─────────────┘ ├──────────────┤                   │
│                  │  {{admin1}}  │                   │
│                  └──────────────┘                   │
│                                                     │
└─────────────────────────────────────────────────────┘
```

The above illustration shows how Companies, Apps, Accounts and Billing Contacts relate to each other:

* Each App belongs to a Company.
* A Company can have multiple Apps.
* A Company can have multiple members ("employees") to collaborate on the Apps.
* A Company also can have multiple Billing Contacts to pay for the Apps.
* Each App is associated with one Billing Contact of the Company.

## Managing Companies

Don't worry when this all sounds very complex at the beginning. We believe in graceful disclosure: Companies are virtually invisible and for all intends and purposes synonym to your Account when working alone - until you need them.

### Creating a Company

You can create as many Companies as you need — free of charge. In the the Dashboard > Your Account > Companies > "Create a Company" button. Following the guided create process, you will not only create a new Company, but also it's first Billing Contact. Once created, you will be the Owner of the new Company.

<div data-markdown="1" data-user="known">

* [Create a new Company](https://dashboard.fortrabbit.com/account/company/new)

</div>

### Deleting a Company

As an Owner you can also decide to delete your Company. This is a huge step, as all Apps owned by the Company will be deleted and all the team will loose access. To do so: In the Dashboard > Your Account > Companies > {{ Your Company }} > Hit the "Delete Company" button and follow the instructions.

#### Leaving a Company 

With Company collaboration (see below) you can also leave a Company. That will keep the Company with fortrabbit, but you will loose access. When you cancel your Account and you are part of a Company with Owners left, you will leave the Company. 


### Collaboration

There are two levels of collaboration

1. [App level collaboration](app-collaboration): Grant code access on a per-App basis
2. **[Company level collaboration](company-collaboration)**: Grant company-wide access to all Apps and the Companies themselves

Since collaboration can easily become rather complex, we also have [collaboration overview article](collaboration), which shows you the big picture.

<!-- 

TODO: rewrite/review when Company Plans

### Support

Beside basic free support, you an also get [Professional Support](//www.fortrabbit.com/support) from us. Support plans are booked on behalf the Company and are available for the whole team.

-->

### Automatic resource exhaustion alerts

Each App with fortrabbit has limited resources, most of them are scalable or extendible. We advice to start small and only scale when needed. Some resources scale by usage. For example, when your App has users who are uploading images, the web space or the Object Storage space will get fuller and fuller by time.

All collaborators on the App will see those usage metrics at the App overview in the Dashboard. When a resource is about to hit the limit, it will be shown in a yellow color to alert you.

All Owners of the App will get an e-mail, once a usage metric is about to hit the limit. Please see our [specs page](https://www.fortrabbit.com/specs#limits) to learn about the resources with App alerts and how the limits are handled.

<!--

TODO: uncomment and extend when Technical Contact feature launches

#### Setting a technical contact

If you have a Company collaboration plan booked, all Owners and Admins of the Company can change the technical contact.

In the Dashboard under "Your Account" > "Companies" > {{ Company }} > "Technical contact" you can set one or more contacts. This can be any Account associated with the Company or any e-mail address you like.

You can define the services you want to receive alerts for. By default all services are enabled. Further: you can tune the settings to include or exclude certain Apps. You can also overwrite those settings on App level.

Individual Accounts can opt-out of receiving those alerts by deselecting this from their Accounts notification settings.

-->

### Working with multiple Companies

Just like in real life, you can create or join any number of Companies with your Account. So one Account can own multiple Companies while also being involved in other Companies as Admins or even App level collaborators.


### Moving an App from one Company to another

In some cases you might want to move the App to a different Company. This will change billing AND team. Of course you first need to be at least Admin in two Companies.


### Changing the Company of an App

2. Go to the App in the Dashboard, click the "Change ownership" button
3. This will open a form, where you choose a different Company (and Billing Contact)

This action can only be done by Accounts who have Owner or Admin privileges on both Companies.