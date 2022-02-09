# QB-BANKROBBERY

This is if you want to update your qb-bankrobbery script from the old **mhacking**, and replace it with a **No Pixel Inspired** Hacking Minigame!

# Fleeca Bank
- Delete The Function from lines 113 to 120

```
local function OnHackDone(success)
    if success then
        TriggerEvent('mhacking:hide')
        TriggerServerEvent('qb-bankrobbery:server:setBankState', closestBank, true)
    else
        TriggerEvent('mhacking:hide')
    end
end
```

- Config.lua

```
------ / Hack The Fleeca Bank (Main Door) / Laptop Minigame
Config.FleecaTime = 15
Config.FleecaBlocks = 4
Config.FleecaRepeat = 2

------ / Hack The Pacific Bank (Main Door) / Laptop Minigame
Config.PacificTime = 15
Config.PacificBlocks = 4
Config.PacificRepeat = 2
```

- Replace the lines 326 and 327 | C & P this snippet (fleeca.lua)

```
exports['hacking']:OpenHackingGame(Config.FleecaTime, Config.FleecaBlocks, Config.FleecaRepeat, 
                    function(Success)
                        if Success then
                            TriggerServerEvent('qb-bankrobbery:server:setBankState', closestBank, true)
                        else
                            QBCore.Functions.Notify("You Failed To Hack The Bank!", "error")
                        end
                    end)
```

# Pacific Bank

- Delete The Function from lines 8 to 15

```
local function OnHackPacificDone(success)
    if success then
        TriggerEvent('mhacking:hide')
        TriggerServerEvent('qb-bankrobbery:server:setBankState', "pacific", true)
    else
        TriggerEvent('mhacking:hide')
    end
end
```

- Replace the lines 104 and 105 | C & P this snippet (pacific.lua)

```
exports['hacking']:OpenHackingGame(Config.PacificTime, Config.PacificBlocks, Config.PacificRepeat, 
                    function(Success)
                        if Success then
                            TriggerServerEvent('qb-bankrobbery:server:setBankState', "pacific", true)
                        else
                            QBCore.Functions.Notify("You Failed To Hack The Bank!", "error")
                        end
                    end)
```