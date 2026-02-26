local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local plr = Players.LocalPlayer
local char = plr.Character or plr.CharacterAdded:Wait()
local root = char:WaitForChild("HumanoidRootPart")
local hum = char:WaitForChild("Humanoid")

plr.CharacterAdded:Connect(function(c)
    char = c
    root = c:WaitForChild("HumanoidRootPart")
    hum = c:WaitForChild("Humanoid")
end)

local gui = Instance.new("ScreenGui")
gui.Parent = plr.PlayerGui

local main = Instance.new("Frame")
main.Size = UDim2.new(0,220,0,180)
main.Position = UDim2.new(0,20,0,20)
main.BackgroundColor3 = Color3.new(.1,.1,.1)
main.BackgroundTransparency = .2
main.Active = true
main.Draggable = true
main.Parent = gui

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1,0,0,30)
title.BackgroundTransparency = 1
title.Text = "IA 二创 - 10 Hour Burst Man"
title.TextColor3 = Color3.new(1,1,1)
title.Parent = main

local god = false
local autoMario = false
local aimLock = false

local function btn(text, y)
    local b = Instance.new("TextButton")
    b.Size = UDim2.new(0,200,0,35)
    b.Position = UDim2.new(0,10,0,y)
    b.BackgroundColor3 = Color3.new(.2,.2,.2)
    b.Text = text
    b.TextColor3 = Color3.new(1,1,1)
    b.Parent = main
    return b
end

local b1 = btn("无敌模式", 40)
local b2 = btn("自动吸马里奥", 80)
local b3 = btn("锁头BOSS", 120)

b1.MouseButton1Click:Connect(function()
    god = not god
    b1.BackgroundColor3 = god and Color3.new(0,.7,0) or Color3.new(.2,.2,.2)
end)

b2.MouseButton1Click:Connect(function()
    autoMario = not autoMario
    b2.BackgroundColor3 = autoMario and Color3.new(0,.7,0) or Color3.new(.2,.2,.2)
end)

b3.MouseButton1Click:Connect(function()
    aimLock = not aimLock
    b3.BackgroundColor3 = aimLock and Color3.new(0,.7,0) or Color3.new(.2,.2,.2)
end)

RunService.Heartbeat:Connect(function()
    if god and hum then
        hum.Health = hum.MaxHealth
    end

    local boss = workspace:FindFirstChild("10 Hour Burst Man")
    local head = boss and boss:FindFirstChild("Head")

    if autoMario and root then
        for _,v in pairs(workspace:GetDescendants()) do
            if v:IsA("BasePart") and v.Name == "Mario" then
                local dist = (v.Position - root.Position).Magnitude
                if dist < 35 then
                    v.Velocity = (root.Position - v.Position).Unit * 80
                end
            end
        end
    end

    if aimLock and head then
        for _,v in pairs(workspace:GetDescendants()) do
            if v:IsA("BasePart") and (v.Name:match("Bullet") or v.Name:match("Projectile") or v.Name:match("Attack")) then
                v.Velocity = (head.Position - v.Position).Unit * 350
            end
        end
    end
end)
