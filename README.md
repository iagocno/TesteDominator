local Dominator = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

-- Criando uma janela usando a Fluxus UI Lib
local fluxusWindow = Dominator.createFluxusWindow("Janela Fluxus", Vector2.new(300, 200), Vector2.new(100, 100))

-- Adicionando um botão à janela Fluxus
Dominator.addFluxusButton(fluxusWindow, "Clique Aqui", function()
    print("Botão Fluxus clicado!")
end)

-- Criando uma janela usando a Orion Lib
local orionWindow = Dominator.createOrionWindow("Janela Orion", Vector2.new(300, 200), Vector2.new(500, 100))

-- Adicionando um botão à janela Orion
Dominator.addOrionButton(orionWindow, "Clique Aqui", function()
    print("Botão Orion clicado!")
end)

-- Usando funções personalizadas
Dominator.doSomethingCool()
Dominator.advancedFeature()
