## Reflashing Your Biogotchi ##

This tutorial will walk you through flashing your Biogotchi using the Arduino IDE and the included libraries.

***Work In Progress** - come back later for details on reflashing!*

## Dev Notes ##

	Non-condition Acitivity
		Sub-activity
		--Conditional Activity - Task
### States ###

`int state` stores the current state

| state | value | note |
|-------|-------|------|
| ST_BOOT | 0 | temporary state on boot up |
| ST_LIVE | 1 | general animated living state |
| ST_MENU | 2 | menu screen open |
| ST_SCREEN | 3 | batt saver screen sleep |
| ST_SLEEP | 4 | ESP32 deep sleep | 

**Power On / Wake Up**
```
	Opening Graphic  Logo
	-- First Time On - Intro Screen
		Hatch Sequence
	-- Regular On - Load Organism
		Load Status
```
**Battery Sleep**
```
	Sleep During  Gameplay
	--Activity Timeout - Screen Sleep w/Poll Timer
	--Battery Button - ESP32 Deep Sleep w/Status Save
	Wake 
	--Poll Timer Up - Wake Routine
		Check Status
		--Status Change - Notify On Need [hungry/sick/etc.]
	--Battery Button during sleep - Wake <return to full battery use>
		Wake Screen
		Wake Organism
		Reset Activity Timeout Timer
	
```
**Filesystem Access**
```
First Badge Flash
	SPIFFS Initialization
		Run SPIFFS_Test.ino from the Arduino Examples to initialize (expect an error on first run - wait until the test continues past the error, signaling the SPIFFS has been properly created and will now be usable)
		
	Adding encoded JPEGs
		Add jpegs to Arduino project folder
		Run tools/JPEGEncoder.ino sketch (TBA)
		Upload via tools/Uploader.ino sketch (TBA)
		Test with TFT_SPIFFS_Jpeg

General Filesystem Access
	Save Status
		Add status string to /stats.dat
		Print status report card to Serial
		Return code 
			[0 = success
			10 = SPIFFS error]
	
	Load Status
		Open /stats.dat from SPIFFS
		Parse stats arrays and data
		Return code 
			[0 = success
			10 = SPIFFS error]
```


