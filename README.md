# GRiSP.io
This repository is dedicated exclusively to tracking issues for the [GRiSP.io](https://grisp.io) platform. Here, you can report bugs, request features, and discuss problems specifically related to GRiSP io. Please note that this is not the place for general discussions or questions about GRiSP io; it is solely for issue tracking.

Before posting a new issue, kindly check if it has already been reported or addressed. This helps us avoid duplicates and respond more efficiently to your concerns.

✨Thank you for contributing to the improvement of GRiSP.io!

## How to use your GRiSP2 board with GRiSP.io
### Link a device
#### Automatic linking (ethernet only)
1. **Download** the prebuilt Application linked to your account on [GRiSP.io](https://app.grisp.io/grisp-manager)
2. **Prepare Your SD Card:** Extract the zip file onto a `Fat32` (on Mac is called Format `MS-DOS FAT`) formatted SD card and insert it into your `GRiSP2` board. 
3. **Initiate Automatic Registration:** Connect your board to the internet via an ethernet cable. It will automatically link to your account, which you can verify under the Devices section on [grisp.io](https://app.grisp.io/grisp-manager).

#### Manual linking (Ethernet and Wi-Fi)
**Prerequirement**: You need to setup a development Environment following this [guide](https://github.com/grisp/grisp/wiki/Setting-Up-a-Development-Environment)

If you prefer a hands-on approach or require a custom setup, you can follow these steps:

In this tutorial, we will use the name `robot` for the project. The SD card path `/tmp/sd_card` should be replaced with the path where your SD-card is mounted.

1. **Creating the project**: Follow the CLI instruction by `rebar3 grisp configure`. It will guide you in the creation of the application with all the required dependencies. In the following example, we setup a Wi-Fi connection but this can be skipped by pressing "n". We also activate distributed Erlang if you want to use the remote shell. Additionally, you will have to replace the value "MyToken" by your own private token from [grisp.io](https://app.grisp.io/grisp-manager)
```
   $ cd ~/GRiSP
   $ rebar3 grisp configure
   App name (robot)> # Enter the name of your application
   Erlang version (25)> # Specify the Erlang version to use, default is version 25
   SD Card Path (/path/to/SD-card)> # Define the path to the SD card where the application will be deployed
   Use Wi-Fi ?(y/N)> y # Here if you want to use ethernet press "n"
   Use Network ?(y/N)> y
   Wi-Fi SSID (My Wifi)> my_wifi
   Wi-Fi Password (...)> my_psk
   Enable GRiSP.io integration ?(y/N)> y
   Do you need to link your GRiSP-2 board ?(y/N)> y
   Please enter your personal device linking token (...)> MyToken # Enter your private token from GRiSP io account
   Enable Distributed Erlang ?(y/N)> y
   Erlang Cookie (grisp)> mycookie
   $ cd robot
```
2. **Deploy and access the Erlang shell on your board:** [Deploy](https://github.com/grisp/grisp/wiki/Deploying-a-GRiSP-Application) your application and then access to the Erlang shell on your board. There are two ways to connect to the GRiSP board shell, depending on whether you want to use a [serial (USB)](https://github.com/grisp/grisp/wiki/Connecting-over-Serial) or the [remote shell](https://github.com/grisp/grisp/wiki/Connecting-over-WiFI-and-Ethernet#remote-shell).

3. **Link the device using the following command:** In the Erlang shell of your board run:
```
grisp_connect:link_device().
```
