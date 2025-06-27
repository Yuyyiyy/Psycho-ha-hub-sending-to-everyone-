
  = game:GetService("Players")
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

if not isAllowed(player.Name) then
    player:Kick("HAHA  🖕🖕STUPID 🤣")
    return
end

local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "PsychoHAHub"
screenGui.ResetOnSpawn = false

local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Name = "MainFrame"
mainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 25)
mainFrame.BorderColor3 = Color3.fromRGB(255, 215, 0)
mainFrame.Position = UDim2.new(0.25, 0, 0.2, 0)
mainFrame.Size = UDim2.new(0, 500, 0, 420)
mainFrame.Visible = true
mainFrame.BorderSizePixel = 4
mainFrame.Active = true
mainFrame.Draggable = true
Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 15)
local mainStroke = Instance.new("UIStroke", mainFrame)
mainStroke.Thickness = 3
mainStroke.Color = Color3.fromRGB(184, 134, 11)

local title = Instance.new("TextLabel", mainFrame)
title.Text = "🤣Psycho HA Hub🤣"
title.Font = Enum.Font.SourceSansBold
title.TextSize = 42
title.TextColor3 = Color3.fromRGB(255, 215, 0)
title.BackgroundTransparency = 1
title.Position = UDim2.new(0.05, 0, 0.01, 0)
title.Size = UDim2.new(0.9, 0, 0.15, 0)

local scroll = Instance.new("ScrollingFrame", mainFrame)
scroll.BackgroundTransparency = 1
scroll.Size = UDim2.new(1, -20, 0.65, 0)
scroll.Position = UDim2.new(0, 10, 0.2, 0)
scroll.ScrollBarThickness = 6
scroll.BorderSizePixel = 0
scroll.CanvasSize = UDim2.new(0, 0, 0, 0)
Instance.new("UICorner", scroll).CornerRadius = UDim.new(0, 10)
local scrollStroke = Instance.new("UIStroke", scroll)
scrollStroke.Thickness = 2
scrollStroke.Color = Color3.fromRGB(184, 134, 11)

local layout = Instance.new("UIGridLayout", scroll)
layout.CellSize = UDim2.new(0, 140, 0, 50)
layout.CellPadding = UDim2.new(0, 10, 0, 10)
layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    scroll.CanvasSize = UDim2.new(0, 0, 0, layout.AbsoluteContentSize.Y + 20)
end)

local buttonsPagesData = {{
    {Text = "Instant Spawn", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/6c6a1996b7efda399ee6c667a0e96510/raw/dce1e15f00e12059b72516403f01401d950913cf/gistfile1.txt"},
    {Text = "No cooldown 75%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/246d84003ec77b3348b785f4c4b40951/raw/2e03b6f231e8ddeba6c7e40afedd919907138ddf/gistfile1.txt"},
    {Text = "No cooldown 100%", ScriptLink = "https://pastebin.com/raw/Qxnj4RG9"},
    {Text = "Aura", ScriptLink = "https://pastebin.com/raw/qZPVbxFc"},
    {Text = "No clip for damage hitbox", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/04661c54b473431b9ab554de484e1e1f/raw/2a08e9b05c7cd4c64001138728a6b3c316a805e7/gistfile1.txt"},
    {Text = "Anti spy chat", ScriptLink = "https://pastebin.com/raw/u0eJBiH9"},
    {Text = "Chat spy", ScriptLink = "https://pastebin.com/raw/ECZP85Ud"},
    {Text = "Anti lag", ScriptLink = "https://pastebin.com/raw/u5KgwBeD"},
    {Text = "Damage kill", ScriptLink = ""},
    {Text = "SPT auto grab", ScriptLink = "https://pastebin.com/raw/MHN7tVU8"},
    {Text = "Loopbring",  = "https://pastebin.com/raw/wzMiStPG"},
    {Text = "Use tools", ScriptLink = "https://pastebin.com/raw/fnGNW8Lk"},
    {Text = "Auto grab", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/eb3b21915928414653a2b8dd9a40980e/raw/782a51c0004924e47d86c0c008acd280e5af16c3/gistfile1.txt"},
    {Text = "Damage hitbox", ScriptLink = "https://pastebin.com/raw/BF4LJ4QB"},
    {Text = "FPS", ScriptLink = "https://pastebin.com/raw/ZMM98Aaj"},
    {Text = "Lag server", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/6f38723afc3d835dc1f8bc96b9f61bd8/raw/9d7b2525de18a7f1220d5c78fcfdf34b7da5e05f/gistfile1.txt"},
    {Text = "No cooldown 20%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/435a09384699c8f3e910444d877f123c/raw/29721b83c34f0c51059a6839e978c1b0fc4a7570/gistfile1.txt"},
    {Text = "No cooldown 30%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/602ad74771fa6ed8b0118b8b2303c0cb/raw/a90c5000987fe694ae8fd250df0e981032245b4a/gistfile1.txt"},
    {Text = "No cooldown 50%", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/b2fc36b1230d4bb9b06db2a419f50a8a/raw/e442c967add6123afd88d717b773361f7ad62af2/gistfile1.txt"},
    {Text = "Auto base", ScriptLink = "https://pastefy.app/kS9BglBQ/raw"},
    {Text = "Fling", ScriptLink = "https://pastebin.com/raw/uh8c1JPM"},
    {Text = "Script 22", ScriptLink = "https://pastebin.com/raw/TeleportGUI789"}
}}

local function clearScroll()
    for _, child in pairs(scroll:GetChildren()) do
        if child:IsA("TextButton") then
            child:Destroy()
        end
    end
end

local function createScriptButtons(page)
    clearScroll()
    local pageData = buttonsPagesData[page]
    for index = 1, #pageData do
        local data = pageData[index]
        if data.Text ~= "" then
            local button = Instance.new("TextButton", scroll)
            button.Name = "ScriptButton" .. index
            button.TextWrapped = true
            button.TextYAlignment = Enum.TextYAlignment.Center
            button.Text = data.Text
            button.Font = Enum.Font.SourceSansSemibold
            button.TextColor3 = Color3.fromRGB(255, 215, 0)
            button.TextSize = 20
            button.BackgroundColor3 = Color3.fromRGB(15, 15, 30)
            button.BorderColor3 = Color3.fromRGB(255, 215, 0)
            button.AutoButtonColor = true
            button.Size = UDim2.new(0, 140, 0, 50)
            local btnCorner = Instance.new("UICorner", button)
            btnCorner.CornerRadius = UDim.new(0, 8)
            local btnStroke = Instance.new("UIStroke", button)
            btnStroke.Thickness = 1.5
            btnStroke.Color = Color3.fromRGB(184, 134, 11)
            btnStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
            button.MouseButton1Click:Connect(function()
                print(data.Text .. " button clicked")
                local success, err = pcall(function()
                    loadstring(game:HttpGet(data.ScriptLink))()
                end)
                if not success then
                    warn("Failed to load script:", err)
                end
            end)
        end
    end
end

createScriptButtons(1)
