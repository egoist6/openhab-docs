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

### a. Install OpenJDK runtime v17
|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. [Download OpenJDK](https://cdn.azul.com/zulu/bin/zulu17.44.53-ca-jre17.0.8.1-win_x64.msi)| |
|2. Double click the `.msi` file to start installation. | Requires admin rights. |
|3. Change "Set JAVA_HOME variable" to "Will be installed on local drive." | ![java_home](https://github.com/egoist6/openhab-docs/assets/76903043/e3bf9c45-3fae-417a-b4c9-75328048d90b)|

### b.  Install openHAB
|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. [Download openHAB](https://www.openhab.org/download/) ||
|2. Click on `Windows` -> `Stable` -> `Download openHAB Stable Runtime`.|![download_openhab](https://github.com/egoist6/openhab-docs/assets/76903043/9e59b846-4aa6-450d-bad4-dd7ec60add08) |
|3. There is no installation program. Simply unzip the downloaded `.zip` file to your preferred folder like `C:\Program Files\openHAB` (requires admin rights) or `C:\openHAB`. | ![unzip_openhab](https://github.com/egoist6/openhab-docs/assets/76903043/0bf58a31-2132-4fe8-8a4b-0609d156372b)|
|Note: If your openHAB-PC/server does not have internet access, you need to download the "Add-ons" package from the downloads page. Click on `Download openHAB Stable Add-ons` and copy the `.kar` file to `..\openHAB\addons`.| ![image](https://github.com/egoist6/openhab-docs/assets/76903043/cb85bf03-1946-4ec7-951c-68f2b4b55a42)|

### c. Start openHAB
|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. Double click on `..\openHAB\start.bat` and minimize the window when you see the following screen.<br />(In case Windows Defender pops up, click "Allow Access".)|![image](https://github.com/egoist6/openhab-docs/assets/76903043/f5ff4a12-3c49-48de-95de-fe6aa99c82b6) If you want to run openHAB as a service, [see here](installation/windows.html#set-up-openhab-to-run-as-a-windows-service).|
|2. Open your browser and navigate to openHAB's GUI: [http://localhost:8080/](http://localhost:8080/) (or `<IP-address>:8080/` if you connect from your mobile phone). On the very first start you are asked to create an admin user. | ![create_admin](https://github.com/egoist6/openhab-docs/assets/76903043/e84ee45e-3ed2-4ff5-a8a6-3d0cce8c5e89)|

## Step 2: Setup Wizard

Estimated time: 1 minute

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. After you have created an admin user, a **Setup Wizard** is started automatically. Set Language, Region, Time Zone and Location | ![setup_wizzard_location](https://github.com/egoist6/openhab-docs/assets/76903043/8a5391b1-acc6-4723-aa04-4ab2e6f72ede) Your location will not be sent to outside your network and this step can also be skipped by clicking on `Configure in Settings Later`.<br\>You can cancel this wizard at any time and continue later by navigating to the following site: [http://localhost:8080/setup-wizard/](http://localhost:8080/setup-wizard/).  |
|2a. Click on `Select Add-ons to Install` and select the vendor of your smart device (e.g. [Philips hue](https://www.openhab.org/addons/bindings/hue/), [Lutron](https://www.openhab.org/addons/bindings/lutron/), [yeelight](https://www.openhab.org/addons/bindings/yeelight/), [LIFX](https://www.openhab.org/addons/bindings/lifx/), ...) or the protocol name supported by your smart device (e.g. [KNX](https://www.openhab.org/addons/bindings/knx/), [ZigBee](https://www.openhab.org/addons/bindings/zigbee/), [Z-Wave](https://www.openhab.org/addons/bindings/zwave/), [DALI](https://www.openhab.org/addons/bindings/dali/), [MQTT](https://www.openhab.org/addons/bindings/mqtt/), ...) - in our example "[Shelly](https://www.openhab.org/addons/bindings/shelly/)".<br /><br />2b. Click on `Install 4 add-ons` -> `Get Started`. You will be redirected back to openHAB's GUI, called **MainUI**.<br /><br />Note: Add-ons which connect to your smart device (or services) are called **binding** in openHAB. | ![setup_wizzard_binding](https://github.com/egoist6/openhab-docs/assets/76903043/0dd40791-5996-4de2-b20f-f8767f9c706d) The setup wizard already added three pre-defined add-ons. During this Guide they are not required but we recommend to install them for a later purpose.|
|3. For the next step we will be activating MainUI's side bar. | ![mainui_sidebar](https://github.com/egoist6/openhab-docs/assets/76903043/96c82687-809e-4924-8bac-3e24d090c0ac)|

## Step 3: Adding a smart device to openHAB

Estimated time: 3 minutes

A lightbulb (and many other smart devices) are Internet of **Things** devices (IoT). From now on we simply call those devices in openHAB a [**Thing**](/concepts/things.html), which is a digital representation of your real world smart device.

Before we continue with the next step, please follow our recommendation:

> [!IMPORTANT]
> Whenever you add a new binding to openHAB, please [**always read the documentation of the Add-on!**](https://www.openhab.org/addons/)
> It will save you a lot of time.

### a. Add a Thing to openHAB

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|1. Depending on your binding there are different configuration options available. In our example we can provide credentials if the Things are password protected.<br />Click on `Settings` -> Add-on Settings: `Show All` -> `<name of Binding>`.<br />In our case all Things have already been discovered automatically. | ![mainui_binding_config](https://github.com/egoist6/openhab-docs/assets/76903043/1b0e759f-b47a-410b-825a-b80a4503b878)|
|2. Scan for new Things.<br />In case your binding did not discovered your Things yet, we can scan for new Things.<br />Click on `Settings` -> `Things` -> press the `+` button -> `<name of binding>` -> `Scan`. | ![mainui_things_scan](https://github.com/egoist6/openhab-docs/assets/76903043/1a853cbb-f8cf-45cb-8e75-b42caf8ea1c5) |
|3. Add a new Thing.<br />After discovery, click on `<Thing name>` -> `Add as Thing` and enter a meaningful name of your Thing.<br />(You could also select `Add All` at the bottom of the list).<br /><br />Congratulations, you have added your first Thing to openHAB! | ![mainui_things_add](https://github.com/egoist6/openhab-docs/assets/76903043/7db86de8-053d-445c-9e91-86b67f1b273f) We recommend to define a syntax for your Thing names, such as: _BindingName-RoomName-PlaceOrPurpose-ThingType_ and apply them consistently across all your Things.|

For the next step we need to provide a little bit of background information first. Please read this section:

> [!IMPORTANT]
> As you already know a Thing in openHAB is the digital representation of a smart device in our real world. A smart device (and its openHAB Thing) offer a lot of functionalities or capabilities. In case of a smart light bulb (or a smart device controlling a light bulb) these are: set brightness, detect physical button press, power consumption, trigger alarms (e.g. overheating), signal strength, and many more.
> 
> A Thing in openHAB provides these different information, status, events, etc. seperately in different Communication-[**Channels**](/concepts/things.html#channels). A **Thing Channel** is similiar to a physical postbox, where information is provided so that a postman can pick them up and transport it to the receiver (such as our MainUI GUI).
> 
> In our example the postman is called [**Item**](/docs/concepts/items.html). The nice thing about our postman (i.e. item) is, he also works for us and can transport commands (like switch on light) back to the **Thing Channel**. To be more precise with the terms we use, an **Item** has a _state_ (like on/off, closed/open, 34 °C, 50%, 2 kWh), can send _commands_, can _trigger a rule_, can be _persisted_ and _interact with the GUI_ we are creating in one of the next steps.

### b. Add Items to a Thing

Let's start adding an Item (postman) to a Thing Channel (mailbox):

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|<li> Click on `Things`, select the Thing we just created and switch to the tab `Channels`.<br/><li> (As you can see there are a few channels available but for now we just need the channel for changing the brightness of our smart dimmer.)<br/><li> Click `Brightness` -> `Add Link to Item...` -> `Create a new Item`<br/><li> (For simplicity of this Guide we leave all Item attributes and profiles as they are. You'll find [more information here](/configuration/items.html).)<br/><li>Click `Link`| ![mainui_add_item_to_thing](https://github.com/egoist6/openhab-docs/assets/76903043/7df7a9a4-d6cd-4481-9600-3d79791e9a85)|
|We have successfully added an Item to a Thing Channel. All Items can be seen here: | ![mainui_item](https://github.com/egoist6/openhab-docs/assets/76903043/21eac381-98d0-47eb-bb5e-d795cfef0bb5)|

## Step 4: Create a button on GUI 

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|<li>


## What next?
<li>[Model](/tutorial/model.html)
<li>![image](https://github.com/egoist6/openhab-docs/assets/76903043/9f8c085b-faf7-4f3e-8101-f36da3912cc0)

➡️ 

