OSPi
====

A Python port of the Arduino based OpenSprinkler firmware V 1.8.3
-----------------------------------------------------------------
OpenSprinkler Pi (OSPi) Interval Program Demo<br/>
Creative Commons Attribution-ShareAlike 3.0 license<br/>
June 2013, http://rayshobby.net

***********
UPDATES
===========
***********

August 25 2013
--------------
Additions, bug fixes:<br/>
1. Implemented improved installation and update methods using GitHub.<br/>
2. Added a "Run now" button to the programs page. Allows a schedule program to be started at any time. This overrides (stops) any running program.<br/>
3. Added a readout of the Raspberry Pi's CPU temperature to the home page.<br/>
4. Fixed a bug that would allow a station to be stopped / started without a password ueing the HTML API.<br/>
5. Fixed a bug that would display an incorrect start day for a schedule program.<br/>

August 1 2013 Reved to firmware V 1.8.3
---------------------------------------
Now supports concurrent operation.<br/>
Additions, bug fixes:<br/>
1. Added Sequential/Concurrent option.<br/>
2. Added a function to detect Pi board rev and auto-configure GPIO pins for rev 1 boards.<br/>
3. Fixed a bug in manual mode that would cause any zone with a master association to stop the master when turned off, even if another station with a master association was still running.<br/>
4. Changed how ospi.py handles master zone associations. The program should now work with more than 3 expansion boards (untested in hardware but at least 5 expansion boards, 64 stations work in software).<br/>

July 21 2013
------------
Bug fixes:<br/>
1. Fixed a bug that kept an in progress program running after it was disabled.<br/>
2. Added error checking to prevent an 'lg' KeyError<br/>
3. When a new program was added, it became program 1 instead of being added at the end of the list. - fixed.<br/>
4. When Rain Delay was set, running stations did not stop. - Fixed.<br/>
5. Added a 1.5s delay in the screen refresh of manual Mode to allow active stations and last run log time to update.<br/>

July 19 2013
------------
Code re-factored:<br/>
1. Eliminated over 100 lines of redundant code. The code is now much closer to the micro-controller version. Manual Mode and Run-once now rely on the main loop algorithm. This eliminates potential conflicts and makes the code easier to maintain. The program should now be more stable and have fewer bugs although the UI is a little slower.<br/>
2. Changed bit-wise operations to make them more reliable.<br/>
3. Station names now accept Unicode characters allowing names to be entered in any language.<br/>
4. Faveicon now appears on all pages.<br/>
5. A small bug in the display of Master valve off time in the program preview has been fixed. The off time was 1 minute short.<br/>
6. A file named 'sd_reference.txt' has been added to the OSPi directory. It contains a list with descriptions of the values contained in the global settings dictionary variable (gv.sd) which holds most settings for the program. These values are kept in memory and also stored in the file OSPi/data/sd.json to persist across system restarts. This is for the benefit of anyone who wishes to tinker with the code.<br/>

It is recommended to re-install the entire OSPi directory from GitHub. You can keep your current settings by saving the contents of the OSPi/data directory to another location before installation, then replace the contents of the newly installed directory with your saved files.

july 10 2013
------------
Bug fixes and additions:<br/>
1. Fixed a bug that prevented zones 9+ from running.<br/>
2. The Run once program was not observing the station delay setting - Fixed<br/>
3. Made the sd variable an attribute of the gv module. All references to sd... are now gv.sd... This should potentially fix several bugs, Specifically the Rain delay seems to be working properly now.<br/>
4. The Graph Programs time marker was not recognizing the time zone setting from the Options page - fixed.<br/>
5. Time displayed on the last run line of the main page was not correct - fixed.<br/>
6. Added a faveicon which will help distinguish the OpenSprinkler tabs on the browser.<br/>
7. Added an import statement and file which provide a stub for adding user written custom functions to the interval program without modifying the program itself.<br/>

Jun 26 2013
-----------
1. Last run logging is now working for manual mode when an optional time value is selected, even if more that one station is started.<br/>
2. Fixed a bug that prevented the home page display from updating when running irrigation programs.<br/>
3. Includes a fix from Samer that allows the program preview time marker to update properly.<br/>

Jun 20, 2013
------------
This update includes:<br/>
1. Changed the way ospi.py handles time. It now uses the time zone setting from the OS options page. It also eliminates the auto daylight savings time adjustment that was causing problems for some users.<br/>
2. Fixes a bug mentioned on the forum that caused Samer's app to not update in program mode.<br/>
3. Fixes a bug that caused a program to re-start after the "Stop all stations" button was clicked.<br/>
4. A partial fix for the "last run" problems. Still need to get manual mode with an optional time setting working.<br/>
5. Added a docstring at the top of the ospi.py file with the date for version tracking.

Jun 19, 2013
------------
  Applied Samer Albahra's patch so that the program will work with Samer's mobile web app.
  Per forum discussion: http://rayshobby.net/phpBB3/viewtopic.php?f=2&t=154&start=40#p781<br/>
 

NOTE
====
This folder contains the interval program demo for OpenSprinkler Pi written by Dan Kimberling. It is compatible with the microcontroller-based OpenSprinkler firmware 1.8, the instructions of which can be found at:
  
  http://rayshobby.net/?page_id=730

The program makes use of web.py (http://webpy.org/) for the web interface. 

******************************************************
Full credit goes to Dan for his generous contributions
in porting the microcontroller firmware to Python.
******************************************************

================================================================

***********************
Installation and set up
***********************

For complete and up-to-date installation and set up instructions, see the Rays Hobby wiki page at:
http://rayshobby.net/mediawiki/index.php?title=Python_Interval_Program_for_OSPi