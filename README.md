local redzlib = loadstring(game:HttpGet("https://raw.githubusercontent.com/tbao143/Library-ui/refs/heads/main/Redzhubui"))()
local Window = redzlib:MakeWindow({Title = "kakah Hub |Brookhaven 1.0", SubTitle = "by kakah", SaveFolder = "UniversalScriptConfig"})
Window:AddMinimizeButton({Button = {Image = "rbxassetid://77855434347030", BackgroundTransparency = 0}, Corner = {CornerRadius = UDim.new(0, 8)}})

local customSpeed, customJump, customGravity, customHealth = 16, 50, 196.2, 100
local speedEnabled, jumpEnabled, gravityEnabled, infiniteJumpEnabled, healthEnabled = false, false, false, false, false
local jumpConnection

local MainCheatsTab = Window:MakeTab({"Universal Exploits", "bug"})
MainCheatsTab:AddSection({"Speed Hacks"})
local SpeedToggle = MainCheatsTab:AddToggle({Name = "Enable Speed Hack", Description = "Toggle WalkSpeed", Default = false})
SpeedToggle:Callback(function(val) speedEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.WalkSpeed = val and customSpeed or 16 end end)
MainCheatsTab:AddTextBox({Name = "Speed Modifier", Description = "Set custom WalkSpeed", PlaceholderText = "Enter speed value", Callback = function(val) local num = tonumber(val) if num then customSpeed = num if speedEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.WalkSpeed = customSpeed end end end end})

MainCheatsTab:AddSection({"JumpPower Hacks"})
local JumpToggle = MainCheatsTab:AddToggle({Name = "Enable Jump Hack", Description = "Toggle JumpPower", Default = false})
JumpToggle:Callback(function(val) jumpEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.JumpPower = val and customJump or 50 end end)
MainCheatsTab:AddTextBox({Name = "JumpPower Modifier", Description = "Set custom JumpPower", PlaceholderText = "Enter jump value", Callback = function(val) local num = tonumber(val) if num then customJump = num if jumpEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.JumpPower = customJump end end end end})

MainCheatsTab:AddSection({"Gravity Hacks"})
local GravityToggle = MainCheatsTab:AddToggle({Name = "Enable Gravity Hack", Description = "Toggle Workspace.Gravity", Default = false})
GravityToggle:Callback(function(val) gravityEnabled = val game.Workspace.Gravity = val and customGravity or 196.2 end)
MainCheatsTab:AddTextBox({Name = "Gravity Modifier", Description = "Set custom Gravity", PlaceholderText = "Enter gravity value", Callback = function(val) local num = tonumber(val) if num then customGravity = num if gravityEnabled then game.Workspace.Gravity = customGravity end end end})

MainCheatsTab:AddSection({"Infinite Jump"})
local InfiniteJumpToggle = MainCheatsTab:AddToggle({Name = "Enable Infinite Jump", Description = "Toggle Infinite Jump", Default = false})
InfiniteJumpToggle:Callback(function(val) infiniteJumpEnabled = val if val then if not jumpConnection then jumpConnection = game:GetService("UserInputService").JumpRequest:Connect(function() if infiniteJumpEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid:ChangeState(Enum.HumanoidStateType.Jumping) end end end) end else if jumpConnection then jumpConnection:Disconnect() jumpConnection = nil end end end)

MainCheatsTab:AddSection({"Health Hacks"})
local HealthToggle = MainCheatsTab:AddToggle({Name = "Enable Health Hack", Description = "Toggle MaxHealth", Default = false})
HealthToggle:Callback(function(val) healthEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.MaxHealth = val and customHealth or 100 humanoid.Health = humanoid.MaxHealth end end)
MainCheatsTab:AddTextBox({Name = "Health Modifier", Description = "Set custom MaxHealth", PlaceholderText = "Enter health value", Callback = function(val) local num = tonumber(val) if num then customHealth = num if healthEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.MaxHealth = customHealth humanoid.Health = customHealth end end end end})

MainCheatsTab:AddSection({"Anti-AFK"})
local afkEnabled, afkConnection = false, nil
local VirtualUser = game:GetService("VirtualUser")
local AFKToggle = MainCheatsTab:AddToggle({Name = "Enable Anti-AFK", Description = "Prevent idle kick", Default = false})
AFKToggle:Callback(function(val) afkEnabled = val if val then if not afkConnection then afkConnection = game.Players.LocalPlayer.Idled:Connect(function() VirtualUser:CaptureController() VirtualUser:ClickButton2(Vector2.new()) end) end else if afkConnection then afkConnection:Disconnect() afkConnection = nil end end end)

local UniversalScriptsTab = Window:MakeTab({"Universal Scripts", "code"})
UniversalScriptsTab:AddButton({Name = "Infinite Yield", Description = "Loads Infinite Yield", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end})
UniversalScriptsTab:AddButton({Name = "Dex Explorer", Description = "Loads Dex Explorer", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/peyton2465/Dex/master/out.lua")) end})
UniversalScriptsTab:AddButton({Name = "CMD FE", Description = "Loads CMD FE script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/lxte/cmd/main/main.lua", true))() end})

local MadaScriptTab = Window:MakeTab({"Mada Script", "home"})
MadaScriptTab:AddSection({"Mada Script Scripts"})
MadaScriptTab:AddButton({Name = "⚡ KOLINSKI admin FE", Description = "Loads KOLINSKI admin FE script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/KOLINSKI/refs/heads/main/KOLINSKI.lua", true))() end})
MadaScriptTab:AddButton({Name = "👑 Mada Admin", Description = "Loads Mada Admin script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/Nameless-admin/refs/heads/main/Source", true))() end})
MadaScriptTab:AddButton({Name = "🎵 Nameless music", Description = "Loads Nameless music script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/Nameless-music-lunch/refs/heads/main/Main", true))() end})
MadaScriptTab:AddButton({Name = "🔧 Honoka Executor", Description = "Loads Honoka Executor script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/honoka-executor/main/Honoka%20executor", true))() end})
MadaScriptTab:AddButton({Name = "⚡ Mada Jims rng", Description = "Execute Mada Jims rng script", Callback = function() loadstring(game:HttpGet("https://api.websim.com/blobs/0198f1b6-61d5-722a-a1a2-54553ac4f64e.txt"))() end})

local MusicTab = Window:MakeTab({"Music", "music"})
local sound = Instance.new("Sound", game.Workspace)
MusicTab:AddTextBox({Name = "Music ID Input", Description = "Enter a music ID to play", PlaceholderText = "Music ID", Callback = function(val) if val ~= "" then sound.SoundId = "rbxassetid://" .. val sound:Play() end end})
local presets = {"107764433772204","16662830706","1836142077","112723885774179","81902909302285"}
for _, id in ipairs(presets) do MusicTab:AddButton({Name = "Play " .. id, Description = "Play preset music", Callback = function() sound.SoundId = "rbxassetid://" .. id sound:Play() end}) end

local BrookMusicTab = Window:MakeTab({"Brook Music", "music"})
BrookMusicTab:AddTextBox({Name = "Overboard Music", Description = "Enter Music ID for Overboard", PlaceholderText = "Overboard Music ID", Callback = function(val) if val ~= "" then local args = {[1] = "PickingScooterMusicText", [2] = val} game:GetService("ReplicatedStorage").RE:FindFirstChild("1NoMoto1rVehicle1s"):FireServer(unpack(args)) end end})
BrookMusicTab:AddTextBox({Name = "House Music", Description = "Enter Music ID for House", PlaceholderText = "House Music ID", Callback = function(val) if val ~= "" then local args = {[1] = "PickHouseMusicText", [2] = val} game:GetService("ReplicatedStorage").RE:FindFirstChild("1Player1sHous1e"):FireServer(unpack(args)) end end})local redzlib = loadstring(game:HttpGet("https://raw.githubusercontent.com/tbao143/Library-ui/refs/heads/main/Redzhubui"))()
local Window = redzlib:MakeWindow({Title = "Mada Hub 3.7", SubTitle = "by Mada", SaveFolder = "UniversalScriptConfig"})
Window:AddMinimizeButton({Button = {Image = "rbxassetid://77855434347030", BackgroundTransparency = 0}, Corner = {CornerRadius = UDim.new(0, 8)}})

local customSpeed, customJump, customGravity, customHealth = 16, 50, 196.2, 100
local speedEnabled, jumpEnabled, gravityEnabled, infiniteJumpEnabled, healthEnabled = false, false, false, false, false
local jumpConnection

local MainCheatsTab = Window:MakeTab({"Universal Exploits", "bug"})
MainCheatsTab:AddSection({"Speed Hacks"})
local SpeedToggle = MainCheatsTab:AddToggle({Name = "Enable Speed Hack", Description = "Toggle WalkSpeed", Default = false})
SpeedToggle:Callback(function(val) speedEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.WalkSpeed = val and customSpeed or 16 end end)
MainCheatsTab:AddTextBox({Name = "Speed Modifier", Description = "Set custom WalkSpeed", PlaceholderText = "Enter speed value", Callback = function(val) local num = tonumber(val) if num then customSpeed = num if speedEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.WalkSpeed = customSpeed end end end end})

MainCheatsTab:AddSection({"JumpPower Hacks"})
local JumpToggle = MainCheatsTab:AddToggle({Name = "Enable Jump Hack", Description = "Toggle JumpPower", Default = false})
JumpToggle:Callback(function(val) jumpEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.JumpPower = val and customJump or 50 end end)
MainCheatsTab:AddTextBox({Name = "JumpPower Modifier", Description = "Set custom JumpPower", PlaceholderText = "Enter jump value", Callback = function(val) local num = tonumber(val) if num then customJump = num if jumpEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.JumpPower = customJump end end end end})

MainCheatsTab:AddSection({"Gravity Hacks"})
local GravityToggle = MainCheatsTab:AddToggle({Name = "Enable Gravity Hack", Description = "Toggle Workspace.Gravity", Default = false})
GravityToggle:Callback(function(val) gravityEnabled = val game.Workspace.Gravity = val and customGravity or 196.2 end)
MainCheatsTab:AddTextBox({Name = "Gravity Modifier", Description = "Set custom Gravity", PlaceholderText = "Enter gravity value", Callback = function(val) local num = tonumber(val) if num then customGravity = num if gravityEnabled then game.Workspace.Gravity = customGravity end end end})

MainCheatsTab:AddSection({"Infinite Jump"})
local InfiniteJumpToggle = MainCheatsTab:AddToggle({Name = "Enable Infinite Jump", Description = "Toggle Infinite Jump", Default = false})
InfiniteJumpToggle:Callback(function(val) infiniteJumpEnabled = val if val then if not jumpConnection then jumpConnection = game:GetService("UserInputService").JumpRequest:Connect(function() if infiniteJumpEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid:ChangeState(Enum.HumanoidStateType.Jumping) end end end) end else if jumpConnection then jumpConnection:Disconnect() jumpConnection = nil end end end)

MainCheatsTab:AddSection({"Health Hacks"})
local HealthToggle = MainCheatsTab:AddToggle({Name = "Enable Health Hack", Description = "Toggle MaxHealth", Default = false})
HealthToggle:Callback(function(val) healthEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.MaxHealth = val and customHealth or 100 humanoid.Health = humanoid.MaxHealth end end)
MainCheatsTab:AddTextBox({Name = "Health Modifier", Description = "Set custom MaxHealth", PlaceholderText = "Enter health value", Callback = function(val) local num = tonumber(val) if num then customHealth = num if healthEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.MaxHealth = customHealth humanoid.Health = customHealth end end end end})

MainCheatsTab:AddSection({"Anti-AFK"})
local afkEnabled, afkConnection = false, nil
local VirtualUser = game:GetService("VirtualUser")
local AFKToggle = MainCheatsTab:AddToggle({Name = "Enable Anti-AFK", Description = "Prevent idle kick", Default = false})
AFKToggle:Callback(function(val) afkEnabled = val if val then if not afkConnection then afkConnection = game.Players.LocalPlayer.Idled:Connect(function() VirtualUser:CaptureController() VirtualUser:ClickButton2(Vector2.new()) end) end else if afkConnection then afkConnection:Disconnect() afkConnection = nil end end end)

local UniversalScriptsTab = Window:MakeTab({"Universal Scripts", "code"})
UniversalScriptsTab:AddButton({Name = "Infinite Yield", Description = "Loads Infinite Yield", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end})
UniversalScriptsTab:AddButton({Name = "Dex Explorer", Description = "Loads Dex Explorer", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/peyton2465/Dex/master/out.lua")) end})
UniversalScriptsTab:AddButton({Name = "CMD FE", Description = "Loads CMD FE script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/lxte/cmd/main/main.lua", true))() end})

local MadaScriptTab = Window:MakeTab({"Mada Script", "home"})
MadaScriptTab:AddSection({"Mada Script Scripts"})
MadaScriptTab:AddButton({Name = "⚡ KOLINSKI admin FE", Description = "Loads KOLINSKI admin FE script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/KOLINSKI/refs/heads/main/KOLINSKI.lua", true))() end})
MadaScriptTab:AddButton({Name = "👑 Mada Admin", Description = "Loads Mada Admin script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/Mada-admin/refs/heads/main/Mada%20admin2.txt", true))() end})
MadaScriptTab:AddButton({Name = "🎵 Nameless music", Description = "Loads Nameless music script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/Nameless-music-lunch/refs/heads/main/Main", true))() end})
MadaScriptTab:AddButton({Name = "🔧 Honoka Executor", Description = "Loads Honoka Executor script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/honoka-executor/main/Honoka%20executor", true))() end})
MadaScriptTab:AddButton({Name = "⚡ Mada Jims rng", Description = "Execute Mada Jims rng script", Callback = function() loadstring(game:HttpGet("https://api.websim.com/blobs/0198f1b6-61d5-722a-a1a2-54553ac4f64e.txt"))() end})

local MusicTab = Window:MakeTab({"Music", "music"})
local sound = Instance.new("Sound", game.Workspace)
MusicTab:AddTextBox({Name = "Music ID Input", Description = "Enter a music ID to play", PlaceholderText = "Music ID", Callback = function(val) if val ~= "" then sound.SoundId = "rbxassetid://" .. val sound:Play() end end})
local presets = {"107764433772204","16662830706","1836142077","112723885774179","81902909302285"}
for _, id in ipairs(presets) do MusicTab:AddButton({Name = "Play " .. id, Description = "Play preset music", Callback = function() sound.SoundId = "rbxassetid://" .. id sound:Play() end}) end

local BrookMusicTab = Window:MakeTab({"Brook Music", "music"})
BrookMusicTab:AddTextBox({Name = "Overboard Music", Description = "Enter Music ID for Overboard", PlaceholderText = "Overboard Music ID", Callback = function(val) if val ~= "" then local args = {[1] = "PickingScooterMusicText", [2] = val} game:GetService("ReplicatedStorage").RE:FindFirstChild("1NoMoto1rVehicle1s"):FireServer(unpack(args)) end end})
BrookMusicTab:AddTextBox({Name = "House Music", Description = "Enter Music ID for House", PlaceholderText = "House Music ID", Callback = function(val) if val ~= "" then local args = {[1] = "PickHouseMusicText", [2] = val} game:GetService("ReplicatedStorage").RE:FindFirstChild("1Player1sHous1e"):FireServer(unpack(args)) end end})local redzlib = loadstring(game:HttpGet("https://raw.githubusercontent.com/tbao143/Library-ui/refs/heads/main/Redzhubui"))()
local Window = redzlib:MakeWindow({Title = "kakah hub 1.0", SubTitle = "by kakah", SaveFolder = "UniversalScriptConfig"})
Window:AddMinimizeButton({Button = {Image = "rbxassetid://77855434347030", BackgroundTransparency = 0}, Corner = {CornerRadius = UDim.new(0, 8)}})

local customSpeed, customJump, customGravity, customHealth = 16, 50, 196.2, 100
local speedEnabled, jumpEnabled, gravityEnabled, infiniteJumpEnabled, healthEnabled = false, false, false, false, false
local jumpConnection

local MainCheatsTab = Window:MakeTab({"Universal Exploits", "bug"})
MainCheatsTab:AddSection({"Speed Hacks"})
local SpeedToggle = MainCheatsTab:AddToggle({Name = "Enable Speed Hack", Description = "Toggle WalkSpeed", Default = false})
SpeedToggle:Callback(function(val) speedEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.WalkSpeed = val and customSpeed or 16 end end)
MainCheatsTab:AddTextBox({Name = "Speed Modifier", Description = "Set custom WalkSpeed", PlaceholderText = "Enter speed value", Callback = function(val) local num = tonumber(val) if num then customSpeed = num if speedEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.WalkSpeed = customSpeed end end end end})

MainCheatsTab:AddSection({"JumpPower Hacks"})
local JumpToggle = MainCheatsTab:AddToggle({Name = "Enable Jump Hack", Description = "Toggle JumpPower", Default = false})
JumpToggle:Callback(function(val) jumpEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.JumpPower = val and customJump or 50 end end)
MainCheatsTab:AddTextBox({Name = "JumpPower Modifier", Description = "Set custom JumpPower", PlaceholderText = "Enter jump value", Callback = function(val) local num = tonumber(val) if num then customJump = num if jumpEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.JumpPower = customJump end end end end})

MainCheatsTab:AddSection({"Gravity Hacks"})
local GravityToggle = MainCheatsTab:AddToggle({Name = "Enable Gravity Hack", Description = "Toggle Workspace.Gravity", Default = false})
GravityToggle:Callback(function(val) gravityEnabled = val game.Workspace.Gravity = val and customGravity or 196.2 end)
MainCheatsTab:AddTextBox({Name = "Gravity Modifier", Description = "Set custom Gravity", PlaceholderText = "Enter gravity value", Callback = function(val) local num = tonumber(val) if num then customGravity = num if gravityEnabled then game.Workspace.Gravity = customGravity end end end})

MainCheatsTab:AddSection({"Infinite Jump"})
local InfiniteJumpToggle = MainCheatsTab:AddToggle({Name = "Enable Infinite Jump", Description = "Toggle Infinite Jump", Default = false})
InfiniteJumpToggle:Callback(function(val) infiniteJumpEnabled = val if val then if not jumpConnection then jumpConnection = game:GetService("UserInputService").JumpRequest:Connect(function() if infiniteJumpEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid:ChangeState(Enum.HumanoidStateType.Jumping) end end end) end else if jumpConnection then jumpConnection:Disconnect() jumpConnection = nil end end end)

MainCheatsTab:AddSection({"Health Hacks"})
local HealthToggle = MainCheatsTab:AddToggle({Name = "Enable Health Hack", Description = "Toggle MaxHealth", Default = false})
HealthToggle:Callback(function(val) healthEnabled = val local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.MaxHealth = val and customHealth or 100 humanoid.Health = humanoid.MaxHealth end end)
MainCheatsTab:AddTextBox({Name = "Health Modifier", Description = "Set custom MaxHealth", PlaceholderText = "Enter health value", Callback = function(val) local num = tonumber(val) if num then customHealth = num if healthEnabled then local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.MaxHealth = customHealth humanoid.Health = customHealth end end end end})

MainCheatsTab:AddSection({"Anti-AFK"})
local afkEnabled, afkConnection = false, nil
local VirtualUser = game:GetService("VirtualUser")
local AFKToggle = MainCheatsTab:AddToggle({Name = "Enable Anti-AFK", Description = "Prevent idle kick", Default = false})
AFKToggle:Callback(function(val) afkEnabled = val if val then if not afkConnection then afkConnection = game.Players.LocalPlayer.Idled:Connect(function() VirtualUser:CaptureController() VirtualUser:ClickButton2(Vector2.new()) end) end else if afkConnection then afkConnection:Disconnect() afkConnection = nil end end end)

local UniversalScriptsTab = Window:MakeTab({"Universal Scripts", "code"})
UniversalScriptsTab:AddButton({Name = "Infinite Yield", Description = "Loads Infinite Yield", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end})
UniversalScriptsTab:AddButton({Name = "Dex Explorer", Description = "Loads Dex Explorer", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/peyton2465/Dex/master/out.lua")) end})
UniversalScriptsTab:AddButton({Name = "CMD FE", Description = "Loads CMD FE script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/lxte/cmd/main/main.lua", true))() end})

local MadaScriptTab = Window:MakeTab({"Mada Script", "home"})
MadaScriptTab:AddSection({"Mada Script Scripts"})
MadaScriptTab:AddButton({Name = "⚡ KOLINSKI admin FE", Description = "Loads KOLINSKI admin FE script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/KOLINSKI/refs/heads/main/KOLINSKI.lua", true))() end})
MadaScriptTab:AddButton({Name = "👑 Mada Admin", Description = "Loads Mada Admin script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/Nameless-admin/refs/heads/main/Source", true))() end})
MadaScriptTab:AddButton({Name = "🎵 Nameless music", Description = "Loads Nameless music script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/Nameless-music-lunch/refs/heads/main/Main", true))() end})
MadaScriptTab:AddButton({Name = "🔧 Honoka Executor", Description = "Loads Honoka Executor script", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Jfdedit3/honoka-executor/main/Honoka%20executor", true))() end})
MadaScriptTab:AddButton({Name = "⚡ kakah Jims rng", Description = "Execute Mada Jims rng script", Callback = function() loadstring(game:HttpGet("https://api.websim.com/blobs/0198f1b6-61d5-722a-a1a2-54553ac4f64e.txt"))() end})

local MusicTab = Window:MakeTab({"Music", "music"})
local sound = Instance.new("Sound", game.Workspace)
MusicTab:AddTextBox({Name = "Music ID Input", Description = "Enter a music ID to play", PlaceholderText = "Music ID", Callback = function(val) if val ~= "" then sound.SoundId = "rbxassetid://" .. val sound:Play() end end})
local presets = {"107764433772204","16662830706","1836142077","112723885774179","81902909302285"}
for _, id in ipairs(presets) do MusicTab:AddButton({Name = "Play " .. id, Description = "Play preset music", Callback = function() sound.SoundId = "rbxassetid://" .. id sound:Play() end}) end

local BrookMusicTab = Window:MakeTab({"Brook Music", "music"})
BrookMusicTab:AddTextBox({Name = "Overboard Music", Description = "Enter Music ID for Overboard", PlaceholderText = "Overboard Music ID", Callback = function(val) if val ~= "" then local args = {[1] = "PickingScooterMusicText", [2] = val} game:GetService("ReplicatedStorage").RE:FindFirstChild("1NoMoto1rVehicle1s"):FireServer(unpack(args)) end end})
BrookMusicTab:AddTextBox({Name = "House Music", Description = "Enter Music ID for House", PlaceholderText = "House Music ID", Callback = function(val) if val ~= "" then local args = {[1] = "PickHouseMusicText", [2] = val} game:GetService("ReplicatedStorage").RE:FindFirstChild("1Player1sHous1e"):FireServer(unpack(args)) end end})
