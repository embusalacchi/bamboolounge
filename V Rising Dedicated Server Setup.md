Title: V Rising Dedicated Server Setup
Date: June 10th, 2022

## V Rising Dedicated Server Setup
I put up a dedicated V Rising server for a few of us to use and while the documentation is generally decent I kept running into weird issues with file paths and the configuration files.  I figured I would put my experience into a post to remember what I did and maybe help someone else.

The V Rising Dedicated Server documentation on [GitHub](https://github.com/StunlockStudios/vrising-dedicated-server-instructions) is a good starting point.  That said there seem to be some inconsistencies with where the dedicated server looks for your custom configuration files.  Initially I was using the ``"-persistentDataPath c:\servers\v-rising\save-data"` flag and expecting to find the configuration .json files in the .\Settings folder but it didn't seem to find them there.  Eventually after a bunch of trial and error I just decided to use the default path and it seemed to work as expected.  

My final configuration looks like this:
* Startup Command: `VRisingServer.exe -serverName "The Bamboo Lounge" -saveName "bbl1" -logFile "C:\Servers\v-rising\logs\VRisingServer.log" -address "my.internal.ip.address"`
* My ServerGameSettings.json, ServerHostSettings.json, adminlist.txt and banlist.txt are located here: `C:\Users\<yourusername>\AppData\LocalLow\Stunlock Studios\VRisingServer\Saves\v1\bbl1`
* Logfiles are going to the correct spot as designated by the command line above: `C:\Servers\v-rising\logs\VRisingServer.log`
* I am using nssm to create a V Rising Windows service that makes sure it stays running.  Make sure you run the service as the user found in the path above!
* I have a scheduled task that stops the service, run the SteamCMD AppUpdate command, and then restarts the service every night at 2:30am.  This is to make sure the server version is regularly updated.
* I am using Tailscale extensively for my private networking.  I use small droplets at Digital Ocean to give my external facing services a static public IP address and use firewall rules to redirect them to servers in my house over tailscale.  With the ServerHostSettings.json referenced below I have opened up and redirected UDP/9876 and UDP/9877 to the V Rising server. I also have the V Rising server using the same droplet as an exit node for all traffic. Please note: I saw issues connecting through the server browser using non-standard UDP ports.  This MAY be something unrelated but I could only get it to work using the default ports.  

**ServerHostSettings.json: ** 
```
{
  "Name": "The Bamboo Lounge",
  "Description": "Standard PVE Server",
  "Port": 9876,
  "QueryPort": 9877,
  "Address": "my.private.ip.address",
  "MaxConnectedUsers": 24,
  "MaxConnectedAdmins": 4,
  "ServerFps": 30,
  "SaveName": "bbl1",
  "Password": "<supersecretpassword>",
  "Secure": true,
  "ListOnMasterServer": true,
  "AutoSaveCount": 50,
  "AutoSaveInterval": 600,
  "AdminOnlyDebugEvents": true,
  "DisableDebugEvents": false,
  "API": {},
  "Rcon": {
    "Enabled": false,
    "Port": 25575,
    "Password": ""
  }
}
```

