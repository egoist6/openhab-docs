---
layout: documentation
title: Quick Guide for new users
---

# Quick Guide

This Quick Guide is aimed at new users who simply want to install openHAB on their PC to see how it works. 
It will give you step-by-step instructions for the whole process from downloading openHAB until switching on/off a smart device by your mobile phone and automatically at the time you go to bed.

You will see how easy it is and you do not have to be a home automation or IT expert.

> [!Note]
> Minimum skill level required for this Quick Guide:
> 
> We recommend that you have knowledge how to unzip files and what IP addresses are.

[[toc]]

## Step 1: Install and Start openHAB

Estimated time: 3 minutes

We are going to intall openHAB on a Windows PC. Almost any Windows PC will do, as openHAB requires very little resources. If you want to install openHAB on a different platform, please refer for Step 1 of this Quick Guide to our [Installation Documentation](installation.html).

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|Download openHAB<li>Go to [openHAB Download Website](https://www.openhab.org/download/) <li>Click `Windows` ➡️ `Stable` ➡️ `Download openHAB Stable Runtime`.|![download_openhab](https://github.com/egoist6/openhab-docs/assets/76903043/9e59b846-4aa6-450d-bad4-dd7ec60add08) |
|Installation<li>As there is no installation program, simply unzip the downloaded `.zip` file to your preferred folder like `C:\Program Files\openHAB` (requires admin rights) or `C:\openHAB`. | ![unzip_openhab](https://github.com/egoist6/openhab-docs/assets/76903043/0bf58a31-2132-4fe8-8a4b-0609d156372b)|
|Download & Install OpenJDK<li>Download OpenJDK from [OpenJDK Download Website](https://cdn.azul.com/zulu/bin/zulu17.44.53-ca-jre17.0.8.1-win_x64.msi)<li>Double click the `.msi` file to start installation|openHAB requires Java runtime (JRE) version 17<br/>Installation of OpenJDP requires admin rights |
|Before installation starts, change "Set JAVA_HOME variable" to "Will be installed on local drive." | ![java_home](https://github.com/egoist6/openhab-docs/assets/76903043/e3bf9c45-3fae-417a-b4c9-75328048d90b)|
|Start openHAB<li>Double click `..\openHAB\start.bat` and minimize the window when you see the following screen.<li>(In case Windows Defender pops up, click `Allow Access`.)|![image](https://github.com/egoist6/openhab-docs/assets/76903043/f5ff4a12-3c49-48de-95de-fe6aa99c82b6) If you want to run openHAB as a service, [see here](/installation/windows.html#set-up-openhab-to-run-as-a-windows-service).|
|Open openHAB GUI<li>Open [http://localhost:8080/](http://localhost:8080/) in your browser<li>(or `<IP-address>:8080/` if you connect from another device (such as your mobile phone).<li>On the very first start you are asked to create an admin user.<br/><br/>Congratulations, you have successfully installed openHAB! | ![create_admin](https://github.com/egoist6/openhab-docs/assets/76903043/e84ee45e-3ed2-4ff5-a8a6-3d0cce8c5e89)|

## Step 2: Setup Wizard

Estimated time: 1 minute

On the first run and after you have created an admin user, a **Setup Wizard** is started automatically in the GUI.

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|Basic Settings<li>Set Language, Region, Time Zone<li>Set Location of your home<li>Click `Configure in Settings Later` to skip this step| ![setup_wizzard_location](https://github.com/egoist6/openhab-docs/assets/76903043/8a5391b1-acc6-4723-aa04-4ab2e6f72ede) Your location will not be sent outside your network.<br/>You can cancel this wizard at any time and continue later by navigating to the following site: [http://localhost:8080/setup-wizard/](http://localhost:8080/setup-wizard/).  |
|Add-ons<li>Click `Select Add-ons to Install` ➡️ select the vendor of your smart device (e.g. [Philips hue](https://www.openhab.org/addons/bindings/hue/), [Lutron](https://www.openhab.org/addons/bindings/lutron/), [yeelight](https://www.openhab.org/addons/bindings/yeelight/), [LIFX](https://www.openhab.org/addons/bindings/lifx/), ...) or the protocol name supported by your smart device (e.g. [KNX](https://www.openhab.org/addons/bindings/knx/), [ZigBee](https://www.openhab.org/addons/bindings/zigbee/), [Z-Wave](https://www.openhab.org/addons/bindings/zwave/), [DALI](https://www.openhab.org/addons/bindings/dali/), [MQTT](https://www.openhab.org/addons/bindings/mqtt/), ...) - we use"[Shelly](https://www.openhab.org/addons/bindings/shelly/)" in our example.<li>Click `Install 4 add-ons` ➡️ `Get Started`.<li>You will be redirected back to openHAB's GUI, called **MainUI**.<li>Note: Add-ons which connect to your smart device (or services) are called **Bindings** in openHAB. | ![setup_wizzard_binding](https://github.com/egoist6/openhab-docs/assets/76903043/0dd40791-5996-4de2-b20f-f8767f9c706d) The setup wizard already added three pre-defined add-ons. During this Quick Guide they are not required but we recommend to install them for a later purpose.|
|Pin MainUI's side bar (optional) | ![mainui_sidebar](https://github.com/egoist6/openhab-docs/assets/76903043/96c82687-809e-4924-8bac-3e24d090c0ac)|

## Step 3: Adding a smart device to openHAB

Estimated time: 3 minutes

Smart lightbulbs, smart roller shutter, temperature sensors (and many other smart devices) are called _Internet of **Things**_ devices (IoT). In openHAB we call those IoT devices also a [**"Thing"**](/concepts/things.html). An openHAB Thing is the digital representative of your real world IoT device.

Before we continue with the next step, please follow our recommendation:

> [!IMPORTANT]
> Whenever you add a new binding to openHAB, please [**always read the documentation of the Add-on!**](https://www.openhab.org/addons/)
> It will save you a lot of time.

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|Configure Binding (optional)<li>Check if there are any important settings available for your Binding first<li>Click `Settings` ➡️ `Show All` (Add-on Settings) ➡️ `<name of Binding>`.<li>(These settings depend on your specific Binding. In our case we provide credentials, because the smart controller is password protected)<li>Note: In our case openHAB has already discovered many Things automatically. | ![mainui_binding_config](https://github.com/egoist6/openhab-docs/assets/76903043/1b0e759f-b47a-410b-825a-b80a4503b878)|
|Scan for new Things<li>In case your binding did not discovered your Things yet, we can scan for new Things.<li>Click `Settings` ➡️ `Things` ➡️ press the `+` button ➡️ `<name of binding>` ➡️ `Scan`. | ![mainui_things_scan](https://github.com/egoist6/openhab-docs/assets/76903043/1a853cbb-f8cf-45cb-8e75-b42caf8ea1c5) |
|Add a new Thing<li>After discovery, click `<Thing name>` ➡️ `Add as Thing` ➡️ enter a meaningful name of your Thing.<li>(You could also select `Add All` at the bottom of the list).<br /><br />Congratulations, you have added your first Thing to openHAB! | ![mainui_things_add](https://github.com/egoist6/openhab-docs/assets/76903043/7db86de8-053d-445c-9e91-86b67f1b273f) We recommend to define a syntax for your Thing names, such as: _BindingName-RoomName-PlaceOrPurpose-ThingType_ and apply them consistently across all your Things.|

> [!IMPORTANT]
> For the next step we need to provide a little bit of background information first:
> 
> As you already know a Thing in openHAB is the digital representation of a smart device in our real world. A smart device (and its openHAB Thing) offers a lot of functionalities or capabilities. In case of a smart light bulb (or a smart device controlling a light bulb) these are: set brightness, detect physical button press, power consumption, trigger alarms (e.g. overheating), signal strength, and many more.
> 
> A Thing in openHAB provides these different information, status, events, etc. seperately in different Communication-[**Channels**](/concepts/things.html#channels). A **Thing Channel** is similiar to a physical postbox, where information is provided so that a postman can pick them up and transport it to the receiver (such as our MainUI GUI).
> 
> In our example the postman is called [**Item**](/docs/concepts/items.html). The nice thing about our postman (i.e. Item) is, he also works for us and can transport commands (like "switch on light") back to the **Thing Channel**. To be more precise with the terms we use, an **Item** has a _state_ (like on/off, closed/open, 34 °C, 50%, 2 kWh), can receive _commands_, can _trigger a rule_, can be _persisted_ and _interact with the GUI_ we are creating in one of the next steps.

Let's continue with adding an Item (postman) to a Thing Channel (mailbox):

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|Add Item to a Thing<li> Click `Things` ➡️ select the Thing we just created ➡️ switch to the tab `Channels`.<li> (As you can see there are quite a few channels available but for now we just need the channel for changing the brightness of our smart dimmer.)<li> Click `Brightness` ➡️ `Add Link to Item...` ➡️ `Create a new Item` ➡️ `Link`<li> (During this Quick Guide it is not required to change Item attributes and profiles as you may have noticed in this step. You'll find [more information here for later on](/configuration/items.html).)| ![mainui_add_item_to_thing](https://github.com/egoist6/openhab-docs/assets/76903043/7df7a9a4-d6cd-4481-9600-3d79791e9a85)|
|Overview of all Items in openHAB.<br/><br/>Congratulations, you have added your first Item to an openHAB Thing! | ![mainui_item](https://github.com/egoist6/openhab-docs/assets/76903043/21eac381-98d0-47eb-bb5e-d795cfef0bb5)|

## Step 4: Configure GUI / create automation

Estimated time: x minutes

In our last step we will be adding a slider button for our dimmable smart device to the GUI. The button switches the light off and restores the dimmed value when switching on. If you click the menu icon of the button `⋮`, a popup appears where you comfortably can set the new value.

todo: add gif here of slider widget, to see what we are going to do in this step.

|Steps|Notes|
|----------------------------------------------------------------|---------------------------------------------------------------|
|Add slider button to GUI<li>Click `Pages` ➡️ `Add Block` ➡️ `Add Cells` ➡️ `+` ➡️ `Slider Cell`<li>(for roller shutters use `Rollershutter Cell`)<li>(for color lamps use `Colorpicker Cell`)<li>(for switches use `Label Cell`)| ![mainui_add_slider](https://github.com/egoist6/openhab-docs/assets/76903043/75912670-9a07-44be-ae04-ffa5239bfbe8)|
|Configure slider button<br/>Explanation of the configuration parameters:<li>`Header`, `Title`, `Subtitle`, `Footer`: these are labels<li>`Slider Item`: item which we send a command to when using a slider<li>`Action`: Action to perform when the button is pressed (here: Toggle Item)<li>`Action Item`: item which we send a command to when pressing the button| ![mainui_configure_slider](https://github.com/egoist6/openhab-docs/assets/76903043/4bad9112-5b9f-4d79-abcc-081a5d0aede2)|
|Test slider button<li>Click `Run Now`, toggle on off, open popup |  |
|no button color change to see if Light is on or off, advanced settings =(@'ShellyLivingRoomFloorLampDimmer_Brightness' == "0")?true:false, hit save button||
|View the whole page<li>Open [http://localhost:8080/page/overview](http://localhost:8080/page/overview) in a new tab of your browser<li>(or `<IP-address>:8080/page/overview` on your mobile Phone)|  |
|done. these are the fundamentals. now home **automation** begins: create rule and schedule| |

todo
add a result in the beginning what the reader will have learnt by the end of each step

## What next?

![Model](/tutorial/model.html)
Widgets
Examples of widgets and pages
![image](https://github.com/egoist6/openhab-docs/assets/76903043/9f8c085b-faf7-4f3e-8101-f36da3912cc0)
