# DOBOT Collaborative Robot Universal Training Platform Operation Guide

## DOBOT Collaborative Robot Universal Training Platform — Without PLC System Module

{% embed url="https://openelab.io/products/dobot-cobot-universal-training-platform?variant=46636171395270" %}

## DOBOT Collaborative Robot Universal Training Platform — With PLC System Module

{% embed url="https://openelab.io/products/dobot-cobot-universal-training-platform?variant=46636171428038" %}

## Choose the correct instructions before setup

The training platform is sold in **With PLC System Module** and **Without PLC System Module** configurations. A DOBOT robot and the Vision Kit are not included in either OpenELAB variant. Choose the operation instruction by both the robot installed on the platform and the PLC configuration actually delivered. Do not interchange controller wiring, I/O assignments, emergency-stop connections, or software procedures between the six combinations below.

![Official illustration of universal training platforms with different compatible robots](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8Sm9VB6buwyJGVPa3wIJ%2Funiversal-platform-installation-p5-Im0.jpg?alt=media)

## Read the matching full manual in this Wiki

| Installed robot | Without PLC                                                                                                                                                                                                     | With PLC                                                                                                                                                                                                  |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MG400           | [MG400 without PLC](https://wiki.openelab.io/dobot/dobot-collaborative-robot-universal-training-platform-operation-guide/dobot-mg400-universal-training-platform-without-plc-operation-instruction)             | [MG400 with PLC](https://wiki.openelab.io/dobot/dobot-collaborative-robot-universal-training-platform-operation-guide/dobot-mg400-universal-training-platform-with-plc-operation-instruction)             |
| CR3             | [CR3 without PLC](https://wiki.openelab.io/dobot/dobot-collaborative-robot-universal-training-platform-operation-guide/dobot-cr3-universal-training-platform-without-plc-operation-instruction)                 | [CR3 with PLC](https://wiki.openelab.io/dobot/dobot-collaborative-robot-universal-training-platform-operation-guide/dobot-cr3-universal-training-platform-with-plc-operation-instruction)                 |
| Magician E6     | [Magician E6 without PLC](https://wiki.openelab.io/dobot/dobot-collaborative-robot-universal-training-platform-operation-guide/dobot-magician-e6-universal-training-platform-without-plc-operation-instruction) | [Magician E6 with PLC](https://wiki.openelab.io/dobot/dobot-collaborative-robot-universal-training-platform-operation-guide/dobot-magician-e6-universal-training-platform-with-plc-operation-instruction) |

The official [English operation-instruction archive](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260722/1770703893557_Collaborative%20Robot%20Universal%20Training%20Platform%20Operation%20Instruction-EN.rar) contains all six combination-specific manuals and four supporting guides. Download and extract it, then use the matching file:

| Installed robot | Without PLC                                                                                                                                                                      | With PLC                                                                                                                                                                       |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| MG400           | `01-Collaborative Robot Universal Training Platform（MG400_exclude PLC）_2023-07-07_en.pdf` — MG400 General Training System Operation Instruction, V2.0 (2023-05-21)               | `02-Collaborative Robot Universal Training Platform（MG400_include PLC）_20260211_en.pdf` — MG400 General Training System Operation Instruction, V4.1 (2026-02-11)               |
| CR3             | `03-Collaborative Robot Universal Training Platform（CR3_exclude PLC）_2023-07-07_en.pdf` — CR3 General Training System Operation Instruction, V1.0 (2023-06-02)                   | `04-Collaborative Robot Universal Training Platform（CR3_include PLC）_20260211_en.pdf` — CR3 General Training System Operation Instruction, V1.1 (2026-02-11)                   |
| Magician E6     | `05-Collaborative Robot Universal Training Platform (Magician E6 _exclude PLC)_2023-08-02_en.pdf` — Magician E6 General Training System Operation Instruction, V1.0 (2023-08-02) | `06-Collaborative Robot Universal Training Platform (Magician E6 _include PLC)_20260211_en.pdf` — Magician E6 General Training System Operation Instruction, V1.2 (2026-02-11) |

The date in an archive filename is not always the issue date printed inside its PDF. The document issue and version shown above come from each PDF cover. These are **alternative manuals**, not sequential chapters to perform together.

## Installation and first-use workflow

1. Identify the delivered platform configuration and the exact robot model. Check the component list before assembly; the official installation guide shows MG400, CR3, and Magician E6 mounting as separate procedures.
2. Read `Universal Training Platform Installation Guide_20240328_en.pdf` for the platform layout, cable descriptions, shipping list, robot mounting, vision-system installation (if that optional kit is present), air-pump-box installation, and conveyor assembly. Its base I/O table is explicitly for the **configuration without PLC**.
3. Open the matching one of the six operation instructions above. Follow its model-specific installation, software setup, I/O and exercise chapters. For the PLC configuration, use the manual marked `include PLC`; its PLC/HMI material is not a substitute for the non-PLC wiring instructions.
4. Before any electrical work, review `Universal Training Platform E-STOP Switch Wiring Guide_20240328_en.pdf`. The guide gives different MG400, Magician E6, and CR3 emergency-stop connections. Electrical changes should be performed by qualified personnel using the instructions for the installed robot, with the system isolated from power.
5. For the conveyor, use `Conveyor Kit Operation Guide_20240328_en.pdf` together with the selected robot-specific manual. The conveyor guide illustrates MG400 I/O connections; do not assume those pin assignments apply to CR3 or Magician E6.
6. If converting an existing **Without PLC** platform to **With PLC**, use `Universal Training Platform Wiring Instructions (Exclude PLC to Include PLC)_20240328_en.pdf`. It covers the PLC module accessories, the with-PLC I/O table, output and input cables, power cables, and junction-box rewiring. This conversion guide is not an instruction to rewire a platform already delivered with PLC.

![Official platform layout and wiring overview from the installation guide](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2CZEO6m5ULB1yHA63Xha%2Funiversal-platform-installation-p6-Im1.jpg?alt=media)

## Software and exercise scope by combination

The operation instructions contain the detailed robot-control, application, and demonstration steps. Their software versions describe the examples used in the respective documents; check the installed software and controller before following screenshots or loading example programs.

| Combination              | Software versions stated in its preface                                              | Example areas described                                                                                                              |
| ------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| MG400, without PLC       | DobotStudio Pro 2.6.1; DobotVisionStudio 4.1.2                                       | Three-color light, trajectory simulation, robot handling, static palletizing, vision sorting, phone-chip assembly, dynamic tracking. |
| MG400, with PLC          | DobotStudio Pro 2.6.1; DobotVisionStudio 4.1.2; TIA Portal V15.1 for PLC programming | Trajectory simulation, static palletizing, robot handling, vision sorting, phone-chip assembly, and PLC/HMI integration.             |
| CR3, without PLC         | DobotStudio Pro 2.6.1; DobotVisionStudio 4.1.2                                       | Three-color light, trajectory simulation, conveyor, static palletizing, vision sorting, phone-chip assembly, dynamic tracking.       |
| CR3, with PLC            | DobotStudio Pro 2.6.1; DobotVisionStudio 4.1.2                                       | Robot and PLC/HMI integration, PLC program download and I/O configuration, plus the model-specific exercise procedures.              |
| Magician E6, without PLC | DobotStudio Pro 4.1; DobotVisionStudio 4.1.2                                         | Three-color light, trajectory simulation, static palletizing, robot handling, vision sorting, vision-guided assembly.                |
| Magician E6, with PLC    | DobotStudio Pro 4.4; DobotVisionStudio 4.1.2; TIA Portal V15.1 for PLC programming   | Trajectory simulation, static palletizing, robot handling, vision sorting, vision-guided assembly, and PLC/HMI integration.          |

The MG400 and Magician E6 PLC manuals state that the PLC program is preloaded; TIA Portal is separately purchased and is not needed unless PLC programming is required. Confirm the installed PLC program and software version before changing or downloading a project.

## Supporting documents in the official archive

| File                                                                                           | Use it for                                                                                        |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `Universal Training Platform Installation Guide_20240328_en.pdf` (V1.0)                        | Common platform layout and installation; separate MG400, CR3, and Magician E6 installation paths. |
| `Conveyor Kit Operation Guide_20240328_en.pdf`                                                 | Conveyor assembly and a documented MG400 wiring example.                                          |
| `Universal Training Platform E-STOP Switch Wiring Guide_20240328_en.pdf`                       | Robot-specific emergency-stop switch wiring.                                                      |
| `Universal Training Platform Wiring Instructions (Exclude PLC to Include PLC)_20240328_en.pdf` | Conversion of a non-PLC platform to the PLC configuration.                                        |

For pin-level wiring, safety circuits, calibration, and program downloads, follow the complete matching official PDF in the [English source archive](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260722/1770703893557_Collaborative%20Robot%20Universal%20Training%20Platform%20Operation%20Instruction-EN.rar). Do not substitute a different robot or PLC variant's procedure.
