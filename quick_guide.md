---
layout: documentation
title: Quick Guide for new users
---

# Quick Guide

This Quick Guide is aimed at new users.
We are going to show you how to install openHAB, add lightbulbs and switch lights on by
- a press of a button on your mobile phone and
- in an automated way by openHAB at the time when you go to bed.

You will see how easy it is and you do not have to be a home automation or IT expert (and we assume that you know how to unzip files and what IP addresses are).

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
  - Unzip to a folder of your choice e.g. `C:\Program Files\openHAB`
  - ![openHAB Folders](images/openHAB_Folders.png)
  - Note:
    -  Installing into `C:\Program Files\openHAB` requires admin rights. Alternatively choose a different folder, e.g. `C:\openHAB`

c. Start openHAB
  - Double click on `C:\openHAB\start.bat`
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/f5ff4a12-3c49-48de-95de-fe6aa99c82b6)
  - (In case Windows Defender pops up, click "Allow Access" for java.exe to communicate)
  - Open your browser and type in the following URL: `localhost:8080` (or `<IP-address of your PC>:8080` if you connect from your mobile phone)
  - On the very first start you are asked to create a new user
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/d57f141f-e7c7-4161-9a63-78cc16d65ee3)
  - Note:
    - If you want to run openHAB as a service, see [here](installation/windows.html#set-up-openhab-to-run-as-a-windows-service)

## Step 2: Adding Lightbulbs to openHAB

a. Binding
➡️ [Prerequisites]({{base}}/installation/index.html#prerequisites).

  
