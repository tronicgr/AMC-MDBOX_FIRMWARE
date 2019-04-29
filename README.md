# AMC-MDBOX_FIRMWARE
Firmware releases for AMC-MDBOX

## Firmware procedure AMC-MDBOX:
https://www.youtube.com/watch?v=13y8JGdSdX0


### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1b_8DOF_Soft_pos4 ======= 
```
release date: 12/10/2018: 
Basic firmware with new ID (FF FF) and support for 8DOF
```


### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1e_8DOF_Park_4DOF_TL ======= 

```
release date: 4/25/2019: 
  -Soft start of the platform from Park position
  -Automatic Park when motion software stops sending motion data.
  -Optional Button to switch between Park and Standby positions of the platform (configurable by parameters in LCD menu)
  -Emergency Switch that disables drives
  -Force Offline switch if you need to pause motion and park the platform without closing the motion software or game.
  -Slow movements manual test buttons (from the AMC panel)
```



## Videos related to enc_6dof_AMC-mdbox_SERVO_1.4_rev1e_8DOF_Park_4DOF_TL release:
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

## Wiring Diagram for emergency buttons and switches
![Alt Text](https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/AMC-MDBOX%20park-standby-emergency-force-offline%20diagram.jpg)


### ======= enc_6dof_AMC-mdbox_SERVO_1.4_rev1f_8DOF_Park_4DOF_TL ======= 
```
release date: 4/29/2019   (Rev1f)
-Added parameters access via terminal
-Added restoring default parameters by holding Menu Exit button while pressing Reset button
  A message should appear on the screen that "default parameters are restored", you can release the Menu exis button then.
```

## The parameters can be changed via terminal (250000 bps)
```
 ---List of commands---
| Display Parameter    |   | Save Parameter |
CMD01 Motornumber:          spv012-spv018
*CMD02 Dataformat:          spv021-spv022
*CMD03 Print Feedback:      spv031-spv032
CMD04 Park Position:        spv04001-spv04254
CMD05 Park Move Speed:      spv05001-spv05100
CMD06 Park Move Timeout:    spv0601-spv0690
CMD07 Standby Position:     spv07010-spv07245
CMD08 Standby Speed:        spv08000-spv08100
CMD09 Standby Timeout:      spv0901-spv0990
CMD10 Disable park type:    spv111-spv114
*CMD11 Output type:         spv111-spv114
*CMD12 Output mode:         spv121-spv124
CMD13 Actuator Limits:      spv1300-spv1350
CMD14 Kill switch mode:     spv141-spv142
CMD44 Display all parameters values
CMD45 Print this help page
spv45 Saves all parameters at once
RQM - Displays model,revision and number of motors
Park - Parks the actuators if in standby mode

  *Commands with asterisk in front may not change value

The CMD$$ displays each parameter, and spv$$### saves each parameter with the value indicated. 
To actually store the parameters in the flash memory you need to send "spv45" to save all 
parameters at once. The "$$" on the spv is the command number, and the "###" is the value, 
Some parameters have single digit value, some two digit value and some 3 digit value. 
All values are characters!

Here is a list of the default parameters values you should get when you issue the CMD44 command
(if not like this, you may reset the default parameters via button combination)

01.Motornumber 2-8: 4
02.Dataformat 1-2: 1
03.Print Feedback 1-2: 1
04.Park Position 0-254: 1
05.Park_Move_Speed 1-100%: 11
06.Park_Move_Timeout 1-90: 5
07.Standby Position 10-245: 127
08.Standby Speed 0-100%: 24
09.Standby Timeout 1-90: 5
10.Disable park type 1-4: 1
11.Output type 1-4: 4
12.Output mode 1-4: 3
13.Actuator Limits 0-50%: 1
14.Kill switch mode 1-2: 1
```
