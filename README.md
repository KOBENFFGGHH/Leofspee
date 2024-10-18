local UserInputService = game:GetService("UserInputService")
local VirtualInputManager = game:GetService("VirtualInputManager")
local TweenService = game:GetService("TweenService")
local tween = game:service"TweenService"
local RunService = game:GetService("RunService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local Mouse = LocalPlayer:GetMouse()
local GuiService = game:GetService("GuiService")
local SoundClick2 = Instance.new("Sound")
SoundClick2.Name = "Sound Effect"
SoundClick2.SoundId = "rbxassetid://130785805"
SoundClick2.Volume = 1
SoundClick2.Parent = game.Workspace
local UIStroke = Instance.new("UIStroke")
local UICorner = Instance.new("UICorner")
local ScreenGui = Instance.new("ScreenGui")
local ImageButton = Instance.new("ImageButton")
local RobloxButton = Enum.ButtonStyle.RobloxButton
ScreenGui.Parent = game.CoreGui:WaitForChild("RobloxGui"):WaitForChild("Modules")
ScreenGui.Name = "dsfwefwfwdfsfasdadaxczcw"
ImageButton.Parent = ScreenGui
ImageButton.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
ImageButton.Size = UDim2.new(0, 45, 0, 45)
ImageButton.Draggable = true
ImageButton.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
ImageButton.BackgroundTransparency = 0
ImageButton.Image = "rbxassetid://16663324629"
function LoadFunction()    
        ImageButton.MouseEnter:Connect(function()
        TweenService:Create(
            ImageButton,
            TweenInfo.new(.2, Enum.EasingStyle.Back, Enum.EasingDirection.InOut),
            {Size = UDim2.new(0, 80, 0, 80)}
        ):Play()
    end)
    ImageButton.MouseLeave:Connect(function()
        TweenService:Create(
            ImageButton,
            TweenInfo.new(.2, Enum.EasingStyle.Back, Enum.EasingDirection.InOut),
            {Size = UDim2.new(0, 50, 0, 50)}
        ):Play()
    end)
    
    local LoadFocus = false
    
    ImageButton.MouseButton1Down:Connect(function()
        if LoadFocus == false then 
            LoadFocus = false
            TweenService:Create(
                ImageButton,
                TweenInfo.new(.2, Enum.EasingStyle.Back, Enum.EasingDirection.InOut),
                {Rotation = 180}
            ):Play()
            SoundClick2:Play()
            TweenService:Create(
                ImageButton,
                TweenInfo.new(.4, Enum.EasingStyle.Quart, Enum.EasingDirection.In),
                {ImageTransparency = 0}
            ):Play()
            wait(.5)
            TweenService:Create(
                ImageButton,
                TweenInfo.new(.2, Enum.EasingStyle.Back, Enum.EasingDirection.InOut),
                {Rotation = 0}
            ):Play()
            TweenService:Create(
                ImageButton,
                TweenInfo.new(.4, Enum.EasingStyle.Quart, Enum.EasingDirection.In),
                {ImageTransparency = 0}
            ):Play()
            wait(.5)	
            
        end
    end)
end
    LoadFunction()
    ImageButton.MouseButton1Down:connect(function()
    game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
    game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
    end)
	function Vec(text)
		local Notification = require(game.ReplicatedStorage.Notification)
		local notification = Notification.new(text)
		notification.Duration = 4
		notification:Display()
	end
	local function tablefound(ta, object)
		for i,v in pairs(ta) do
			if v == object then
				return true
			end
		end
		return false
	end
local thongbao = loadstring(game:HttpGet("https://raw.githubusercontent.com/MaGiXxScripter0/keysystemv2api/master/ui/notify_ui.lua"))()
thongbao.New("Welcome To Attack Hub", 10)
local Library = loadstring(game:HttpGet("https://pastebin.com/raw/frKsq2Nu"))()
local ThemeManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/GhostDuckyy/UI-Libraries/refs/heads/main/LinoriaLib/addons/ThemeManager.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/GhostDuckyy/UI-Libraries/refs/heads/main/LinoriaLib/addons/SaveManager.lua"))()

local Window = Library:CreateWindow({
Title = "Attack Hub",
AutoShow = true,
Center = true,
})

local Tabs = {
["General"] = Window:AddTab("General"),
["Configurations"] = Window:AddTab("Configurations"),
}

ThemeManager:SetLibrary(Library)
SaveManager:SetLibrary(Library)
SaveManager:IgnoreThemeSettings()
SaveManager:SetIgnoreIndexes({ 'MenuKeybind' })
SaveManager:BuildConfigSection(Tabs['Configurations'])
ThemeManager:ApplyToTab(Tabs['Configurations'])
SaveManager:LoadAutoloadConfig()

local function UpdateTime()
local GameTime = math.floor(workspace.DistributedGameTime+0.5)
local Hour = math.floor(GameTime/(60^2))%24
local Minute = math.floor(GameTime/(60^1))%60
local Second = math.floor(GameTime/(60^0))%60
Library:SetWatermark('Attack Hub |  Hr(s) : '..Hour..' Min(s) : '..Minute..' Sec(s) : '..Second)
end
spawn(function()
while true do
UpdateTime()	game:GetService("RunService").RenderStepped:Wait()
end
end)

local Main = Tabs["General"]:AddLeftGroupbox('Main')

Main:AddToggle('MyToggle', {
    Text = 'Auto Farm Speed',
    Default = false,
    Tooltip = 'ออโต้ฟาร์ม ความเร็ว',
    Callback = function(value)
        _G.Auto_Farm = value
    end
})
spawn(function()
while wait() do
if _G.Auto_Farm then
pcall(function()
local args = {
    [1] = "collectOrb",
    [2] = "Gem",
    [3] = "City"
}
game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer(unpack(args))
local args = {
    [1] = "collectOrb",
    [2] = "Orange Orb",
    [3] = "City"
}
game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer(unpack(args))
end)
end
end
end)
Main:AddToggle('MyToggle', {
    Text = 'Auto Farm Diamond',
    Default = false,
    Tooltip = 'ออโต้ฟาร์ม เพชร',
    Callback = function(value)
_G.Auto_Farm_Diamond = value
    end
})
spawn(function()
while wait() do
if _G.Auto_Farm_Diamond then
pcall(function()
local args = {
    [1] = "collectOrb",
    [2] = "Gem",
    [3] = "City"
}
game:GetService("ReplicatedStorage").rEvents.orbEvent:FireServer(unpack(args))
end)
end
end
end)
Main:AddToggle('MyToggle', {
    Text = 'Auto Rebirth',
    Default = false,
    Tooltip = 'การเกิดใหม่ ตอนที่ Level Max',
    Callback = function(value)
        _G.Auto_Rebirth = value
    end
})
spawn(function()
while wait() do
if _G.Auto_Rebirth then
pcall(function()
local args = {
    [1] = "rebirthRequest"
}
game:GetService("ReplicatedStorage").rEvents.rebirthEvent:FireServer(unpack(args))
end)
end
end
end)
Main:AddButton({
    Text = 'Tp to location New',
    Func = function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-866.3868408203125, 4.21060848236084, 2165.70654296875)
    end,
    DoubleClick = false,
    Tooltip = ''
})
local Set = Tabs["General"]:AddRightGroupbox('Settings');
Set:AddSlider('', {
    Text = 'Walk Speed',
    Default = 50,
    Min = 0,
    Max = 1000,
    Rounding = 1,
    Compact = false,
    Callback = function(value)
   game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
   end
})
Set:AddSlider('', {
    Text = 'Jump Power',
    Default = 50,
    Min = 0,
    Max = 1000,
    Rounding = 1,
    Compact = false,
    Callback = function(Value)
game.Players.LocalPlayer.Character.Humanoid.JumpPower = value
    end
})
Set:AddToggle('MyToggle', {
    Text = 'WhiteScreen',
    Default = false,
    Tooltip = 'เอามาทำไมวะ',
    Callback = function(v)
        _G.WhiteScreen = v
    end
})
spawn(function()
    while wait() do
        if _G.WhiteScreen == true then
            game:GetService("RunService"):Set3dRenderingEnabled(false)
        elseif _G.WhiteScreen == false then
            game:GetService("RunService"):Set3dRenderingEnabled(true)
        end
    end
end)

Set:AddSlider('MySlider', {
    Text = 'FPS Lock',
    Default = 60,
    Min = 1,
    Max = 1200,
    Rounding = 0,
    Compact = false,
    Callback = function(v)
        SelectFPSLock = v
    end
})

Set:AddToggle('MyToggle', {
    Text = 'Lock FPS',
    Default = false,
    Tooltip = 'Lock FPS',

    Callback = function(v)
        _G.Lock_FPS = v
        if _G.Lock_FPS == true then 
        setfpscap(SelectFPSLock)
        else 
            setfpscap(120)
        end 
    end
})
