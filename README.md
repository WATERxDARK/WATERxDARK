
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/kickTh/New-Ui/main/Kavo-UI.txt"))()
local Window = Library.CreateLib("scriptTEST : WATER HUB", "DarkTheme")

local Tab = Window:NewTab("FARM")
local Section = Tab:NewSection("FARM")

local Weaponlist = {}
local Weapon = nil

for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
end

Section:NewDropdown("select weapon", " ", Weaponlist, function(currentOption)
    Weapon = currentOption
end)

Section:NewToggle("Auto Equip", " ", function(a)
AutoEquiped = a
end)

spawn(function()
while wait() do
if AutoEquiped then
pcall(function()
game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(Weapon))
end)
end
end
end)


Section:NewButton("FastAttack", "", function()
    
(getgenv()).Config = {
 ["FastAttack"] = true,
 ["ClickAttack"] = true
} 

coroutine.wrap(function()
local StopCamera = require(game.ReplicatedStorage.Util.CameraShaker)StopCamera:Stop()
    for v,v in pairs(getreg()) do
        if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework then
             for v,v in pairs(debug.getupvalues(v)) do
                if typeof(v) == "table" then
                    spawn(function()
                        game:GetService("RunService").RenderStepped:Connect(function()
                            if getgenv().Config['FastAttack'] then
                                 pcall(function()
                                     v.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
                                     v.activeController.attacking = false
                                     v.activeController.increment = 4
                                     v.activeController.blocking = false   
                                     v.activeController.hitboxMagnitude = 150
    		                         v.activeController.humanoid.AutoRotate = true
    	                      	     v.activeController.focusStart = 0
    	                      	     v.activeController.currentAttackTrack = 0
                                     sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRaxNerous", math.huge)
                                 end)
                             end
                         end)
                    end)
                end
            end
        end
    end
end)();

spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
        if getgenv().Config['ClickAttack'] then
             pcall(function()
                game:GetService'VirtualUser':CaptureController()
			    game:GetService'VirtualUser':Button1Down(Vector2.new(0,1,0,1))
            end)
        end
    end)
end)
end)

Section:NewButton("MELEE", "", function()
    local args = {
    [1] = "AddPoint",
    [2] = "Melee",
    [3] = 1
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

end)

local Tab = Window:NewTab("MIN1")
local Section = Tab:NewSection("MIN1")

Section:NewButton("farm money", "", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/scriptpastebin/raw/main/chestfarm"))()
end)

Section:NewButton("ฆ่าคน", "", function()
    local args = {
    [1] = "PlayerHunter"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

end)

Section:NewButton("สุ่มผล", "", function()
    local args = {
    [1] = "Cousin",
    [2] = "Buy"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

end)

Section:NewButton("ฮาคิ", "", function()
    local args = {
    [1] = "BuyHaki",
    [2] = "Buso"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

end)

local Tab = Window:NewTab("MIN2")
local Section = Tab:NewSection("MIN2")

Section:NewButton("ไม่รู้", "", function()
    local args = {
    [1] = "BuyHaki",
    [2] = "Geppo"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

end)

Section:NewButton("ไม่รู้", "", function()
    local args = {
    [1] = "Buso"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

end)

local Tab = Window:NewTab("MIN3")
local Section = Tab:NewSection("MIN3")
Section:NewButton("KEYBOARD", "", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/kC3dAMvt"))()
end)



local Tab = Window:NewTab("Setting")
local Section = Tab:NewSection("Keybund")
Section:NewKeybind("KeybindText", "KeybindInfo", Enum.KeyCode.RightControl, function()
	Library:ToggleUI()
end)
