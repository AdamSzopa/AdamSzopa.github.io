---
layout: post
title:  "KDE in app stores"
published: false
date:   2020-03-28 12:00:00 +0100
categories: KDE
---

## INTRODUCTION

If you are a user of KDE software, there is a good chance that you're on a Linux distribution and you download the software using that distributions repositories.
But the fact is, you can get KDE software from a number of sources on different platforms. As project coordinator for KDE e.V. helping with [KDE Goals](https://kde.org/goals) I was tasked to look at app download statistics. Please join me in my quest to understand how popular are KDE apps on  various app stores.

## ANDROID

Let's start  with one of the most popular operating systems in the world, Android.

### Google Play

First, we have the Play Store, the default way of downloading apps in the Google ecosystem. You can find all of the KDE published apps under a [single developer account](https://play.google.com/store/apps/dev?id=4758894585905287660).

![KDE on the Google Play Store](/assets/playstore.png)

There are only 7 apps published, but one is a very popular one: [KDE Connect](https://play.google.com/store/apps/details?id=org.kde.kdeconnect_tp). It has over **half a million** downloads, and a respectable 4,6 rating with almost 15 thousand reviews. If we dig deeper when logged in into the developer console, we can see it has over 200 thousand active users.

I think the last metric is very important; raw downloads stats are informative, sure - but you can achieve a high download count with a good marketing push even if the app is mediocre. On the other hand, active users are those that installed and decided to keep the app.

By the way, Google Play defines "active installs" as those that had the app installed and were online in the last 30 days.

Here are the stats for all available apps:

|Name|Active Installs|
|--|--|
|KDE Connect| 226 679 |
|KStars|2 015|
|KTuberling|658|
|KAlgebra|572|
|Behaim Globe|511|
|Kirigami Gallery|165|
|Klimbgrades|92|

### F-Droid

The Google Play store in not the only way one can install apps. You can directly download .apk files and install them manually or use a 3-rd party store like F-Droid. I'm not sure if there is way to link to all KDE apps available there, but you can search for individual apps, like [KDE Connect](https://f-droid.org/en/packages/org.kde.kdeconnect_tp/). There are no stats for downloads or active users on F-Droid.

## WINDOWS

I would expect that most Windows users don't use an app store to get a KDE app - for many years the normal workflow to install new software is to google the name, find a download link, get the installer and install manually.
But Windows does come with an app store of it own, and of course, KDE has apps available there as well. I couldn't find a way to link to a single publisher, so the best I can do is a [pre-made search link](https://www.microsoft.com/en-gb/search/shop/Apps?q=KDE%20e.V.).

On this app store we have even less apps published, only 6. The Windows store has a number of stats available to the developers, but I'll highlight 30 day "acquisitions" which should be comparable to the statistic from Google Play.

| Name | Acquisitions |
|--|--|
| Kate | 32 067 |
|Okular|23 811|
|Filelight|2 992|
|Kile|2 391|
|KStars|1 825|
|Elisa|945|

We don't have a single juggernaut this time, the numbers are comparable between the top 2 apps.
Fun observation: KStars has a similar amount of users on both the Google Play Store and the Windows Store.
Not so fun fact: Kate has 61 user reviews, Okular 108. That's not much compared to the number of users, if you're one of them consider writing one!

Note: The public listing on the store shows even less reviews, for example only 3 total reviews for Kate. I'm not sure if this is somehow filtered for me due to location or language.

![Kate on the Microsoft Store](/assets/kate_msstore.png)

But I mentioned that the Windows Store is not the primary way of getting KDE apps on Windows. Using the stats available in the Microsoft Partner Center, I can see that Krita alone had reported **millions of installs**. Other apps like Kdenlive, Kile, Kdevelop and Okular all have at least 200 thousand installs. I'm not sure how to interpret all of the data, but it shows the huge difference in the popularity of download methods.

## SNAPCRAFT

This distribution independent app store hosts [96 KDE apps](https://snapcraft.io/publisher/kde). To get usage numbers I needed to go into each app manually, go to the metric tab and there I can see "Weekly active devices".

If there is ever a need to revisit these numbers more often I would spend some time to get the stats in a automated way, because the huge amount of apps published and the need for manual accessing each app makes this task very time consuming.

Anyway, here are the top 10 apps:

| Name | Installs |
|--|--|
| Okular | 34 862 |
|Krita|33 874|
|Kdenlive|14 516|
|Kolourpaint|9 607|
|Ark|6 928|
|Ktorrent|6 210|
|Kate| 3 483|
|Umbrello|3 253|
|Ktouch|3 186|
|KCalc|3 066|
|...||
|All other apps combined|48 668|

Some observations:

 - Not visible in the above list is the **huge amount games**! Most of them have anywhere from 200 to 1000 active users. Perhaps they're good candidates to include in the other app stores?
 - Elisa and Kile are both available on the Windows Store but not on the Snap Store. I think that's a missed opportunity.
 - Some of the least popular packages are Kdevelop, Calligra, Filelight and Kontact. I think it shows that users of those apps either had them preinstalled on their systems or are predominantly looking for them elsewhere.

![Kmines screenshot](/assets/kmines.png)
*Can you get on my level in Kmines?*
 
## FLATHUB

This other Linux focused app store has 38 KDE apps available. Similarly to the Windows Store instead of a publisher listing I can offer a [search link](https://flathub.org/apps/search/kde). 

This store needed the most amount of work from me. Compared to the other stores, there is no "developer account" I could login to, instead all of the stats are available [in the open](https://flathub.org/stats/). I like this approach, but unfortunately the data provided is just raw download numbers that need some treatment to be useful.  I used this [python tool](https://gitlab.com/ahayzen/flathub-api-stats-generator) to help me with that.

The other issue is understanding the numbers. The other app stores all provide some sort of metric that shows the active users in a time frame, but here I only have downloads. This means that if I would try to look at the number of downloads of an app in the last 30 days, but the app had 1 or more updates in that time it would duplicate users (once for the initial download, then again for each update downloaded).

To make some sense from all of this, I decided to look at the number of downloads since the last app update - assuming that active users keep apps up to date, this should more or less show the current usage. Again, I needed to do this work manually (check the last update date and ask for stats from then to now, for every app) and if this is not a one-off exercise a better way needs to be developed.

Fortunately for me, most of the apps were updated on March 5th so I could query for many of them at the same time. Since I gathered the stats on March 28th, it should be enough time for most users to download the update and thus show up as a active user.
There are however some problems still: some apps show no update date at all (perhaps they were truly never updated) or had updates a long time ago (querying from that date would show huge cumulative download numbers). The other issue is that Krita was updated on March 25th, which could result in smaller reported number of downloads as users haven't updated yet.

Based on all of these assumptions, I present my compiled list of top 10 apps that were updated on March 5th:

|Name| Downloads or updates between March 5-28 |
|--|--|
| Kalzium | 38 959 |
|Kgeography |38 561|
|Knavalbattle|36 107|
|Kbounce|31 467|
|Kbruch|31 282|
|Kblocks|30 971|
|Kdenlive|30 843|
|kwordquiz |30 169|
|Ksudoku|30 133|
|Kgoldrunner|30 038|

Now this is quite different from all other app stores. The app composition is different (3 educational apps, 6 games), and the download numbers are quite similar in the top 10. This means that either my method if flawed or flathub users are very different compared to other app stores.

For completion, some other stats:

|Name| Downloads |
|--|--|
| Gcompris March 5-28 | 22 363 |
|Gcompris since last update 2019-12-01|67 961|
|Kdenlive March 5-28|30 843|
|Kdenlive since last update 2020-02-11|54 484|

## CONCLUSIONS

What did I learn after going through all of this data?

While perhaps not the most popular way of acquiring KDE software, app stores sill serve hundreds of thousands of users. This number can get much higher if **more apps become published on all of the stores** and the existing listings get some more love - **reviews, better descriptions and screenshots**.

Direct file downloads from repositories or mirrors dwarf the app store download numbers, but the stats from those are not collected for privacy reasons.

On the other hand, a successful app store listing is something we can show the world and say "look here, this is a popular KDE app, check it out and maybe check out the others".
If you'd like to help with promoting KDE apps, check out the wiki page for one of KDE's current goals [All about the Apps](https://community.kde.org/Goals/All_about_the_Apps).


### PS

Some apps have their own listings on app stores like [Gcompris on the Play Store](https://play.google.com/store/apps/details?id=net.gcompris.full) or [Krita on Steam](https://store.steampowered.com/app/280680/Krita/). I did not include those in my stats.
