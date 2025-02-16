local DominatorUi = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/Dominator/refs/heads/main/source"))()

local window = DominatorUi:CreateWindow("Minha Janela")

local tab1 = window:CreateTab("Aba 1")
local tab2 = window:CreateTab("Aba 2")

-- Adicionando um botão na Aba 1
local button = Instance.new("TextButton", tab1)
button.Text = "Clique Aqui"
button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0, 20, 0, 20)
button.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
button.TextColor3 = Color3.fromRGB(255, 255, 255)
button.Font = Enum.Font.Gotham
button.TextSize = 18

button.MouseButton1Click:Connect(function()
    print("Botão clicado!")
end)
