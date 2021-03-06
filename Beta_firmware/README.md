Beta versions. 

---------------------------------------------------------------------------------------------------------------------
--- enc_6dof_AMC-mdbox_2_03_beta_spike6 ---

Beta release for AMC config tool v1.2 and AMC-mdbox firmware v2.03 beta spike6:

- Download it and try it, but not before you update to the newest v2.03 beta spike6 firmware. 

https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/Beta_firmware/AMC_Config_tool_1_2.zip
https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/Beta_firmware/enc_6dof_AMC-mdbox_2_03_beta_spike6.zip

- See how it operates here: https://www.youtube.com/watch?v=EQ3INaih13k

![Alt Text](https://github.com/tronicgr/AMC-MDBOX_FIRMWARE/blob/master/Beta_firmware/AMC-Config-tool-v1_2_MDBX.jpg)

- fixed issue with jump occuring if Force offline switch is used while online. The actuators now return to online position smoothly.


---------------------------------------------------------------------------------------------------------------------
--- enc_6dof_AMC-mdbox_2_03_beta_spike5 ---

- Fixed the disable Auto park issue where all actuators where parking on Force Offline switch even the TL and Surge ones.
- Fixed issue where the Disable autopark parameter was reverting to default value.
- Fixed issue where the online motion where not restoring from Force Offline mode when you were modifying parameters. The changes to the parameters are temporary now and you can save them as normal after you disconnect from Simtools or other motion software.
- Changed the order of appearance for the Spike Filter "Range" and "Level" so you won't have to go back to modify the level twice.

See detailed info about the changes on the video here: https://www.youtube.com/watch?v=gPdzp0ytFX8

---------------------------------------------------------------------------------------------------------------------

--- enc_6dof_AMC-mdbox_2_03_beta_spike4 ---

-Added spike filter that can be adjusted by two parameters:
- 1. Level: it defines the distance in data points that the input position have to exceed for the spike filter to kick in. This is absolute 16bit value 0-65535, default value 32767. If the spike filter kicks in too often, increase this value.
- 2. Enable or Disable the Spike Filter
- 3. Also added two stage positioning algorithm to move faster for large distances and slow down when near target for these artificial movements.
- 4. Fixes the transition to online motion data if the Force-Offline switch is used, avoiding jumps or jolts in the motion.
- 5. Fixed the position seek during spike filtering to to a range instead a point to allow catching up to real time motion data immediately after a crash.
- 6. Added Range parameter for the Spike Filter to better fine tune for lower values of the spike filter value.
- 7. The YELLOW LED will light steady during spike filter being engaged and will revert to GREEN LED when it catches up to live data.

This new Spike Filter works by detecting spikes in position data larger that the defined level (most likely crashes) and it will automatically activate the Force Offline mode, that places the actuators in seek position mode until all motors catch up with live motion data. So for the duration of the crash the motors will avoid doing any intense jolts and most likely the motion will come back on when the vehicle is standing still. It should work wonders in long duration crashes like when you have rollover down a bank for example...

To enable the indication LEDs you need to set DIP switch #2 to ON position. 

The LED's are not PWM, they are solid ON now.
