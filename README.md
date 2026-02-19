-- S.S HUB - Custom UI Script
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local UICorner = Instance.new("UICorner") 
local Title = Instance.new("TextLabel")
local SpeedLabel = Instance.new("TextLabel")
local SpeedInput = Instance.new("TextBox")
local JumpLabel = Instance.new("TextLabel")
local JumpInput = Instance.new("TextBox")
local ActivateBtn = Instance.new("TextButton")
local UnwalkLabel = Instance.new("TextLabel")
local UnwalkBtn = Instance.new("TextButton")

-- Screen Settings
ScreenGui.Parent = game.CoreGui 
ScreenGui.Name = "SS_HUB_GUI"

-- Main Frame
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
MainFrame.Position = UDim2.new(0.5, -100, 0.5, -75)
MainFrame.Size = UDim2.new(0, 220, 0, 180) 
MainFrame.BorderSizePixel = 0

-- UI Corners
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 8)
corner.Parent = MainFrame

-- Neon Green Border
UIStroke.Parent = MainFrame
UIStroke.Color = Color3.fromRGB(50, 255, 50)
UIStroke.Thickness = 2

-- Title: S.S HUB
Title.Parent = MainFrame
Title.Text = "S.S HUB"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.BackgroundTransparency = 1
Title.Position = UDim2.new(0, 10, 0, 5)
Title.Size = UDim2.new(0, 120, 0, 30)
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 20

-- Speed Settings
SpeedLabel.Parent = MainFrame
SpeedLabel.Text = "Speed"
SpeedLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
SpeedLabel.BackgroundTransparency = 1
SpeedLabel.Position = UDim2.new(0, 10, 0, 45)
SpeedLabel.Size = UDim2.new(0, 60, 0, 30)

SpeedInput.Parent = MainFrame
SpeedInput.Text = "30"
SpeedInput.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
SpeedInput.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedInput.Position = UDim2.new(0, 110, 0, 45)
SpeedInput.Size = UDim2.new(0, 80, 0, 25)

-- Jump Settings
JumpLabel.Parent = MainFrame
JumpLabel.Text = "Jump"
JumpLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
JumpLabel.BackgroundTransparency = 1
JumpLabel.Position = UDim2.new(0, 10, 0, 80)
JumpLabel.Size = UDim2.new(0, 60, 0, 30)

JumpInput.Parent = MainFrame
JumpInput.Text = "70"
JumpInput.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
JumpInput.TextColor3 = Color3.fromRGB(255, 255, 255)
JumpInput.Position = UDim2.new(0, 110, 0, 80)
JumpInput.Size = UDim2.new(0, 80, 0, 25)

-- Activate Button
ActivateBtn.Parent = MainFrame
ActivateBtn.Text = "ON"
ActivateBtn.BackgroundColor3 = Color3.fromRGB(0, 180, 0)
ActivateBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
ActivateBtn.Position = UDim2.new(0, 145, 0, 10)
ActivateBtn.Size = UDim2.new(0, 50, 0, 25)

-- Unwalk Feature
UnwalkLabel.Parent = MainFrame
UnwalkLabel.Text = "Unwalk"
UnwalkLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
UnwalkLabel.BackgroundTransparency = 1
UnwalkLabel.Position = UDim2.new(0, 10, 0, 115)
UnwalkLabel.Size = UDim2.new(0, 60, 0, 30)

UnwalkBtn.Parent = MainFrame
UnwalkBtn.Text = "OFF"
UnwalkBtn.BackgroundColor3 = Color3.fromRGB(150, 0, 0)
UnwalkBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
UnwalkBtn.Position = UDim2.new(0, 110, 0, 115)
UnwalkBtn.Size = UDim2.new(0, 80, 0, 25)

-- Functionality
ActivateBtn.MouseButton1Click:Connect(function()
    local char = game.Players.LocalPlayer.Character
    if char and char:FindFirstChild("Humanoid") then
        char.Humanoid.WalkSpeed = tonumber(SpeedInput.Text) or 16
        char.Humanoid.JumpPower = tonumber(JumpInput.Text) or 50
        char.Humanoid.UseJumpPower = true
    end
end)

local unwalking = false
UnwalkBtn.MouseButton1Click:Connect(function()
    local char = game.Players.LocalPlayer.Character
    if char and char:FindFirstChild("Humanoid") then
        unwalking = not unwalking
        if unwalking then
            char.Humanoid.WalkSpeed = 0
            UnwalkBtn.Text = "ON"
            UnwalkBtn.BackgroundColor3 = Color3.fromRGB(0, 180, 0)
        else
            char.Humanoid.WalkSpeed = tonumber(SpeedInput.Text) or 16
            UnwalkBtn.Text = "OFF"
            UnwalkBtn.BackgroundColor3 = Color3.fromRGB(150, 0, 0)
        end
    end
end)
