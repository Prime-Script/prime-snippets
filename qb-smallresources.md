# Small Resources

1. Disable control of vehicle while in the air

```
CreateThread(function()
    while true do
        local sleep = 1000
        local ped = PlayerPedId()
        if IsPedInAnyVehicle(ped) and not IsPedInAnyPlane(ped) and not IsPedInAnyHeli(ped) then
            local veh = GetVehiclePedIsIn(ped)
            local air = IsEntityInAir(veh)
            sleep = 100
            if air then
                sleep = 0
                DisableAllControlActions(0)
                EnableControlAction(0, 1, true)
                EnableControlAction(0, 2, true)
                EnableControlAction(0, 245, true)
                EnableControlAction(0, 0, true)
                EnableControlAction(0, 322, true)
                EnableControlAction(0, 288, true)
                EnableControlAction(0, 213, true)
                EnableControlAction(0, 249, true)
                EnableControlAction(0, 75, true)
            end
        end
        Wait(sleep)
    end
end)
```

2. This fixes an exploit regarding aim assist

```
CreateThread(function()
  while true do
    Wait(0)
        if IsPedArmed(PlayerPedId(), 2) and IsPedArmed(PlayerPedId(), 4) then
          SetPlayerLockon(PlayerId(), false)
        end
  end
end)
```