---
layout:       post
title:        "Making tools up-to-date ⚒"
description:  "Commands to update applications and others tools"
date:         2018-11-12 17:00:00 +0200
categories:   tools
image:        /assets/img/post/making-tools-up-to-date-0.png
---

![Cover]({{ page.image }}){:.cover-img}

## "There is a new update"

Mostly new features and bug fixes are delivered with the new version of the installed applications. Checking every 5-minutes the application's website is not the most efficient approach. How to do it in a better way?

## Checking "Update automatically"

First of all check if your application contains something like "automatic updates" in the settings. Nowadays it is an industry standard for the modern apps. If your application is downloaded via `App Store`, make sure that in the preferences the `Automatic Updates` option is marked.

## Updating tools - a classic way

Not all the apps and tools you are using contains GUI. Moreover, sometimes you would like to update something without opening every app. How can this be achieved? Using special commands in terminal! For example: when you install app via `brew` there is a command like:

```bash
$ brew update
$ brew upgrade
```

For the `Ruby` scripts installed via `gem`:

```bash
$ gem update --system
$ gem update
```

Command `gem update --system` updates the `gem` itself. (if there is a new version)


You can update even `macOS` using:

```bash
$ softwareupdate --install --all
```

Probably you notice that these commands are different for each manager / tool. Some commands are changed in the future. There are also things like `npm`, `apm`, `mas` etc. How to handle all of them?

## Updating all tools - a better way

The best way is to gather all of the commands, write them into one file and run it. You can use my small tool which aggregates most of them. I called its [Updater for macOS](https://github.com/albinekcom/updater-for-macos). Every updater is in a separate file, the main script `updater_for_macos.sh` takes a tool name as an argument and execute all the code included in a particular file. So when you use it in that way:

```bash
$ ./updater_for_macos.sh --macos --brew
```

It looks for these two files (`macos.sh` and `brew.sh`) and invoke the code in them. If you want to add something more which is not included here right now, you can fork this repository, add a a new file in the `lib` directory and pass that name as an argument. It is just that easy. 😉

## Updating all tools - an automatic way

"Automate everything what you can". According to that mantra let's run this script automatically. There are few ways to do it but for `macOS` I can recommend [`launchd`](https://www.launchd.info).

To make it easy for everyone I have included a file `com.albinek.mac.updater_for_macos.plist` as an example. Download it, modify values like `PATH` (the path to your user's directory) and `ProgramArguments` (path to your updater script and with the tools' names you would like to have up-to-date). You can also change the time when this script will be invoked. Now you only need to move this file to `~/Library/LaunchAgents/` directory and load it using `launchctl` command.

```bash
$ launchctl load com.albinek.mac.updater_for_macos.plist
```

Since that moment your updater is executed automatically and you do not need to take care about it anymore. 😉

## Other platforms?

On Linux you can always use the manual way but probably you will need a file with updating `apt-get` to make most of your tools updated. [cron](https://en.wikipedia.org/wiki/Cron) can be helpful in enabling automatic updating.

## Conclusions

- Make sure that `Automatic Updates` is enabled in your applications.
- Use already implemented solutions like [Updater for macOS](https://github.com/albinekcom/updater-for-macos) for making the tools on your computer up-to-date.
- If something is repeatable and it needs to be done - automate it!
