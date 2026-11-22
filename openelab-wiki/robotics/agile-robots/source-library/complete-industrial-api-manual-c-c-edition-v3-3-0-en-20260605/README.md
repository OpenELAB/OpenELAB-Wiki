# Industrial C/C++ API manual V3.3.0 — complete reference

{% hint style="info" %}
**Complete supplied source:** Industrial API Manual (C\&C++ Edition) \_V3.3.0\_EN\_20260605.pdf · **Coverage:** 190 original PDF pages. [Return to the Agile Robots source library](../).
{% endhint %}

Every source page is retained in the original order. The **Original page** view preserves complete diagrams, photographs, tables, equations, connector orientation, notices and examples. The **Searchable text** view preserves native PDF text or the slide’s native text, embedded links and substantive speaker notes. Text extraction can retain reading-order/character defects; use the original image for exact layout, table columns and code indentation.

{% hint style="warning" %}
This is the supplied Industrial C/C++ API V3.3.0 reference dated 2026-06-05. Match the delivered SDK and controller firmware. Preserve argument types, array lengths, coordinate conventions, return codes and per-function units. State inspection, writes, enable/reset, calibration and motion have different effects.
{% endhint %}

**Attribution:** the manufacturer and contributors identified in the supplied document. Original notices remain visible on every source page. Navigation, revision notes and the linked engineering explanations are OpenELAB editorial additions.

## Reading sections

| Full in-wiki section                   | Original PDF pages |
| -------------------------------------- | ------------------ |
| [Read pages 1–72](pages-001-072.md)    | 1–72               |
| [Read pages 73–144](pages-073-144.md)  | 73–144             |
| [Read pages 145–190](pages-145-190.md) | 145–190            |

## Complete chapter and function index

| Source section / function                                | Original page                            |
| -------------------------------------------------------- | ---------------------------------------- |
| Overview                                                 | [PDF 10](pages-001-072.md#pdf-page-10)   |
| Compatibility Statement                                  | [PDF 10](pages-001-072.md#pdf-page-10)   |
| Function Description                                     | [PDF 10](pages-001-072.md#pdf-page-10)   |
| 1 initSrvNetInfo                                         | [PDF 10](pages-001-072.md#pdf-page-10)   |
| 2 initSrv                                                | [PDF 11](pages-001-072.md#pdf-page-11)   |
| 3 initSrvV2                                              | [PDF 12](pages-001-072.md#pdf-page-12)   |
| 4 destroySrv                                             | [PDF 14](pages-001-072.md#pdf-page-14)   |
| 5 setPushPeriod                                          | [PDF 15](pages-001-072.md#pdf-page-15)   |
| 6 moveTCP                                                | [PDF 15](pages-001-072.md#pdf-page-15)   |
| 7 rotationTCP                                            | [PDF 16](pages-001-072.md#pdf-page-16)   |
| 8 moveJoint                                              | [PDF 17](pages-001-072.md#pdf-page-17)   |
| 9 moveJToTarget                                          | [PDF 18](pages-001-072.md#pdf-page-18)   |
| 10 moveJToPose                                           | [PDF 19](pages-001-072.md#pdf-page-19)   |
| 11 moveJ                                                 | [PDF 20](pages-001-072.md#pdf-page-20)   |
| 12 moveL                                                 | [PDF 21](pages-001-072.md#pdf-page-21)   |
| 13 moveLToTarget                                         | [PDF 22](pages-001-072.md#pdf-page-22)   |
| 14 moveLToPose                                           | [PDF 23](pages-001-072.md#pdf-page-23)   |
| 15 moveLToPose\_ex                                       | [PDF 24](pages-001-072.md#pdf-page-24)   |
| 16 speedJ                                                | [PDF 26](pages-001-072.md#pdf-page-26)   |
| 17 speedL                                                | [PDF 27](pages-001-072.md#pdf-page-27)   |
| 18 freeDriving                                           | [PDF 28](pages-001-072.md#pdf-page-28)   |
| 19 stop                                                  | [PDF 29](pages-001-072.md#pdf-page-29)   |
| 20 forward                                               | [PDF 29](pages-001-072.md#pdf-page-29)   |
| 21 inverse                                               | [PDF 30](pages-001-072.md#pdf-page-30)   |
| 22 getJointPos                                           | [PDF 31](pages-001-072.md#pdf-page-31)   |
| 23 getJointAngularVel                                    | [PDF 31](pages-001-072.md#pdf-page-31)   |
| 24 getJointCurrent                                       | [PDF 32](pages-001-072.md#pdf-page-32)   |
| 25 getJointTorque                                        | [PDF 33](pages-001-072.md#pdf-page-33)   |
| 26 getTcpPos                                             | [PDF 33](pages-001-072.md#pdf-page-33)   |
| 27 getTcpExternalForce                                   | [PDF 34](pages-001-072.md#pdf-page-34)   |
| 28 releaseBrake                                          | [PDF 35](pages-001-072.md#pdf-page-35)   |
| 29 holdBrake                                             | [PDF 35](pages-001-072.md#pdf-page-35)   |
| 30 changeControlMode                                     | [PDF 36](pages-001-072.md#pdf-page-36)   |
| 31 getLibraryVersion                                     | [PDF 36](pages-001-072.md#pdf-page-36)   |
| 32 formatError                                           | [PDF 36](pages-001-072.md#pdf-page-36)   |
| 33 getLastError                                          | [PDF 37](pages-001-072.md#pdf-page-37)   |
| 34 setLastError                                          | [PDF 37](pages-001-072.md#pdf-page-37)   |
| 35 getLastWarning                                        | [PDF 38](pages-001-072.md#pdf-page-38)   |
| 36 setLastWarning                                        | [PDF 38](pages-001-072.md#pdf-page-38)   |
| 37 setDefaultActiveTcp                                   | [PDF 39](pages-001-072.md#pdf-page-39)   |
| 38 getLinkState                                          | [PDF 39](pages-001-072.md#pdf-page-39)   |
| 39 getTcpForce                                           | [PDF 40](pages-001-072.md#pdf-page-40)   |
| 40 getJointForce                                         | [PDF 41](pages-001-072.md#pdf-page-41)   |
| 41 isCollision                                           | [PDF 41](pages-001-072.md#pdf-page-41)   |
| 42 initDHCali                                            | [PDF 42](pages-001-072.md#pdf-page-42)   |
| 43 getDHCaliResult                                       | [PDF 42](pages-001-072.md#pdf-page-42)   |
| 44 setDH                                                 | [PDF 43](pages-001-072.md#pdf-page-43)   |
| 45 setWrd2BasRT                                          | [PDF 44](pages-001-072.md#pdf-page-44)   |
| 46 setFLa2TcpRT                                          | [PDF 45](pages-001-072.md#pdf-page-45)   |
| 47 getRobotState                                         | [PDF 45](pages-001-072.md#pdf-page-45)   |
| 48 resume                                                | [PDF 46](pages-001-072.md#pdf-page-46)   |
| 49 setJointCollision                                     | [PDF 47](pages-001-072.md#pdf-page-47)   |
| 50 setCartCollision                                      | [PDF 47](pages-001-072.md#pdf-page-47)   |
| 51 enterForceMode                                        | [PDF 48](pages-001-072.md#pdf-page-48)   |
| 52 leaveForceMode                                        | [PDF 49](pages-001-072.md#pdf-page-49)   |
| 53 setDefaultActiveTcpPose                               | [PDF 49](pages-001-072.md#pdf-page-49)   |
| 54 setResultantCollision                                 | [PDF 50](pages-001-072.md#pdf-page-50)   |
| 55 setJointImpeda                                        | [PDF 50](pages-001-072.md#pdf-page-50)   |
| 56 getJointImpeda                                        | [PDF 51](pages-001-072.md#pdf-page-51)   |
| 57 setCartImpeda                                         | [PDF 52](pages-001-072.md#pdf-page-52)   |
| 58 getCartImpeda                                         | [PDF 52](pages-001-072.md#pdf-page-52)   |
| 59 zeroSpaceFreeDriving                                  | [PDF 53](pages-001-072.md#pdf-page-53)   |
| 60 createPath                                            | [PDF 54](pages-001-072.md#pdf-page-54)   |
| 61 addMoveL                                              | [PDF 54](pages-001-072.md#pdf-page-54)   |
| 62 addMoveJ                                              | [PDF 55](pages-001-072.md#pdf-page-55)   |
| 63 runPath                                               | [PDF 57](pages-001-072.md#pdf-page-57)   |
| 64 destroyPath                                           | [PDF 57](pages-001-072.md#pdf-page-57)   |
| 65 rpy2Axis                                              | [PDF 57](pages-001-072.md#pdf-page-57)   |
| 66 axis2RPY                                              | [PDF 58](pages-001-072.md#pdf-page-58)   |
| 67 homogeneous2Pose                                      | [PDF 58](pages-001-072.md#pdf-page-58)   |
| 68 pose2Homogeneous                                      | [PDF 59](pages-001-072.md#pdf-page-59)   |
| 69 enableTorqueReceiver                                  | [PDF 59](pages-001-072.md#pdf-page-59)   |
| 70 sendTorque\_rt                                        | [PDF 60](pages-001-072.md#pdf-page-60)   |
| 71 enableCollisionDetection                              | [PDF 60](pages-001-072.md#pdf-page-60)   |
| 72 setActiveTcpPayload                                   | [PDF 61](pages-001-072.md#pdf-page-61)   |
| 73 servoJ                                                | [PDF 61](pages-001-072.md#pdf-page-61)   |
| 74 servoL                                                | [PDF 62](pages-001-072.md#pdf-page-62)   |
| 75 servoJ\_ex                                            | [PDF 63](pages-001-072.md#pdf-page-63)   |
| 76 servoL\_ex                                            | [PDF 64](pages-001-072.md#pdf-page-64)   |
| 77 speedJ\_ex                                            | [PDF 66](pages-001-072.md#pdf-page-66)   |
| 78 speedL\_ex                                            | [PDF 66](pages-001-072.md#pdf-page-66)   |
| 79 dumpToUDisk                                           | [PDF 68](pages-001-072.md#pdf-page-68)   |
| 80 inverse\_ext                                          | [PDF 68](pages-001-072.md#pdf-page-68)   |
| 81 getJointLinkPos                                       | [PDF 69](pages-001-072.md#pdf-page-69)   |
| 82 createComplexPath                                     | [PDF 70](pages-001-072.md#pdf-page-70)   |
| 83 addMoveLByTarget                                      | [PDF 70](pages-001-072.md#pdf-page-70)   |
| 84 addMoveLByPose                                        | [PDF 72](pages-001-072.md#pdf-page-72)   |
| 85 addMoveJByTarget                                      | [PDF 73](pages-073-144.md#pdf-page-73)   |
| 86 addMoveJByPose                                        | [PDF 74](pages-073-144.md#pdf-page-74)   |
| 87 addMoveCByTarget                                      | [PDF 76](pages-073-144.md#pdf-page-76)   |
| 88 addMoveCByPose                                        | [PDF 77](pages-073-144.md#pdf-page-77)   |
| 89 runComplexPath                                        | [PDF 79](pages-073-144.md#pdf-page-79)   |
| 90 destroyComplexPath                                    | [PDF 79](pages-073-144.md#pdf-page-79)   |
| 91 saveEnvironment                                       | [PDF 79](pages-073-144.md#pdf-page-79)   |
| 92 enterForceMode\_ex                                    | [PDF 80](pages-073-144.md#pdf-page-80)   |
| 93 readDI                                                | [PDF 81](pages-073-144.md#pdf-page-81)   |
| 94 readDO                                                | [PDF 81](pages-073-144.md#pdf-page-81)   |
| 95 readAI                                                | [PDF 82](pages-073-144.md#pdf-page-82)   |
| 96 readAO                                                | [PDF 83](pages-073-144.md#pdf-page-83)   |
| 97 setAIMode                                             | [PDF 83](pages-073-144.md#pdf-page-83)   |
| 98 writeDO                                               | [PDF 84](pages-073-144.md#pdf-page-84)   |
| 99 writeAO                                               | [PDF 85](pages-073-144.md#pdf-page-85)   |
| 100 readBusCurrent                                       | [PDF 85](pages-073-144.md#pdf-page-85)   |
| 101 readBusVoltage                                       | [PDF 86](pages-073-144.md#pdf-page-86)   |
| 102 getDH                                                | [PDF 86](pages-073-144.md#pdf-page-86)   |
| 103 getOriginalJointTorque                               | [PDF 87](pages-073-144.md#pdf-page-87)   |
| 104 getJacobiMatrix                                      | [PDF 87](pages-073-144.md#pdf-page-87)   |
| 105 resetDH                                              | [PDF 88](pages-073-144.md#pdf-page-88)   |
| 106 runProgram                                           | [PDF 88](pages-073-144.md#pdf-page-88)   |
| 107 stopProgram                                          | [PDF 89](pages-073-144.md#pdf-page-89)   |
| 108 getVariableValue                                     | [PDF 89](pages-073-144.md#pdf-page-89)   |
| 109 setVariableValue                                     | [PDF 90](pages-073-144.md#pdf-page-90)   |
| 110 isTaskRunning                                        | [PDF 90](pages-073-144.md#pdf-page-90)   |
| 111 pauseProgram                                         | [PDF 91](pages-073-144.md#pdf-page-91)   |
| 112 resumeProgram                                        | [PDF 92](pages-073-144.md#pdf-page-92)   |
| 113 stopAllProgram                                       | [PDF 92](pages-073-144.md#pdf-page-92)   |
| 114 isAnyTaskRunning                                     | [PDF 92](pages-073-144.md#pdf-page-92)   |
| 115 cleanErrorInfo                                       | [PDF 93](pages-073-144.md#pdf-page-93)   |
| 116 setCollisionLevel                                    | [PDF 93](pages-073-144.md#pdf-page-93)   |
| 117 mappingInt8Variant                                   | [PDF 94](pages-073-144.md#pdf-page-94)   |
| 118 mappingDoubleVariant                                 | [PDF 94](pages-073-144.md#pdf-page-94)   |
| 119 mappingInt8IO                                        | [PDF 95](pages-073-144.md#pdf-page-95)   |
| 120 mappingDoubleIO                                      | [PDF 95](pages-073-144.md#pdf-page-95)   |
| 121 setMappingAddress                                    | [PDF 96](pages-073-144.md#pdf-page-96)   |
| 122 lockMappingAddress                                   | [PDF 97](pages-073-144.md#pdf-page-97)   |
| 123 unlockMappingAddress                                 | [PDF 98](pages-073-144.md#pdf-page-98)   |
| 124 getJointCount                                        | [PDF 98](pages-073-144.md#pdf-page-98)   |
| 125 getWayPoint                                          | [PDF 98](pages-073-144.md#pdf-page-98)   |
| 126 setWayPoint                                          | [PDF 99](pages-073-144.md#pdf-page-99)   |
| 127 addWayPoint                                          | [PDF 103](pages-073-144.md#pdf-page-103) |
| 128 deleteWayPoint                                       | [PDF 103](pages-073-144.md#pdf-page-103) |
| 129 getDefaultActiveTcp                                  | [PDF 103](pages-073-144.md#pdf-page-103) |
| 130 getDefaultActiveTcpPose                              | [PDF 104](pages-073-144.md#pdf-page-104) |
| 131 getActiveTcpPayload                                  | [PDF 105](pages-073-144.md#pdf-page-105) |
| 132 zeroSpaceManualMove                                  | [PDF 105](pages-073-144.md#pdf-page-105) |
| 133 moveTcp\_ex                                          | [PDF 106](pages-073-144.md#pdf-page-106) |
| 134 rotationTCP\_ex                                      | [PDF 107](pages-073-144.md#pdf-page-107) |
| 135 setExternalAppendTorCutoffFreq                       | [PDF 108](pages-073-144.md#pdf-page-108) |
| 136 poseTransform                                        | [PDF 108](pages-073-144.md#pdf-page-108) |
| 137 setEndKeyEnableState                                 | [PDF 109](pages-073-144.md#pdf-page-109) |
| 138 updateForce                                          | [PDF 110](pages-073-144.md#pdf-page-110) |
| 139 inverseClosedFull                                    | [PDF 111](pages-073-144.md#pdf-page-111) |
| 140 getInverseClosedResultSize                           | [PDF 112](pages-073-144.md#pdf-page-112) |
| 141 getInverseClosedJoints                               | [PDF 112](pages-073-144.md#pdf-page-112) |
| 142 destoryInverseClosedItems                            | [PDF 113](pages-073-144.md#pdf-page-113) |
| 143 nullSpaceFreeDriving                                 | [PDF 113](pages-073-144.md#pdf-page-113) |
| 144 nullSpaceManualMove                                  | [PDF 113](pages-073-144.md#pdf-page-113) |
| 145 getGravInfo                                          | [PDF 113](pages-073-144.md#pdf-page-113) |
| 146 setGravInfo                                          | [PDF 114](pages-073-144.md#pdf-page-114) |
| 147 getGravAxis                                          | [PDF 114](pages-073-144.md#pdf-page-114) |
| 148 setGravAxis                                          | [PDF 115](pages-073-144.md#pdf-page-115) |
| 149 speedLOnTcp                                          | [PDF 115](pages-073-144.md#pdf-page-115) |
| 150 getTcpForceInToolCoordinate                          | [PDF 116](pages-073-144.md#pdf-page-116) |
| 151 calculateJacobi                                      | [PDF 117](pages-073-144.md#pdf-page-117) |
| 152 calculateJacobiTF                                    | [PDF 118](pages-073-144.md#pdf-page-118) |
| 153 getMechanicalJointsPositionRange                     | [PDF 119](pages-073-144.md#pdf-page-119) |
| 154 getMechanicalMaxJointsVel                            | [PDF 120](pages-073-144.md#pdf-page-120) |
| 155 getMechanicalMaxJointsAcc                            | [PDF 120](pages-073-144.md#pdf-page-120) |
| 156 getMechanicalMaxCartVelAcc                           | [PDF 121](pages-073-144.md#pdf-page-121) |
| 157 getJointsPositionRange                               | [PDF 122](pages-073-144.md#pdf-page-122) |
| 158 getMaxJointsVel                                      | [PDF 122](pages-073-144.md#pdf-page-122) |
| 159 getMaxJointsAcc                                      | [PDF 123](pages-073-144.md#pdf-page-123) |
| 160 getMaxCartTranslationVel                             | [PDF 123](pages-073-144.md#pdf-page-123) |
| 161 getMaxCartRotationVel                                | [PDF 124](pages-073-144.md#pdf-page-124) |
| 162 getMaxCartTranslationAcc                             | [PDF 124](pages-073-144.md#pdf-page-124) |
| 163 getMaxCartRotationAcc                                | [PDF 125](pages-073-144.md#pdf-page-125) |
| 164 setJointsPositionRange                               | [PDF 125](pages-073-144.md#pdf-page-125) |
| 165 setMaxJointsVel                                      | [PDF 126](pages-073-144.md#pdf-page-126) |
| 166 setMaxJointsAcc                                      | [PDF 126](pages-073-144.md#pdf-page-126) |
| 167 setMaxCartTranslationVel                             | [PDF 127](pages-073-144.md#pdf-page-127) |
| 168 setMaxCartRotationVel                                | [PDF 127](pages-073-144.md#pdf-page-127) |
| 169 setMaxCartTranslationAcc                             | [PDF 128](pages-073-144.md#pdf-page-128) |
| 170 setMaxCartRotationAcc                                | [PDF 128](pages-073-144.md#pdf-page-128) |
| 171 requireHandlingError                                 | [PDF 129](pages-073-144.md#pdf-page-129) |
| 172 getJointsSoftLimitRange                              | [PDF 129](pages-073-144.md#pdf-page-129) |
| 173 setJointsSoftLimitRange                              | [PDF 130](pages-073-144.md#pdf-page-130) |
| 174 getFunctionOptI4                                     | [PDF 130](pages-073-144.md#pdf-page-130) |
| 175 setFunctionOptI4                                     | [PDF 131](pages-073-144.md#pdf-page-131) |
| 176 enterRescueMode                                      | [PDF 132](pages-073-144.md#pdf-page-132) |
| 177 leaveRescueMode                                      | [PDF 132](pages-073-144.md#pdf-page-132) |
| 178 getCartImpedanceCoordinateType                       | [PDF 133](pages-073-144.md#pdf-page-133) |
| 179 setCartImpedanceCoordinateType                       | [PDF 133](pages-073-144.md#pdf-page-133) |
| 180 setJointLockedInCartImpedanceMode                    | [PDF 134](pages-073-144.md#pdf-page-134) |
| 181 getJointLockedInCartImpedanceMode                    | [PDF 135](pages-073-144.md#pdf-page-135) |
| 182 setThresholdTorque                                   | [PDF 135](pages-073-144.md#pdf-page-135) |
| 183 getThresholdTorque                                   | [PDF 136](pages-073-144.md#pdf-page-136) |
| 184 setHeartbeatParam                                    | [PDF 136](pages-073-144.md#pdf-page-136) |
| 185 getHeartbeatParam                                    | [PDF 137](pages-073-144.md#pdf-page-137) |
| 186 customRobotState                                     | [PDF 137](pages-073-144.md#pdf-page-137) |
| 187 getCustomRobotState                                  | [PDF 138](pages-073-144.md#pdf-page-138) |
| 188 getTcpPoseByTcpName                                  | [PDF 139](pages-073-144.md#pdf-page-139) |
| 189 getTcpPoseByWorkPieceName                            | [PDF 140](pages-073-144.md#pdf-page-140) |
| 190 getPayLoadByTcpName                                  | [PDF 140](pages-073-144.md#pdf-page-140) |
| 191 setDefaultToolTcpCoordinate                          | [PDF 141](pages-073-144.md#pdf-page-141) |
| 192 setDefaultWorkPieceTcpCoordinate                     | [PDF 141](pages-073-144.md#pdf-page-141) |
| 193 getDefaultTcpCoordinate                              | [PDF 142](pages-073-144.md#pdf-page-142) |
| 194 getDefaultWorkPieceCoordinate                        | [PDF 142](pages-073-144.md#pdf-page-142) |
| 195 setVelocityPercentValue                              | [PDF 143](pages-073-144.md#pdf-page-143) |
| 196 getVelocityPercentValue                              | [PDF 143](pages-073-144.md#pdf-page-143) |
| 197 switchRescueMode                                     | [PDF 144](pages-073-144.md#pdf-page-144) |
| 198 getAvoidSingular                                     | [PDF 144](pages-073-144.md#pdf-page-144) |
| 199 setAvoidSingular                                     | [PDF 145](pages-145-190.md#pdf-page-145) |
| 200 get\_version                                         | [PDF 145](pages-145-190.md#pdf-page-145) |
| 201 getInterpolaterCycleInterval                         | [PDF 147](pages-145-190.md#pdf-page-147) |
| 202 modifyInterferenceZone                               | [PDF 147](pages-145-190.md#pdf-page-147) |
| 203 getInterferenceZone                                  | [PDF 148](pages-145-190.md#pdf-page-148) |
| 204 addInterferenceZoneIO                                | [PDF 150](pages-145-190.md#pdf-page-150) |
| 205 delInterferenceZoneIO                                | [PDF 150](pages-145-190.md#pdf-page-150) |
| 206 getInterferenceZoneIO                                | [PDF 151](pages-145-190.md#pdf-page-151) |
| 207 delInterferenceZone                                  | [PDF 151](pages-145-190.md#pdf-page-151) |
| 208 controllInterferenceZone                             | [PDF 152](pages-145-190.md#pdf-page-152) |
| 209 getInterferenceZoneSwitch                            | [PDF 152](pages-145-190.md#pdf-page-152) |
| 210 getProcessNumSetting                                 | [PDF 152](pages-145-190.md#pdf-page-152) |
| 211 setProcessNumSetting                                 | [PDF 153](pages-145-190.md#pdf-page-153) |
| 212 delProcessNum                                        | [PDF 154](pages-145-190.md#pdf-page-154) |
| 213 getArcRestartParameter                               | [PDF 155](pages-145-190.md#pdf-page-155) |
| 214 setArcRestartParameter                               | [PDF 155](pages-145-190.md#pdf-page-155) |
| 215 weave\_start                                         | [PDF 156](pages-145-190.md#pdf-page-156) |
| 216 weave\_end                                           | [PDF 160](pages-145-190.md#pdf-page-160) |
| 217 getPausePosition                                     | [PDF 160](pages-145-190.md#pdf-page-160) |
| 218 multipleArcing                                       | [PDF 160](pages-145-190.md#pdf-page-160) |
| 219 moveJToTargetWhenPause                               | [PDF 161](pages-145-190.md#pdf-page-161) |
| 220 moveJToPoseWhenPause                                 | [PDF 161](pages-145-190.md#pdf-page-161) |
| 221 moveLToTargetWhenPause                               | [PDF 162](pages-145-190.md#pdf-page-162) |
| 222 moveLToPoseWhenPause                                 | [PDF 162](pages-145-190.md#pdf-page-162) |
| 223 pauseTask                                            | [PDF 163](pages-145-190.md#pdf-page-163) |
| 224 addWayPointByPose                                    | [PDF 163](pages-145-190.md#pdf-page-163) |
| 225 addWayPointByJoints                                  | [PDF 164](pages-145-190.md#pdf-page-164) |
| 226 setWayPointByPose                                    | [PDF 165](pages-145-190.md#pdf-page-165) |
| 227 setWayPointByJoints                                  | [PDF 165](pages-145-190.md#pdf-page-165) |
| 228 powerOn                                              | [PDF 166](pages-145-190.md#pdf-page-166) |
| 229 powerOnConfirmation                                  | [PDF 167](pages-145-190.md#pdf-page-167) |
| 230 powerOff                                             | [PDF 167](pages-145-190.md#pdf-page-167) |
| Appendix A: DianaApi Interface Error Code                | [PDF 168](pages-145-190.md#pdf-page-168) |
| Appendix B: How to Ensure the Unique Inverse Kinematics  | [PDF 180](pages-145-190.md#pdf-page-180) |
| Appendix C：Further explanation of real-time instructions | [PDF 183](pages-145-190.md#pdf-page-183) |
