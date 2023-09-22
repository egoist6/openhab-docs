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
  - Double click on `C:\openHAB\start.bat` and minimize the window when you see the following screen.
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/f5ff4a12-3c49-48de-95de-fe6aa99c82b6)
  - (In case Windows Defender pops up, click "Allow Access" for java.exe to communicate)
  - Open your browser and navigate to the following URL: [http://localhost:8080/](http://localhost:8080/) (or `<IP-address of your PC>:8080` if you connect from your mobile phone)
  - On the very first start you are asked to create a new user
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/d57f141f-e7c7-4161-9a63-78cc16d65ee3)
  - Note:
    - If you want to run openHAB as a service, see [here](installation/windows.html#set-up-openhab-to-run-as-a-windows-service)

## Step 2: Setup Wizard

- After you have created your user and you are logged on, a **Setup Wizard** is automatically started:
- ![image](https://github.com/egoist6/openhab-docs/assets/76903043/9bf16d68-7d49-4a53-b633-7091bad70da7)
  - You can cancel at any time this wizzard and continue later by navigating to the following site: [http://localhost:8080/setup-wizard/](http://localhost:8080/setup-wizard/)
- Set your location:
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/5b5dff26-4344-4faf-9619-3d4ab0e49139)
  - This data will not be sent to outside your network (you can also skip this step by clicking on `Configure in Settings Later`)
  - This data is required for services such as determining your bank holidays for your location
- Install Add-Ons:
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/cbd7da10-b7a8-465a-90af-6d0468b9672a)
  - there are already three pre-defined add-ons selected to be installed. During this Guide they are not required but we recommend to install them for a later purpose
  - Click on `Select Add-ons to Install` and pick an adapter for your smart lighting system/switch such as:
    - Philips hue
    - Shelly
    - Lutron
    - yeelight
    - LIFX
    - KNX, ZigBee, Z-Wave, DALI, MQTT smart switch
    - and many more
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/82078937-451a-43dc-85df-e4566e2e47f9)
  - now click `Install 4 add-ons`
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/11389822-2e8f-4fbf-b75e-9ae9229a058b)
  - now click on `Get Started` and we are ready for the next step

## Step 3: Adding Lightbulbs to openHAB

a. 



➡️ http://localhost:8080/setup-wizard/
[Prerequisites]({{base}}/installation/index.html#prerequisites).

  
