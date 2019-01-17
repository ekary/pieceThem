# pieceThem
Simple Bashing Function for Scoundrels in the text-rpg Starmourn.


Install and Usage:

Simply import the XML then restart mudlet. Once you are back in, the bashing function is by default assigned to the F1 key. This script makes use of the server side targetting system which you set with "st" so for example:
      st creeper
would set your target as creeper, and when you hit F1 you would attempt to attack a creeper were one in your location. You can change the targetting by editing the script called "Gunslinger Attack" to use ..target or whatever your targetting variable is called. For example, the check for rapidfire reads as follows:
     
     elseif bullets > 1 and pieceThem.rapidfire then
         send("gun rapidfire &tar")
         
now if your targetting variable is "target" then you would change the rapidfire condition to look like this:
      
      elseif bullets > 1 and pieceThem.rapidfire then
         send("gun rapidfire "..target)
        
and you would follow that template for each of the conditions until they are all set to your targetting variable.

Skill Requirements:

This script assumes you have the following abilities:

    1) Crackshot
    2) Stim
    3) Rapidfire
    4) Eject
    5) Point Blank
    6) Kneecap

and that you have rippers in your bandolier with shrapnel attached. If you are missing any of those skills, you can simply comment out that particular part of the Gunslinger Attack condition list. For example, if you don't have eject then you would take the lines that look like this:

    elseif bullets > 0 and pieceThem.eject then
         send("gun eject")
	       send("ied fling ripper at &tar")
  elseif bullets < 1 and pieceThem.eject then
         send("gun eject")
         send("ied fling ripper at &tar")
         
to comment out a line, you simply put "--" before it, so to comment out the eject conditions you would change it to look like this:
    
      --elseif bullets > 0 and pieceThem.eject then
         --send("gun eject")
	       --send("ied fling ripper at &tar")
      --elseif bullets < 1 and pieceThem.eject then
         --send("gun eject")
         --send("ied fling ripper at &tar")
         
 now the function won't check for eject, nor try to send the corresponding attacks if eject is true. You can follow that same template to comment out any other abilities you might be lacking. The only exception is if you are commenting out the very first line in the condition list which is:
 
      if pieceThem.interrupt and bullets > 0 then
      
If you commend that out for some reason, then you must change the first elseif after that to just if.


