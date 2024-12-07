-- Script GUI com campo de texto e botão para executar o valor
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextBox = Instance.new("TextBox")
local Button = Instance.new("TextButton")

-- Configurações do ScreenGui
ScreenGui.Parent = game.CoreGui
ScreenGui.Name = "ArceusExecutorGUI"

-- Configurações do Frame
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.5, -100, 0.5, -50)
Frame.Size = UDim2.new(0, 200, 0, 100)
Frame.AnchorPoint = Vector2.new(0.5, 0.5)

-- Configurações do TextBox
TextBox.Parent = Frame
TextBox.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
TextBox.BorderSizePixel = 0
TextBox.Position = UDim2.new(0.5, 0, 0.2, 0)
TextBox.Size = UDim2.new(0.9, 0, 0.3, 0)
TextBox.AnchorPoint = Vector2.new(0.5, 0.5)
TextBox.Font = Enum.Font.SourceSans
TextBox.PlaceholderText = "Digite o código aqui..."
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
TextBox.TextScaled = true

-- Configurações do Button
Button.Parent = Frame
Button.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Button.BorderSizePixel = 0
Button.Position = UDim2.new(0.5, 0, 0.75, 0)
Button.Size = UDim2.new(0.6, 0, 0.3, 0)
Button.AnchorPoint = Vector2.new(0.5, 0.5)
Button.Font = Enum.Font.SourceSans
Button.Text = "Executar"
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.TextScaled = true

-- Função para executar o código inserido
Button.MouseButton1Click:Connect(function()
    local code = TextBox.Text
    if code ~= "" then
        local success, errorMessage = pcall(function()
            loadstring(code)()
        end)
        if not success then
            warn("Erro ao executar o código: " .. errorMessage)
        end
    else
        warn("Por favor, insira um código no campo de texto.")
    end
end)
