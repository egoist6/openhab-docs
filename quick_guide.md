---
layout: documentation
title: Quick Guide for new users
---

# Quick Guide

This Quick Guide is aimed at new users.
We are going to show you how to install openHAB, add lightbulbs and switch lights on by
- a press of a button on your mobile phone and
- in an automated way by openHAB at the time when you go to bed.

You will see how easy it is and you do not have to be a home automation or IT expert.

[[toc]]

## Step 1: Install and Start openHAB

Estimated time: 3 minutes
We are going to intall openHAB on a Windows PC. Almost any Windows PC will do, as openHAB just requires very little resources. If you want to install openHAB on a different platform, please refer for Step 1 to our [Installation Documentation](installation.html)

a. Install OpenJDK runtime v17:
  - [Download Link](https://cdn.azul.com/zulu/bin/zulu17.44.53-ca-jre17.0.8.1-win_x64.msi)
  - Double click the `.msi` file to start installation (requires admin rights)
  - At the beginning of the installation, change "Set JAVA_HOME variable" to "Will be installed on local drive"
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/1d11492a-ec31-4ee6-92d4-73be16294c35)

b. Install openHAB:
  - [Download-Link](https://www.openhab.org/download/) (click on "Windows" -> "Stable" -> "Download openHAB Stable Runtime")
  - Unzip to a folder of your choice e.g. `C:\Program Files\openHAB`  (requires admin rights, or choose a different folder, e.g. `C:\openHAB`)
  - ![openHAB Folders](images/openHAB_Folders.png)

c. Start openHAB
  - Double click on `C:\openHAB\start.bat`
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/375930c3-28f5-4f24-ab53-8ade3e8db6d6)
  - (In case Windows Defender pops up, click "Allow Access" for java.exe to communicate)

DONE!

##Step 2:

a. Open your browser and type in the following URL: `localhost:8080`

![image](https://github.com/egoist6/openhab-docs/assets/76903043/bb4139a6-57e1-4c92-b405-c3cbab623831)

➡️

  
