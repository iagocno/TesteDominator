if not game:IsLoaded() then game.Loaded:Wait() end
if game.PlaceId == 15536298749 then

    local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/main/source"))() -- Substitua pela URL correta da sua biblioteca
    local Window = lib:CreateWindow("Dominator UI")

    -- Criar as Abas
    local Home = Window:CreateTab("Home")
    local AutoFarm = Window:CreateTab("Auto Farm")
    local Misc = Window:CreateTab("Misc")

    -- Criar Seções dentro das Abas
    local Info = Home:CreateSection("Informações")
    local Discord = Home:CreateSection("Discord")
    local Farm = AutoFarm:CreateSection("Farm")
    local Others = Misc:CreateSection("Extras")

    -- Informações do jogador
    Info:CreateButton("Nome: " .. game.Players.LocalPlayer.Name, "Nome de Usuário", function() end)
    Info:CreateButton("ID: " .. game.Players.LocalPlayer.UserId, "ID do jogador", function() end)
    Info:CreateButton("Executor: " .. identifyexecutor(), "Executor usado", function() end)

    -- Botão de Discord
    Discord:CreateButton("Discord", "Entrar no servidor", function()
        setclipboard("https://discord.gg/seuconvite")
    end)

    -- Auto Collect Coins
    Farm:CreateToggle("Auto Collect Coins", "Coletar moedas automaticamente", false, function(state)
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

    -- Anti AFK
    Others:CreateButton("AntiAFK", "Ativar", function()
        game:GetService("Players").LocalPlayer.Idled:Connect(function()
            game:GetService("VirtualUser"):CaptureController()
            game:GetService("VirtualUser"):ClickButton2(Vector2.new())
        end)
    end)

    -- FPS Booster
    Others:CreateButton("FPS Booster", "Reduzir lag", function()
        sethiddenproperty(game.Lighting, "Technology", 2)
        game.Lighting.FogEnd = 9e9
    end)
end
