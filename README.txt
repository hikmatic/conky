Before using conkyrc1, conkyrc2 and conky_accuw some steps must be done first.
in this conky configuration , there is no images,all based on symbols  so we need to have some special fonts instead.
1-Install these fonts if you don't have aleready.
  -DS-Digital
  -ConkySymbols
  -light LED Board-7
  -pixel LCD7
  -Poky
  -(*)OpenLogos
  -(**)CutOutsFor3DFX
  -(***)conkyweather
   *:necessary for Calendar
   **:necessary for ubuntu and tux logo 
   ***:necessary for weather 
2-Mail
   it requieres to install conkyemail 
   for ubuntu:sudo apt-get install conkyemail 
3-Music
  for the moment I configured only Clementine and audacious
  it requieres conkyclementine 
  for ubuntu:sudo apt-get install conkyclementine
  how to use in conkyrc file:
  ${exec conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=your_email_without_@ --password=your_password --ssl}
4-Lua file ( for conkyrc2)
   in conkyrc2 file change the directory to your bargraph.lua location lua_load /home/user/bargraph.lua
4-Weather
  conkyForecast not supported by weather.com so, we will use shell script which will parse the weather from accuwteather.com
    1-place accuweather_conky in your home folder
    2-website www.accuweather.com , type your address in searcg bar, if your city is found then copy the addresse and keep it (for my Case Fes Morocco) http://www.accuweather.com/en/ma/fes/243090/weather-forecast/243090
    3-in accuw_script paste this accuweather addresse in address="http://www.accuweather.com/en/ma/fes/243090/weather-forecast/243090"

4-start conky with your session
   -create a shell script then add it to startup applications
    here is my script
##conky_start.sh     
#!/bin/bash
 sleep 16;  
conky -d -c ~/.conky/.conkyrc1 &
sleep 2; 
conky -d -c ~/.conkyrc2 & conky -d -c ~/conky_accuw &
exec killall conky
sleep 2; 
conky -d -c ~/.conky/.conkyrc1 &
conky -d -c ~/.conkyrc2 &
conky -d -c ~/conky_accuw &
conky -d -c ~/.conky/.conkyrc1 &
exit 

For insterface you can replace ppp0 by your interface

  
   
