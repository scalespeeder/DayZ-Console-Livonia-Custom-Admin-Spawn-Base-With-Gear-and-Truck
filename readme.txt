DayZ Livonia "Admin Spawn Tent Base" For Console and PC json Custom Spawner Mod Instructions & Terms Of Use

This custom object spawner json file will spawn in an Admin Tent with truck & parts at 7100.00 / 6957.85 in Livonia (north of Radunin, in the middle of the map).

Limited Testing on PC Livonia Local Server DAYZ Version 1.19 Jan 2023.

Created by @scalespeeder. Please report bugs & errors to scalespeeder@gmail.com with screenshots.

Many Thanks To Inclement Dab for his amazing DayZ Editor that makes this all possible: https://steamcommunity.com/sharedfiles/filedetails/?id=2250764298

TERMS OF USE
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS
OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN
AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH
THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Using these modded xml / json files and instructions could break the functioning of your DAYZ server, requiring a reinstall that would wipe
all player progress.

Using these modded files neccessitates increased regular restarts to prevent server crashing.

It is suggested you thoroughly test your server after applying these files to ensure proper
functioning of your server.

I always recomend you validate your files at: https://www.xmlvalidation.com/ and https://jsonformatter.curiousconcept.com/

There are four parts to implementing this base: Spawning the base; Editing The Truck types Entry; Editing the Admin Spawn Coordinates; removing it all when you're done.
I recommend you read all the instructions before proceeding.

--------------------------

Instructions To Spawn Base:

Click the "Code" button and "Download Zip" on the Github Repository and extract the files on your local PC for access.

(Optional: For advanced users I have included the original DayZ Editor Mod file "livoniaadminspawnbase.dze" which can be imported into DayZ Editor Mod on PC for customisation.)

Ensure your DayZ Server has activated the cfggameplay.json. For console users on Nitrado Servers, go to "General Settings" on your server and tick "Enable cfggameplay.json".

On PC Servers add the following line to your serverDZ.cfg:

enableCfgGameplayFile = 1;

(On some PC servers, including Nitrado, the serverDZ.cfg is "hidden", so you need to enable "expert mode" in settings,
then go to "expert settings", which is the serverDZ.cfg. Stop the server before making changes this way.)

Upload "livoniaadmintentbase.json" from the extracted files to inside the "custom" folder of the mission directory on your server. This file places the tent and items on your map.
(If you haven't got a "custom" folder, create one.)

Open the cfggameplay.json file in the correct mission file for your server and look for the "objectSpawnersArr" line.

This file tells your server to access your custom file.

Edit it to look like this: 

	"objectSpawnersArr": ["custom/livoniaadmintentbase.json"],
	
If you already are calling custom jsons to spawn items, seperate the files like this:

	"objectSpawnersArr": ["custom/livoniaadmintentbase.json","custom/anotherfile.json","custom/differentfile.json"],
	
Save your changes & upload if you need to.

Restart your server and the "Admin Spawn Tent Base" will appear immediatly. When you have spawned in as admin and taken your gear(see below), remove the entry from the "objectSpawnersArr" line,

so it looks like 

"objectSpawnersArr": [""],

or

"objectSpawnersArr": ["custom/anotherfile.json","custom/differentfile.json"],

Then save and restart your server so that the base and it's contents despawn.

----------------------------------------------------------------

Instructions To Ensure Truck Doesn't De-Spawn On Server Restarts:

Open your types.xml file (it'll be in the db folder of your mission directory)

Find the "Truck_01_Covered" entry and replace it with the entry below:

<type name="Truck_01_Covered">
        <nominal>0</nominal>
        <lifetime>28800</lifetime> <!-- lifetime increased to prevent despawn on restart-->
        <restock>1800</restock>
        <min>0</min>
        <quantmin>-1</quantmin>
        <quantmax>-1</quantmax>
        <cost>100</cost>
        <flags count_in_cargo="0" count_in_hoarder="0" count_in_map="1" count_in_player="0" crafted="0" deloot="0"/>
    </type>
	
-------------------------------------------------	
	
Instructions To Make The Admin Spawn At The Base:

Tell your players that the server will be down for maintenance. Stop the server. Change the password (so other players can't get in). Make sure the base files have been uploaded & cfgameplay & types file edited. (See Above)

Find & open your cfgplayerspawnpoints.xml file.

Below <generator_posbubbles> insert the following line:

<pos x="7125.98" z="6965.25" /> <!-- player will spawn near admin tent base north of Radunin -->

and "blank off" the rest of the coordinates by placing remark / comment brackets around the rest of the coordinates. The start of a remark / comment bracket is <!-- and the end is -->
so that part of the file should look like this: 

		<!--<pos x="6041" z="10719" />
			<pos x="6179" z="10885" />
			<pos x="7021" z="11830" />
			<pos x="7744" z="12151" />
			<pos x="7918" z="11472" />
			<pos x="8650" z="12275" />
			<pos x="8279" z="12104" />
			<pos x="7554" z="11516" />
			<pos x="8591" z="11982" />
			<pos x="8191" z="11890" />
			<pos x="8683" z="11856" />
			<pos x="9297" z="11777" />
			<pos x="6682" z="11660" />
			<pos x="7853" z="11609" />
			<pos x="6079" z="11181" />
			<pos x="8003" z="11939" />
			<pos x="7736" z="11904" />
			<pos x="633" z="7621" />
			<pos x="1883" z="8240" />
			<pos x="6475" z="10619" />
			<pos x="8724" z="11396" />
			<pos x="5431" z="9898" />
			<pos x="9096" z="11439" />
			<pos x="1168" z="7977" />
			<pos x="2537" z="8213" />
			<pos x="6733" z="10595" />
			<pos x="6294" z="10596" />
			<pos x="5479" z="10245" />
			<pos x="6019" z="10427" />
			<pos x="6622" z="10308" />
			<pos x="6958" z="11271" />
			<pos x="5807" z="10430" />
			<pos x="4099" z="9101" />
			<pos x="2683" z="8147" />
			<pos x="3644" z="8701" />
			<pos x="3032" z="8033" />
			<pos x="6704" z="10912" />
			<pos x="6834" z="11458" />
			<pos x="8404" z="11398" />
			<pos x="3714" z="9055" />
			<pos x="5779" z="10109" />
			<pos x="3847" z="8844" />
			<pos x="1999" z="7959" />
			<pos x="3677" z="8256" />
			<pos x="6898" z="10977" />
			<pos x="947" z="7951" />
			<pos x="1602" z="8064" />
			<pos x="3726" z="8562" />
			<pos x="4071" z="8580" />
			<pos x="2343" z="7736" />
			<pos x="776" z="6766" />
			<pos x="4715" z="9267" />
			<pos x="2274" z="7437" />
			<pos x="5000" z="8978" />
			<pos x="5000" z="8770" />
			<pos x="4394" z="8124" />
			<pos x="756" z="7205" />
			<pos x="3454" z="7809" />
			<pos x="2124" z="7319" />
			<pos x="4286" z="9002" />
			<pos x="1414" z="7816" />
			<pos x="5167" z="9182" />
			<pos x="4554" z="9272" />
			<pos x="1775" z="7813" />
			<pos x="5407" z="9569" />
			<pos x="1520" z="6860" />
			<pos x="862" z="7552" />
			<pos x="1053" z="7057" />
			<pos x="1268" z="6816" />
			<pos x="2231" z="7855" />
			<pos x="5088" z="9277" />
			<pos x="1157" z="7753" />
			<pos x="4227" z="8841" />
			<pos x="5469" z="9219" />
			<pos x="2408" z="7575" />
			<pos x="1857" z="6858" />
			<pos x="5313" z="9394" />
			<pos x="4329" z="8596" />
			<pos x="4234" z="8463" />
			<pos x="924" z="7647" />
			<pos x="2649" z="7495" />
			<pos x="10754" z="11390" />
			<pos x="9970" z="10735" />
			<pos x="10306" z="11025" />
			<pos x="10851" z="11449" />
			<pos x="11260" z="10782" />
			<pos x="11282" z="9972" />
			<pos x="10525" z="11504" />
			<pos x="11847" z="9854" />
			<pos x="11866" z="9788" />
			<pos x="11961" z="9411" />
			<pos x="12093" z="9522" />
			<pos x="11307" z="11588" />
			<pos x="10978" z="10617" />
			<pos x="9611" z="11525" />
			<pos x="11235" z="10487" />
			<pos x="11175" z="11685" />
			<pos x="9754" z="11778" />
			<pos x="11351" z="11312" />
			<pos x="11221" z="11195" />
			<pos x="10138" z="11500" />
			<pos x="9773" z="11569" />
			<pos x="10927" z="11651" />
			<pos x="10372" z="11416" />
			<pos x="9822" z="11243" />
			<pos x="10678" z="10751" />
			<pos x="11018" z="11012" />
			<pos x="11307" z="10152" />
			<pos x="10387" z="11264" />
			<pos x="10906" z="10848" />
			<pos x="11522" z="10173" />
			<pos x="10141" z="11199" />-->
			
Save and then restart the server. Login, and kill your current character. You should re-spawn at the admin base. Take all the gear you want and fix the truck if necessary. Move away from the base.
Exit the game and stop the server. Open up cfgplayerspawnpoints.xml again, delete the base spawn coordinates & remove the remark / comments brackets from the rest of the comments. Remove the base 
reference from the objectspawnarray line in your cfggameplay.json. Change the password back to what it was. Tell your players that the server is coming out of maintenance mode.

When you restart the server the base will disapear but you'll have all your admin gear.

Enjoy! Thanks, Rob.

Thanks, Rob.
