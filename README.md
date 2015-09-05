# SafeZonesAltis
Original Script by Friendly
Edit for Altis by BoleParty[TGM]

There`s another option out there which is working with ProtectionZones and you could use that one instead. Do what you feel like:)


Stock Epoch AntiHack maybe does a cleanup on the player eventhandlers but i was using InfiStar so i can`t tell for sure.

In case you are using InfiStar in run.sqf change following settings to false:

/*  revert allowDamage   */ _RAD = false; /* true or false */ /* if you have safezones using "player allowDamage false;" or similar.. set _RAD = false; */

/*  HandleDamage check   */ _HDC = false; /* true or false */ /* *experimental + Epoch only* - probably publicVariableServer spam but no more godmode hackers. */

/*  Revert HandleDamage  */ _RHD = false; /* true or false */ /* Needs to be  false  for Paintball script */
/
*  Use EH_Fired check   */ _EHF = false; /* true or false */ /* Some mods revert the EventHandlers by default and can cause problems with this check. Tested on Epoch and AltisLife.  */
*

In your scripts.txt to allowDamage line add: !"player allowDamage false;" !"player allowDamage true;" and
to removeEventHandler line add: !"player removeEventhandler["HandleDamage", _safeZoneDamageEH];"

The safezone.sqf put anywhere into your mission file.

Edit your init.sqf and add: [] execVM "safezone.sqf";

If you don`t have an init.sqf just create one and add this line to it.

You can put this file into any folder being located in your mission.pbo so just set the correct path in your init.sqf (for example: [] execVM "scripts\safezone.sqf";

Replace your mission.sqm with the attached one or add the code yourself. If you wanna do all on your own then propbably your mission.sqm is still encrypted so you need to decrypt it. I use eliteness for this action and you can download it from here:

http://www.ofpec.com/editors-depot/index.php?action=details&id=383


Your markers class needs to be replaced with following code:

 class Markers
 {
  items = 9;
  class Item0
  {
   position[] = {14939.9,0.0534991,15083.3};
   name = "center";
   type = "Empty";
  };
  class Item1
  {
   position[] = {23600.6,3.19,18000.7};
   name = "respawn_east";
   type = "Empty";
  };
  class Item2
  {
   position[] = {23600.6,3.19,18000.8};
   name = "respawn_west";
   type = "Empty";
  };
  class Item3
		{
			position[]={6181.6802,83.907501,16876.699};
			name="westsafezone";
			text="Safe Zone";
			type="mil_warning";
			colorName="ColorRed";
		};
		class Item4
		{
			position[]={13334.1,2.23509,14517.9};
			name="centralspawn";
			markerType="ELLIPSE";
			type="Empty";
			colorName="ColorGreen";
			fillName="Grid";
			a=250;
			b=250;
		};
		class Item5
		{
			position[]={13326.2,2.29283,14546.7};
			name="centralsafezone";
			text="Safe Zone";
			type="mil_warning";
			colorName="ColorRed";
		};
		class Item6
		{
			position[]={18464.301,23.3512,14263.8};
			name="eastspawn";
			markerType="ELLIPSE";
			type="Empty";
			colorName="ColorGreen";
			fillName="Grid";
			a=250;
			b=250;
		};
		class Item7
		{
			position[]={18461.801,24.769199,14300};
			name="eastsafezone";
			text="Safe Zone";
			type="mil_warning";
			colorName="ColorRed";
		};
		class Item8
		{
			position[]={6195.4902,89.220802,16839.301};
			name="westspawn";
			markerType="ELLIPSE";
			type="Empty";
			colorName="ColorGreen";
			fillName="Grid";
			a=250;
			b=250;
		};
 };
    
Directly after your class Markers add:

class Sensors
	{
		items=3;
		class Item0
		{
			position[]={18461.801,24.769199,14300};
			a=250;
			b=250;
			activationBy="ANY";
			repeating=1;
			interruptable=1;
			age="UNKNOWN";
			name="eastsafezone";
			expCond="(player distance eastsafezone) < 250;";
			expActiv="hint ""You Entered A Safe Zone -  Acts Of War Strictly Forbidden"";  inSafeZone = true;";
			expDesactiv="hint ""You are leaving the Safe Zone!""; inSafeZone = false;";
			class Effects
			{
			};
		};
		class Item1
		{
			position[]={6181.6802,83.907501,16876.699};
			a=250;
			b=250;
			activationBy="ANY";
			repeating=1;
			interruptable=1;
			age="UNKNOWN";
			name="westsafezone";
			expCond="(player distance westsafezone) < 250;";
			expActiv="hint ""You Entered A Safe Zone -  Acts Of War Strictly Forbidden""; inSafeZone = true;";
			expDesactiv="hint ""You are leaving the Safe Zone!""; inSafeZone = false;";
			class Effects
			{
			};
		};
		class Item2
		{
			position[]={13326.2,2.29283,14546.7};
			a=250;
			b=250;
			activationBy="ANY";
			repeating=1;
			interruptable=1;
			age="UNKNOWN";
			name="centralsafezone";
			expCond="(player distance centralsafezone) < 250;";
			expActiv="hint ""You Entered A Safe Zone - Acts Of War Strictly Forbidden""; inSafeZone = true;";
			expDesactiv="hint ""You are leaving the Safe Zone!""; inSafeZone = false;";
			class Effects
			{
			};
		};
	};



After your changes you don`t need to encrypt the file again as the server will read the decrypted mission.sqm without any issues.

In case you need help with installation process just contact me:

info@tacongamingmilita.com or boleparty@tacongamingmilitia.com

Regards
BoleParty
