# Final Fantasy Mystic Quest AP World Setup Guide

## Required Software

- [Archipelago](https://github.com/ArchipelagoMW/Archipelago/releases). Make sure to check the box for `SNI Client`

- Hardware or software capable of loading and playing SNES ROM files
    - An emulator capable of connecting to SNI such as:
        - snes9x-rr from: [snes9x rr](https://github.com/gocha/snes9x-rr/releases),
        - BizHawk from: [BizHawk Website](http://tasvideos.org/BizHawk.html)
        - RetroArch 1.10.1 or newer from: [RetroArch Website](https://retroarch.com?page=platforms). Or,
    - An SD2SNES, FXPak Pro ([FXPak Pro Store Page](https://krikzz.com/store/home/54-fxpak-pro.html)), or other
      compatible hardware

- Your legally obtained Final Fantasy Mystic Quest 1.1 ROM file, probably named `Final Fantasy - Mystic Quest (U) (V1.1).sfc`
The Archipelago community cannot supply you with this.

- The AP World file: [ffmq.apworld](https://github.com/wildham0/FFMQRApWorld/blob/main/ffmq.apworld) (Current Version: 2013-06-18)

## Installation Procedures

### Windows Setup

1. During the installation of Archipelago, you will have been asked to install the SNI Client. If you did not do this,
   or you are on an older version, you may run the installer again to install the SNI Client.
2. After installing Archipelago, find the folder it was installed into (which by default is "C:\ProgramData\Archipelago";
   this will be called the "Root Folder" from here on), then enter the "lib" folder, then the "worlds" folder, and move the .apworld file there.
3. If you are using an emulator, you should assign your Lua capable emulator as your default program for launching ROM
   files.
    1. Extract your emulator's folder to your Desktop, or somewhere you will remember.
    2. Right-click on a ROM file and select **Open with...**
    3. Check the box next to **Always use this app to open .sfc files**
    4. Scroll to the bottom of the list and click the grey text **Look for another App on this PC**
    5. Browse for your emulator's `.exe` file and click **Open**. This file should be located inside the folder you
       extracted in step one.

## Create a Config (.yaml) File

### What is a config file and why do I need one?

All players (host or not) will need a .yaml config file containing the settings they want for their game.

### Where do I get a config file?

You can use the following config file template: [Final_Fantasy_Mystic_Quest.yaml](https://github.com/wildham0/FFMQRApWorld/blob/main/Final_Fantasy_Mystic_Quest.yaml)

## Joining a MultiWorld Game

### Obtain your patch file and create your ROM

When you join a multiworld game, you will be asked to provide your config file to whoever is hosting. Once that is done,
the host will provide you with either a link to download your patch file, or with a zip file containing
everyone's patch files. Your patch file should have a `.apmq` extension.

Go to the [FFMQR website](https://ffmqrando.net/Archipelago) and select your Final Fantasy Mystic Quest 1.1 ROM
and the .apmq file you received, choose optional preferences, and click `Generate` to get your patched ROM.

Manually launch the SNI Client, and run the patched ROM in your chosen software or hardware.

### Connect to the client

#### With an emulator

When the client launched automatically, SNI should have also automatically launched in the background. If this is its
first time launching, you may be prompted to allow it to communicate through the Windows Firewall.

##### snes9x-rr

1. Load your ROM file if it hasn't already been loaded.
2. Click on the File menu and hover on **Lua Scripting**
3. Click on **New Lua Script Window...**
4. In the new window, click **Browse...**
5. Select the connector lua file included with your client
    - Look in the Archipelago folder for `/SNI/lua/x64` or `/SNI/lua/x86` depending on if the
      emulator is 64-bit or 32-bit.
6. If you see an error while loading the script that states `socket.dll missing` or similar, navigate to the folder of 
the lua you are using in your file explorer and copy the `socket.dll` to the base folder of your snes9x install.

##### BizHawk

1. Ensure you have the BSNES core loaded. You may do this by clicking on the Tools menu in BizHawk and following these
   menu options:  
   `Config --> Cores --> SNES --> BSNES`  
   Once you have changed the loaded core, you must restart BizHawk.
2. Load your ROM file if it hasn't already been loaded.
3. Click on the Tools menu and click on **Lua Console**
4. Click the Open Folder icon that says `Open Script` via the tooltip on mouse hover, or click the Script Menu then `Open Script...`, or press `Ctrl-O`.
5. Select the `Connector.lua` file included with your client
    - Look in the Archipelago folder for `/SNI/lua/x64` or `/SNI/lua/x86` depending on if the
      emulator is 64-bit or 32-bit. Please note the most recent versions of BizHawk are 64-bit only.

##### RetroArch 1.10.1 or newer

You only have to do these steps once. Note, RetroArch 1.9.x will not work as it is older than 1.10.1.

1. Enter the RetroArch main menu screen.
2. Go to Settings --> User Interface. Set "Show Advanced Settings" to ON.
3. Go to Settings --> Network. Set "Network Commands" to ON. (It is found below Request Device 16.) Leave the default
   Network Command Port at 55355.

![Screenshot of Network Commands setting](/static/generated/docs/A%20Link%20to%20the%20Past/retroarch-network-commands-en.png)
4. Go to Main Menu --> Online Updater --> Core Downloader. Scroll down and select "Nintendo - SNES / SFC (bsnes-mercury
   Performance)".

When loading a ROM, be sure to select a **bsnes-mercury** core. These are the only cores that allow external tools to
read ROM data.

#### With hardware

This guide assumes you have downloaded the correct firmware for your device. If you have not done so already, please do
this now. SD2SNES and FXPak Pro users may download the appropriate firmware on the SD2SNES releases page. SD2SNES
releases page: [SD2SNES Releases Page](https://github.com/RedGuyyyy/sd2snes/releases)

Other hardware may find helpful information on the usb2snes platforms
page: [usb2snes Supported Platforms Page](http://usb2snes.com/#supported-platforms)

1. Close your emulator, which may have auto-launched.
2. Power on your device and load the ROM.

### Connect to the Archipelago Server

Your client should have automatically connected you to the AP Server. There are a few
reasons this may not happen however, including if the game is hosted on the website but was generated elsewhere. If the
client window shows "Server Status: Not Connected", simply ask the host for the address of the server, and copy/paste it
into the "Server" input field then press enter.

The client will attempt to reconnect to the new server address, and should momentarily show "Server Status: Connected".

### Play the game

When the client shows both SNES Device and Server as connected, you're ready to begin playing. Congratulations on
successfully joining a multiworld game!

## Hosting a MultiWorld game

The recommended way to host a game is to use our hosting service. The process is relatively simple:

1. Collect config files from your players.
2. Put the newly collected .yaml files in your "Root/Players" folder.
3. Make sure once again that you have the FFMQ .apworld file in the "Root/lib/worlds" directory.
4. Run "ArchipelagoGenerate.exe". If it doesn't spit out an error, a .zip file should appear in your "Root/output" folder with everything the players need to connect to the game.
5. Go to the [Host Game page](https://archipelago.gg/uploads) on Archipelago.gg and uploads your .archipelago file.
7. Click "Create New Room". This will take you to the server page. Provide the link to this page to your players, so
   they may download their patch files from there. For FFMQR player, their .apmq file should be distribitued manually by the the host.
8. Note that a link to a MultiWorld Tracker is at the top of the room page. The tracker shows the progress of all
   players in the game. Any observers may also be given the link to this page.
9. Once all players have joined, you may begin playing.
