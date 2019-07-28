## Reflashing Your Biogotchi ##

This tutorial will walk you through flashing your Biogotchi using the Arduino IDE and the included libraries.

***Work In Progress** - come back later for details on reflashing!*

## Dev Notes ##

	Non-condition Acitivity
		Sub-activity
		--Conditional Activity - Task
### States ###

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
	--Reset Button 3s Hold - ESP32 Deep Sleep w/Status Save
	Wake 
	--Poll Timer Up - Wake Routine
		Check Status
		--Status Change - Notify On Need [hungry/sick/etc.]
	--Reset Button Press - Wake <full battery use>
		Wake Screen
		Wake Organism
		Reset Activity Timeout Timer
	
```


