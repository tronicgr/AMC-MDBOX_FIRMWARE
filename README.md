# AMC-MDBOX_FIRMWARE
Firmware releases for AMC-MDBOX

### Firmware procedure AMC-MDBOX:
https://www.youtube.com/watch?v=13y8JGdSdX0


If you get a message that it exceeds the buffer size, increase the flash size to 128k in the options:
![Alt Text](https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/Flash_size_128k.jpg)


### You can use the AMC config tool to access and modify the parameters in the AMC-MDBOX:
https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/Simtools_interface_plugin/AMC_Config_Tool_1_1.zip

![Alt Text](https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/Simtools_interface_plugin/AMC_config_MDBOX.jpg)

### Simtools Manual for 4DOF (+TL) platforms v5.1   (Contact me for full version)
https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/AMC-MDBOX%204DOF%20manual%20v5.1%20short.pdf


## Firmware revisions:

### ======= enc_6dof_AMC-mdbox_2_02 =======
```
release date: 08/19/2019: 
-Added new disable park option for 6DOF + rotation type platforms
-Fixed a missing link for saving permanently remotely parameters via AMC Config Tool.
-Updated the AMC Config Tool to support this addition disable park option as well (AMC tool v1.1)
```

### ======= enc_6dof_AMC-mdbox_2_01 =======
```
release date: 08/01/2019: 
-Small bugfix where the the stroke position was set to 100% with Emergency Switch activated on power on.
```

### ======= enc_6dof_AMC-mdbox_2_00 =======
```
release date: 06/17/2019: 
-Provides access to parameters via AMC Config utility
```

### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1h_8DOF_Park_4DOF_TL ======= 
```
release date: 6/4/2019   (Rev1h)
  -Fixed delayed start on power on for 4DOF + TL to allow slow movement of traction loss actuator to middle position
  
```

### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1g_8DOF_Park_4DOF_TL ======= 
```
release date: 5/8/2019   (Rev1g)
-Added indication LEDs outputs for the various states of the controller
  Green = Motor online
  Yellow = Standby
  Yellow+Red = Park
  Red = Forced Offline
- Added wiring diagram for the indication LEDs, see below.
```

### Videos related to enc_6dof_AMC-mdbox_SERVO_1.4_rev1g_8DOF_Park_4DOF_TL release:

Demostration of Indicator LEDs: 
https://www.youtube.com/watch?v=kvUKilD3APA

### Wiring Diagram for Indication LEDs 
![Alt Text](https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/Indication%20LEDs%20for%20AMC-MDBOX.jpg)

### The mosfet driver for the 12v indication LEDs can be found here:
https://www.amazon.com/dp/B07NWD8W26/
```
Search for: "Anmbest 5PCS DC 5V-36V Dual High-Power MOSFET Drive Module 0-20KHz PWM Brightness Control"
```



### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1f_8DOF_Park_4DOF_TL ======= 
```
release date: 4/30/2019   (Rev1f)
-Added parameters access via terminal
-Added restoring default parameters by holding Menu Exit button while pressing Reset button
  A message should appear on the screen that "default parameters are restored", 
  you can release the Menu Exit button then.
```
### Videos related to enc_6dof_AMC-mdbox_SERVO_1.4_rev1f_8DOF_Park_4DOF_TL release:

Demostration of Auto park/standby: 
https://www.youtube.com/watch?v=yZuzgQdwbfI


### The parameters can be changed via terminal (250000 bps)

### ---List of commands---

Command Number | Display Parameter | Save Parameter
------------| ------------ | -------------
CMD01 |Motornumber: | spv012-spv018
CMD04 |Park Position: | spv04001-spv04254
CMD05 |Park Move Speed: | spv05001-spv05100
CMD06 |Park Move Timeout: | spv0601-spv0690
CMD07 |Standby Position: | spv07010-spv07245
CMD08 |Standby Speed: | spv08000-spv08100
CMD09 |Standby Timeout: | spv0901-spv0990
CMD10 |Disable park type: | spv111-spv115
CMD13 |Actuator Limits: | spv1300-spv1350
CMD14 |Kill switch mode: | spv141-spv142
CMD44 |Display all parameters 
CMD45 |Print this help page 
CMD55 |Print delimited parameter list for simtools
spv45 |Saves all parameters at once
RQM |  Displays model,revision and number of motors
Park | Parks the actuators if in standby mode

```
  Some Commands may not change value - locked

The CMD$$ displays each parameter, and spv$$### saves each parameter with the value indicated. 
To actually store the parameters in the flash memory you need to send "spv45" to save all 
parameters at once. The "$$" on the spv is the command number, and the "###" is the value, 
Some parameters have single digit value, some two digit value and some 3 digit value. 
All values are characters!

Here is a list of the default parameters values you should get when you issue the CMD44 command
(if not like this, you may reset the default parameters via button combination)

01.Motornumber 2-8: 4
04.Park Position 0-254: 1
05.Park_Move_Speed 1-100%: 11
06.Park_Move_Timeout 1-90: 5
07.Standby Position 10-245: 127
08.Standby Speed 0-100%: 24
09.Standby Timeout 1-90: 5
10.Disable park type 1-5: 1
13.Actuator Limits 0-50%: 1
14.Kill switch mode 1-2: 1

CMD55 returns the following numeric values separated by colon ( : ) punctuation mark:
"data:" <Motornumber> ":" <Parkposition> ":" <Parkmovespeed> ":" <Parkmovetimeout> ":" <StandbyPosition> ":" <StandbySpeed> ":"<StandbyTimeout> ":" <Disableparktype> ":" <ActuatorLimits> ":" <Killswitchmode> ":" <Firmwareversion> ":" <AMCModel>

```


### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1e_8DOF_Park_4DOF_TL ======= 

```
release date: 4/25/2019: 
  -Soft start of the platform from Park position
  -Automatic Park when motion software stops sending motion data.
  -Optional Button to switch between Park and Standby positions of the platform 
    (configurable by parameters in LCD menu)
  -Emergency Switch that disables drives
  -Force Offline switch if you need to pause motion and park the platform 
    without closing the motion software or game.
  -Slow movements manual test buttons (from the AMC panel)
```



### Videos related to enc_6dof_AMC-mdbox_SERVO_1.4_rev1e_8DOF_Park_4DOF_TL release:
Auto park/standby guide
https://www.youtube.com/watch?v=F8TXNYhdhe0

Demo of emergency switch
https://www.youtube.com/watch?v=68zQTiNyDcU

Using switch on S1 to Force OFFLINE mode
https://www.youtube.com/watch?v=tnvYDmFxvb0

Default parameters for LCD menu
https://www.youtube.com/watch?v=UWvaFFCBdIk

Manual buttons movement
https://www.youtube.com/watch?v=p4ygx0DuxDU

### Wiring Diagram for emergency buttons and switches
![Alt Text](https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/AMC-MDBOX%20park-standby-emergency-force-offline%20diagram.jpg)






### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1b_8DOF_Soft_pos4 ======= 
```
release date: 12/10/2018: 
Basic firmware with new ID (FF FF) and support for 8DOF
```





