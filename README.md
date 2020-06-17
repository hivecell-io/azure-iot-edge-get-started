# azure-iot-edge-get-started
Initial guide to start simple test application on Hivecell One, connected with Azure IoT Edge

---
platform: Ubuntu 18.04

device: Hivecell One

language: Java 

---

Run a simple Java sample on Hivecell One device running Ubuntu 18.04.
===
---

# Table of Contents

-   [Introduction](#Introduction)
-   [Step 1: Prerequisites](#Prerequisites)
-   [Step 2: Prepare your Device](#PrepareDevice)
-   [Step 3: Manual Test for Azure IoT Edge on device](#Manual)
-   [Step 4: Next Steps](#NextSteps)
-   [Step 5: Troubleshooting](#Step-5-Troubleshooting)

<a name="Introduction"></a>
# Introduction

**About this document**

This document describes how to connect Hivecell One device running Ubuntu 18.04 with Azure IoT Edge Runtime and Device Management and run simple package from Azure Marketplace. This multi-step process includes:

-   Configuring Azure IoT Hub
-   Deploying Azure IoT Runtime on device
-   Registering your IoT device
-   Deploing client component to test device management capability 

<a name="Prerequisites"></a>
# Step 1: Prerequisites

You should have the following items ready before beginning the process:

-   [Setup your IoThub](https://account.windowsazure.com/signup)
-   [Provision your device and get its credentials][lnk-manage-iot-hub]
-   [Sign up to IOT Hub](https://account.windowsazure.com/signup?offer=ms-azr-0044p)
-   [Add the Edge Device](https://docs.microsoft.com/en-us/azure/iot-edge/quickstart-linux)
-   [Add the Edge Modules](https://docs.microsoft.com/en-us/azure/iot-edge/quickstart-linux#deploy-a-module)
-   {enter your device name here} device.

<a name="PrepareDevice"></a>
# Step 2: Prepare your Device

- Unpack device from the box on receival
- Attach ethernet cable and power cable on the back pancel.  You can check how it is done on the following video:
(https://www.youtube.com/watch?v=KbPPrv7RZS0)
- Power on the device as per video above
- Once it is loaded you are able to connect to it via the ssh. Credentials for initial ssh connect are provided in the box, device was shipped in.

<a name="Manual"></a>
# Step 3: Manual Test for Azure IoT Edge on device

<a name="Step-3-1-IoTEdgeRunTime"></a>
## 3.1 Edge RuntimeEnabled (Mandatory)

**Details of the requirement:**

The following components come pre-installed or at the point of distribution on the device to customer(s):

-   Azure IoT Edge Security Daemon
-   Daemon configuration file
-   Moby container management system
-   Hivecell Platform agent

*Edge Runtime Enabled:*

**Check the iotedge daemon command:** 

Open the command prompt on your Hivecell One device, confirm that the Azure IoT edge Daemon is under running state

    systemctl status iotedge

 
 ![]()

Open the command prompt on your IoT Edge device, confirm that the module deployed from the cloud is running on your IoT Edge device

    sudo iotedge list

 ![]() 

On the device details page of the Azure, you should see the runtime modules - edgeAgent, edgeHub and tempSensor modueles are under running status

 ![](./images/tempSensor.PNG)

<a name="Step-3-2-DeviceManagement"></a>
## 3.2 Device Management (Mandatory)

**Pre-requisites:** Device Connectivity.

**Description:** A device that can perform basic device management operations (Reboot and Firmware update) triggered by messages from IoT Hub.

## 3.2.1 Firmware Update (Using Microsoft SDK Samples):

Specify the path {{enter the path}} where the firmwareupdate client components are installed.

To run the simulated device application, open a shell or command prompt window and navigate to the **iot-hub/Tutorials/FirmwareUpdate** folder in the Node.js project you downloaded. Then run the following commands:

    npm install
    node SimulatedDevice.js "{your device connection string}"

To run the back-end application, open another shell or command prompt window. Then navigate to the **iot-hub/Tutorials/FirmwareUpdate** folder in the Node.js project you downloaded. Then run the following commands:

    npm install
    node ServiceClient.js "{your service connection string}"

IoT device client will get the message and report the status to the device twin.

 ![](./images/devicetwin.PNG)

**Update firmware**

Confirm the IoT hub, Device ID, method name and method payload as below:

-   Press “call Method” button
-   Check the returning status as below:

 ![](./images/firmware.PNG)


## 3.2.2 Reboot (Using Microsoft SDK Samples):

Specify the path {{enter the path}} where the components are installed 

Confirm the IoT hub, Device ID, method name as below:

-   Press “call Method” button
-   Check the returning status as below:

 ![](./images/reboot.PNG)


IoT device client will get the message and report the status to the device twin.

 ![](./images/devicetwinmessage.PNG)

## 3.3.3 Firmware Update (Modified SDK samples/Custom made application):

If the Client components are custom made please add the steps to execute the Firmware Update through Device Twin.

**Note**: Client Components must be shipped with the device 

## 3.3.4 Reboot (Modified SDK samples/Custom made application):

If the Client components are custom made please add the steps to execute the Device Reboot through Direct Methods

**Note**: Client Components must be shipped with the device 

<a name="NextSteps"></a>
# Step 4: Next steps

Once you shared the documents with us, we will contact you in the following 48 to 72 business hours with next steps.

<a name="Step-5-Troubleshooting"></a>
# Step 5: Troubleshooting

Please contact engineering support on **<mailto:iotcert@microsoft.com>** for help with troubleshooting.

[setup-devbox-linux]: https://github.com/Azure/azure-iot-sdk-c/blob/master/doc/devbox_setup.md
[lnk-setup-iot-hub]: ../setup_iothub.md
[lnk-manage-iot-hub]: ../manage_iot_hub.md
