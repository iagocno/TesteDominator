if not game:IsLoaded() then game.Loaded:Wait() end
if game.PlaceId == 15536298749 then
    local cloneref = cloneref or function(...) return ... end
    local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/main/source"))()
    local VirtualUser = cloneref(game:GetService("VirtualUser"))

    -- Função para notificação
    local function playNotificationSound()
        local soundService = cloneref(game:GetService("SoundService"))
        local notificationSound = Instance.new("Sound")

        notificationSound.SoundId = "rbxassetid://8745692251"
        notificationSound.Volume = 0.5
        notificationSound.Parent = soundService

        notificationSound:Play()
    end

    -- Função para enviar notificações
    local function sendNotification(title, text, duration)
        game.StarterGui:SetCore("SendNotification", {
            Title = title,
            Text = text,
            Duration = duration or 3,
        })
    end

    -- Criando a janela principal
    local Window = lib:CreateWindow("Meu Script")

    -- Criando as abas
    local Home = Window:NewTab("Home")
    local Main = Window:NewTab("Main")
    local Credits = Window:NewTab("Créditos")

    -- Criando as seções nas abas
    local Info = Home:AddSection("Informações da Conta")
    local Discord = Home:AddSection("Discord / Suporte")
    local Farm = Main:AddSection("Auto Farm")
    local Others = Main:AddSection("Extras")
    local CreditsSection = Credits:AddSection("Créditos")

    -- Abas de informações
    Info:AddButton("Nome do Jogo: " .. game.PlaceId, "ID do Jogo", function() end)
    Info:AddButton("Nome de Usuário: " .. game.Players.LocalPlayer.Name, "Seu nome de usuário", function() end)
    Info:AddButton("Executor: " .. identifyexecutor(), "Executor usado", function() end)

    -- Discord
    Discord:AddButton("Discord Server", "Entrar no servidor", function()
        setclipboard("https://discord.gg/seuconvite")
    end)

    -- Auto Farm (seções de farm)
    Farm:AddToggle("Auto Collect Coins", "Coletar moedas automaticamente", false, function(state)
        getgenv().AutoCollect = state
        task.spawn(function()
            while getgenv().AutoCollect do
                task.wait(0.1)
                for _, v in pairs(workspace:GetDescendants()) do
                    if v.Name:lower() == "coins" and v:IsA("BasePart") then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
                    end
                end
            end
        end)
    end)

    Farm:AddButton("AntiAFK", "Ativar Anti-AFK", function()
        sendNotification("AntiAFK", "Ativado", 10)
        game:GetService("Players").LocalPlayer.Idled:Connect(function()
            VirtualUser:CaptureController()
            VirtualUser:ClickButton2(Vector2.new())
        end)
    end)

    -- Seções Extras
    Others:AddButton("FPS Booster", "Reduzir lag", function()
        sethiddenproperty(game.Lighting, "Technology", 2)
        game.Lighting.FogEnd = 9e9
        settings().Rendering.QualityLevel = "Level01"
    end)

    Others:AddButton("Destroy GUI", "Destruir o GUI", function()
        Window:Destroy()
    end)

    -- Créditos
    CreditsSection:AddButton("Creditos", "Feito com amor por Alwi", function()
        sendNotification("Créditos", "Feito por Alwi", 10)
    end)
    
    -- Botão de Fechar/Destroy GUI
    local destroyButton = Instance.new("TextButton")
    destroyButton.Size = UDim2.new(0, 100, 0, 50)
    destroyButton.Position = UDim2.new(0.5, -50, 0.9, -25)
    destroyButton.Text = "Destruir GUI"
    destroyButton.Parent = Window

    destroyButton.MouseButton1Click:Connect(function()
        Window:Destroy()
    end)

end
