
-- ULTRA HUB | SPEED
-- Delta Mobile

local Players = game:GetService("Players")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "UltraHub"
gui.ResetOnSpawn = false
gui.Parent = game:GetService("CoreGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 240, 0, 190)
frame.Position = UDim2.new(0.5, -120, 0.4, 0)
frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true
frame.Parent = gui

local stroke = Instance.new("UIStroke")
stroke.Color = Color3.fromRGB(0, 140, 255)
stroke.Thickness = 2
stroke.Parent = frame

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -40, 0, 40)
title.BackgroundTransparency = 1
title.Text = "ULTRA HUB"
title.TextColor3 = Color3.fromRGB(0, 170, 255)
title.TextSize = 23
title.Font = Enum.Font.GothamBold
title.Parent = frame

local minimize = Instance.new("TextButton")
minimize.Size = UDim2.new(0, 35, 0, 35)
minimize.Position = UDim2.new(1, -38, 0, 3)
minimize.Text = "-"
minimize.TextSize = 25
minimize.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
minimize.TextColor3 = Color3.new(1, 1, 1)
minimize.Parent = frame

local speedBox = Instance.new("TextBox")
speedBox.Size = UDim2.new(0, 200, 0, 40)
speedBox.Position = UDim2.new(0, 20, 0, 60)
speedBox.PlaceholderText = "SPEED (1 - 300)"
speedBox.Text = "16"
speedBox.TextSize = 17
speedBox.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
speedBox.TextColor3 = Color3.new(1, 1, 1)
speedBox.Parent = frame

local apply = Instance.new("TextButton")
apply.Size = UDim2.new(0, 200, 0, 40)
apply.Position = UDim2.new(0, 20, 0, 115)
apply.Text = "APLICAR SPEED"
apply.TextSize = 16
apply.Font = Enum.Font.GothamBold
apply.BackgroundColor3 = Color3.fromRGB(0, 110, 220)
apply.TextColor3 = Color3.new(1, 1, 1)
apply.Parent = frame

apply.MouseButton1Click:Connect(function()
    local value = tonumber(speedBox.Text)

    if value and value >= 1 and value <= 300 then
        local character = player.Character
        local humanoid = character and character:FindFirstChildOfClass("Humanoid")

        if humanoid then
            humanoid.WalkSpeed = value
        end
    else
        speedBox.Text = "1 - 300"
    end
end)

minimize.MouseButton1Click:Connect(function()
    local hidden = speedBox.Visible
    speedBox.Visible = not hidden
    apply.Visible = not hidden
    frame.Size = hidden and
        UDim2.new(0, 240, 0, 40) or
        UDim2.new(0, 240, 0, 190)
    minimize.Text = hidden and "+" or "-"
end)
