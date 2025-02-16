-- Dominator UI Library - DEEPSEEK VERSION
if not game:IsLoaded() then
    game.Loaded:Wait()
end

if _G.DominatorUiLoaded then
    return
end
_G.DominatorUiLoaded = true

local DominatorUi = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

local Window = DominatorUi:CreateWindow("Dominator UI")

local Home = Window:CreateTab("Home")
local AutoFarm = Window:CreateTab("Auto Farm")
local Misc = Window:CreateTab("Misc")

local Info = Home:CreateTab("Informações")
local Discord = Home:CreateTab("Discord")
local Farm = AutoFarm:CreateTab("Farm")
local Others = Misc:CreateTab("Extras")

Info:AddButton("Nome: " .. game.Players.LocalPlayer.Name, "Nome de Usuário", function() end)
Info:AddButton("ID: " .. game.Players.LocalPlayer.UserId, "ID do jogador", function() end)
Info:AddButton("Executor: " .. identifyexecutor(), "Executor usado", function() end)

Discord:AddButton("Discord", "Entrar no servidor", function()
    setclipboard("https://discord.gg/seuconvite")
end)

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

Others:AddButton("AntiAFK", "Ativar", function()
    game:GetService("Players").LocalPlayer.Idled:Connect(function()
        VirtualUser:CaptureController()
        VirtualUser:ClickButton2(Vector2.new())
    end)
end)

Others:AddButton("FPS Booster", "Reduzir lag", function()
    sethiddenproperty(game.Lighting, "Technology", 2)
    game.Lighting.FogEnd = 9e9
end)
