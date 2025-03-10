local gui = Instance.new("ScreenGui")
local frame = Instance.new("Frame")
local textLabel = Instance.new("TextLabel")
local textButton = Instance.new("TextButton")
local textBox = Instance.new("TextBox")

-- GUI
gui.Name = "gui"
gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
gui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Frame
frame.Parent = gui
frame.Size = UDim2.new(0, 200, 0, 150) -- Aumentei a altura para acomodar a TextBox
frame.Position = UDim2.new(0.5, -100, 0.5, -75) -- Centralizado na tela
frame.BackgroundColor3 = Color3.new(1, 0, 0)
frame.Active = true -- Permite que o frame receba eventos de entrada
frame.Draggable = true -- Torna o frame arrastável

-- TextLabel
textLabel.Parent = frame
textLabel.Text = "MUSIC GUI"
textLabel.Size = UDim2.new(1, 0, 0.3, 0) -- Ajustei a altura para acomodar a TextBox
textLabel.Position = UDim2.new(0, 0, 0, 0)
textLabel.BackgroundColor3 = Color3.new(0, 0, 0)
textLabel.TextColor3 = Color3.new(1, 1, 1)

-- TextBox
textBox.Parent = frame
textBox.PlaceholderText = "Digite o ID da música"
textBox.Size = UDim2.new(1, 0, 0.3, 0)
textBox.Position = UDim2.new(0, 0, 0.3, 0)
textBox.BackgroundColor3 = Color3.new(0, 0, 0)
textBox.TextColor3 = Color3.new(1, 1, 1)
textBox.TextScaled = true

-- TextButton
textButton.Parent = frame
textButton.Text = "Tocar"
textButton.Size = UDim2.new(1, 0, 0.3, 0)
textButton.Position = UDim2.new(0, 0, 0.6, 0)
textButton.BackgroundColor3 = Color3.new(0.5, 0.5, 0.5)
textButton.TextColor3 = Color3.new(1, 1, 1)

-- Cria um som e o configura
local sound = Instance.new("Sound")
sound.Parent = game.Workspace
sound.Volume = 1 -- Volume do som (0 a 1)

-- Função para tocar música ao clicar no botão
textButton.MouseButton1Click:Connect(function()
    local musicId = textBox.Text
    if musicId ~= "" then
        sound.SoundId = "rbxassetid://" .. musicId
        sound:Play()
        textButton.Text = "Parar de tocar"
    else
        textButton.Text = "Tocar"
    end
end)

-- ImageLabel (Background)
local background = Instance.new("ImageLabel")
background.Parent = gui
background.Image = "rbxassetid://109251560" -- ID da sua imagem
background.Size = UDim2.new(1, 0, 1, 0) -- Cobre toda a tela
background.Position = UDim2.new(0, 0, 0, 0) -- Alinha no canto superior esquerdo
background.BackgroundTransparency = 1 -- Fundo transparente
background.ScaleType = Enum.ScaleType.Fit -- Ajusta a imagem à tela
