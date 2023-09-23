---
layout: documentation
title: Quick Guide for new users
---

# Quick Guide

This Quick Guide is aimed at new users.
It will show you how to install openHAB, how to add a smart device (for a dimmable lightbulb) and how to switch on the light by
- a press of a button on your mobile phone and
- in an automated way by openHAB at the time when you go to bed.

You will see how easy it is and you do not have to be a home automation or IT expert (and we only assume that you know how to unzip files and what IP addresses are).

[[toc]]

## Step 1: Install and Start openHAB

Estimated time: 3 minutes

We are going to intall openHAB on a Windows PC. Almost any Windows PC will do, as openHAB requires very little resources. If you want to install openHAB on a different platform, please refer for Step 1 of this Quick Guide to our [Installation Documentation](installation.html).

### A. Install OpenJDK runtime v17
|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. [Download OpenJDK](https://cdn.azul.com/zulu/bin/zulu17.44.53-ca-jre17.0.8.1-win_x64.msi)| |
|2. Double click the `.msi` file to start installation. | Requires admin rights. |
|3. Change "Set JAVA_HOME variable" to "Will be installed on local drive." | ![java_home](https://github.com/egoist6/openhab-docs/assets/76903043/e3bf9c45-3fae-417a-b4c9-75328048d90b)|

### B.  Install openHAB
|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. [Download openHAB](https://www.openhab.org/download/) ||
|2. Click on `Windows` -> `Stable` -> `Download openHAB Stable Runtime`.|![download_openhab](https://github.com/egoist6/openhab-docs/assets/76903043/9e59b846-4aa6-450d-bad4-dd7ec60add08) |
|3. There is no installation program. Simply unzip the downloaded `.zip` file to your preferred folder like `C:\Program Files\openHAB` (requires admin rights) or `C:\openHAB`. | ![unzip_openhab](https://github.com/egoist6/openhab-docs/assets/76903043/0bf58a31-2132-4fe8-8a4b-0609d156372b)|
|Note: If your openHAB-PC/server does not have internet access, you need to download the "Add-ons" package from the downloads page. Click on `Download openHAB Stable Add-ons` and copy the `.kar` file to `..\openHAB\addons`.| ![image](https://github.com/egoist6/openhab-docs/assets/76903043/cb85bf03-1946-4ec7-951c-68f2b4b55a42)|

### C. Start openHAB
|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. Double click on `..\openHAB\start.bat` and minimize the window when you see the following screen. (In case Windows Defender pops up, click "Allow Access".)|![image](https://github.com/egoist6/openhab-docs/assets/76903043/f5ff4a12-3c49-48de-95de-fe6aa99c82b6) If you want to run openHAB as a service, [see here](installation/windows.html#set-up-openhab-to-run-as-a-windows-service).|
|2. Open your browser and navigate to openHAB's GUI: [http://localhost:8080/](http://localhost:8080/) (or `<IP-address>:8080/` if you connect from your mobile phone). On the very first start you are asked to create an admin user. | ![create_admin](https://github.com/egoist6/openhab-docs/assets/76903043/e84ee45e-3ed2-4ff5-a8a6-3d0cce8c5e89)|

## Step 2: Setup Wizard

Estimated time: 1 minute

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. After you have created an admin user, a **Setup Wizard** is started automatically. The wizard will configure a few  basic settings. | You can cancel this wizard at any time and continue later by navigating to the following site: [http://localhost:8080/setup-wizard/](http://localhost:8080/setup-wizard/).|
|2. Set Language, Region, Time Zone and Location | ![setup_wizzard_location](https://github.com/egoist6/openhab-docs/assets/76903043/8a5391b1-acc6-4723-aa04-4ab2e6f72ede) Your location will not be sent to outside your network and this step can also be skipped by clicking on `Configure in Settings Later`.  |
|3a. Click on `Select Add-ons to Install` and select the vendor ([Philips hue](https://www.openhab.org/addons/bindings/hue/), [Lutron](https://www.openhab.org/addons/bindings/lutron/), [yeelight](https://www.openhab.org/addons/bindings/yeelight/), [LIFX](https://www.openhab.org/addons/bindings/lifx/), ...) or protocol name ([KNX](https://www.openhab.org/addons/bindings/knx/), [ZigBee](https://www.openhab.org/addons/bindings/zigbee/), [Z-Wave](https://www.openhab.org/addons/bindings/zwave/), [DALI](https://www.openhab.org/addons/bindings/dali/), [MQTT](https://www.openhab.org/addons/bindings/mqtt/), ...) of your smart device - in our example "[Shelly](https://www.openhab.org/addons/bindings/shelly/)". Add-ons which connect to your smart device (or services) are called **binding** in openHAB. | ![setup_wizzard_binding](https://github.com/egoist6/openhab-docs/assets/76903043/0dd40791-5996-4de2-b20f-f8767f9c706d) The setup wizard already added three pre-defined add-ons. During this Guide they are not required but we recommend to install them for a later purpose.|
|3b. Click `Install 4 add-ons`||
|3c. Click `Get Started` to close the Setup Wizard and you'll be redirected back to openHAB's GUI, called **MainUI**.||
|4. For the next step we will be activating MainUI's side bar. | ![mainui_sidebar](https://github.com/egoist6/openhab-docs/assets/76903043/96c82687-809e-4924-8bac-3e24d090c0ac)|

## Step 3: Adding a smart device to openHAB

A lightbulb (and many other smart devices) are Internet of **Things** devices (IoT). From now on we simply call those devices in openHAB a [**Thing**](/concepts/things.html), which is a digital representation of your real world smart device.

Before we continue with the next step, please follow our recommendation:

::: tip
Whenever you add a new binding to openHAB, please [**always read the documentation of the Add-on**](https://www.openhab.org/addons/)!
It will save you a lot of time.
:::

Let's add a Thing now:

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. Depending on your binding there are configuration options available. In our example we can provide credentials if the Things are password protected. Click on `Settings` -> `Bindings` -> `<name of Binding>` -> `gear icon` |![mainui_config_binding](https://github.com/egoist6/openhab-docs/assets/76903043/b066fbda-0a6e-46a1-b700-854dfdbdc5ac)|
|2. Navigate to Things. Click on `Settings` -> `Things`. Depending on your binding your system might have already discovered all your Things automatically (in our example Shelly Things) which you can see in your `Inbox`. |![mainui_things](https://github.com/egoist6/openhab-docs/assets/76903043/5be4e197-3301-4e89-9bda-fd8bbf9be18a)|
|3. Scan for new Things. If your system did not discover your devices, press the `+` button -> `<name of binding>` -> `Scan`. This will start the discovery process. |![mainui_things_scan](https://github.com/egoist6/openhab-docs/assets/76903043/230c0c7a-f5f0-4181-b72d-e576c69be3e8)|
|4. Add a new Thing. After the Thing has been discovered, click on the Thing, then select in the popup dialog `Add as Thing` to add it to your system.| GIF |


We recommend to provide a name which identifies your Thing such as: `Shelly-LivingRoom-DiningTable-Dimmer`
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
[Model](/tutorial/model.html)
![image](https://github.com/egoist6/openhab-docs/assets/76903043/9f8c085b-faf7-4f3e-8101-f36da3912cc0)

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

  
