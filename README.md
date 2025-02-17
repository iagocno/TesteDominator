-- Dominator GUI Completo

local Dominator = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

local Window = Dominator:CreateWindow("Dominator Hub")

-- Aba Home
local HomeTab = Window:AddButton("🏠 Home", function()
    print("Aba Home selecionada")
end)

-- Aba Principal
local MainTab = Window:AddButton("🔧 Main", function()
    print("Aba Main selecionada")
end)

-- Aba Créditos
local CreditsTab = Window:AddButton("📜 Créditos", function()
    print("Aba Créditos selecionada")
end)

-- Botão de Teletransporte pelos Checkpoints
local TeleportButton = Window:AddButton("🚀 Teleportar Checkpoints", function()
    for _, checkpoint in ipairs(workspace:FindFirstChild("Checkpoints"):GetChildren()) do
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = checkpoint.CFrame
        wait(1) -- Pequeno intervalo entre os teletransportes
    end
end)

-- Botão de Minimizar/Maximizar
local ToggleButton = Window:AddButton("🛑 Minimizar/Maximizar", function()
    Window:Toggle()
end)
