-- Verifica se o GUI já está em execução
if _G.DominatorUI_Loaded then
    return
end
_G.DominatorUI_Loaded = true

-- Carrega a biblioteca Dominator UI
local DominatorLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

-- Cria a janela principal
local Window = DominatorLib:CreateWindow({
    Name = "Dominator UI",
    HidePremium = false,
    SaveConfig = true,
    ConfigFolder = "DominatorConfig"
})

-- Adiciona abas
local HomeTab = Window:CreateTab("Home")
local CreditsTab = Window:CreateTab("Créditos")
local MainTab = Window:CreateTab("Main")

-- Adiciona seções e elementos na aba Home
local HomeSection = HomeTab:CreateSection("Bem-vindo")
HomeSection:CreateLabel("Bem-vindo ao Dominator UI!")

-- Adiciona seções e elementos na aba Créditos
local CreditsSection = CreditsTab:CreateSection("Créditos")
CreditsSection:CreateLabel("Desenvolvido por SeuNome")
CreditsSection:CreateButton({
    Name = "Fechar GUI",
    Callback = function()
        DominatorLib:Destroy()
        _G.DominatorUI_Loaded = false
    end
})

-- Adiciona seções e elementos na aba Main
local MainSection = MainTab:CreateSection("Funcionalidades")
MainSection:CreateToggle({
    Name = "Ativar Função X",
    Default = false,
    Callback = function(state)
        if state then
            print("Função X ativada")
            -- Código para ativar a função X
        else
            print("Função X desativada")
            -- Código para desativar a função X
        end
    end
})

-- Torna a janela movível
Window:MakeDraggable()

-- Função para destruir o GUI e interromper funções ativas
function DestroyGUI()
    DominatorLib:Destroy()
    _G.DominatorUI_Loaded = false
    -- Adicione aqui o código para interromper quaisquer funções em execução
end

-- Adiciona o botão de destruir GUI na aba Home
HomeSection:CreateButton({
    Name = "Fechar GUI",
    Callback = DestroyGUI
})
