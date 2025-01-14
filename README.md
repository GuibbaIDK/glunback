loadstring([[
-- Criação da GUI
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")  -- O quadrado
local TitleLabel = Instance.new("TextLabel")  -- O título
local RollbackButton = Instance.new("TextButton")
local StopButton = Instance.new("TextButton")
local RejoinButton = Instance.new("TextButton")

-- Configurações gerais do ScreenGui
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.Name = "RollbackGUI"

-- Configurações do Frame (quadrado)
MainFrame.Parent = ScreenGui
MainFrame.Size = UDim2.new(0, 350, 0, 400)  -- Tamanho do frame
MainFrame.Position = UDim2.new(0.5, -175, 0.5, -200)  -- Centraliza na tela
MainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)  -- Cor de fundo escuro
MainFrame.BorderSizePixel = 5  -- Borda do Frame
MainFrame.BorderColor3 = Color3.fromRGB(255, 255, 255)  -- Cor da borda (branca)
MainFrame.BackgroundTransparency = 0.2  -- Transparência do fundo
MainFrame.Visible = true  -- Garante que o frame seja visível

-- Configurações do Título
TitleLabel.Parent = MainFrame
TitleLabel.Size = UDim2.new(1, 0, 0.2, 0)  -- Ajusta o tamanho do título
TitleLabel.Position = UDim2.new(0, 0, 0, 0)
TitleLabel.Text = "Guibbs Rollback - Anime Adventures"
TitleLabel.TextSize = 20  -- Tamanho da fonte
TitleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)  -- Cor branca
TitleLabel.BackgroundTransparency = 1  -- Sem fundo
TitleLabel.TextXAlignment = Enum.TextXAlignment.Center  -- Alinhamento horizontal
TitleLabel.TextYAlignment = Enum.TextYAlignment.Center  -- Alinhamento vertical

-- Função para criar e posicionar os botões
local function createButton(text, posY, bgColor, txtColor, width)
    local btn = Instance.new("TextButton")
    btn.Parent = MainFrame
    btn.Size = UDim2.new(0, width or 250, 0, 60)  -- Tamanho do botão
    btn.Position = UDim2.new(0.5, -125, posY, 0)  -- Alinha o botão no centro
    btn.Text = text
    btn.BackgroundColor3 = bgColor  -- Cor do fundo do botão
    btn.TextColor3 = txtColor  -- Cor do texto
    btn.TextSize = 18  -- Tamanho do texto
    btn.TextAlign = Enum.TextXAlignment.Center  -- Alinha o texto no meio
    btn.TextButtonStyle = Enum.ButtonStyle.RobloxRound  -- Estilo redondo
    return btn
end

-- Inicializando os botões
RollbackButton = createButton("Turn On Rollback", 0.3, Color3.fromRGB(0, 255, 0), Color3.fromRGB(0, 0, 0))  -- Verde (Ativar)
StopButton = createButton("Rollback Off", 0.5, Color3.fromRGB(255, 0, 0), Color3.fromRGB(255, 255, 255))  -- Vermelho (Desativar)
RejoinButton = createButton("Reentrar no Jogo", 0.7, Color3.fromRGB(0, 0, 255), Color3.fromRGB(255, 255, 255))  -- Azul

-- Função de clique para o botão "Turn On Rollback"
RollbackButton.MouseButton1Click:Connect(function()
    -- Alterar para "Rollback Off" e ativar o modo
    RollbackButton.Text = "Rollback Off"
    RollbackButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)  -- Mudar para vermelho
    print("Rollback ativado!")
end)

-- Função de clique para o botão "Rollback Off"
StopButton.MouseButton1Click:Connect(function()
    -- Alterar para "Turn On Rollback" e desativar o modo
    RollbackButton.Text = "Turn On Rollback"
    RollbackButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)  -- Mudar para verde
    print("Rollback desativado!")
end)

-- Função para reentrar no jogo
RejoinButton.MouseButton1Click:Connect(function()
    game:GetService("TeleportService"):Teleport(game.PlaceId, game.Players.LocalPlayer)
end)

print("GUI de rollback carregada com sucesso!")
]])()
