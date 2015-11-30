---
layout: post
title:  "Hello World"
date:   2015-11-22 20:10:56 -0500
categories: jekyll update
---

In Mavericks, (Mac OS X 10.9) making a bootable full-OS installer isn't quite as straightforward as it had been in 10.7 and 10.8. In Lion and Mountain Lion, you could just use the Disk Utility to restore the .../Contents/SharedSupport/InstallESD.dmg to a drive or partition, and boot directly from that.

In 10.9 you can't do that. You *could* still do it through the GUI, using Disk Utility to restore the BaseSystem.dmg, which is an invisible file within the InstallESD.dmg once its mounted. But then you'd have to go through the rigamarole of first deleting the /Volumes/Mac OS X Base System/System/Installation/Packages symlink and copy in its place the Packages folder on the root level of the mounted InstallESD.dmg. Cumbersome.

A neater way to do this is to use the new built-in command line tool <pre>createinstallmedia</pre> which is located in the Mavericks install application package.

If you run it with no arguments as Apple's article suggests, you'll be given a small tutorial plus this example:

	createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install OS X Mavericks.app

If my Mavericks installer is in my /Users/Shared folder, and my destination volume is /Volumes/Untitled, then the command would look like this:

	/Users/Shared/Install\ OS\ X\ Mavericks.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Users/Shared/Install\ OS\ X\ Mavericks.app

One of the additional options available from the help screen is the `--nointeraction` flag, which erases the target disk without asking for confirmation. You can tack onto the end of the command string, like so:

	/Users/Shared/Install\ OS\ X\ Mavericks.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Users/Shared/Install\ OS\ X\ Mavericks.app --nointeraction

It should only take a few minutes, and you'll see the progress right in the Terminal window. When it's done—behold—a full-OS-bootable Mavericks installer. 
