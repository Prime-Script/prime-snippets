# Loading Screen

This is for people that are wanting to get rid of the bridge at the start when loading into your FiveM server

# How to setup

- First create a **client.lua** if one doesn't already exist

- Add this snippet into the **client.lua**

```
local Ran = false

-- This will wait until the client is loaded into the map
AddEventHandler("playerSpawned", function ()
    if not Ran then
        -- This will close the loading screen
        ShutdownLoadingScreenNui()
        Ran = true
    end
end)
```

- Then add this snippet to the top of the **fxmanifest.lua / __resource.lua**

```
-- This is telling the script we will manually shut the loading screen
loadscreen_manual_shutdown "yes"

client_script "client.lua"
```