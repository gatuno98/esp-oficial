-- Função para desenhar as linhas
function drawESP(player)
    -- Posição do jogador atual
    local myPos = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
    
    -- Posição do outro jogador
    local otherPlayerPos = player.Character.HumanoidRootPart.Position
    
    -- Calculando a distância
    local distance = (myPos - otherPlayerPos).magnitude
    
    -- Criando a linha visual
    local line = Instance.new("Line")
    line.Color = Color3.fromRGB(255, 255, 255)  -- Cor branca
    line.Thickness = 0.1  -- Espessura fina
    line.From = myPos
    line.To = otherPlayerPos
    line.Parent = game.Workspace
    
    -- Exibindo o nome e a distância perto da linha
    local textLabel = Instance.new("BillboardGui")
    textLabel.Adornee = player.Character.Head
    textLabel.Size = UDim2.new(0, 100, 0, 50)
    textLabel.StudsOffset = Vector3.new(0, 2, 0)  -- Offset para ficar acima da cabeça
    textLabel.Parent = player.Character.Head
    
    local label = Instance.new("TextLabel")
    label.Text = player.Name .. " - " .. math.floor(distance) .. " studs"
    label.TextColor3 = Color3.fromRGB(255, 255, 255)  -- Texto branco
    label.BackgroundTransparency = 1
    label.Parent = textLabel
end

-- Loop para desenhar linhas para todos os jogadores no servidor
for _, player in pairs(game.Players:GetPlayers()) do
    if player ~= game.Players.LocalPlayer then
        drawESP(player)
    end
end
