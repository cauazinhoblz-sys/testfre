Jogadores locais = jogo:GetService("Jogadores")
local LocalPlayer = Jogadores.LocalPlayer
local RunService = jogo:GetService("RunService")
Serviço de Entrada de Usuário local = jogo:GetService("Serviço de Entrada de Usuário")
câmera local = espaço de trabalho.CurrentCamera
 
espEnabled local = falso
velocidade local habilitada = falso
velocidade padrão local = 16
local noclipEnabled = falso
noclipConnection local = nulo
espDrawings locais = {}
 
-- POSIÇÃO DE TELEPORTE para “fugir”
local TELEPORT_POSITION = Vector3.new(0, 10, 0) -- você pode mudar para onde quiser
 
-- Função de teletransporte de emergência
função local teleportToSafety()
    caractere local = LocalPlayer.Character
    se personagem e personagem:FindFirstChild("HumanoidRootPart") então
        personagem.HumanoidRootPart.CFrame = CFrame.new(TELEPORT_POSITION)
        print("Teletransportado para um local seguro.")
    fim
fim
 
-- Ativa teleporte através da tecla “T”
UserInputService.InputBegan:Connect(função(entrada, jogoProcessado)
    se gameProcessed então retorna end
    se input.KeyCode == Enum.KeyCode.T então
        teleportToSafety()
    fim
fim)
 
-- ========================== GUI ==========================
ScreenGui local = Instância.new("ScreenGui")
ScreenGui.Name = "Hub"
ScreenGui.Parent = LocalPlayer:WaitForChild("Guia do Jogador")
ScreenGui.ResetOnSpawn = falso
 
MainFrame local = Instância.new("Quadro")
MainFrame.Nome = "HubFrame"
MainFrame.Parent = ScreenGui
MainFrame.Tamanho = UDim2.novo(0, 240, 0, 260)
MainFrame.Posição = UDim2.new(0,5, -120, 0,5, -130)
MainFrame.BackgroundColor3 = Cor3.fromRGB(30, 30, 30)
MainFrame.BorderColor3 = Cor3.fromRGB(10, 10, 10)
MainFrame.Active = verdadeiro
MainFrame.Draggable = verdadeiro
 
TítuloLabel local = Instância.new("TextLabel")
TitleLabel.Name = "Título"
TitleLabel.Parent = MainFrame
TitleLabel.Size = UDim2.new(1, 0, 0, 30)
TitleLabel.Position = UDim2.new(0, 0, 0, 0)
TitleLabel.Text = "ME CHUPA MGZIN"
TitleLabel.Font = Enum.Font.SourceSansBold
TitleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TitleLabel.BackgroundColor3 = Cor3.fromRGB(50, 50, 50)
TitleLabel.BorderSizePixel = 0
 
-- Botão ESP
ESPButton local = Instância.new("TextButton")
ESPButton.Name = "Botão ESP"
ESPButton.Parent = MainFrame
ESPButton.Size = UDim2.new(0,8, 0, 0, 30)
ESPButton.Posição = UDim2.new(0.1, 0, 0.2, 0)
ESPButton.Text = "ESP (DESLIGADO)"
ESPButton.Font = Enum.Font.SourceSansSemibold
ESPButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ESPButton.BackgroundColor3 = Cor3.fromRGB(70, 130, 180)
ESPButton.BorderColor3 = Cor3.fromRGB(40, 80, 120)
 
-- Botão Velocidade
SpeedButton local = Instância.new("TextButton")
SpeedButton.Name = "Botão de Velocidade"
SpeedButton.Parent = MainFrame
SpeedButton.Size = UDim2.new(0,8, 0, 0, 30)
SpeedButton.Position = UDim2.new(0,1, 0, 0,35, 0)
SpeedButton.Text = "Velocidade (DESLIGADO)"
SpeedButton.Font = Enum.Font.SourceSansSemibold
SpeedButton.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedButton.BackgroundColor3 = Cor3.fromRGB(60, 179, 113)
SpeedButton.BorderColor3 = Cor3.fromRGB(35, 120, 80)
 
-- Botão Noclip
NoclipButton local = Instância.new("TextButton")
NoclipButton.Nome = "NoclipButton"
NoclipButton.Parent = Quadro Principal
NoclipButton.Size = UDim2.new(0,8, 0, 0, 30)
NoclipButton.Posição = UDim2.new(0,1, 0, 0,5, 0)
NoclipButton.Text = "Sem clipe (DESLIGADO)"
NoclipButton.Font = Enum.Font.SourceSansSemibold
NoclipButton.TextColor3 = Color3.fromRGB(255, 255, 255)
NoclipButton.BackgroundColor3 = Cor3.fromRGB(255, 165, 0)
NoclipButton.BorderColor3 = Cor3.fromRGB(180, 110, 0)
 
-- Botão Fugir
FleeButton local = Instância.new("TextButton")
FleeButton.Name = "FleeButton"
FleeButton.Parent = Quadro Principal
FleeButton.Size = UDim2.new(0,8, 0, 0, 30)
FleeButton.Position = UDim2.new(0,1, 0, 0,65, 0)
FleeButton.Text = "Fugir"
FleeButton.Font = Enum.Font.SourceSansSemibold
FleeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
FleeButton.BackgroundColor3 = Color3.fromRGB(220, 20, 60) -- vermelho forte
FleeButton.BorderColor3 = Cor3.fromRGB(160, 0, 20)
 
-- Caixa de Texto de Velocidade
SpeedTextBox local = Instance.new("Caixa de Texto")
SpeedTextBox.Name = "Caixa de Texto Rápida"
SpeedTextBox.Parent = Quadro Principal
SpeedTextBox.Size = UDim2.new(0,8, 0, 0, 25)
SpeedTextBox.Position = UDim2.new(0,1, 0, 0,8, 0)
SpeedTextBox.PlaceholderText = "Velocidade (Padrão: 16)"
SpeedTextBox.Font = Enum.Font.SourceSans
SpeedTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedTextBox.BackgroundColor3 = Cor3.fromRGB(50, 50, 50)
SpeedTextBox.BorderColor3 = Cor3.fromRGB(80, 80, 80)
SpeedTextBox.TextSize = 14
SpeedTextBox.Text = "16"
 
-- Botão Fechar
BotãoFechar local = Instância.new("BotãoTexto")
CloseButton.Name = "FecharBotão"
BotãoFechar.Parente = MainFrame
BotãoFechar.Tamanho = UDim2.novo(0, 25, 0, 25)
CloseButton.Position = UDim2.new(1, -25, 0, 0)
FecharButton.Texto = "X"
BotãoFechar.Fonte = Enum.Fonte.SourceSansBold
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
BotãoFechar.CorDeFundo3 = Cor3.fromRGB(200, 0, 0)
BotãoFechar.CorDaBorda3 = Cor3.fromRGB(120, 0, 0)
CloseButton.TextSize = 18
 
BotãoFechar.BotãoMouse1Clique:Conectar(função()
    ScreenGui:Destruir()
fim)
 
-- ======================== LÓGICA (ESP, Speed, Noclip) =========================
 
função local createEspDrawings(jogador)
    desenhos locais = {
        Caixa = Desenho.new("Quadrado"),
        HealthBar = Desenho.new("Linha"),
        NameTag = Desenho.new("Texto"),
        DistanceTag = Desenho.new("Texto"),
        Tracer = Desenho.new("Linha")
    }
    para _, desenhando em pares (desenhos) faça
        desenho.Visível = falso
    fim
    desenhos de retorno
fim
 
função local toggleESP(habilitado)
    espEnabled = habilitado
    para _, desenhos em pares (espDrawings) fazem
        para _, desenhando em pares (desenhos) faça
            desenho.Visível = falso
        fim
    fim
    se habilitado então
        ESPButton.Text = "ESP (LIGADO)"
    outro
        ESPButton.Text = "ESP (DESLIGADO)"
    fim
fim
 
RunService.RenderStepped:Connect(função()
    se não espEnabled então retorne end
    para o jogador, desenhos em pares (espDrawings) fazem
        se player.Character e player.Character:FindFirstChild("Humanoid") 
            e player.Character.Humanoid.Health > 0 e player ~= LocalPlayer então
            local rootPart = jogador.Personagem:FindFirstChild("HumanoidRootPart")
            cabeça local = jogador.Personagem:FindFirstChild("Cabeça")
            se rootPart e head então
                rootPos local, rootVisible = câmera:WorldToViewportPoint(rootPart.Position)
                headPos local = câmera:WorldToViewportPoint(head.Position + Vector3.new(0, 0.5, 0))
                legPos local = câmera:WorldToViewportPoint(rootPart.Position - Vector3.new(0, 3, 0))
                se rootVisible então
                    para _, desenhando em pares (desenhos) faça
                        desenho.Visível = verdadeiro
                    fim
                    desenhos.Box.Color = jogador.TeamColor.Color
                    desenhos.Box.Size = Vector2.new(1000 / rootPos.Z, headPos.Y - legPos.Y)
                    desenhos.Box.Position = Vector2.new(rootPos.X - desenhos.Box.Size.X / 2,
                                                        rootPos.Y - desenhos.Caixa.Tamanho.Y / 2)
                    Taxa de saúde local = jogador.Personagem.Humanoide.Saúde / jogador.Personagem.Humanoide.SaúdeMáxima
                    desenhos.HealthBar.From = Vector2.new(desenhos.Box.Position.X + desenhos.Box.Size.X + 5,
                        desenhos.Box.Position.Y + desenhos.Box.Size.Y * (1 - healthRatio))
                    desenhos.HealthBar.To = Vector2.new(desenhos.Box.Position.X + desenhos.Box.Size.X + 5,
                        desenhos.Box.Position.Y + desenhos.Box.Size.Y)
                    desenhos.HealthBar.Color = Color3.new(1 - healthRatio, healthRatio, 0)
                    desenhos.NameTag.Position = Vector2.new(desenhos.Box.Position.X + desenhos.Box.Size.X / 2,
                                                             desenhos.Caixa.Posição.Y - 20)
                    desenhos.NameTag.Text = player.Name
                    desenhos.DistanceTag.Position = Vector2.new(desenhos.Box.Position.X + desenhos.Box.Size.X / 2,
                                                                desenhos.Box.Position.Y + desenhos.Box.Size.Y)
                    dist local = (LocalPlayer.Character.HumanoidRootPart.Position - rootPart.Position).Magnitude
                    desenhos.DistanceTag.Text = tostring(math.floor(dist)) .. "m"
                    local lHead = LocalPlayer.Character:FindFirstChild("Cabeça")
                    se lHead então
                        local lHeadV = câmera:WorldToViewportPoint(lHead.Position)
                        desenhos.Tracer.From = Vector2.new(lHeadV.X, lHeadV.Y)
                        desenhos.Tracer.To = Vector2.new(rootPos.X, rootPos.Y)
                        desenhos.Tracer.Color = jogador.TeamColor.Color
                    fim
                outro
                    para _, desenhando em pares (desenhos) faça
                        desenho.Visível = falso
                    fim
                fim
            fim
        outro
            para _, desenhando em pares (desenhos) faça
                desenho.Visível = falso
            fim
        fim
    fim
fim)
 
Jogadores.JogadorAdicionado:Conectar(função(plr)
    espDrawings[plr] = criarEspDrawings(plr)
fim)
para _, plr em pares(Players:GetPlayers()) faça
    espDrawings[plr] = criarEspDrawings(plr)
fim
 
função local toggleSpeed(habilitado)
    humanoide local = LocalPlayer.Character e LocalPlayer.Character:FindFirstChildOfClass("Humanoide")
    se não for humanoide então retorne fim
    speedEnabled = habilitado
    se habilitado então
        local newSpeed ​​= tonumber(SpeedTextBox.Text) ou defaultSpeed
        humanoid.WalkSpeed ​​= novaVelocidade
        SpeedButton.Text = "Velocidade (LIGADO)"
    outro
        humanoid.WalkSpeed ​​= velocidade padrão
        SpeedButton.Text = "Velocidade (DESLIGADO)"
    fim
fim
 
LocalPlayer.CharacterAdded:Conectar(função(char)
    toggleSpeed(falso)
    toggleNoclip(falso)
fim)
 
função local updateNoclip()
    caractere local = LocalPlayer.Character
    se personagem então
        para _, parte em pares(character:GetDescendants()) faça
            se parte:IsA("BasePart") então
                part.CanCollide = falso
            fim
        fim
    fim
fim
 
função local toggleNoclip(habilitado)
    noclipEnabled = habilitado
    se habilitado então
        NoclipButton.Text = "Sem clipe (LIGADO)"
        noclipConnection = RunService.RenderStepped:Connect(updateNoclip)
    outro
        NoclipButton.Text = "Sem clipe (DESLIGADO)"
        se noclipConnection então
            noclipConnection:Desconectar()
            noclipConnection = nulo
        fim
        caractere local = LocalPlayer.Character
        se personagem então
            para _, parte em pares(character:GetDescendants()) faça
                se parte:IsA("BasePart") então
                    part.CanCollide = verdadeiro
                fim
            fim
        fim
    fim
fim
 
-- Conexões dos botões
ESPButton.MouseButton1Click:Conectar(função()
    toggleESP(não espEnabled)
fim)
SpeedButton.MouseButton1Click:Conectar(função()
    toggleSpeed(não speedEnabled)
fim)
NoclipButton.MouseButton1Click:Conectar(função()
    toggleNoclip(não habilitado para noclip)
fim)
FleeButton.MouseButton1Click:Conectar(função()
    teleportToSafety()
fim)
 
