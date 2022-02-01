local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

local Window = Library.CreateLib("Play HUB | Blox Fruit 17", "DarkTheme")



-- Fram



local Tab = Window:NewTab("Fram")

local FramSection = Tab:NewSection("Auto Armed")



local Weaponlist = {}

local Weapon = nil



for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do

    table.insert(Weaponlist,v.Name)

end



FramSection:NewDropdown("select weapon", " ", Weaponlist, function(currentOption)

    Weapon = currentOption

end)



FramSection:NewToggle("Auto Equip", " ", function(a)

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







FarmSection:NewButton("Fart Attack", "ButtonInfo", function()

    spawn(function()

   game:GetService("RunService").RenderStepped:Connect(function()

    pcall(function()

        local Combat = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)

        local Cemara = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)

        Cemara.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}

        Combat.activeController.timeToNextAttack = 0

    end)

end) 

end)





spawn(function()

   game:GetService("RunService").RenderStepped:Connect(function()

    pcall(function()

        game:GetService'VirtualUser':CaptureController()

        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))

    end)

end) 

end)

end)







FarmSection:NewButton("Fram Gods V.1", "ButtonInfo", function()

    _G.AutoFarm_Level = true

_G.FastAttack = true

 

 

 

 

 

 

 

 

 

function checklevel()

    local Level = game:GetService("Players").LocalPlayer.Data.Level.Value

    if Level == 1 or Level <= 11 then

        MON = "Bandit [Lv. 5]"

        QUESTTITLE = "Bandit"

        QUESTPOS = CFrame.new(1060.0158691406, 16.424287796021, 1547.9769287109)

        MONPOS = CFrame.new(1148.8698730469, 16.432844161987, 1630.5396728516)

        QUESTNAME = "BanditQuest1"

        QUESTNUMBER = 1

        SPAWNPOINT = "Default"

        SPAWNPOINTPOS = CFrame.new(973.96197509766, 16.273551940918, 1413.2775878906)

    end

end

Method = CFrame.new(0,25,0)

 

spawn(function()

   while wait(3) do

       if Methodnow == 1 then

        Methodnow = 2

        Method = CFrame.new(0,25,0)

        else

        Methodnow = 1

        Method = CFrame.new(0,0,25)

       end

    end

end)

 

spawn(function()

   while wait() do

       if _G.WARP then

           game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true

        else

            game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false

        end

    end

end)

 

spawn(function()

    game:GetService("RunService").Heartbeat:Connect(function()

        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid") and _G.AutoFarm_Level then

            setfflag("HumanoidParallelRemoveNoPhysics", "False")

            setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")

            game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)

        end

    end)

end)

 

 

spawn(function()

    while wait() do

        if _G.AutoFarm_Level then

            pcall(function()

                checklevel()

    

                if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,QUESTTITLE) then

                    local args = {

                        [1] = "AbandonQuest"

                    }

                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

                end

                if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then

                    

                    if game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT then

                        local args = {

                            [1] = "SetTeam",

                            [2] = "Pirates"

                        }

                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

                        wait(0.5)

                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = QUESTPOS

                        wait(0.8)

                            local args = {

                                [1] = "StartQuest",

                                [2] = QUESTNAME,

                                [3] = QUESTNUMBER

                            }

                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

                        wait(0.8)

                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = MONPOS

                    else

                        _G.WARP = true

                        repeat 

                            wait()

                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = SPAWNPOINTPOS

                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")

                        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT or _G.AutoFarm_Level == false

                        _G.WARP = false

                    end

                end

                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do

                    for i2,v2 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do

                        if v.Name == MON and v2.Name == MON then

                            v2.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame

                            v2.HumanoidRootPart.CanCollide = false

                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * Method

                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)

                        end

                    end

                end

            end)

        end

    end

end)

 

  spawn(function()

   game:GetService("RunService").RenderStepped:Connect(function()

    pcall(function()

        local Combat = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)

        local Cemara = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.CameraShaker)

        Cemara.CameraShakeInstance.CameraShakeState = {FadingIn = 3, FadingOut = 2, Sustained = 0, Inactive = 1}

        Combat.activeController.timeToNextAttack = 0

    end)

end) 

end)





spawn(function()

   game:GetService("RunService").RenderStepped:Connect(function()

    pcall(function()

        game:GetService'VirtualUser':CaptureController()

        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))

    end)

end) 

end)

end)





FarmSection:NewButton("Farm Gods V.2", "ButtonInfo", function()

    loadstring(game:HttpGet"https://raw.githubusercontent.com/KuppaHX/Saza/main/SazaLoader.lua")()

end)





FarmSection:NewButton("Farm Gods V.3", "ButtonInfo", function()

    loadstring(game:HttpGet"https://raw.githubusercontent.com/natoppo044/modzcaster/main/Saza.lua")()

end)





FarmSection:NewButton("Farm Gods V.4", "ButtonInfo", function()

    loadstring(game:HttpGet("https://raw.githubusercontent.com/hajibeza/RIPPER-HUB/main/Bf%20Mobile"))()

end)





FarmSection:NewButton("Farm Gods V.5", "ButtonInfo", function()

    loadstring(game:HttpGet("https://raw.githubusercontent.com/Strikehubv2z/StormSKz/main/All_in_one"))()

end)





 FarmSection:NewButton("Farm Gods V.6", "ButtonInfo", function()

    loadstring(game:HttpGet("https://raw.githubusercontent.com/natoppo044/modzcaster/main/Bloxfruit17.lua", true))()

end)





FarmSection:NewButton("Farm Gods V.7", "ButtonInfo", function()

    loadstring(game:HttpGet("https://raw.githubusercontent.com/natoppo044/modzcaster/main/dinobf.lua", true))()

end)





FarmSection:NewButton("Farm Gods V.8", "ButtonInfo", function()

    loadstring(game:HttpGet"https://raw.githubusercontent.com/xDepressionx/Free-Script/main/AllScript.lua")()

end)





FarmSection:NewButton("Farm Gods V.9", "ButtonInfo", function()

    loadstring(game:HttpGet("https://raw.githubusercontent.com/Frerfgzz/free-script/main/SMZHUBv1"))()

end)





FarmSection:NewButton("Farm Gods V.10", "ButtonInfo", function()

    loadstring(game:HttpGet("https://raw.githubusercontent.com/kickTh/fly/main/TP.lua.txt", true))()

end)





FarmSection:NewButton("FLY", "ButtonInfo", function()

    --ARCEUS X FLY V2 SCRIPT BY me_ozoneYT

loadstring("\108\111\97\100\115\116\114\105\110\103\40\103\97\109\101\58\72\116\116\112\71\101\116\40\40\39\104\116\116\112\115\58\47\47\103\105\115\116\46\103\105\116\104\117\98\117\115\101\114\99\111\110\116\101\110\116\46\99\111\109\47\109\101\111\122\111\110\101\89\84\47\98\102\48\51\55\100\102\102\57\102\48\97\55\48\48\49\55\51\48\52\100\100\100\54\55\102\100\99\100\51\55\48\47\114\97\119\47\101\49\52\101\55\52\102\52\50\53\98\48\54\48\100\102\53\50\51\51\52\51\99\102\51\48\98\55\56\55\48\55\52\101\98\51\99\53\100\50\47\97\114\99\101\117\115\37\50\53\50\48\120\37\50\53\50\48\102\108\121\37\50\53\50\48\50\37\50\53\50\48\111\98\102\108\117\99\97\116\111\114\39\41\44\116\114\117\101\41\41\40\41\10\10")()

end)



-- teleport



local Tab = Window:NewTab("teleport")

local TPSection = Tab:NewSection("TPSection")



TPSection:NewButton("Bandit [Lv. 0]"", "", function()

    game.Players.localPlayer.Charater.HumanoidRootPart.CFrame = (Frame.new(21392e-08, 1, 5.53303181e-08, -0.999909997, 6.04876931e-08, -0.0133908205)

end)





TPSection:NewButton("Monkey [Lv. 10]", "ButtonInfo", function()

    game.Players.localPlayer.Charater.HumanoidRootPart.CFrame = (Frame.new(364261e-08, 1, 1.25761606e-08, 0.880756438, -5.21796428e-09, -0.473569542)

end)





-- Raid



local Tab = Window:NewTab("Raid")

local RaidSection = Tab:NewSection("RaidSection")



RaidSection:NewButton("Auto Raid"", "ButtonInfo", function()

    loadstring(game:HttpGet("https://pastebin.com/raw/UCsB5xC3", true))()

end)



-- ESP



local Tab = Window:NewTab("ESP")

local ESPSection = Tab:NewSection("ESPSection")



ESPSection:NewButton("Auto ESP"", "ButtonInfo", function()

    loadstring(game:HttpGet("https://pastebin.com/raw/UCsB5xC3", true))()

end)





ESPSection:NewButton("ESPPlayYer"", "ButtonInfo", function()

    while wait() do

     pcall(function()

       for i,v in pairs(game.Players:GetChildren()) do

            if not v.Character.Head:FindFirstChild("ESP") then

                local BillboardGui = Instance.new("BillboardGui")

                local TextLabel = Instance.new("TextLabel")

                BillboardGui.Parent = v.Character.Head

                BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

                BillboardGui.Active = true

                BillboardGui.Name = "ESP"

                BillboardGui.AlwaysOnTop = true

                BillboardGui.LightInfluence = 1.000

                BillboardGui.Size = UDim2.new(0, 200, 0, 50)

                BillboardGui.StudsOffset = Vector3.new(0, 2.5, 0)

                TextLabel.Parent = BillboardGui

                TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)

                TextLabel.BackgroundTransparency = 1.000

                TextLabel.Size = UDim2.new(0, 200, 0, 50)

                TextLabel.Font = Enum.Font.GothamBold

                TextLabel.Text = v.Name

                TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

                TextLabel.TextScaled = true

                TextLabel.TextSize = 14.000

                TextLabel.TextStrokeTransparency = 0.000

                TextLabel.TextWrapped = true

            end

        end

    end) 

end

end)



-- Armed



local Tab = Window:NewTab("Shop")

local ArmedSection = Tab:NewSection("ArmedSection")



ArmedSection:NewButton("Superhuman"", "ButtonInfo", function()

    Weapon - "Superhuman"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





ArmedSection:NewButton("Dragon Breath"", "ButtonInfo", function()

    Weapon - "Dragon Breath"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





ArmedSection:NewButton("Electric"", "ButtonInfo", function()

    Weapon - "Electric"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





ArmedSection:NewButton("Water Karate-fu"", "ButtonInfo", function()

    Weapon - "Water Karate-fu"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





ArmedSection:NewButton("Dark Step"", "ButtonInfo", function()

    Weapon - "Dark Step"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





ArmedSection:NewButton("Electric V.2"", "ButtonInfo", function()

    Weapon - "Electric Claw"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





ArmedSection:NewButton("Dragon  V.2"", "ButtonInfo", function()

    Weapon - "Dragon Talon"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





ArmedSection:NewButton("Dark Step V.2"", "ButtonInfo", function()

    Weapon - "Death Step"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlaye

end)

end

end)



ArmedSection:NewButton("Water Karate-fu V.2"", "ButtonInfo", function()

    Weapon - "Sharkman Karate"

while wait() do

pcall(function()

game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack)

end)

end

end)





-- KillPlayYer





local Tab = Window:NewTab("KillPlayYer")

local KillPlayYerSection = Tab:NewSection("Teleport")

 

--------------------

 

players = {}

 

for i,v in pairs(game:GetService("Players"):GetChildren()) do

   table.insert(players,v.Name)

end

 

KillPlayYerSection:NewDropdown("Select Player", " ", players, function(abc)

    Select = abc

end)

 

 

KillPlayYerSection:NewButton("Refresh", " ", function()

    table.clear(players)

for i,v in pairs(game:GetService("Players"):GetChildren()) do

   table.insert(players,v.Name)

end

end)

 

KillPlayYerSection:NewButton("Teleport", " ", function()

    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[Select].Character.HumanoidRootPart.CFrame

end)






