-- Define variables
local enemyFolder = workspace:WaitForChild("Enemies") -- The folder where enemies are stored

-- Function to add highlight to an enemy
local function highlightEnemy(enemy)
    -- Check if the enemy already has a highlight
    if not enemy:FindFirstChild("Highlight") then
        local highlight = Instance.new("Highlight")
        highlight.FillColor = Color3.new(1, 0, 0) -- Set fill color to red
        highlight.OutlineColor = Color3.new(1, 1, 1) -- Set outline color to white
        highlight.FillTransparency = 0.5 -- Adjust fill transparency
        highlight.OutlineTransparency = 0 -- Outline is fully visible
        highlight.Parent = enemy
    end
end

-- Function to check and highlight all enemies
local function highlightAllEnemies()
    for _, enemy in pairs(enemyFolder:GetChildren()) do
        -- Check if the enemy is a model or character and add highlight
        if enemy:IsA("Model") or enemy:IsA("BasePart") then
            highlightEnemy(enemy)
        end
    end
end

-- Continuously check for new enemies and highlight them
while true do
    highlightAllEnemies()
    wait(999) -- Wait for 1 second before checking again
end
