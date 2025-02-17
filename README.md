-- Script GUI para usar com a Dominator Library e adicionar abas

-- Carregar a biblioteca Dominator
local Dominator = loadstring(game:HttpGet("https://raw.githubusercontent.com/iagocno/TesteDominator/refs/heads/main/README.md"))()

-- Criar a janela principal
local window = Dominator:CreateWindow("Minha Janela com Abas")

-- Função para criar as abas
local function createTab(tabName)
    -- Criar o frame da aba
    local tabFrame = Instance.new("Frame")
    tabFrame.Size = UDim2.new(1, 0, 0, 100)
    tabFrame.BackgroundColor3 = Color3.fromRGB(35, 37, 42)
    tabFrame.Parent = window.MainFrame
    
    -- Criar o botão da aba
    local tabButton = Instance.new("TextButton")
    tabButton.Size = UDim2.new(0, 100, 0, 30)
    tabButton.Position = UDim2.new(0, 10 + (110 * (tabName - 1)), 0, 10)
    tabButton.Text = "Aba " .. tabName
    tabButton.TextColor3 = Color3.fromRGB(243, 243, 243)
    tabButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    tabButton.Font = Enum.Font.Roboto
    tabButton.TextSize = 14
    tabButton.Parent = window.MainFrame
    
    -- Criar o conteúdo da aba (inicialmente oculto)
    local contentFrame = Instance.new("Frame")
    contentFrame.Size = UDim2.new(1, -20, 0, 200)
    contentFrame.Position = UDim2.new(0, 10, 0, 40)
    contentFrame.BackgroundColor3 = Color3.fromRGB(30, 32, 37)
    contentFrame.Parent = window.MainFrame
    contentFrame.Visible = false  -- Conteúdo oculto até a aba ser clicada

    -- Função para exibir o conteúdo da aba
    tabButton.MouseButton1Click:Connect(function()
        for _, child in pairs(window.MainFrame:GetChildren()) do
            if child:IsA("Frame") and child ~= tabButton then
                child.Visible = false  -- Ocultar outras abas
            end
        end
        contentFrame.Visible = true  -- Exibir a aba clicada
    end)

    -- Adicionando elementos à aba (exemplo: botão, checkbox, etc.)
    local buttonInTab = window:AddButton("Botão na Aba " .. tabName, function()
        print("Botão na Aba " .. tabName .. " pressionado!")
    end)

    local toggleButtonInTab = Instance.new("TextButton")
    toggleButtonInTab.Size = UDim2.new(0, 180, 0, 30)
    toggleButtonInTab.Position = UDim2.new(0, 10, 0, 60)
    toggleButtonInTab.Text = "Toggle Button"
    toggleButtonInTab.TextColor3 = Color3.fromRGB(243, 243, 243)
    toggleButtonInTab.BackgroundColor3 = Color3.fromRGB(38, 40, 45)
    toggleButtonInTab.Font = Enum.Font.Roboto
    toggleButtonInTab.TextSize = 14
    toggleButtonInTab.Parent = contentFrame
    toggleButtonInTab.MouseButton1Click:Connect(function()
        print("Toggle button pressionado na Aba " .. tabName)
    end)
    
    return tabButton
end

-- Criar abas
createTab(1)
createTab(2)
createTab(3)

-- Função para minimizar/maximizar a janela
window.ToggleMinimize()
