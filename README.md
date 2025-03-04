lua
-- Script básico para coletar itens em Roblox

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

-- Função para coletar itens
local function collectItem(item)
    if item:IsA("Part") and item.Name == "Pote" then
        item:Destroy() -- Remove o item do jogo
        print("Item coletado: " .. item.Name)
    end
end

-- Conectar a função de coleta ao evento Touched
for _, item in pairs(workspace:GetChildren()) do
    if item:IsA("Part") and item.Name == "Pote" then
        item.Touched:Connect(function(hit)
            if hit.Parent == character then
                collectItem(item)
            end
        end)
    end
end# Primeiro-script-
