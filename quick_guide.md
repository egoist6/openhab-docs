---
layout: documentation
title: Quick Guide for new users
---

# Quick Guide

This Quick Guide is aimed at new users.
We are going to show you how to install openHAB, add a dimmable lightbulb and switch the light on by
- a press of a button on your mobile phone and
- in an automated way by openHAB at the time when you go to bed.

You will see how easy it is and you do not have to be a home automation or IT expert (and we assume that you know how to unzip files and what IP addresses are).

[[toc]]

## Step 1: Install and Start openHAB

Estimated time: 3 minutes

We are going to intall openHAB on a Windows PC. Almost any Windows PC will do, as openHAB just requires very little resources. If you want to install openHAB on a different platform, please refer for Step 1 of this Quick Guide to our [Installation Documentation](installation.html)

a. Install OpenJDK runtime v17:
  - [Download Link](https://cdn.azul.com/zulu/bin/zulu17.44.53-ca-jre17.0.8.1-win_x64.msi)
  - Double click the `.msi` file to start installation (requires admin rights)
  - At the beginning of the installation, change "Set JAVA_HOME variable" to "Will be installed on local drive"
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/1d11492a-ec31-4ee6-92d4-73be16294c35)

|qwerti   | tffv     |
|----------------------------------------------------------------|---------------------------------------------------------------|
|- testdv d v dvdvdh jh kh khkjj hlkjhlkjh lkjhkjh lkjhhvdvddvd \\n- vdvvvvdfvd dv fff     | ![image](https://github.com/egoist6/openhab-docs/assets/76903043/1d11492a-ec31-4ee6-92d4-73be16294c35)  |

|sfsf     | fddvfsvssscdcsc|

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

Estimated time: 1 minute

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
  - click `Install 4 add-ons`
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/11389822-2e8f-4fbf-b75e-9ae9229a058b)
- After installation of Add-ons click on `Get Started` to close the Setup Wizard

## Step 3: Adding Lightbulbs to openHAB

a. Adding a Dimmable Lightbulb Thing
  - A lightbulb (and many other smart devices) are Internet of **Things** devices (IoT). From now on we simply call those devices in openHAB a [**Thing**](/concepts/things.html), a digital representative of your real world lightbulb. Let's create a Thing:
  - Before you start adding a new Thing, please [**always read the documentation of the Add-on**](https://www.openhab.org/addons/)
    - Notes:
      o Some add-ons (adapters) might install a Bridge Thing first. In this case read the [Add-on's doc](https://www.openhab.org/addons/) how to procede.
      o If your Things are password protected, please provide your credentials in the Add-on by clicking `Settings` -> `Bindings` -> `<Add-on Name>` -> `Gear Icon` 
  - Click on `Settings` -> `Things`
  - Depending an your Add-on your system has already detected all your Things automatically (in our example Shelly Things) which you can see on your `Inbox` button.
  - If your system did not detect all your devices press the `+` button: ![image](https://github.com/egoist6/openhab-docs/assets/76903043/79cef2a7-8c0f-47bd-845b-d905e9ecc579)
  - click on your Shelly Add-on: ![image](https://github.com/egoist6/openhab-docs/assets/76903043/a61bd43b-6493-4c6e-b37c-ae9774acc20c)
  - and press scan: ![image](https://github.com/egoist6/openhab-docs/assets/76903043/7bf634ca-7d5d-484d-9c5a-065c5c0a611f)
  - Click on the Thing you want to add and select in the next popup dialog `Add as Thing`: ![image](https://github.com/egoist6/openhab-docs/assets/76903043/d804ff92-c4b3-4556-914d-23c6ba0034af)
  - We recommend to provide a name which identifies your Thing such as: `Shelly-LivingRoom-DiningTable-Dimmer`
    - Tip: It makes sense to define a syntax for your Thing names, such as: `AddonName-Room-PlaceOrPurpose-ThingType` and apply them consistently across all your Things.
  - Hit `ok`
  - ![image](https://github.com/egoist6/openhab-docs/assets/76903043/728ffdd3-e12d-4bda-a1e6-ecbd840d0a34)
  - Your thing has been added and we navigate back to the main menu by clickig twice in the upper left corner on `<Things` -> `<Settings`
- Click on `Things`: ![image](https://github.com/egoist6/openhab-docs/assets/76903043/153d69cf-d1c4-4b5b-8fab-e87629f74fdc)

- and your screen should look like this: ![image](https://github.com/egoist6/openhab-docs/assets/76903043/1f713c53-83b5-481b-9661-3b30f66eb811)

  - Click on the Thing we just created.As we said above, this Thing is the digital representative of your smart dimmer (dimmable lightbulb).
  - The Thing config page has three tabs. Click on the tab `Channels`: ![image](https://github.com/egoist6/openhab-docs/assets/76903043/155f560d-1b00-426b-b961-237fadf3344a)
  - As you can see, your Thing offers a lot of functionalities or capabilities (like set brightness, button press, power consumption, trigger alarms (e.g. overheating), signal strength, and many more), which want to start sending their information. These communication channels are simply called [**Channels**](/concepts/things.html#channels) and you need to activate them as you might do not need all of them.
  cont. and create brightness thing

Gui interacts with Items, have a state, receive commands, persist, 
rewrite addons to binding

## What next?
Model

➡️ 

italic: _text_
table: |
yellow block
  ::: warning
  :::
blue block
  ::: tip
  :::

[Prerequisites]({{base}}/installation/index.html#prerequisites).

  
