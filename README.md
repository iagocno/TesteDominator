-- GUI Menu para testar Dominator Library
-- Usando Orion UI e Fluxus UI

local Dominator = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

-- Criar GUI Orion
Dominator.CreateOrionGUI()

-- Criar GUI Fluxus
Dominator.CreateFluxusGUI()

-- Botões de teste para funcionalidades
local Orion = loadstring(game:HttpGet("https://raw.githubusercontent.com/jensonhirst/Orion/main/source"))()
local Window = Orion:MakeWindow({Name = "Dominator Test Hub", HidePremium = false, SaveConfig = false})
local Tab = Window:MakeTab({Name = "Testes", Icon = "rbxassetid://4483345998", PremiumOnly = false})

Tab:AddButton({
    Name = "Teleportar ao Spawn",
    Callback = function()
        Dominator.TeleportTo(Vector3.new(0, 10, 0))
    end
})

Tab:AddSlider({
    Name = "Velocidade do Jogador",
    Min = 16,
    Max = 100,
    Default = 16,
    Callback = function(value)
        Dominator.SetWalkSpeed(value)
    end
})

Tab:AddSlider({
    Name = "Poder do Pulo",
    Min = 50,
    Max = 500,
    Default = 50,
    Callback = function(value)
        Dominator.SetJumpPower(value)
    end
})

Orion:Init()
