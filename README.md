-- Verifica se o GUI já está carregado
if _G.DominatorUI_Loaded then
    return
end
_G.DominatorUI_Loaded = true

-- Carregar a biblioteca Dominator UI
local DominatorLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

-- Criar a interface principal
local Window = DominatorLib:CreateWindow({
    Title = "Dominator UI",
    Size = UDim2.new(0, 500, 0, 350), -- Define o tamanho do GUI
    Position = UDim2.new(0.5, -250, 0.5, -175), -- Centraliza na tela
    Draggable = true, -- Permite mover o GUI
    CloseButton = true -- Ativa o botão de fechar
})

-- Criar abas (se for suportado)
local HomeTab = Window:CreateTab("Home")
local CreditsTab = Window:CreateTab("Créditos")
local MainTab = Window:CreateTab("Main")

-- Criar uma seção na aba "Home"
local HomeSection = HomeTab:CreateSection("Bem-vindo ao Dominator UI")
HomeSection:CreateLabel("Selecione uma opção abaixo:")

-- Adicionar um botão de fechar GUI
HomeSection:CreateButton({
    Name = "Fechar GUI",
    Callback = function()
        DominatorLib:Destroy()
        _G.DominatorUI_Loaded = false
    end
})

-- Criar uma seção na aba "Créditos"
local CreditsSection = CreditsTab:CreateSection("Créditos")
CreditsSection:CreateLabel("Feito por SeuNome")

-- Criar uma seção na aba "Main"
local MainSection = MainTab:CreateSection("Opções Principais")

-- Adicionar um toggle (interruptor)
MainSection:CreateToggle({
    Name = "Modo Turbo",
    Default = false,
    Callback = function(state)
        if state then
            print("Modo Turbo ativado!")
        else
            print("Modo Turbo desativado!")
        end
    end
})

-- Adicionar um slider (se suportado)
MainSection:CreateSlider({
    Name = "Velocidade",
    Min = 0,
    Max = 100,
    Default = 50,
    Callback = function(value)
        print("Velocidade ajustada para:", value)
    end
})

