if not game:IsLoaded() then game.Loaded:Wait() end
if game.PlaceId == 15536298749 then
    local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

    -- Verifica se a GUI já está carregada
    if _G.DominatorUILoaded then return end
    _G.DominatorUILoaded = true

    -- Criar a Janela
    local Window = lib:CreateWindow("Dominator UI")

    -- Criar as Abas
    local Home = Window:CreateTab("Home")
    local Settings = Window:CreateTab("Settings")
    local Credits = Window:CreateTab("Credits")

    -- Criar Seções dentro da Aba Home
    local InfoSection = Home:AddSection("Informações do Jogador")
    local DiscordSection = Home:AddSection("Discord")

    -- Adicionar Botões na Seção de Informações
    InfoSection:AddButton("Nome: " .. game.Players.LocalPlayer.Name, "Nome de Usuário", function() end)
    InfoSection:AddButton("ID: " .. game.Players.LocalPlayer.UserId, "ID do jogador", function() end)

    -- Adicionar Botão de Discord
    DiscordSection:AddButton("Discord", "Entrar no servidor", function()
        setclipboard("https://discord.gg/seuconvite")
    end)

    -- Criar Seções dentro da Aba Settings
    local ToggleSection = Settings:AddSection("Configurações")
    local SliderSection = Settings:AddSection("Ajustes")

    -- Adicionar Toggle
    ToggleSection:AddToggle("Ativar Modo AFK", "Evita ser kickado", false, function(state)
        if state then
            game:GetService("Players").LocalPlayer.Idled:Connect(function()
                game:GetService("VirtualUser "):CaptureController()
                game:GetService("VirtualUser "):ClickButton2(Vector2.new())
            end)
        end
    end)

    -- Adicionar Slider
    SliderSection:AddSlider({
        Name = "Ajustar Volume",
        Min = 0,
        Max = 100,
        Default = 50,
        Callback = function(value)
            print("Volume ajustado para: " .. value)
        end
    })

    -- Criar Seções dentro da Aba Credits
    local CreditsSection = Credits:AddSection("Créditos")
    CreditsSection:AddButton("Desenvolvido por SeuNome", "Créditos", function() end)

    -- Botão para Fechar a GUI
    Window:CreateButton({
        Name = "Fechar GUI",
        Callback = function()
            Window:Destroy()
            _G.DominatorUILoaded = false
        end
    })
end
