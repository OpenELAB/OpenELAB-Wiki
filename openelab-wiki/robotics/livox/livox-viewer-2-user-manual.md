# LIVOX Viewer 2 User Manual

> LIVOX Viewer 2 User Manual

{% embed url="https://www.livoxtech.com/downloads" %}

| : **Searching for Keywords** Search for keywords such as “cloud” and “firmware” to find a topic. If you are using Adobe Acrobat Reader to read this document, press Ctrl+F on Windows or Command+F on Mac to begin a search. |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| :**Navigating to a Topic** View a complete list of topics in the table of contents. Click on a topic to navigate to that section.                                                                                            |
| :**Printing this Document** This document supports high resolution printing.                                                                                                                                                 |

### Using this Manual <a href="#block-394d4c79856d80c8b0a6da8ad159de05" id="block-394d4c79856d80c8b0a6da8ad159de05"></a>

**Legend**

| :Prohibited | :Important | :Hints and Tips | <p><img src="https://s3-us-west-2.amazonaws.com/public.notion-static.com/c9870ad6-a7c7-40a4-9d0d-802128cdc7c8/7.png" alt="" data-size="original"></p><p>:Reference</p> |
| ----------- | ---------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Purpose <a href="#block-394d4c79856d80c8af63dda2d1b77dfd" id="block-394d4c79856d80c8af63dda2d1b77dfd"></a>

This user manual describes the functions and operating environments of Livox Viewer 2, to provide users with information on the scope and methods of use as well as updates of the software. Livox updates this user manual from time to time. Visit the Livox official website to download the latest user manual.

## Term Definition <a href="#block-394d4c79856d800c9322f6507cc96dee" id="block-394d4c79856d800c9322f6507cc96dee"></a>

**Direct connection:** Connecting one end of a network cable to the Livox device and the other end to the network port.

**Extrinsic parameters:** They describe the conversion of data captured by a Livox device from its own coordinate system to the world coordinate system, and include six variables namely roll, pitch, yaw, x, y, and z. For the definitions of and how to calculate the parameters, see the “Calibrating Extrinsic Parameters” section.

## **Introduction** <a href="#block-394d4c79856d80489b1ac8948dbf97ab" id="block-394d4c79856d80489b1ac8948dbf97ab"></a>

### Livox Viewer 2 <a href="#block-394d4c79856d807a94c7cb1d11e8d0b3" id="block-394d4c79856d807a94c7cb1d11e8d0b3"></a>

Livox Viewer 2 is a software designed specially to display all point cloud data transmitted to a computer in real time. Users can view, record, and store point cloud data with ease for future use.

### Supported Systems <a href="#block-394d4c79856d8003967cde81b0d6adb2" id="block-394d4c79856d8003967cde81b0d6adb2"></a>

Livox Viewer 2 is compatible with Windows 10 (64 bit) and Ubuntu 18.04 (64 bit).

### System Requirements <a href="#block-394d4c79856d80079673e89c6492a152" id="block-394d4c79856d80079673e89c6492a152"></a>

No special configurations are required for using Livox Viewer 2, except for the graphics card of the computer due to the point cloud display function of the software. If you will be running real-time display of point cloud data from multiple Livox LiDARs, make sure your computer is using an independent graphics card of higher specifications. The display quality of Livox Viewer 2 is positively correlated to the graphics card performance of the computer.

## Getting Ready <a href="#block-394d4c79856d806aaf68ffedfc15ea5b" id="block-394d4c79856d806aaf68ffedfc15ea5b"></a>

### Connecting Livox LiDAR to PC <a href="#block-394d4c79856d80db95a3ce4f48364a06" id="block-394d4c79856d80db95a3ce4f48364a06"></a>

Make sure the Livox device is plugged into a 12V power source. If you are using a Livox HAP, connect the device directly to the network port on the PC with a network cable.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/84b38ff4-f939-4555-841a-e7c7fde9058f/image/w=1920,quality=90,fit=scale-down" alt="image" height="69.70962753295898" width="83.98750305175781">

| • The above connection method only works with Livox devices whose IP address type has not been changed. • Network cables can also be connected to a network switch or router, but make sure to differentiate between a switch and a router.，plug the cable into the LAN port and not the WAN port of the router. Plugging into the wrong network port may cause the Livox device to malfunction. • The topology of physical connections for Livox devices can be found in the user manual of the respective product. |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Disabling Firewall on Computer <a href="#block-394d4c79856d80f5b3ced5cd0b1522ae" id="block-394d4c79856d80f5b3ced5cd0b1522ae"></a>

Due its use of a higher network port number for communication, your Livox device may be blocked by the firewall of the operating system. Before using Livox Viewer 2, make sure to disable the firewall on your PC so that data can be transmitted smoothly from the Livox device.

### Configuring IP Address on PC <a href="#block-394d4c79856d80ca898fe3f62062e3ab" id="block-394d4c79856d80ca898fe3f62062e3ab"></a>

When connecting your PC to a router, you need to set a dynamic IP address on your PC (“Obtain an IP address automatically” for Windows users). For connecting your PC with a Livox device, set a static IP in the IP settings of your PC, with an IP address of 192.168.1.2, subnet mask of 255.255.255.0, and default gateway of 192.168.1.1.

### Checking Graphics Card Driver on PC <a href="#block-394d4c79856d80f0a61cf3bb31772f25" id="block-394d4c79856d80f0a61cf3bb31772f25"></a>

Before using Livox Viewer 2, make sure your PC has been installed with a compatible driver for its display adapter. If the driver malfunctions, Livox Viewer 2 may not be able to start up or may crash upon activation. Make sure that the CPU of your PC supports the AVX2 (Advanced Vector Extensions 2) instruction set (Intel users are advised to use CPUs with 8th Generation Intel® Core™ i5 or higher processors).

## Using the Software <a href="#block-394d4c79856d800797bbc33257a94eab" id="block-394d4c79856d800797bbc33257a94eab"></a>

### Downloading the Livox Viewer 2 <a href="#block-394d4c79856d8087a67bf3282713e065" id="block-394d4c79856d8087a67bf3282713e065"></a>

Visit the Livox official website www.livoxtech.com and download the latest version of Livox Viewer 2.

**For Windows users:** Download and unzip the file, and open the program LivoxViewer2.exe in the root directory of the unzipped folder. **Ubuntu users:** Download and unzip the file, and run the following command in the root directory of the unzipped folder: ./livox\_viewer\_2.sh.

### Interface Introduction <a href="#block-394d4c79856d80cb814bde059924a0b2" id="block-394d4c79856d80cb814bde059924a0b2"></a>

Open Livox Viewer 2, and the software interface will appear. The interface consists of three parts: the toolbar, device manager, and point cloud display interface.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bc3d0525-f4eb-4c72-959f-0a60d2b69f73/image/w=1920,quality=90,fit=scale-down" alt="Point Cloud Display Interface" height="301.9718309859155" width="720">

Point Cloud Display Interface

**Toolbar Buttons**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e22bd7f7-74c7-493b-826f-e343ae8b5456/image/w=1920,quality=90,fit=scale-down" alt="image" height="20.507774879614768" width="709.796875">

The functions of the toolbar buttons are as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9fd656ab-42dc-42e7-aaf1-50cff83c33d8/image/w=1920,quality=90,fit=scale-down" alt="image" height="42.57674418604651" width="199">

the IP address of the adapter, which must be configured to be in the same network segment as the Livox device, in order to detect

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3c0746be-1033-4e73-9a06-b5af3fd385e1/image/w=1920,quality=90,fit=scale-down" alt="image" height="50.16216216216216" width="58">

open saved point cloud data files in lvx2 or cxv format.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f04ce168-6349-4be9-936b-6dff8894de23/image/w=1920,quality=90,fit=scale-down" alt="image" height="38.37931034482759" width="42">

show/hide Livox device manager.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5a1ea65d-bfef-4cae-85e2-de5268547e92/image/w=1920,quality=90,fit=scale-down" alt="image" height="37.33333333333333" width="36">

set attribute and parameter settings for the Livox device.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/aca6c98f-f008-41f6-be81-85513693d5af/image/w=1920,quality=90,fit=scale-down" alt="image" height="50.4406779661017" width="48">

show/hide electronic table to frame and select point clouds on interface.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ffd3dd0a-c904-4291-bfa8-4fe6f3458b61/image/w=1920,quality=90,fit=scale-down" alt="image" height="49.24242424242424" width="50">

show/hide extrinsic parameter calibration tools.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5e3d746d-cd26-434d-974c-165228173847/image/w=1920,quality=90,fit=scale-down" alt="image" height="44.59649122807018" width="41">

show/hide grid coordinates.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/63bb998a-1eae-46f5-b463-bea002b3557a/image/w=1920,quality=90,fit=scale-down" alt="image" height="50.88" width="48">

reset point cloud interface and display all point clouds in the center.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/92b46319-3904-4873-812e-5cf6f2dc410a/image/w=1920,quality=90,fit=scale-down" alt="image" height="61.09022556390977" width="250">

select angle for viewing point cloud data, from right, front, top, or rear view.

Besides clicking the icon to switch viewing angles, users can also adjust the point cloud view in the following manner: a. Roll the scroll wheel on the mouse to zoom in/out;

b. Right-click and drag the mouse to pan across the point cloud;

c. Left-click and drag the mouse to adjust the viewing angle.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6b56012d-2c06-48ce-be24-5a4e9b9ba397/image/w=1920,quality=90,fit=scale-down" alt="image" height="32.890756302521005" width="103">

set the size of the central point of the point cloud, between: 1px, 2px, 3px, 4px, or 5px.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4746f7db-8011-4f3d-9b6a-7d2bec44e064/image/w=1920,quality=90,fit=scale-down" alt="image" height="29.428571428571427" width="103">

set a color scheme for the point cloud, including with fixed colors, or based on reflectivity, LiDAR ID, depth, or altitude (by default, point cloud will be colored according to reflectivity).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b41e485f-53cd-403a-a9f2-9999d2950356/image/w=1920,quality=90,fit=scale-down" alt="image" height="27.094488188976378" width="111">

frame integration time, which can be set as 100, 200, 500, 1000, or 3000 ms; the longer the frame integration time, the denser the point cloud image.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ec437fc6-4fee-40a1-bc26-dd1bae482b9f/image/w=1920,quality=90,fit=scale-down" alt="image" height="21.082191780821915" width="57">

including firmware upgrade, file converter, noise filter, grid property, and color coding.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/79d68b55-f479-44f7-adc6-555f21998bb4/image/w=1920,quality=90,fit=scale-down" alt="image" height="28.30769230769231" width="23">

debugging tools, for emailing the local operation and debugging logs to the developer of Livox Viewer 2.

full screen/window mode.

:

**Livox Device Manager**

In the menu bar, click to open the device manager. The device manager interface is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b619a1f1-c08c-490a-b01f-05256ef3601a/image/w=1920,quality=90,fit=scale-down" alt="image" height="449.65155807365437" width="337">

If Livox Viewer 2 detects a linked device, the information of the device (including its serial number, device type, current status, and error code) and the relevant control buttons will appear in the window of the device manager.

: connect or disconnect the selected device.

: show or hide the point cloud data of the current linked device.

: start or stop capturing data with the current linked device.

**Point Cloud Display Interface**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bf653861-4edb-40e8-926e-45182849c91b/image/w=1920,quality=90,fit=scale-down" alt="image" height="369.42682926829275" width="709.9921875">

Livox Viewer 2 will connect to a device and start capturing data; or users may open a saved point cloud recording file and the interface will display the point cloud image. In the bottom left of the point cloud interface are reference coordinates, while at the center is a distance grid that runs from 10 to 300 m.

### Frequently Used Functions <a href="#block-394d4c79856d80569045ecb8bf104792" id="block-394d4c79856d80569045ecb8bf104792"></a>

The following are the frequently used functions of Livox Viewer 2.

**Viewing Real-time Point Cloud Images**

After connecting to a Livox device, select the device whose point cloud images you would like to view from the device list in the manager.

1.  Click&#x20;

    <img src="https://s3-us-west-2.amazonaws.com/public.notion-static.com/c8f61869-ec3f-43e9-ad5a-cf17a634087e/11.png" alt="" height="100%" width="100%">

    &#x20;to connect to a device.
2.  After connecting to the device, click&#x20;

    <img src="https://s3-us-west-2.amazonaws.com/public.notion-static.com/4e1a708c-f42b-4fa7-9def-a5f9ef7d9d6d/13.png" alt="" height="100%" width="100%">

    &#x20;to begin capturing data. The point clouds captured will be drawn on the point cloud interface.
3. During the data capturing, click the record button to start or stop recording the point cloud data.

**Playing Back Point Cloud Images**

Click  in the toolbar to open a lvx2 or csv point cloud file. After the file is read, the Device List interface will display information of the recording device for the lvx2 file.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2a1d3ec4-715c-4619-82d6-f4f5d822774f/image/w=1920,quality=90,fit=scale-down" alt="image" height="388.7012987012987" width="292">

Below the toolbar is the player control bar:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7779688a-6cf8-4a38-94f4-b79d72ef27d3/image/w=1920,quality=90,fit=scale-down" alt="image" height="37.13636363636364" width="688">

The functions of the player control bar are as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/90ec73cd-5f06-4f57-b203-d82952a47863/image/w=1920,quality=90,fit=scale-down" alt="image" height="31.30769230769231" width="88">

set playback speed at 0.5, 1.0, 2.0, 4.0, or 8.0 times.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d1b3eb39-1dd4-48d7-b1ee-cb1270d0875e/image/w=1920,quality=90,fit=scale-down" alt="image" height="36.6" width="244">

playback progress bar and time. Users can drag the progress bar to start playing at any point.

: return to the starting point.

: go back to the previous frame.

&#x20;: play/stop

: move to the next frame.

: jump to the end.

: start recording. Click again to end recording.

: stop playing

&#x20;: show/hide point cloud images of the selected Livox device.

* When playing a lvx2 point cloud file, you can use the recording function to convert any part of the current file into a new lvx2 file.

**Adjusting Device Parameters**

After connecting to the Livox device, click the  button in the toolbar to open the parameter setting interface for the device as shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/877a33bf-703a-47e2-a774-c1b27b2d164c/image/w=1920,quality=90,fit=scale-down" alt="image" height="295.8252100840336" width="579">

On the interface, you can view and modify the parameters of the Livox device.

**Calibrating Extrinsic Parameters**

Click the  button in the toolbar to open the calibration tools for extrinsic parameters. The tool interface is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/357ce999-4d91-40f5-84f2-008ca443666d/image/w=1920,quality=90,fit=scale-down" alt="image" height="373.62162162162167" width="576">

&#x20;: group multiple devices. The change of any extrinsic parameter will apply to all selected devices.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d62c8ca4-2cc9-4b2f-92b3-bdbbd971a34e/image/w=1920,quality=90,fit=scale-down" alt="image" height="31.29353233830846" width="185">

set the degree of precision for parameter adjustment, between 1, 0.1, and 0.01.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cec0fe4f-6874-4326-bdef-ab7312ce5876/image/w=1920,quality=90,fit=scale-down" alt="image" height="32.268292682926834" width="189">

drag the bar to set the selected parameter.

: increase or decrease the parameter value. Each click will change the value at the current degree of precision set.

: save the current set parameters into an xml file.

: read parameters from an xml file.

: After adjusting the point cloud data for all devices, click Apply at the bottom of the interface, and the set parameters will be written into the Livox devices and apply to Livox Viewer 2 (only the industrial versions of Livox devices are currently supported).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/84b38ff4-f939-4555-841a-e7c7fde9058f/image/w=1920,quality=90,fit=scale-down" alt="image" height="69.70962753295898" width="83.98750305175781">

* If the user does not click Apply after completing an adjustment, Livox Viewer 2 will revert the extrinsic parameters for the devices to their pre-calibration status.

**Manual Calibration of Extrinsic Parameter**

1. Connect the Livox device, enable data capture and obtain point cloud data. Then click parameters.
2. A table will appear on the calibration interface showing the Livox device broadcast codes for all the point clouds and their corresponding extrinsic parameters. The selected points clouds and those of the same device group will turn red, while other point clouds will be white.
3. Move the cursor to the parameter you wish to change (such as roll, pitch, yaw, x, y, z), and adjust the parameter by rolling the scroll wheel, left-clicking and dragging the mouse left and right, or simply entering the value you wish to set. The modified parameters will be applied in real time on the point cloud images.
4. Click again to close the calibration interface. You may continue capturing point cloud data or execute other functions.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/84b38ff4-f939-4555-841a-e7c7fde9058f/image/w=1920,quality=90,fit=scale-down" alt="image" height="69.70962753295898" width="83.98750305175781">

* The degree of precision can be set at the bottom of the interface.

**Calculating Extrinsic Parameters**

The point clouds of Livox rotate in the x-y-z sequence of the Tait-Bryan angles. In this sequence, the point clouds will first rotate in the direction of the x-axis (roll) of the world coordinate system, followed by its y-axis (pitch), and finally its z-axis (yaw).

The matrices can be expressed as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b80eed6f-db43-4f54-bea5-a32780b62147/image/w=1920,quality=90,fit=scale-down" alt="image" height="142.58227848101265" width="704">

**Framing and Viewing Point Cloud Data**

Click on the toolbar to open the electronic data table. The interface will appear as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7bff015d-0a33-4589-9836-80bfcd9cba4d/image/w=1920,quality=90,fit=scale-down" alt="image" height="522.7435897435897" width="296">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3f197c99-2184-4c89-9a59-8c6d63fd79e4/image/w=1920,quality=90,fit=scale-down" alt="image" height="30.514285714285716" width="89">

click to enable point cloud framing. When clicked the button will be highlighted in yellow. Left-click and drag the mouse to frame and select data, which will be displayed in a table in the lower blank space of the interface. In addition, the selected point cloud will be highlighted in red.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0106ad61-2e0b-48c6-90cb-566fbfc2157c/image/w=1920,quality=90,fit=scale-down" alt="image" height="70.10679611650485" width="87">

select the desired framing mode from the drop-down list. The default framing mode is Rectangle, which can be swithed to Polygonal or Lasso.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7481860d-0cf3-44df-b24d-1a23ddba25a8/image/w=1920,quality=90,fit=scale-down" alt="image" height="23.650485436893202" width="87">

select this option to enable the Multi-select function. Once enabled, the previously selected data will not be erased by selections made afterwards.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9de6f3e0-143a-486b-8727-7d6ddc9f2055/image/w=1920,quality=90,fit=scale-down" alt="image" height="20.271844660194176" width="87">

select this option to enable the Hide Unselect function. Once enabled, the unselected point cloud data will be hidden each time a point cloud data selection is made.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b9dc1523-f70b-4a7f-874a-cf36b4a1b7c4/image/w=1920,quality=90,fit=scale-down" alt="image" height="538.8717948717949" width="296">

The statistical data for the framed and selected point clouds will be shown at the top of the table. Save: save the framed and selected data in a csv file;

Selected points num: calculate the number of cloud points framed and selected;

Mean: calculate the mean value of the parameter;

Std: calculate the standard deviation of the parameter (1σ);

Max: calculate the maximum value of the parameter;

Min: calculate the minimum value of the parameter;

**Upgrading Firmware**

In the menu bar, select `Tools` →`FirmwareUpgrade` which will open a firmware upgrade interface as shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/eb901f04-8118-4c23-8972-d865c39782b8/image/w=1920,quality=90,fit=scale-down" alt="image" height="299.41850220264314" width="432">

This is the firmware address option field for the specific device.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b736d5f2-b732-4bd7-8a4c-4f5521375074/image/w=1920,quality=90,fit=scale-down" alt="image" height="39.06295754026355" width="667">

From right to left below: upgrade progress bar, device type and connection status, and device serial number.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/eaafbd14-20d3-488d-8cd7-f2964cd55b53/image/w=1920,quality=90,fit=scale-down" alt="image" height="62.496328928046985" width="665">

Follow the steps below to upgrade firmware:

1. Click the in the corresponding device bar and select a new firmware. Then click Download in the lower right corner to download the latest firmware from the official website.
2. Click the button to the left of the serial number, select the device to upgrade, and connect to the device in Lidar List.
3. After connecting to the device, click Start Upgrade. The upgrade completes when the progress bar reaches 100%.

**Converting File Format**

Click `Tools` , select `File Converter`to open the file converter window:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3f5cb056-d00b-47ef-9238-d9f6ebd4daad/image/w=1920,quality=90,fit=scale-down" alt="image" height="186.7064083457526" width="432">

The file conversion process is as follows:

1\. Click `Lvx2 To Csv` and select your desired file types for conversion from the list (the default choice is Lvx2 To Csv).

2.Click  at the top to select the source file. A target file of the same name will be created automatically in the folder of the source file. Then enter the target file address below. You may also enter the source file address manually. This will not automatically create a target file.

3.Click below to select the target file to override/create, or enter a target file address manually.

4.Click “Start” to start file conversion. A notification will pop up once the conversion is complete.

**Noise Filter**

Click `Tools` ,select `Noise Filter` to open the noise filter interface.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1673af9b-5975-4a95-984c-179b2aac8238/image/w=1920,quality=90,fit=scale-down" alt="image" height="221.91304347826085" width="336">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e554956e-d5e1-4ce3-8cf0-80e13ced77e1/image/w=1920,quality=90,fit=scale-down" alt="image" height="33.390243902439025" width="148">

select the noise filtering strength for the corresponding noise type.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/060e419a-a7eb-490f-8a15-ec81c842f538/image/w=1920,quality=90,fit=scale-down" alt="image" height="36.151975683890576" width="313">

refers to `atmospheric particles, such as dust, rain, fog and snow`.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3bc7dfcf-a81b-4077-90da-de9de33ef038/image/w=1920,quality=90,fit=scale-down" alt="image" height="29.43243243243243" width="132">

refers to `dragging noises between objects`.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/26eaceb9-c58f-4eed-b881-4951d797024e/image/w=1920,quality=90,fit=scale-down" alt="image" height="27.63157894736842" width="60">

refers to `dragging noises near the lidar`.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/16e62479-2284-42f5-90a8-ded61b2d26e0/image/w=1920,quality=90,fit=scale-down" alt="image" height="28.735159817351597" width="203">

select this option to highlight the filtered points (unselected means the filtered points are hidden).

**Grid Property**

Click `Tools` and select `Grid Property` to open the grid property configuration interface.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/12555afb-6bb4-427e-a143-80cb5491d4e4/image/w=1920,quality=90,fit=scale-down" alt="image" height="291.9938366718028" width="336">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/af8a143c-65d4-4e4b-9081-1fcba71fb82b/image/w=1920,quality=90,fit=scale-down" alt="image" height="28.71844660194175" width="87">

Click to select the gird shape from the drop-down list.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/464677db-622b-4740-a96e-ab5f5c00e0d6/image/w=1920,quality=90,fit=scale-down" alt="image" height="26.93069306930693" width="85">

the values in entry fields on the right are the RGB values for the grid `R: 255 G: 255 B:255` which can be changed manually. Besides, click to open the color wheel, and left-click on the color wheel to change the color instantly.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fd5df24e-5336-4d3c-803a-8f4fd568968a/image/w=1920,quality=90,fit=scale-down" alt="image" height="29.666666666666664" width="89">

Set the grid height by changing the value in entry field on the right.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f94a314d-44c1-4171-a03d-984cc42ddf50/image/w=1920,quality=90,fit=scale-down" alt="image" height="269.1066715542522" width="615.875">

Select the range and the step from the drop-down list for the circle grid or rectangle grid, respectively. Click `Apply` to save and apply all the settings. Click `Cancel` to cancel.

**Color Coding**

Click `Tools` and select `Color Coding` to open the color coding interface.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/38cea90f-7f37-4b7b-8b59-af90917290c0/image/w=1920,quality=90,fit=scale-down" alt="image" height="588.8740849194729" width="667">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cd2c1ce6-a9ba-4487-98cc-f5195bb4c6e5/image/w=1920,quality=90,fit=scale-down" alt="image" height="126.77070828331333" width="704">

If the color scheme is set to `Color: Lidar ID` , set the point cloud color in the column above for the corresponding LiDAR sensor based on ID. The IDs shown here match with the sequence of the LiDAR sensors shown on the device list. Change the RGB values manually or click to open the color wheel on the right to change the color instantly.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9dc7b358-97ee-42dd-822d-9f5f40e0b8f0/image/w=1920,quality=90,fit=scale-down" alt="image" height="126.86746987951807" width="648">

If the color scheme is set to `Color: Distance` , set the horizontal Max Range and Min Range for the point could coloring.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ca214f68-c6f3-4d89-ba77-cfdfe6b943ed/image/w=1920,quality=90,fit=scale-down" alt="image" height="128.81447963800903" width="647">

If the color scheme is set to `Color: Elevation`, set the vertical Max Range and Min Range for point cloud data coloring.

**Reporting an Issue**

Click in the toolbar to open the Debug Setting window:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f81bd772-283c-4995-928f-4dcf38a8f6d9/image/w=1920,quality=90,fit=scale-down" alt="image" height="242.4228028503563" width="405">

The functions of the window are as follows:

1\. Click Report Log File to Developer, and the Bug Report Content window will appear:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/01e2fad0-5da2-491f-8d3e-d22336ff3983/image/w=1920,quality=90,fit=scale-down" alt="image" height="213.8969616908851" width="704">

Enter your personal information and a description of the error, select whether to include log files, then click Confirm to report the issue to the developer. You will receive a notification once the report is successfully sent.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/84b38ff4-f939-4555-841a-e7c7fde9058f/image/w=1920,quality=90,fit=scale-down" alt="image" height="69.70962753295898" width="83.98750305175781">

* If the software crashes, a crash log will be created. When you open the file the next time, you will be asked whether to report the issue and send the crash log file.

1. Click “Show FPS stat” to show/hide FPS data in the top right corner of the screen. The higher the FPS, the smoother the playback.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2d012a54-b210-4cf2-9071-8a79869087bb/image/w=1920,quality=90,fit=scale-down" alt="image" height="128.55868544600938" width="197">

Livox and HAP are the trademarks of Livox Technology Company Limited.

Windows is the registered trademark of Microsoft Corporation and its subsidiaries.
