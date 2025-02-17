-- Script GUI para usar com a Dominator Library

-- Carregar a biblioteca Dominator
local Dominator = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/main/source"))()

-- Criar a janela
local window = Dominator:CreateWindow("Minha Janela Personalizada")

-- Adicionar um botão à janela
window:AddButton("Clique Aqui", function()
    print("Botão pressionado!")
end)

-- Adicionar um separador
window:AddSeparator()

-- Adicionar outro botão
window:AddButton("Outro Botão", function()
    print("Outro botão pressionado!")
end)

-- Criar a funcionalidade de minimização
window.ToggleMinimize()

