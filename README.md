-- Steal a Brainrot – Speed + Noclip Script for Roblox (Xeno compatible)

-- Налаштування швидкості
local speed = 100

-- Отримати гравця
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
character:WaitForChild("Humanoid").WalkSpeed = speed

-- Щоб швидкість не скидалася
character.Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
    character.Humanoid.WalkSpeed = speed
end)

-- NOCLIP: Проходження крізь стіни
game:GetService("RunService").Stepped:Connect(function()
    for _, part in pairs(character:GetDescendants()) do
        if part:IsA("BasePart") and part.CanCollide then
            part.CanCollide = false
        end
    end
end)

print("✅ Speed + Noclip активовано")
