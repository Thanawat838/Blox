_G.FastAttack1 = true

local CombatShaker = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)
local CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework) 
local CameraShakerR = require(game.ReplicatedStorage.Util.CameraShaker)
spawn(function()
    for i = 1,math.huge do
        game:GetService("RunService").RenderStepped:wait()
            if _G.FastAttack1 then
                pcall(function()
                    maxincrement = i
                    CameraShakerR:Stop()
                    CombatShaker.CameraShakeInstance.CameraShakeState = {FadingIn = 3,FadingOut =  2,Sustained = 0,Inactive = 1} 
                    CombatFrameworkR.activeController.attacking = false
                    CombatFrameworkR.activeController.timeToNextAttack = -(math.huge * math.huge)
                    CombatFrameworkR.activeController.increment = 3
                    CombatFrameworkR.activeController.hitboxMagnitude = 25
                    CombatFrameworkR.activeController.blocking = false
                    CombatFrameworkR.activeController.timeToNextBlock = 0
                end)
            end
        game:GetService("RunService").RenderStepped:wait()
    end
end)

if _G.FastAttack1 == true then
    while _G.FastAttack1 do wait()
        for i, v in pairs(game.Workspace["_WorldOrigin"]:GetChildren()) do
            if v.Name == "Sounds" then
                v:Destroy() 
            end
        end
    end
end
