---
layout: post
title: Tinkering with Android Boot Animation
description: Inspired by Watch Dogs
category: articles
tags: [rant, android, hack, learn]
---

Orite lads and lasses!
It has been exactly 6 months since I bought my Nexus 4 (Typically my first
android phone ever). Its a great piece of hardware and the Stock Android 4.4.2
Kitkat is kickass. 

Getting back- 
> Having owned an Android phone for half an year, I think it was about time I
started toying with it.

As a matter of fact I wished myself a lovely year on the new year's eve by
rooting my nexus 4 device and installing the Ubuntu Touch OS on it.
It was a marvellous feeling. I spent the entire new year night getting Ubuntu
Touch on my phone and by 5 a.m. I was ready.

I'll cover that in a separate blog post later.

Now, let me tell you how I wondered about moving from my stock nexus boot animation to
a custom new boot animation.

Enter - [Watch Dogs](http://youtu.be/ulFeUCAI5xM)
=================================================

<div class="video">
<iframe width="100%" height="100%" src="//www.youtube.com/embed/ulFeUCAI5xM?rel=0" frameborder="0" allowfullscreen></iframe>
</div>

There are a number of skills you can invest in, but far and away, __Hacking__
is the must have above Driving, Crafting and Combat.

Haha! No, seriously watch the trailer. Its everything we programmers and 
computer nerds aspire to be in our secret lives.

### So the question how do we do it?

The process is fairly easy once you get your hands around it. And once you do,
you'll be flying off changing your android's boot animations and even making
your own custom versions.

__Prerequisite__ - your android phone should be __rooted__.

If you want to check if your phone is rooted or not, download this simple app -
[Root Checker Basic](https://play.google.com/store/apps/details?id=com.joeykrim.rootcheck).
If it says yes! then Voila! Lets dive in. Else, head over to XDA developers and
you know what to do.

>  Diving in.

__Step 1:__

Download the Watch Dogs inspired Boot animation,
[720p version](https://www.dropbox.com/s/j9evxy8iopkrzvy/bootanimation_wd_nexus4_long.zip) or
[1080p version](https://www.dropbox.com/s/w4vff1j1nqv0nik/bootanimation_wd_1080p_longer.zip)

> I recommend the 720p version if you have a Nexus 4, but the 1080p one would work as
well. Now what you download is a zip file and you would want to keep it that way.

__Step 2:__

We need to put the boot animation file from our `Download` folder to `/system/media`
_(this is why we need to be root)._

From here on there are 2 ways you can achieve the goal:

- do everything via your phone, or
- attach a USB cable.


__Step 3:__

Watch the preview and feel awesome.  

<div class="video">
<iframe width="100%" height="100%" src="//www.youtube.com/embed/34WJE0YXmyE"" frameborder="0" allowfullscreen></iframe>
</div>


__Step 4a: The Phone guy__

Download [Root Browser](https://play.google.com/store/apps/details?id=com.jrummy.root.browserfree).   
Now open Root Browser and do the following:

- Go to `/system/media`.
- Rename the file `bootanimation.zip` to `bootanimation.back`.   
  We change the filename since we'll have to rename our new watchdogs boot animation with
  the same name.
- Go to `/sdcard/Download`.
- Move or copy the `bootanimation_wd_nexus4_long.zip` file to `/system/media`.
- Rename your `bootanimation_wd_nexus4_long.zip` file to `bootanimation.zip` in
  `/system/media` folder.

Bam! You're done!
Time to reboot your phone. Sit back and bathe in the beauty of your new watch
dogs boot animation.

* * *

__Step 4b: The Cable guy__

I assume you have USB debugging enabled and the `adb` (Android Debug Bridge) utility .  
If your phone is rooted you will have that.

Then fire up your terminal and follow along:
{% highlight bash %}
$ adb shell
shell@mako:/ $ su
{% endhighlight %}

Since the `/system` is a Read-only file system, we need to add assign write
permissions to it. (this is temporary and the permisssions resolve after
we exit.)   
FYI mako is the codename for nexus 4.

{% highlight bash %}
root@mako:/ # mount -o remount,rw -t yaffs2 /dev/block/mtdblock3 /system
root@mako:/ # chmod 777 /system/media
root@mako:/ # ls /system/media
Audio
Video
bootanimation.zip
{% endhighlight %}

you see that file `bootanimation.zip` that's our stock animation. And we
have to name our custom watchdogs animation with that name too. So first
lets rename the original bootanimation file to somethine like
`bootanimation.back`.

{% highlight bash %}
root@mako:/ # cd /system/media
root@mako:/system/media # mv bootanimation.zip bootanimation.back
{% endhighlight %}

Its time to move or copy the watchdogs boot animation file.

{% highlight bash %}
root@mako:/system/media # cp /sdcard/Download/bootanimation_wd_nexus4_long.zip .
root@mako:/system/media # mv bootanimation_wd_nexus4_long.zip bootanimation.zip
{% endhighlight %}

Bam! you're done. Congratulations! you true hacker :)
Time to reboot

{% highlight bash %}
$ adb reboot
{% endhighlight %}

Later.

* * *

*P.S. - Actually my sister bought the nexus for me; not that its relevant but don't bug me now! I don't earn yet.*

