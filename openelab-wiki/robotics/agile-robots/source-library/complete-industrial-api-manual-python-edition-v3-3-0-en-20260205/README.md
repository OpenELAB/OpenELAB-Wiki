# Industrial Python API manual V3.3.0 — complete reference

{% hint style="info" %}
**Complete supplied source:** Industrial API Manual (Python Edition) \_V3.3.0\_EN\_20260205.pdf · **Coverage:** 165 original PDF pages. [Return to the Agile Robots source library](../).
{% endhint %}

Every source page is retained in the original order. The **Original page** view preserves complete diagrams, photographs, tables, equations, connector orientation, notices and examples. The **Searchable text** view preserves native PDF text or the slide’s native text, embedded links and substantive speaker notes. Text extraction can retain reading-order/character defects; use the original image for exact layout, table columns and code indentation.

{% hint style="warning" %}
This is the supplied Industrial Python API V3.3.0 reference dated 2026-02-05. It is not the pendant embedded-Python API. Preserve the exact delivered module, signatures, units and return conventions; do not infer parity with the later C/C++ manual.
{% endhint %}

**Attribution:** the manufacturer and contributors identified in the supplied document. Original notices remain visible on every source page. Navigation, revision notes and the linked engineering explanations are OpenELAB editorial additions.

## Reading sections

| Full in-wiki section                   | Original PDF pages |
| -------------------------------------- | ------------------ |
| [Read pages 1–72](pages-001-072.md)    | 1–72               |
| [Read pages 73–144](pages-073-144.md)  | 73–144             |
| [Read pages 145–165](pages-145-165.md) | 145–165            |

## Complete chapter and function index

| Source section / function                                 | Original page                            |
| --------------------------------------------------------- | ---------------------------------------- |
| Overview                                                  | [PDF 9](pages-001-072.md#pdf-page-9)     |
| Compatibility Statement                                   | [PDF 9](pages-001-072.md#pdf-page-9)     |
| Function Description                                      | [PDF 9](pages-001-072.md#pdf-page-9)     |
| 1 initSrv                                                 | [PDF 9](pages-001-072.md#pdf-page-9)     |
| 2 destroySrv                                              | [PDF 10](pages-001-072.md#pdf-page-10)   |
| 3 setPushPeriod                                           | [PDF 11](pages-001-072.md#pdf-page-11)   |
| 4 wait\_move                                              | [PDF 11](pages-001-072.md#pdf-page-11)   |
| 5 moveTCP                                                 | [PDF 12](pages-001-072.md#pdf-page-12)   |
| 6 rotationTCP                                             | [PDF 13](pages-001-072.md#pdf-page-13)   |
| 7 moveJoint                                               | [PDF 14](pages-001-072.md#pdf-page-14)   |
| 8 moveJToTarget                                           | [PDF 15](pages-001-072.md#pdf-page-15)   |
| 9 moveJToPose                                             | [PDF 16](pages-001-072.md#pdf-page-16)   |
| 10 moveJ                                                  | [PDF 17](pages-001-072.md#pdf-page-17)   |
| 11 moveL                                                  | [PDF 18](pages-001-072.md#pdf-page-18)   |
| 12 moveLToTarget                                          | [PDF 19](pages-001-072.md#pdf-page-19)   |
| 13 moveLToPose                                            | [PDF 20](pages-001-072.md#pdf-page-20)   |
| 14 moveLToPose\_ex                                        | [PDF 21](pages-001-072.md#pdf-page-21)   |
| 15 speedJ                                                 | [PDF 22](pages-001-072.md#pdf-page-22)   |
| 16 speedL                                                 | [PDF 23](pages-001-072.md#pdf-page-23)   |
| 17 freeDriving                                            | [PDF 24](pages-001-072.md#pdf-page-24)   |
| 18 stop                                                   | [PDF 25](pages-001-072.md#pdf-page-25)   |
| 19 forward                                                | [PDF 25](pages-001-072.md#pdf-page-25)   |
| 20 inverse                                                | [PDF 26](pages-001-072.md#pdf-page-26)   |
| 21 getJointPos                                            | [PDF 26](pages-001-072.md#pdf-page-26)   |
| 22 getJointAngularVel                                     | [PDF 27](pages-001-072.md#pdf-page-27)   |
| 23 getJointCurrent                                        | [PDF 27](pages-001-072.md#pdf-page-27)   |
| 24 getJointTorque                                         | [PDF 28](pages-001-072.md#pdf-page-28)   |
| 25 getTcpPos                                              | [PDF 28](pages-001-072.md#pdf-page-28)   |
| 26 getTcpExternalForce                                    | [PDF 29](pages-001-072.md#pdf-page-29)   |
| 27 releaseBrake                                           | [PDF 29](pages-001-072.md#pdf-page-29)   |
| 28 holdBrake                                              | [PDF 30](pages-001-072.md#pdf-page-30)   |
| 29 changeControlMode                                      | [PDF 30](pages-001-072.md#pdf-page-30)   |
| 30 getLibraryVersion                                      | [PDF 30](pages-001-072.md#pdf-page-30)   |
| 31 formatError                                            | [PDF 31](pages-001-072.md#pdf-page-31)   |
| 32 getLastError                                           | [PDF 31](pages-001-072.md#pdf-page-31)   |
| 33 setLastError                                           | [PDF 32](pages-001-072.md#pdf-page-32)   |
| 34 setDefaultActiveTcp                                    | [PDF 32](pages-001-072.md#pdf-page-32)   |
| 35 getLinkState                                           | [PDF 33](pages-001-072.md#pdf-page-33)   |
| 36 getTcpForce                                            | [PDF 33](pages-001-072.md#pdf-page-33)   |
| 37 getJointForce                                          | [PDF 34](pages-001-072.md#pdf-page-34)   |
| 38 isCollision                                            | [PDF 34](pages-001-072.md#pdf-page-34)   |
| 39 initDHCali                                             | [PDF 35](pages-001-072.md#pdf-page-35)   |
| 40 getDHCaliResult                                        | [PDF 35](pages-001-072.md#pdf-page-35)   |
| 41 setDH                                                  | [PDF 36](pages-001-072.md#pdf-page-36)   |
| 42 setWrd2BasRT                                           | [PDF 37](pages-001-072.md#pdf-page-37)   |
| 43 setFla2TcpRT                                           | [PDF 37](pages-001-072.md#pdf-page-37)   |
| 44 getRobotState                                          | [PDF 38](pages-001-072.md#pdf-page-38)   |
| 45 resume                                                 | [PDF 39](pages-001-072.md#pdf-page-39)   |
| 46 setJointCollision                                      | [PDF 40](pages-001-072.md#pdf-page-40)   |
| 47 setCartCollision                                       | [PDF 40](pages-001-072.md#pdf-page-40)   |
| 48 enterForceMode                                         | [PDF 41](pages-001-072.md#pdf-page-41)   |
| 49 leaveForceMode                                         | [PDF 42](pages-001-072.md#pdf-page-42)   |
| 50 setDefaultActiveTcpPose                                | [PDF 42](pages-001-072.md#pdf-page-42)   |
| 51 setResultantCollision                                  | [PDF 43](pages-001-072.md#pdf-page-43)   |
| 52 setJointImpeda                                         | [PDF 43](pages-001-072.md#pdf-page-43)   |
| 53 getJointImpeda                                         | [PDF 44](pages-001-072.md#pdf-page-44)   |
| 54 setCartImpeda                                          | [PDF 44](pages-001-072.md#pdf-page-44)   |
| 55 getCartImpeda                                          | [PDF 45](pages-001-072.md#pdf-page-45)   |
| 56 zeroSpaceFreeDriving                                   | [PDF 45](pages-001-072.md#pdf-page-45)   |
| 57 createPath                                             | [PDF 46](pages-001-072.md#pdf-page-46)   |
| 58 addMoveL                                               | [PDF 47](pages-001-072.md#pdf-page-47)   |
| 59 addMoveJ                                               | [PDF 47](pages-001-072.md#pdf-page-47)   |
| 60 runPath                                                | [PDF 48](pages-001-072.md#pdf-page-48)   |
| 61 destroyPath                                            | [PDF 49](pages-001-072.md#pdf-page-49)   |
| 62 rpy2Axis                                               | [PDF 49](pages-001-072.md#pdf-page-49)   |
| 63 axis2RPY                                               | [PDF 49](pages-001-072.md#pdf-page-49)   |
| 64 homogeneous2Pose                                       | [PDF 50](pages-001-072.md#pdf-page-50)   |
| 65 pose2Homogeneous                                       | [PDF 50](pages-001-072.md#pdf-page-50)   |
| 66 enableTorqueReceiver                                   | [PDF 51](pages-001-072.md#pdf-page-51)   |
| 67 sendTorque\_rt                                         | [PDF 51](pages-001-072.md#pdf-page-51)   |
| 68 enableCollisionDetection                               | [PDF 52](pages-001-072.md#pdf-page-52)   |
| 69 setActiveTcpPayload                                    | [PDF 52](pages-001-072.md#pdf-page-52)   |
| 70 servoJ                                                 | [PDF 52](pages-001-072.md#pdf-page-52)   |
| 71 servoL                                                 | [PDF 53](pages-001-072.md#pdf-page-53)   |
| 72 servoJ\_ex                                             | [PDF 54](pages-001-072.md#pdf-page-54)   |
| 73 servoL\_ex                                             | [PDF 56](pages-001-072.md#pdf-page-56)   |
| 74 speedJ\_ex                                             | [PDF 57](pages-001-072.md#pdf-page-57)   |
| 75 speedL\_ex                                             | [PDF 58](pages-001-072.md#pdf-page-58)   |
| 76 dumpToUDisk                                            | [PDF 59](pages-001-072.md#pdf-page-59)   |
| 77 inverse\_ext                                           | [PDF 59](pages-001-072.md#pdf-page-59)   |
| 78 getJointLinkPos                                        | [PDF 60](pages-001-072.md#pdf-page-60)   |
| 79 createComplexPath                                      | [PDF 60](pages-001-072.md#pdf-page-60)   |
| 80 addMoveLSegmentByTarget                                | [PDF 61](pages-001-072.md#pdf-page-61)   |
| 81 addMoveLSegmentByPose                                  | [PDF 63](pages-001-072.md#pdf-page-63)   |
| 82 addMoveJSegmentByTarget                                | [PDF 64](pages-001-072.md#pdf-page-64)   |
| 83 addMoveJSegmentByPose                                  | [PDF 66](pages-001-072.md#pdf-page-66)   |
| 84 addMoveCSegmentByTarget                                | [PDF 67](pages-001-072.md#pdf-page-67)   |
| 85 addMoveCSegmentByPose                                  | [PDF 69](pages-001-072.md#pdf-page-69)   |
| 86 runComplexPath                                         | [PDF 71](pages-001-072.md#pdf-page-71)   |
| 87 destroyComplexPath                                     | [PDF 71](pages-001-072.md#pdf-page-71)   |
| 88 saveEnvironment                                        | [PDF 71](pages-001-072.md#pdf-page-71)   |
| 89 enterForceMode\_ex                                     | [PDF 72](pages-001-072.md#pdf-page-72)   |
| 90 readDI                                                 | [PDF 73](pages-073-144.md#pdf-page-73)   |
| 91 readDO                                                 | [PDF 73](pages-073-144.md#pdf-page-73)   |
| 92 readAI                                                 | [PDF 74](pages-073-144.md#pdf-page-74)   |
| 93 readAO                                                 | [PDF 74](pages-073-144.md#pdf-page-74)   |
| 94 setAIMode                                              | [PDF 75](pages-073-144.md#pdf-page-75)   |
| 95 writeDO                                                | [PDF 76](pages-073-144.md#pdf-page-76)   |
| 96 writeAO                                                | [PDF 76](pages-073-144.md#pdf-page-76)   |
| 97 readBusCurrent                                         | [PDF 77](pages-073-144.md#pdf-page-77)   |
| 98 readBusVoltage                                         | [PDF 77](pages-073-144.md#pdf-page-77)   |
| 99 getDH                                                  | [PDF 78](pages-073-144.md#pdf-page-78)   |
| 100 getOriginalJointTorque                                | [PDF 79](pages-073-144.md#pdf-page-79)   |
| 101 getJacobiMatrix                                       | [PDF 79](pages-073-144.md#pdf-page-79)   |
| 102 resetDH                                               | [PDF 80](pages-073-144.md#pdf-page-80)   |
| 103 runProgram                                            | [PDF 80](pages-073-144.md#pdf-page-80)   |
| 104 stopProgram                                           | [PDF 81](pages-073-144.md#pdf-page-81)   |
| 105 getVariableValue                                      | [PDF 81](pages-073-144.md#pdf-page-81)   |
| 106 setVariableValue                                      | [PDF 82](pages-073-144.md#pdf-page-82)   |
| 107 isTaskRunning                                         | [PDF 82](pages-073-144.md#pdf-page-82)   |
| 108 pauseProgram                                          | [PDF 83](pages-073-144.md#pdf-page-83)   |
| 109 resumeProgram                                         | [PDF 83](pages-073-144.md#pdf-page-83)   |
| 110 stopAllProgram                                        | [PDF 84](pages-073-144.md#pdf-page-84)   |
| 111 isAnyTaskRunning                                      | [PDF 84](pages-073-144.md#pdf-page-84)   |
| 112 cleanErrorInfo                                        | [PDF 85](pages-073-144.md#pdf-page-85)   |
| 113 setCollisionLevel                                     | [PDF 85](pages-073-144.md#pdf-page-85)   |
| 114 getJointCount                                         | [PDF 86](pages-073-144.md#pdf-page-86)   |
| 115 getWayPoint                                           | [PDF 86](pages-073-144.md#pdf-page-86)   |
| 116 setWayPoint                                           | [PDF 87](pages-073-144.md#pdf-page-87)   |
| 117 addWayPoint                                           | [PDF 88](pages-073-144.md#pdf-page-88)   |
| 118 deleteWayPoint                                        | [PDF 89](pages-073-144.md#pdf-page-89)   |
| 119 getDefaultActiveTcp                                   | [PDF 89](pages-073-144.md#pdf-page-89)   |
| 120 getDefaultActiveTcpPose                               | [PDF 90](pages-073-144.md#pdf-page-90)   |
| 121 getActiveTcpPayload                                   | [PDF 90](pages-073-144.md#pdf-page-90)   |
| 122 zeroSpaceManualMove                                   | [PDF 91](pages-073-144.md#pdf-page-91)   |
| 123 moveTcp\_ex                                           | [PDF 91](pages-073-144.md#pdf-page-91)   |
| 124 setExternalAppendTorCutoffFreq                        | [PDF 92](pages-073-144.md#pdf-page-92)   |
| 125 poseTransform                                         | [PDF 93](pages-073-144.md#pdf-page-93)   |
| 126 updateForce                                           | [PDF 93](pages-073-144.md#pdf-page-93)   |
| 127 inverseClosedFull                                     | [PDF 95](pages-073-144.md#pdf-page-95)   |
| 128 getInverseClosedResultSize                            | [PDF 96](pages-073-144.md#pdf-page-96)   |
| 129 getInverseClosedJoints                                | [PDF 96](pages-073-144.md#pdf-page-96)   |
| 130 destoryInverseClosedItems                             | [PDF 97](pages-073-144.md#pdf-page-97)   |
| 131 getGravInfo                                           | [PDF 97](pages-073-144.md#pdf-page-97)   |
| 132 setGravInfo                                           | [PDF 98](pages-073-144.md#pdf-page-98)   |
| 133 getGravAxis                                           | [PDF 98](pages-073-144.md#pdf-page-98)   |
| 134 setGravAxis                                           | [PDF 99](pages-073-144.md#pdf-page-99)   |
| 135 speedLOnTcp                                           | [PDF 99](pages-073-144.md#pdf-page-99)   |
| 136 getTcpForceInToolCoordinate                           | [PDF 100](pages-073-144.md#pdf-page-100) |
| 137 calculateJacobi                                       | [PDF 101](pages-073-144.md#pdf-page-101) |
| 138 calculateJacobiTF                                     | [PDF 101](pages-073-144.md#pdf-page-101) |
| 139 getMechanicalJointsPositionRange                      | [PDF 102](pages-073-144.md#pdf-page-102) |
| 140 getMechanicalMaxJointsVel                             | [PDF 103](pages-073-144.md#pdf-page-103) |
| 141 getMechanicalMaxJointsAcc                             | [PDF 103](pages-073-144.md#pdf-page-103) |
| 142 getMechanicalMaxCartVelAcc                            | [PDF 104](pages-073-144.md#pdf-page-104) |
| 143 getJointsPositionRange                                | [PDF 104](pages-073-144.md#pdf-page-104) |
| 144 getMaxJointsVel                                       | [PDF 105](pages-073-144.md#pdf-page-105) |
| 145 getMaxJointsAcc                                       | [PDF 105](pages-073-144.md#pdf-page-105) |
| 146 getMaxCartTranslationVel                              | [PDF 106](pages-073-144.md#pdf-page-106) |
| 147 getMaxCartRotationVel                                 | [PDF 106](pages-073-144.md#pdf-page-106) |
| 148 getMaxCartTranslationAcc                              | [PDF 107](pages-073-144.md#pdf-page-107) |
| 149 getMaxCartRotationAcc                                 | [PDF 107](pages-073-144.md#pdf-page-107) |
| 150 setJointsPositionRange                                | [PDF 108](pages-073-144.md#pdf-page-108) |
| 151 setMaxJointsVel                                       | [PDF 108](pages-073-144.md#pdf-page-108) |
| 152 setMaxJointsAcc                                       | [PDF 109](pages-073-144.md#pdf-page-109) |
| 153 setMaxCartTranslationVel                              | [PDF 109](pages-073-144.md#pdf-page-109) |
| 154 setMaxCartRotationVel                                 | [PDF 110](pages-073-144.md#pdf-page-110) |
| 155 setMaxCartTranslationAcc                              | [PDF 110](pages-073-144.md#pdf-page-110) |
| 156 setMaxCartRotationAcc                                 | [PDF 111](pages-073-144.md#pdf-page-111) |
| 157 requireHandlingError                                  | [PDF 111](pages-073-144.md#pdf-page-111) |
| 158 getJointsSoftLimitRange                               | [PDF 112](pages-073-144.md#pdf-page-112) |
| 159 setJointsSoftLimitRange                               | [PDF 112](pages-073-144.md#pdf-page-112) |
| 160 getFunctionOptI4                                      | [PDF 113](pages-073-144.md#pdf-page-113) |
| 161 setFunctionOptI4                                      | [PDF 114](pages-073-144.md#pdf-page-114) |
| 162 enterRescueMode                                       | [PDF 114](pages-073-144.md#pdf-page-114) |
| 163 leaveRescueMode                                       | [PDF 115](pages-073-144.md#pdf-page-115) |
| 164 getCartImpedanceCoordinateType                        | [PDF 115](pages-073-144.md#pdf-page-115) |
| 165 setCartImpedanceCoordinateType                        | [PDF 116](pages-073-144.md#pdf-page-116) |
| 166 setJointLockedInCartImpedanceMode                     | [PDF 116](pages-073-144.md#pdf-page-116) |
| 167 getJointLockedInCartImpedanceMode                     | [PDF 117](pages-073-144.md#pdf-page-117) |
| 168 setThresholdTorque                                    | [PDF 117](pages-073-144.md#pdf-page-117) |
| 169 getThresholdTorque                                    | [PDF 118](pages-073-144.md#pdf-page-118) |
| 170 setHeartbeatParam                                     | [PDF 118](pages-073-144.md#pdf-page-118) |
| 171 getHeartbeatParam                                     | [PDF 119](pages-073-144.md#pdf-page-119) |
| 172 customRobotState                                      | [PDF 119](pages-073-144.md#pdf-page-119) |
| 173 getCustomRobotState                                   | [PDF 120](pages-073-144.md#pdf-page-120) |
| 174 getTcpPosByTcpName                                    | [PDF 120](pages-073-144.md#pdf-page-120) |
| 175 getTcpPoseByWorkPieceName                             | [PDF 121](pages-073-144.md#pdf-page-121) |
| 176 getPayLoadByTcpName                                   | [PDF 121](pages-073-144.md#pdf-page-121) |
| 177 setDefaultToolTcpCoordinate                           | [PDF 122](pages-073-144.md#pdf-page-122) |
| 178 setDefaultWorkPieceTcpCoordinate                      | [PDF 122](pages-073-144.md#pdf-page-122) |
| 179 getDefaultTcpCoordinate                               | [PDF 123](pages-073-144.md#pdf-page-123) |
| 180 getDefaultWorkPieceCoordinate                         | [PDF 123](pages-073-144.md#pdf-page-123) |
| 181 setVelocityPercentValue                               | [PDF 124](pages-073-144.md#pdf-page-124) |
| 182 getVelocityPercentValue                               | [PDF 124](pages-073-144.md#pdf-page-124) |
| 183 switchRescueMode                                      | [PDF 125](pages-073-144.md#pdf-page-125) |
| 184 getAvoidSingular                                      | [PDF 125](pages-073-144.md#pdf-page-125) |
| 185 setAvoidSingular                                      | [PDF 126](pages-073-144.md#pdf-page-126) |
| 186 getInterpolaterCycleInterval                          | [PDF 126](pages-073-144.md#pdf-page-126) |
| 187 getTcp\_with\_Quaternions                             | [PDF 127](pages-073-144.md#pdf-page-127) |
| 188 getProcessNumSetting                                  | [PDF 127](pages-073-144.md#pdf-page-127) |
| 189 setProcessNumSetting                                  | [PDF 129](pages-073-144.md#pdf-page-129) |
| 190 delProcessNum                                         | [PDF 129](pages-073-144.md#pdf-page-129) |
| 191 getArcRestartParameter                                | [PDF 130](pages-073-144.md#pdf-page-130) |
| 192 setArcRestartParameter                                | [PDF 131](pages-073-144.md#pdf-page-131) |
| 193 weave\_start                                          | [PDF 131](pages-073-144.md#pdf-page-131) |
| 194 weave\_end                                            | [PDF 134](pages-073-144.md#pdf-page-134) |
| 195 getPausePosition                                      | [PDF 134](pages-073-144.md#pdf-page-134) |
| 196 multipleArcing                                        | [PDF 135](pages-073-144.md#pdf-page-135) |
| 197 moveJToTargetWhenPause                                | [PDF 135](pages-073-144.md#pdf-page-135) |
| 198 moveJToPoseWhenPause                                  | [PDF 136](pages-073-144.md#pdf-page-136) |
| 199 moveLToTargetWhenPause                                | [PDF 136](pages-073-144.md#pdf-page-136) |
| 200 moveLToPoseWhenPause                                  | [PDF 137](pages-073-144.md#pdf-page-137) |
| 201 pauseTask                                             | [PDF 137](pages-073-144.md#pdf-page-137) |
| 202 addWayPointByPose                                     | [PDF 137](pages-073-144.md#pdf-page-137) |
| 203 addWayPointByJoints                                   | [PDF 138](pages-073-144.md#pdf-page-138) |
| 204 setWayPointByPose                                     | [PDF 139](pages-073-144.md#pdf-page-139) |
| 205 setWayPointByJoints                                   | [PDF 139](pages-073-144.md#pdf-page-139) |
| 206 powerOn                                               | [PDF 140](pages-073-144.md#pdf-page-140) |
| 207 powerOnConfirmation                                   | [PDF 141](pages-073-144.md#pdf-page-141) |
| 208 powerOff                                              | [PDF 141](pages-073-144.md#pdf-page-141) |
| Appendix A: DianaApi Interface Error Code                 | [PDF 142](pages-073-144.md#pdf-page-142) |
| Appendix B: How to Ensure the Unique Inverse Kinematics   | [PDF 155](pages-145-165.md#pdf-page-155) |
| Appendix C: Further explanation of real-time instructions | [PDF 157](pages-145-165.md#pdf-page-157) |
