if not game:IsLoaded() then game.Loaded:Wait() end
if game.PlaceId == 15536298749 then

    -- Carrega a biblioteca externa que você mencionou
    local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

    -- Cria a janela principal com o título
    local Window = lib:CreateWindow("Meu Script")

    -- Cria as abas que você pediu
    local Home = Window:NewTab("Home")
    local AutoFarm = Window:NewTab("Auto Farm")
    local Misc = Window:NewTab("Misc")

    -- Adiciona as seções nas abas
    local Info = Home:AddSection("Informações")
    local Discord = Home:AddSection("Discord")
    local Farm = AutoFarm:AddSection("Farm")
    local Others = Misc:AddSection("Extras")

    -- Seção de informações
    Info:AddButton("Nome: " .. game.Players.LocalPlayer.Name, "Nome de Usuário", function() end)
    Info:AddButton("ID: " .. game.Players.LocalPlayer.UserId, "ID do jogador", function() end)
    Info:AddButton("Executor: " .. identifyexecutor(), "Executor usado", function() end)

    -- Seção do Discord
    Discord:AddButton("Discord", "Entrar no servidor", function()
        setclipboard("https://discord.gg/seuconvite")
    end)

    -- Seção de AutoFarm
    Farm:AddToggle("Auto Collect Coins", "Coletar moedas automaticamente", false, function(state)
        getgenv().AutoCollect = state
        while getgenv().AutoCollect do
            task.wait(0.1)
            for _, v in pairs(workspace:GetDescendants()) do
                if v.Name:lower() == "coins" and v:IsA("BasePart") then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
                end
            end
        end
    end)

    -- Seção de Misc
    Others:AddButton("AntiAFK", "Ativar", function()
        game:GetService("Players").LocalPlayer.Idled:Connect(function()
            local VirtualUser = game:GetService("VirtualUser")
            VirtualUser:CaptureController()
            VirtualUser:ClickButton2(Vector2.new())
        end)
    end)
    
    Others:AddButton("FPS Booster", "Reduzir lag", function()
        sethiddenproperty(game.Lighting, "Technology", 2)
        game.Lighting.FogEnd = 9e9
    end)

end
