if not game:IsLoaded() then
    game.Loaded:Wait()
end

local cloneref = cloneref or function(...) return ... end
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/main/source"))()
local Window = lib:CreateWindow("Meu Script")

local Home = Window:NewTab("Home")
local Main = Window:NewTab("Main")
local Credits = Window:NewTab("Créditos")

local Info = Instance.new("TextLabel", Home)
Info.Text = "Bem-vindo ao script!"
Info.Size = UDim2.new(0, 200, 0, 50)
Info.Position = UDim2.new(0.5, -100, 0.2, 0)
Info.TextColor3 = Color3.fromRGB(255, 255, 255)

local ToggleMain = Instance.new("TextButton", Home)
ToggleMain.Text = "Ir para Main"
ToggleMain.Size = UDim2.new(0, 100, 0, 30)
ToggleMain.Position = UDim2.new(0.5, -50, 0.4, 0)
ToggleMain.MouseButton1Click:Connect(function()
    Window:SwitchTab("Main")
end)

local ToggleCredits = Instance.new("TextButton", Main)
ToggleCredits.Text = "Ir para Créditos"
ToggleCredits.Size = UDim2.new(0, 100, 0, 30)
ToggleCredits.Position = UDim2.new(0.5, -50, 0.4, 0)
ToggleCredits.MouseButton1Click:Connect(function()
    Window:SwitchTab("Créditos")
end)

local BackToHome = Instance.new("TextButton", Credits)
BackToHome.Text = "Voltar ao Home"
BackToHome.Size = UDim2.new(0, 100, 0, 30)
BackToHome.Position = UDim2.new(0.5, -50, 0.4, 0)
BackToHome.MouseButton1Click:Connect(function()
    Window:SwitchTab("Home")
end)
