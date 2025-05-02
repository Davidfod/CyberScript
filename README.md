local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Criar a ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "MeuFrameGUI"
screenGui.Parent = playerGui

-- ========================
-- Frame 1: BEM-VINDO
-- ========================
local frame1 = Instance.new("Frame")
frame1.Size = UDim2.new(0, 180, 0, 100)
frame1.Position = UDim2.new(0, 10, 1, -110)
frame1.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame1.BorderSizePixel = 0
frame1.Parent = screenGui

local titulo1 = Instance.new("TextLabel")
titulo1.Size = UDim2.new(1, 0, 0, 30)
titulo1.BackgroundTransparency = 1
titulo1.Text = "Cyber Scripts!"
titulo1.Font = Enum.Font.GothamBold
titulo1.TextSize = 18
titulo1.TextColor3 = Color3.fromRGB(255, 255, 255)
titulo1.Parent = frame1

local botao1 = Instance.new("TextButton")
botao1.Size = UDim2.new(1, -20, 0, 35)
botao1.Position = UDim2.new(0, 10, 0, 50)
botao1.BackgroundColor3 = Color3.fromRGB(80, 170, 255)
botao1.Text = "Click :}"
botao1.Font = Enum.Font.Gotham
botao1.TextSize = 16
botao1.TextColor3 = Color3.fromRGB(255, 255, 255)
botao1.Parent = frame1

-- ========================
-- Frame 2: CORRER E PULAR
-- ========================
local frame2 = Instance.new("Frame")
frame2.Size = UDim2.new(0, 180, 0, 270)
frame2.Position = UDim2.new(0, 10, 1, -280)
frame2.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
frame2.BorderSizePixel = 0
frame2.Visible = false
frame2.Parent = screenGui

local titulo2 = Instance.new("TextLabel")
titulo2.Size = UDim2.new(1, -30, 0, 30)
titulo2.Position = UDim2.new(0, 10, 0, 0)
titulo2.BackgroundTransparency = 1
titulo2.Text = "Corre e Pula!"
titulo2.Font = Enum.Font.GothamBold
titulo2.TextSize = 18
titulo2.TextColor3 = Color3.fromRGB(255, 255, 255)
titulo2.TextXAlignment = Enum.TextXAlignment.Left
titulo2.Parent = frame2

local botaoFechar = Instance.new("TextButton")
botaoFechar.Size = UDim2.new(0, 20, 0, 20)
botaoFechar.Position = UDim2.new(1, -25, 0, 5)
botaoFechar.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
botaoFechar.Text = "X"
botaoFechar.Font = Enum.Font.GothamBold
botaoFechar.TextSize = 14
botaoFechar.TextColor3 = Color3.fromRGB(255, 255, 255)
botaoFechar.Parent = frame2

local botao2 = Instance.new("TextButton")
botao2.Size = UDim2.new(1, -20, 0, 35)
botao2.Position = UDim2.new(0, 10, 0, 40)
botao2.BackgroundColor3 = Color3.fromRGB(255, 80, 80)
botao2.Text = "Correr"
botao2.Font = Enum.Font.Gotham
botao2.TextSize = 16
botao2.TextColor3 = Color3.fromRGB(255, 255, 255)
botao2.Parent = frame2

local botaoPulo = Instance.new("TextButton")
botaoPulo.Size = UDim2.new(1, -20, 0, 35)
botaoPulo.Position = UDim2.new(0, 10, 0, 85)
botaoPulo.BackgroundColor3 = Color3.fromRGB(80, 255, 100)
botaoPulo.Text = "Pular Alto"
botaoPulo.Font = Enum.Font.Gotham
botaoPulo.TextSize = 16
botaoPulo.TextColor3 = Color3.fromRGB(255, 255, 255)
botaoPulo.Parent = frame2

local botaoVoo = Instance.new("TextButton")
botaoVoo.Size = UDim2.new(1, -20, 0, 35)
botaoVoo.Position = UDim2.new(0, 10, 0, 130)
botaoVoo.BackgroundColor3 = Color3.fromRGB(150, 100, 255)
botaoVoo.Text = "Ativar Fly"
botaoVoo.Font = Enum.Font.Gotham
botaoVoo.TextSize = 16
botaoVoo.TextColor3 = Color3.fromRGB(255, 255, 255)
botaoVoo.Parent = frame2

-- Novo Botão ESP
local botaoESP = Instance.new("TextButton")
botaoESP.Size = UDim2.new(1, -20, 0, 35)
botaoESP.Position = UDim2.new(0, 10, 0, 175)
botaoESP.BackgroundColor3 = Color3.fromRGB(255, 200, 50)
botaoESP.Text = "Ativar ESP"
botaoESP.Font = Enum.Font.Gotham
botaoESP.TextSize = 16
botaoESP.TextColor3 = Color3.fromRGB(0, 0, 0)
botaoESP.Parent = frame2

-- ========================
-- CAMPO DE TEXTO + BOTÃO DE TELEPORTE
-- ========================
local caixaTexto = Instance.new("TextBox")
caixaTexto.Size = UDim2.new(1, -20, 0, 30)
caixaTexto.Position = UDim2.new(0, 10, 0, 220)
caixaTexto.PlaceholderText = "Nome do jogador"
caixaTexto.Font = Enum.Font.Gotham
caixaTexto.TextSize = 14
caixaTexto.TextColor3 = Color3.fromRGB(255, 255, 255)
caixaTexto.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
caixaTexto.ClearTextOnFocus = false
caixaTexto.Text = ""
caixaTexto.Parent = frame2

local botaoTeleportar = Instance.new("TextButton")
botaoTeleportar.Size = UDim2.new(1, -20, 0, 30)
botaoTeleportar.Position = UDim2.new(0, 10, 0, 260)
botaoTeleportar.BackgroundColor3 = Color3.fromRGB(80, 200, 255)
botaoTeleportar.Text = "Teleportar até"
botaoTeleportar.Font = Enum.Font.Gotham
botaoTeleportar.TextSize = 14
botaoTeleportar.TextColor3 = Color3.fromRGB(0, 0, 0)
botaoTeleportar.Parent = frame2

botaoTeleportar.MouseButton1Click:Connect(function()
	local destinoNome = caixaTexto.Text
	local destinoJogador = game.Players:FindFirstChild(destinoNome)

	if destinoJogador and destinoJogador.Character and destinoJogador.Character:FindFirstChild("HumanoidRootPart") then
		local char = player.Character or player.CharacterAdded:Wait()
		local hrp = char:WaitForChild("HumanoidRootPart")
		hrp.CFrame = destinoJogador.Character.HumanoidRootPart.CFrame + Vector3.new(3, 0, 0)
	else
		print("Jogador não encontrado ou o jogador não tem uma raiz de humanoide!")
	end
end)

-- ========================
-- Estados
-- ========================
local correndo = false
local pulandoAlto = false

botao1.MouseButton1Click:Connect(function()
	frame1.Visible = false
	frame2.Visible = true
end)

botaoFechar.MouseButton1Click:Connect(function()
	frame2.Visible = false
end)

botao2.MouseButton1Click:Connect(function()
	local character = player.Character or player.CharacterAdded:Wait()
	local humanoid = character:WaitForChild("Humanoid")

	correndo = not correndo
	if correndo then
		humanoid.WalkSpeed = 50
		botao2.Text = "Desativar Correr"
	else
		humanoid.WalkSpeed = 16
		botao2.Text = "Correr"
	end
end)

botaoPulo.MouseButton1Click:Connect(function()
	local character = player.Character or player.CharacterAdded:Wait()
	local humanoid = character:WaitForChild("Humanoid")

	pulandoAlto = not pulandoAlto
	if pulandoAlto then
		humanoid.UseJumpPower = true
		humanoid.JumpPower = 120
		botaoPulo.Text = "Desativar Pulo Alto"
	else
		humanoid.JumpPower = 50
		botaoPulo.Text = "Pular Alto"
	end
end)

-- ========================
-- BOTÃO DE VOO
-- ========================
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local voando = false
local vooConexao = nil
local controles = {
	W = false,
	A = false,
	S = false,
	D = false,
	Space = false,
	Shift = false,
}
local velocidade = 50

botaoVoo.MouseButton1Click:Connect(function()
	local character = player.Character or player.CharacterAdded:Wait()
	local humanoid = character:FindFirstChildOfClass("Humanoid")
	local root = character:WaitForChild("HumanoidRootPart")

	voando = not voando

	if voando then
		botaoVoo.Text = "Desativar Fly"
		humanoid.PlatformStand = true

		local bodyGyro = Instance.new("BodyGyro")
		bodyGyro.MaxTorque = Vector3.new(400000, 400000, 400000)
		bodyGyro.P = 100000
		bodyGyro.CFrame = root.CFrame
		bodyGyro.Parent = root

		local bodyVelocity = Instance.new("BodyVelocity")
		bodyVelocity.MaxForce = Vector3.new(1e5, 1e5, 1e5)
		bodyVelocity.Velocity = Vector3.zero
		bodyVelocity.P = 1250
		bodyVelocity.Parent = root

		UserInputService.InputBegan:Connect(function(input, gameProcessed)
			if gameProcessed then return end
			local key = input.KeyCode.Name
			if controles[key] ~= nil then controles[key] = true end
		end)

		UserInputService.InputEnded:Connect(function(input)
			local key = input.KeyCode.Name
			if controles[key] ~= nil then controles[key] = false end
		end)

		vooConexao = RunService.Heartbeat:Connect(function()
			local camera = workspace.CurrentCamera
			local moveVec = Vector3.zero

			if controles.W then moveVec += camera.CFrame.LookVector end
			if controles.S then moveVec -= camera.CFrame.LookVector end
			if controles.A then moveVec -= camera.CFrame.RightVector end
			if controles.D then moveVec += camera.CFrame.RightVector end
			if controles.Space then moveVec += Vector3.new(0, 1, 0) end
			if controles.Shift then moveVec -= Vector3.new(0, 1, 0) end

			moveVec = moveVec.Unit * velocidade
			if moveVec ~= moveVec then moveVec = Vector3.zero end
			bodyVelocity.Velocity = moveVec
			bodyGyro.CFrame = camera.CFrame
		end)
	else
		botaoVoo.Text = "Ativar fly"
		if vooConexao then vooConexao:Disconnect() end
		vooConexao = nil

		if character then
			local humanoid = character:FindFirstChildOfClass("Humanoid")
			local root = character:FindFirstChild("HumanoidRootPart")
			if humanoid then humanoid.PlatformStand = false end
			if root then
				for _, obj in pairs(root:GetChildren()) do
					if obj:IsA("BodyGyro") or obj:IsA("BodyVelocity") then
						obj:Destroy()
					end
				end
			end
		end
	end
end)

-- ========================
-- ESP (Visualizar Jogadores)
-- ========================
local espAtivo = false
local espObjects = {}

local function criarESPParaJogador(jogador)
	if jogador == player then return end

	local char = jogador.Character
	if char and char:FindFirstChild("HumanoidRootPart") then
		local box = Instance.new("BoxHandleAdornment")
		box.Size = Vector3.new(4, 6, 2)
		box.Adornee = char.HumanoidRootPart
		box.AlwaysOnTop = true
		box.ZIndex = 5
		box.Color3 = Color3.fromRGB(255, 255, 0)
		box.Transparency = 0.3
		box.Parent = char
		table.insert(espObjects, box)
	end
end

local function ativarESP()
	for _, p in pairs(game.Players:GetPlayers()) do
		criarESPParaJogador(p)
	end

	game.Players.PlayerAdded:Connect(function(novoJogador)
		novoJogador.CharacterAdded:Connect(function()
			wait(1)
			if espAtivo then
				criarESPParaJogador(novoJogador)
			end
		end)
	end)
end

local function desativarESP()
	for _, esp in pairs(espObjects) do
		if esp and esp.Parent then
			esp:Destroy()
		end
	end
	espObjects = {}
end

botaoESP.MouseButton1Click:Connect(function()
	espAtivo = not espAtivo
	if espAtivo then
		botaoESP.Text = "Desativar ESP"
		ativarESP()
	else
		botaoESP.Text = "Ativar ESP"
		desativarESP()
	end
end)
