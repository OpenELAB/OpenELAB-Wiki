---
description: >-
  Official AI Drawing Lab V1.1.0 instructions for the DOBOT AI Drawing Kit used
  with Magician E6.
---

# DOBOT AI Drawing Lab User Guide

## DOBOT AI Drawing Kit for Magician E6 STEM Education

{% embed url="https://openelab.io/products/dobot-ai-drawing-kit-magician-e6" %}

[Official manual PDF](https://dobot-cloud-1256299428.cos.accelerate.myqcloud.com/dobot/Dobot%20AI%20Drawing%20Lab%20User%20Guide_V1.1.0_20250704_en.pdf)

## Contents

* Preface
* 1\. Product Introduction
* 2\. Quick Start Guide
* 3\. Installation and Login
* 4\. AI Drawing Lab
* Appendix A Zero Position Calibration
* Appendix B User Coordinate Calibration

## Copyright and Disclaimer

### Copyright © SHENZHEN DOBOT CORP LTD 2025. All rights reserved.

No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "Dobot").

### Disclaimer

To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot arm is used on the premise of fully understanding the robot arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document.

The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot arm.

SHENZHEN DOBOT CORP LTD Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

#### Purpose

This document provides installation and usage guidance for the Dobot AI Drawing Lab, helping users to better understand and use the Dobot AI Drawing Lab.

#### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

#### Compatible versions

| **Product**         | **Version**                        |
| ------------------- | ---------------------------------- |
| AIDrawingLab plugin | V1.1.0-stable and above            |
| DobotStudio Pro     | V4.6.1.0-AIDrawing-stable or above |
| Controller          | V4.6.1.0 or above                  |

### Related documents

| Document                                | Purpose                                                     | Where to obtain it               |
| --------------------------------------- | ----------------------------------------------------------- | -------------------------------- |
| DobotStudio Pro User Guide              | Robot control software.                                     | DOBOT website.                   |
| Dobot Robot Maintenance Tool User Guide | Firmware upgrades, controller-file backup and recovery.     | Contact DOBOT technical support. |
| Dobot Magician E6 User Guide            | Robot functions, technical specifications and installation. | DOBOT website.                   |

### Revision history

| Date       | Version | Change                                      |
| ---------- | ------- | ------------------------------------------- |
| 2025-07-04 | V1.1.0  | Second release; AIDrawingLab plugin V1.1.0. |
| 2025-05-07 | V1.0.0  | First release; AIDrawingLab plugin V1.0.0.  |

#### Symbol conventions

The symbols that may be found in this document are defined as follows.

| **Symbol**  | **Description**                                                                                                                                             |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DANGER**  | <p>Indicates a hazard with a high level of risk which, if not avoided, could<br>result in death or serious injury.</p>                                      |
| **WARNING** | <p>Indicates a hazard with a medium level or low level of risk which, if<br>not avoided, could result in minor or moderate injury, robot arm<br>damage.</p> |
| **NOTICE**  | <p>Indicates a potentially hazardous situation which, if not avoided,<br>could result in robot arm damage, data loss, or unanticipated result.</p>          |
| **NOTE**    | <p>Provides additional information to emphasize or supplement<br>important points in the main text.</p>                                                     |

## 1. Product Introduction

AIDrawingLab is an intelligent drawing plugin integrated into DobotStudio Pro. It enables the generation of base images through text descriptions, voice commands, or 2D camera captures, and effortlessly converts them into executable line drawings for robots with just one click. Paired with the Magician E6 robot, along with its dedicated drawing board and pen, AIDrawingLab brings ideas to life, allowing users to complete the entire creative-to-physical-drawing process in just 5 minutes — all without any programming knowledge.

This plugin is ideal for STEAM education, art studios, and intelligent interactive setups, empowering robots driven by AI to become creative partners.

**Features** :

* **Multimodal AI generation:** Create base images using text input, voice commands, or live image captures.
* **One-click path optimization:** Intelligently analyze image structures to automatically generate high-precision robot motion paths.
* **Seamless hardware collaboration:** Perfectly adapted to the Magician E6 robot, ensuring high-precision pen strokes.
* **End-to-end package:** Comes with a 2D camera, dedicated drawing board, pen, and other necessary hardware for simple setup and immediate use.

![Official manual image, source page 6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaDicJ3EuPGI2oXYoaSXr%2Fai-drawing-p006-img01.jpg?alt=media)

## 2. Quick Start Guide

1. Install the pen holder, camera, drawing board, and software as described in **3. Installation and Login**.
2. Log in to AIDrawingLab.
3. Create a base image using text, voice, or a reference image.
4. Convert the image into line drawings and edit the paths in the workspace.
5. Set the drawing parameters and start drawing.

## 3. Installation and Login

### 3.1 Hardware Installation and Wiring

#### 3.1.1 Hardware Installation

1. Attach the quick-release flange of the pen holder securely to the end of the robot arm.

**NOTICE** To avoid potential interference between the pen and robot during subsequent motions, adjust the robot's J6 axis to 0° before installing the pen holder.

2. Mount the 2D camera onto the quick-release flange of the pen holder.
3. Secure the included A4 drawing board to the robot base by aligning and locking it into the grooves.
4. Place an A4 sheet on the silkscreen area of the drawing board and secure it using the round-handled magnets.
5. The completed installation is illustrated as shown below.

**NOTE** If the drawing board is unavailable, you can roughly position the drawing paper as shown below and temporarily secure it with tape. Ensure the pen holder can freely operate within the drawing area.

![Official manual image, source page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1hMT0FdiqIg5WSH5H9Lk%2Fai-drawing-p008-img01.jpg?alt=media)

#### 3.1.2 Wiring Instruction

* ① Connect the robot's LAN port to the computer's Ethernet port using an Ethernet cable.
* ② Connect the emergency stop switch to the robot's E-STOP interface.
* ③ Connect the camera to the computer's USB port using the camera data cable.

**NOTE** It is recommended to route the camera data cable along the joints of the robot arm and secure it with the included Velcro.

* ④ Connect the robot's power interface to the mains socket using a power adapter cable.

**NOTICE** Please make sure to complete all the wiring before turning on the power.

![Official manual image, source page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgFpf0UVoN6ZX90HzFIFE%2Fai-drawing-p009-img01.jpg?alt=media)

### 3.2 Software Installation

1. Install the **DobotStudio Pro software** (supporting **V4.6.1.0-AIDrawing-stable and above** ) on the computer or the teach pendant. The following takes the installation and uses on the computer as an example for illustration.
2. Open DobotStudio Pro and connect to the robot. For specific procedure, see DobotStudio Pro user guide.
3. Go to the **Dobot+** page, **import** and **install** the AIDrawingLab plugin.

![Official manual image, source page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvxeCmDesKJrV4MSsQm7E%2Fai-drawing-p010-img01.png?alt=media)

![Official manual image, source page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfuSdekt6PgF8MRtpHFwY%2Fai-drawing-p010-img02.jpg?alt=media)

4. After the plugin installation is completed, open the **Application** page. Doubleclick the **AIDrawingLab** icon to enter the AI Drawing Lab login page.

![Official manual image, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTCWd6egmcEyn305B2qKT%2Fai-drawing-p011-img01.jpg?alt=media)

### 3.3 Account Management

#### 3.3.1 Login

1. When entering the AI Drawing Lab for the first time, you need to log in with an activation code. Click " **Activation Code Login** ", enter the activation code (please get the code from your sales representative or agent), and then click "Login" to enter the account registration interface.
2. Enter your username, email (optional), password (the two password entries must match) and region, and click "Login" to enter the initial page of the AI Drawing Lab.

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv8DbVOkX2SRrgoay0203%2Fai-drawing-p012-img01.jpg?alt=media)

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLYyFiHBAmFsWPqdZloWN%2Fai-drawing-p012-img02.jpg?alt=media)

**NOTE**

1. Both the username and password should consist of 4 to 20 characters, which can be a combination of one or more of the following: letters, numbers, underscores, or hyphens. The username must begin with a letter.
2. If an email is entered, you need to click the "Send Code" button and enter the code received in your email. If no email is provided, this step can be skipped.
3. When entering the AI Drawing Lab again, you can directly log in with your registered username, email or activation code.
4. Check "Remember me" to stay logged in by default (valid for 6 months). Re-login is required after expiration.

#### 3.3.2 Logout

Click on the right side of the AI Drawing Lab page, and select **Log out** .

#### 3.3.3 Modify Information

Click on the right side of the AI Drawing Lab page and select "User Center", where you can view the username, email, region, user status, activation code, activation status, activation time, and validity period. Click "To Modify" to modify the password of the currently logged-in account, email and region.

![Official manual image, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2qcC26XywWWgkC1KTPTs%2Fai-drawing-p013-img02.jpg?alt=media)

#### 3.3.4 Reset Password

1. If you forget your password, you can click "Forget password" on the login page to access the password reset screen.

**NOTE** Only account with a registered email can reset the password. If the prompt "User does not exist" appears, please verify whether the email was ever registered.

2. Enter the email used during registration and click "Send Code". After receiving a prompt that the code has been sent successfully, check your email for the verification code. Resend the code after 60 seconds if you do not receive it.

![Official manual image, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhyNSrhvLYfRHbOEFyeBv%2Fai-drawing-p014-img01.jpg?alt=media)

![Official manual image, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs6hndwdwwPoJeTFgnob8%2Fai-drawing-p014-img02.jpg?alt=media)

3. Enter the verification code received in your email, then input a new password (it cannot be the same as your old password). Click "OK" to complete the change.
4. Upon successful password change, you'll be returned to the login page to sign in with your new password.

![Official manual image, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FluLN1IgBYeBB7tlPDAOc%2Fai-drawing-p015-img01.jpg?alt=media)

![Official manual image, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS1aF5lJejckVKuZElCga%2Fai-drawing-p015-img02.jpg?alt=media)

## 4. AI Drawing Lab

### 4.1 AI Drawing

1 Image Description: Conduct AI drawing based on text\
descriptions.\
2 Speech: Select the language to be recognized and convert voice\
commands into text input.\
Reference Image: Capture a real-time photo via camera or\
3 import image. Based on the photo or imported image, AI drawing\
will be generated according to the image description.\
4 Set the ratio and the number of images to be generated.\
5 AI Generate: After clicking this button, generate images\
according to the image description and the set parameters.\
6 Image buffer area: Preview thumbnails or delete images.<br>

**7** Image preview area: Preview large images, save images, or convert images into line drawings.

![Official manual image, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGyzIRVokrzuOhEGn1IoA%2Fai-drawing-p017-img01.jpg?alt=media)

#### 4.1.1 Text-to-Image

The operation process of Text-to-Image is as follows:

1. Enter the **Image Description** with a 500-character limit.

**NOTE** Recommended keywords for picture styles: Animal, 2D, Flat Cartoon, Pop Art, Graffiti, American Comic Style, Flat Illustration, Black Outline with White Background, Chinese Painting, Black-and-White Sketch, Impressionism, Thick-Paint Style, Meticulous Chinese Painting (Gongbi), Ink Wash Painting (Shuimo), Traditional Chinese Style (Gu Feng), ASCII Art.

2. Select the **Aspect Ratio** and **Generation Quantity** .
   * **Aspect Ratio:** The default is 1:1, support 1:1, 4:3, 16:9, and 9:16.
   * **Generation Quantity:** The default is 1. You can generate a maximum of 2 images at a time.
3. Click the "AI Generate" button to start generating the image (it takes about 10 – 15 seconds).
4. The results of AI image generation will be saved in the image buffer area at the bottom-left corner of the page. You can click the delete icon at the top-right corner of the image to delete it.

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbW5SWcOW9C2h2cj6EomN%2Fai-drawing-p018-img01.jpg?alt=media)

5. You can enlarge the image by clicking the magnifying icon at the bottom-right corner of the image preview area.
6. Click the "Save" button in the image preview area to save the current image to your local device. The generated image will be assigned a default file name that includes the timestamp and a description of the image. You can customize the file name and save path.

![Official manual image, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjEopP1j2YgyoIlhMqt1w%2Fai-drawing-p019-img01.png?alt=media)

![Official manual image, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fow7TJ3J5PeiCC9Y9eUCx%2Fai-drawing-p019-img03.png?alt=media)

**NOTE** If the Reference Image feature is enabled, the file name will also include the style keywords you selected.

7. Click the "Convert" button in the preview area to convert the current image into a line drawing and switch to the "Workspace" page. You can adjust the current line drawing and start drawing. For more details, see the introduction to Workspace.

#### 4.1.2 Voice-to-Image

1. Click the dropdown menu next to "Language" and select the language you want to recognize (Auto by default).
2. Click the "Speech" button and speak the description of the image. Speech can be recognized for up to 60 seconds at a time.

**NOTICE** On your computer, go to "Settings > Privacy > App permissions > Microphone" and turn on the option "Allow desktop apps to access your microphone". Otherwise, the speech recognition function will not work.

3. After finishing your voice input, click the "End" button. The system will convert the voice command into text and display it in the "Image Description" input box.
4. The follow-up process is the same as that of Text-to-Image.

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsSEVRcrM4qCQgZ6qIe5h%2Fai-drawing-p020-img01.jpg?alt=media)

#### 4.1.3 Image Generation with a Reference Image

Based on the captured or imported base image, new images are generated by inputting the provided image description keywords.

1. Click the "Enable" button next to "Reference Image".

NOTICE<br>

On your computer, go to "Settings > Privacy > App permissions > Camera" and turn on the option "Allow desktop apps to access your camera". Otherwise, the camera function will not work.

2. Select the source of the base image.
   * **Use Camera:** Select the camera installed on the current robot from the dropdown menu next to the "Use Camera" option.

* a. Long-press the "Run to" button, the robot will automatically move to the capture position (by default, it is above the center point of the A4 drawing board and can capture the whole board). After reaching the position, it will stop running and prompt "Reach the photo-taking position".

![Official manual image, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkp75TA7SQmTNmQSEITth%2Fai-drawing-p021-img02.png?alt=media)

* b. Click the "Capture Image" button to capture the current scene.
* **Open File** : Click the Open File button to import a local image in PNG or JPG format.

**NOTE** The imported image must be no larger than 3MB in size, with a width and height ranging between 512px and 4096px.

3. Select a generated image style in the dropdown menu of Reference Style.
4. Enter relevant descriptions for the currently captured or imported image in the "Image Description" input box, either by typing or using speech recognition.
5. After selecting the **Generation Quantity** (the desired number of images to generate), click the "AI Generate" button. The system will generate new images based on the base image and your description.

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiagTarZljxSZT59Hqbhg%2Fai-drawing-p022-img01.png?alt=media)

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4er0Ejj9pQdEVZrkeT6J%2Fai-drawing-p022-img02.png?alt=media)

**NOTE** After enabling the Reference Image function, the default aspect ratio for image generation is 4:3. For imported image, the aspect ratio is determined by the ratio of the imported image and cannot be adjusted.

### 4.2 Workspace

**1** Line drawing editing: Adjust the drawing trajectory, import and export line drawings, see Editing Line Drawings for details.

2 Parameter setting: Adjust the robot's drawing parameters, see\
Setting Drawing Parameters for details.<br>

3 Start or stop drawing.<br>

**4** Canvas: Adjust the position and size of the line drawing on the canvas.

![Official manual image, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrQ3JsOHXqnqYBwaux1lo%2Fai-drawing-p023-img01.jpg?alt=media)

#### 4.2.1 Editing Line Drawings

* **Compare:** Click the "Compare" switch to display the original image of the line drawing.
* **Remove Background:** Click the "Remove Background" switch to remove the background of the line drawing.
* **Output File:** Export the current line drawing and save it to your local computer. The default file name for the exported image will include the current timestamp and the image description. The image will be exported in _SVG_ , and you can customize the save path and file name as needed.

**NOTE** If the current line drawing is based on an imported local image, the exported file name will default to the current timestamp combined with the imported image's file name.

* **Open File:** Support importing images in _png_ or _jpg_ format saved on the local computer or _SVG_ images saved via the export button. The size of the imported image cannot exceed 3MB.
* **TransformRatio, Simplification, and LineComplexity:** Drag the sliders to adjust the line drawing (you can also click to adjust the transform ratio). The step for TransformRatio is 1%, for Simplification is 20%, and for LineComplexity is 25%.
* **Insert:** Click the "Insert" button to place the adjusted line drawing in the canvas. It is placed in the center by default.
  * Multiple line drawings can be placed in the canvas at the same time.
  * Drag, scale, or rotate the line drawings by using the mouse to control the blue path box on the canvas.
  * Click to rotate 90° clockwise; Click to flip horizontally; Click to center align both horizontally and vertically.
* Right-click on a line drawing to delete the current line drawing.

![Official manual image, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk2QidMDPFRObLSp3merL%2Fai-drawing-p024-img01.png?alt=media)

**NOTE**

* The size of the line drawing cannot exceed the canvas; otherwise, when you click "Start Drawing", a prompt "The trajectory exceeds the canvas range. Please re-edit" will pop up.
* To ensure the best drawing results, it is recommended to draw within a 5mm margin inside the canvas.
* When no path is selected, the bottom buttons are disabled. Clicking the buttons will prompt a message saying, "Please select a drawing path".
* It is recommended to rotate the line drawing placed in the canvas by 180°. In this way, when you face the robot and the drawing board, the image you see is in the correct orientation, which is convenient for observation.
* **Clear:** Click the "Clear" button to clear all line drawings in the canvas.

**NOTE**

During program execution, line drawings cannot be modified. The "Insert" and "Clear" buttons are disabled.

![Official manual image, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxUo03E93Twm3aJVCmWy8%2Fai-drawing-p025-img01.jpg?alt=media)

#### 4.2.2 Setting Drawing Parameters

* **Drawing Speed:** It refers to the motion speed of continuous trajectory (10% – 100%). The effect may not be very obvious after the change. If you want to increase or decrease the overall drawing speed of the Magician E6 robot (it is recommended to set it at 200mm/s), you need to change the factory settings. Here is an example of modification (the value is for reference only, and the specific parameters depend on the actual situation):

Go to "Settings" > "Motion parameters" page, and modify the X/Y/Z speed values in the "Playback settings" column.

* **Pen Lift Height:** When the robot finishes drawing a continuous trajectory and needs to start drawing from another position, it is the height at which the pen is lifted from the surface of the drawing paper.
* **User Coordinate** : Under normal circumstances, the default coordinate system is used. However, if the workspace is not level, leading to significant height differences along the Z-axis and impairing the robot's drawing performance, you can refer to Appendix B Calibrate User Coordinate and select a custom user coordinate system.
* **Zero Position:** It is the position of the upper-left corner of the A4 drawing board, which has been calibrated at the factory. If you need to recalibrate the zero position, see Zero Position Calibration for details.
* **Drawing Height:** It is the height at which the pen tip touches the paper surface. It only needs to be set for the first drawing, and there is no need to set it repeatedly if the drawing height remains unchanged. The setting method is as follows:
  1. Press and hold the "ParallelZ" button to adjust the end-effector until it is level with the surface and the pen tip is perpendicular to the canvas. Once the adjustment is complete, a prompt will appear stating, "Reach the photo-taking position".

![Official manual image, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTlVHr9ZqBRSZHU695S0Z%2Fai-drawing-p026-img02.png?alt=media)

2. Jog the robot to make the pen tip touch the paper surface and press it slightly.

**NOTICE**

* Since the levelness of the drawing paper is not exactly the same, just make sure that the entire drawing paper can touch the pen tip. If the pen tip is pressed too much, the pattern may be deformed due to the increased frictional resistance.
* To better present the final effect, it is recommended to use a flexible pen tip.

3. Click the "AutoZ" button to update the **Drawing Height** . A text prompt will pop up when the update is successful. The current drawing height is displayed in realtime in the input box to the left of the button. You can update the drawing height in real-time by clicking the +/- buttons or by modifying the value in the input box.

**NOTE** Please ensure the drawing height is kept within the range of 1–130mm. Exceeding this range may affect the drawing quality within the A4 area.

#### 4.2.3 Starting/Stopping Drawing

Click the **Start Drawing** button, and the robot will start drawing according to the set drawing parameters.

![Official manual image, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuyhHv7Va2SbDnjWntLEC%2Fai-drawing-p027-img01.jpg?alt=media)

**NOTE** It is prohibited to modify the drawing parameters after starting the drawing process.

Click the **Stop Drawing** button to stop the drawing. At the same time, the pen tip will be lifted to the **Pen Lift Height** .

During the drawing process, you can observe the progress in real-time.

## Appendix A Zero Position Calibration

1. Switch to the **Workspace** page and click the "Calibrate" button next to the **Zero Position** . A prompt box will pop up as follows.
2. Long-press the "Run to" button, the robot will move to the factory-default zero position. After reaching the position, it will stop moving, and a text prompt "Reached the position above the origin" will pop up.
3. Press and hold the "ParallelZ" button to adjust the end-effector until it is level with the surface and the pen tip is perpendicular to the canvas.
4. Enter the Jog panel, jog the X and Y axes of the robot until it moves to the zero position at the upper-left corner of the A4 drawing board.
5. Click the "Calibrate" button to save the new zero position.

![Official manual image, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQCgjlOEpbRIa5oPEc1Iz%2Fai-drawing-p029-img01.jpg?alt=media)

![Official manual image, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm8C5zYkcmVJ2rLBxBMMv%2Fai-drawing-p029-img02.png?alt=media)

## Appendix B User Coordinate Calibration

Click the icon to the right of "User Coordinate" to open the User Coordinate System Calibration pop-up window. Follow the steps provided to configure the settings. The detailed steps are as follows:

1. Click the "Settings" button in the top navigation bar and select "Coordinate system" to access the "User coordinate system".
2. In the top-right corner of the interface, click the setting for custom user coordinate system calibration.

button to use the three-point

![Official manual image, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FixnUxF9Ecc5oac1LmGVT%2Fai-drawing-p030-img01.jpg?alt=media)

![Official manual image, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyWTqwr3p5KedCUhV2A6W%2Fai-drawing-p030-img03.jpg?alt=media)

3. Drag the robot sequentially to the origin (top-left corner of the A4 paper), any point on the line connecting the x-axis and the origin, and any point on the xoy plane, as shown in the figure below.
4. Click "Obtain" to capture the points P1, P2, and P3 in order. Click the Confirm button in the top-right corner and save to complete the calibration of the user coordinate system.

![Official manual image, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fwp3SIglv3eUBcC8nB48L%2Fai-drawing-p031-img01.png?alt=media)

![Official manual image, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9HRPqmwBv4WsZOybzMcK%2Fai-drawing-p031-img02.jpg?alt=media)

5. Return to the Application interface, click the dropdown menu next to "User Coordinate" and select the created custom user coordinate system.

![Official manual image, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhEgl5dB9MVacXgHjGP86%2Fai-drawing-p032-img01.jpg?alt=media)

![Official manual image, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpQBtvdCtBEl5j5NzjgS5%2Fai-drawing-p032-img02.png?alt=media)
