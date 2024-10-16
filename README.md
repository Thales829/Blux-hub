-- Enhanced Auto Raging Demon Script for Blox Fruits
-- Make sure to use this script responsibly and in accordance with the game's rules.

local player = game.Players.LocalPlayer
local target = nil

-- Function to find the nearest target
local function findNearestTarget()
    local nearestDistance = math.huge
    for _, p in pairs(game.Players:GetPlayers()) do
        if p ~= player and p.Character and p.Character:FindFirstChild("Humanoid") and p.Character.Humanoid.Health > 0 then
            local distance = (player.Character.HumanoidRootPart.Position - p.Character.HumanoidRootPart.Position).magnitude
            if distance < nearestDistance then
                nearestDistance = distance
                target = p
            end
        end
    end
end

-- Function to use the Raging Demon
local function useRagingDemon()
    if target and target.Character and target.Character:FindFirstChild("Humanoid") and target.Character.Humanoid.Health > 0 then
        -- Move to the target
        player.Character.HumanoidRootPart.CFrame = target.Character.HumanoidRootPart.CFrame
        -- Code to activate the Raging Demon
        -- Example: player.Character:FindFirstChild("RagingDemon"):Activate()
        print("Raging Demon activated on " .. target.Name)
    end
end

-- Main loop
while true do
    findNearestTarget()
    if target then
        useRagingDemon()
    end
    wait(0.5) -- Reduced wait time for faster response
end
