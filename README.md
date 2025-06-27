local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Allowed users list
local testUsers = {
    "Test1", "test2", "Xdemon123679", "psychopowerful049", "psychopowerful90",
    "Test6", "Test7", "Test8", "Test9", "Test10",
    "Test11", "Test12", "Test13", "Test14", "Test15",
    "testUser16", "testUser17", "testUser18", "testUser19", "testUser20",
    "testUser21", "testUser22", "testUser23", "testUser24", "testUser25",
    "testUser26", "testUser27", "testUser28", "testUser29", "testUser30",
    "testUser31", "testUser32", "testUser33", "testUser34", "testUser35",
    "testUser36"
}

local function isAllowed(name)
    name = string.lower(name)
    for _, allowedName in ipairs(testUsers) do
        if string.lower(allowedName) == name then
            return true
        end
    end
    return false
end

-- Kick unauthorized players
if not isAllowed(player.Name) then
    player:Kick("HAHA 🖕🖕STUPID 🤣")
    return
end

-- GUI setup
local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "PsychoHAHub"
screenGui.ResetOnSpawn = false

-- Main window
local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Name = "MainFrame"
mainFrame.BackgroundColor3 = Color3.fromRGB(10,10,25)
mainFrame.BorderColor3 = Color3.fromRGB(255,215,0)
mainFrame.Position = UDim2.new(0.25,0,0.2,0)
mainFrame.Size = UDim2.new(0,500,0,420)
mainFrame.BorderSizePixel = 4
mainFrame.Active = true
mainFrame.Draggable = true
Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0,15)
local frameStroke = Instance.new("UIStroke", mainFrame)
frameStroke.Thickness = 3
frameStroke.Color = Color3.fromRGB(184,134,11)

-- Title
local title = Instance.new("TextLabel", mainFrame)
title.Text = "🤣Psycho HA Hub🤣"
title.Font = Enum.Font.SourceSansBold
title.TextSize = 42
title.TextColor3 = Color3.fromRGB(255,215,0)
title.BackgroundTransparency = 1
title.Position = UDim2.new(0.05,0,0.01,0)
title.Size = UDim2.new(0.9,0,0.15,0)

-- Scroll area
local scroll = Instance.new("ScrollingFrame", mainFrame)
scroll.BackgroundTransparency = 1
scroll.Size = UDim2.new(1,-20,0.65,0)
scroll.Position = UDim2.new(0,10,0.2,0)
scroll.ScrollBarThickness = 6
scroll.BorderSizePixel = 0
scroll.CanvasSize = UDim2.new(0,0,0,0)
Instance.new("UICorner", scroll).CornerRadius = UDim.new(0,10)
local sStroke = Instance.new("UIStroke", scroll)
sStroke.Thickness = 2
sStroke.Color = Color3.fromRGB(184,134,11)

local layout = Instance.new("UIGridLayout", scroll)
layout.CellSize = UDim2.new(0,140,0,50)
layout.CellPadding = UDim2.new(0,10,0,10)
layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    scroll.CanvasSize = UDim2.new(0,0,0, layout.AbsoluteContentSize.Y + 20)
end)

-- Buttons data
local buttonsPagesData = {{
    {Text = "Instant Spawn", ScriptLink = "https://pastebin.com/raw/WSMe8sJJ"},
    {Text = "No cooldown 75%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/2468.../gistfile1.txt"},
    {Text = "No cooldown 100%", ScriptLink = "https://pastebin.com/raw/TgZyweFX"},
    {Text = "Aura", ScriptLink = "https://pastebin.com/raw/qZPVbxFc"},
    {Text = "No clip for damage hitbox", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/..."},
    {Text = "Anti spy chat", ScriptLink = "https://pastebin.com/raw/u0eJBiH9"},
    {Text = "Chat spy", ScriptLink = "https://pastebin.com/raw/ECZP85Ud"},
    {Text = "Anti lag", ScriptLink = "https://pastebin.com/raw/u5KgwBeD"},
    {Text = "Damage kill", ScriptLink = ""},
    {Text = "SPT auto grab", ScriptLink = "https://pastebin.com/raw/MHN7tVU8"},
    {Text = "Loopbring", ScriptLink = "https://pastebin.com/raw/wzMiStPG"},
    {Text = "Use tools", ScriptLink = "https://pastebin.com/raw/fnGNW8Lk"},
    {Text = "Auto grab", ScriptLink = "https://pastebin.com/raw/AsJv8mHN"},
    {Text = "Damage hitbox", ScriptLink = "https://pastebin.com/raw/BF4LJ4QB"},
    {Text = "FPS", ScriptLink = "https://pastebin.com/raw/ZMM98Aaj"},
    {Text = "Lag server", ScriptLink = "https://pastebin.com/raw/azyg7Zdu"},
    {Text = "No cooldown 20%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/..."},
    {Text = "No cooldown 30%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/..."},
    {Text = "No cooldown 50%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/..."},
    {Text = "Auto base", ScriptLink = "https://pastefy.app/kS9BglBQ/raw"},
    {Text = "Fling", ScriptLink = "https://pastebin.com/raw/uh8c1JPM"},
    {Text = "Script 22", ScriptLink = "https://pastebin.com/raw/TeleportGUI789"},
}}

-- Make buttons
local function clearScroll()
    for _, c in ipairs(scroll:GetChildren()) do
        if c:IsA("TextButton") then
            c:Destroy()
        end
    end
end

local function createScriptButtons()
    clearScroll()
    for i, data in ipairs(buttonsPagesData[1]) do
        if data.Text and data.Text ~= "" then
            local btn = Instance.new("TextButton", scroll)
            btn.Name = "ScriptBtn"..i
            btn.Text = data.Text
            btn.Font = Enum.Font.SourceSansSemibold
            btn.TextSize = 20
            btn.TextColor3 = Color3.fromRGB(255,215,0)
            btn.BackgroundColor3 = Color3.fromRGB(15,15,30)
            btn.BorderColor3 = Color3.fromRGB(255,215,0)
            btn.Size = UDim2.new(0,140,0,50)
            btn.AutoButtonColor = true
            Instance.new("UICorner", btn).CornerRadius = UDim.new(0,8)
            local st = Instance.new("UIStroke", btn)
            st.Thickness = 1.5
            st.Color = Color3.fromRGB(184,134,11)
            st.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

            btn.MouseButton1Click:Connect(function()
                print("Executing:", data.Text)
                local ok, err = pcall(function()
                    loadstring(game:HttpGet(data.ScriptLink))()
                end)
                if not ok then warn("Error loading", data.Text, err) end
            end)
        end
    end
end

createScriptButtons()

-- Toggle Button
local toggleGroup = Instance.new("Frame")
toggleGroup.Name = "ToggleGroup"
toggleGroup.Parent = screenGui
toggleGroup.BackgroundTransparency = 1
toggleGroup.Size = UDim2.new(0, 80, 0, 80)
toggleGroup.AnchorPoint = Vector2.new(0.5, 0.5)
toggleGroup.Position = UDim2.new(0.93, 0, 0.05, 0)

local bg = Instance.new("Frame", toggleGroup)
bg.Name = "BackgroundCircle"
bg.Size = UDim2.new(1, 0, 1, 0)
bg.BackgroundColor3 = Color3.fromRGB(10,10,25)
bg.BorderSizePixel = 0
bg.AnchorPoint = Vector2.new(0.5,0.5)
bg.Position = UDim2.new(0.5,0,0.5,0)
Instance.new("UICorner", bg).CornerRadius = UDim.new(1,0)
local stroke = Instance.new("UIStroke", bg)
stroke.Thickness = 2
stroke.Color = Color3.fromRGB(255,215,0)

local btn = Instance.new("TextButton", toggleGroup)
btn.Name = "ToggleButton"
btn.Text = "🤣"
btn.Font = Enum.Font.SourceSansBold
btn.TextSize = 28
btn.TextColor3 = Color3.fromRGB(255,215,0)
btn.BackgroundTransparency = 1
btn.BorderSizePixel = 0
btn.Size = UDim2.new(0,50,0,50)
btn.AnchorPoint = Vector2.new(0.5,0.5)
btn.Position = UDim2.new(0.5,0,0.5,0)
Instance.new("UICorner", btn).CornerRadius = UDim.new(1,0)
local btnStroke = Instance.new("UIStroke", btn)
btnStroke.Thickness = 2
btnStroke.Color = Color3.fromRGB(255,215,0)
btnStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

-- Open/Close Logic
local isOpen = true
btn.MouseButton1Click:Connect(function()
    isOpen = not isOpen
    mainFrame.Visible = isOpen
end)

-- Rotating HA letters
local outerText, innerText = "HAHAHAHA", "HAHA"
local outerLetters, innerLetters = {}, {}
local outerRad, innerRad = 35, 20
for i = 1, #outerText do
    local tl = Instance.new("TextLabel", toggleGroup)
    tl.Text = outerText:sub(i,i)
    tl.Font = Enum.Font.SourceSansBold
    tl.TextSize = 12
    tl.TextColor3 = Color3.fromRGB(255,215,0)
    tl.BackgroundTransparency = 1
    tl.Size = UDim2.new(0,14,0,14)
    tl.AnchorPoint = Vector2.new(0.5,0.5)
    outerLetters[i] = tl
end
for i = 1, #innerText do
    local tl = Instance.new("TextLabel", toggleGroup)
    tl.Text = innerText:sub(i,i)
    tl.Font = Enum.Font.SourceSansBold
    tl.TextSize = 10
    tl.TextColor3 = Color3.fromRGB(255,215,0)
    tl.BackgroundTransparency = 1
    tl.Size = UDim2.new(0,12,0,12)
    tl.AnchorPoint = Vector2.new(0.5,0.5)
    innerLetters[i] = tl
end

local rotOuter, rotInner = 0, 0
local speedO, speedI = math.rad(60), -math.rad(90)
RunService.RenderStepped:Connect(function(dt)
    rotOuter = (rotOuter + speedO*dt) % (2*math.pi)
    rotInner = (rotInner + speedI*dt) % (2*math.pi)
    local cx, cy = toggleGroup.AbsoluteSize.X/2, toggleGroup.AbsoluteSize.Y/2
    for i, tl in ipairs(outerLetters) do
        local ang = (2*math.pi/#outerLetters)*(i-1) + rotOuter
        tl.Position = UDim2.new(0, cx + outerRad*math.cos(ang), 0, cy + outerRad*math.sin(ang))
    end
    for i, tl in ipairs(innerLetters) do
        local ang = (2*math.pi/#innerLetters)*(i-1) + rotInner
        tl.Position = UDim2.new(0, cx + innerRad*math.cos(ang), 0, cy + innerRad*math.sin(ang))
    end
end)
