-- Dominator UI Library Example

-- Certifique-se de carregar a biblioteca corretamente
local Dominator = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

-- Criar a janela principal
local Window = Dominator:CreateWindow("Dominator UI Test")

-- Criar as abas
local Home = Window:NewTab("Home")
local Main = Window:NewTab("Main")
local Credits = Window:NewTab("Credits")

-- Adicionar seções às abas
local Info = Home:AddSection("Informações do Jogador")
local Features = Main:AddSection("Recursos")
local About = Credits:AddSection("Créditos")

-- Adicionar botões e elementos
Info:AddButton("Nome do Jogador: " .. game.Players.LocalPlayer.Name, "Seu nome de usuário", function() end)
Info:AddButton("ID: " .. game.Players.LocalPlayer.UserId, "Seu ID do Roblox", function() end)

Features:AddToggle("Modo AFK", "Evita ser kickado", false, function(state)
    if state then
        game:GetService("Players").LocalPlayer.Idled:Connect(function()
            game:GetService("VirtualUser"):CaptureController()
            game:GetService("VirtualUser"):ClickButton2(Vector2.new())
        end)
    end
end)

About:AddButton("Fechar GUI", "Fecha a interface", function()
    Window:Destroy()
end)
