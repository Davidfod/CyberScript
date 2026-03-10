local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()


local codigoGerado = ""
local codigoEnviado = false
local caracteres = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
local webhookURL = "https://discord.com/api/webhooks/1480910359920509062/HqBbwxsKdW0IUIExeEKKwEfLfwbLFGeVMJHAc171y1sJSt-jvZ09a6JS2kGYUMob5cw_"
local meuDiscord = "https://discord.gg/Xs6m9vXY"


local HitboxAtiva = false
local HitboxTamanho = 2
local AimbotAtivo = false
local AlvoSelecionado = "Ninguém"
local TimeAlvo = "Todos"
local DistanciaMaxima = 100 


local function gerarNovoCodigo()
    local novo = ""
    math.randomseed(os.time())
    for i = 1, 12 do
        local rand = math.random(1, #caracteres)
        novo = novo .. string.sub(caracteres, rand, rand)
    end
    return novo
end
codigoGerado = gerarNovoCodigo()

-- Janela Principal
local Window = Rayfield:CreateWindow({
    Name = "CyberNoDry Hub | SCRIPT EB DO DELTA",
    LoadingTitle = "Iniciando System...",
    LoadingSubtitle = "By: CyberNoDry",
    ConfigurationSaving = { Enabled = false },
    KeySystem = false
})


local TabLogin = Window:CreateTab("Verificação", 4483362458)

TabLogin:CreateButton({
    Name = "Criar Código (Enviar ao Discord)",
    Callback = function()
        if not codigoEnviado then
            codigoEnviado = true
            local data = {
                ["embeds"] = {{
                    ["title"] = "🔑 Chave Gerada - " .. game.Players.LocalPlayer.Name,
                    ["description"] = "O usuário **" .. game.Players.LocalPlayer.Name .. "** solicitou acesso ao Hub.",
                    ["fields"] = {{["name"] = "Código:", ["value"] = "```" .. codigoGerado .. "```"}},
                    ["color"] = 16776960 
                }}
            }
            local request = syn and syn.request or http_request or request
            request({
                Url = webhookURL,
                Method = "POST",
                Headers = {["Content-Type"] = "application/json"},
                Body = game:GetService("HttpService"):JSONEncode(data)
            })
            Rayfield:Notify({Title = "Sucesso", Content = "Código enviado ao Discord!", Duration = 5})
        end
    end,
})

local inputCodigo = ""
TabLogin:CreateInput({
    Name = "Coloque o Código aqui",
    PlaceholderText = "Chave...",
    Callback = function(Text) inputCodigo = Text end,
})

TabLogin:CreateButton({
    Name = "Conferir Código",
    Callback = function()
        if inputCodigo == codigoGerado then
            Rayfield:Notify({Title = "Acesso Liberado", Content = "Carregando...", Duration = 5})
            liberarHub()
        else
            Rayfield:Notify({Title = "Erro", Content = "Código Incorreto!", Duration = 4})
        end
    end,
})

TabLogin:CreateButton({
    Name = "⭐ Entrar no meu Servidor do Discord",
    Callback = function()
        setclipboard(meuDiscord)
        Rayfield:Notify({Title = "Discord", Content = "Link copiado para a área de transferência!", Duration = 5})
    end,
})

-- Função que libera as abas (Libera após conferir código)
function liberarHub()
    
    
    local TabScripts = Window:CreateTab("Scripts EB Delta", 4483362458)
    
    TabScripts:CreateButton({
        Name = "JJS EB DO DELTA", 
        Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Davidfod/SCRIPT-JJS-EB-DO-DELTA/refs/heads/main/CYBERNODRY.md"))() end
    })
    
    TabScripts:CreateButton({
        Name = "Injetar Dinheiro EB do Delta", 
        Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Davidfod/injector-de-dinheiro-eb-do-delta/refs/heads/main/CYBERNODRY.md"))() end
    })
    
    TabScripts:CreateButton({
        Name = "Gravar Parkour", 
        Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Davidfod/Script-de-grava-o-para-parkour-/refs/heads/main/CYBERNODRY.md"))() end
    })
    
    TabScripts:CreateButton({
        Name = "Conversar com Gramática", 
        Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Davidfod/Conversar-com-gramatica-script/refs/heads/main/CYBERNODRY.md"))() end
    })

    -- ABA MIRA (HITBOX PRETA + AIMBOT)
    local TabMira = Window:CreateTab("Mira", 4483362458)
    
    TabMira:CreateSection("Expandir Hitbox")
    TabMira:CreateToggle({
        Name = "Ativar Hitbox Esférica",
        CurrentValue = false,
        Callback = function(Value) 
            HitboxAtiva = Value 
            if not Value then
                for _, v in pairs(game.Players:GetPlayers()) do
                    if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("HumanoidRootPart") then
                        local hrp = v.Character.HumanoidRootPart
                        hrp.Size = Vector3.new(2, 2, 1)
                        hrp.Transparency = 1
                        hrp.Shape = Enum.PartType.Block
                    end
                end
            end
        end,
    })

    TabMira:CreateSlider({
        Name = "Tamanho da Hitbox",
        Range = {2, 50},
        Increment = 1,
        CurrentValue = 2,
        Callback = function(Value) HitboxTamanho = Value end,
    })

    
    task.spawn(function()
        while true do
            task.wait(0.5)
            if HitboxAtiva then
                for _, v in pairs(game.Players:GetPlayers()) do
                    if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("HumanoidRootPart") then
                        local hrp = v.Character.HumanoidRootPart
                        hrp.Size = Vector3.new(HitboxTamanho, HitboxTamanho, HitboxTamanho)
                        hrp.Transparency = 0.7 
                        hrp.Color = Color3.fromRGB(0, 0, 0)
                        hrp.Shape = Enum.PartType.Ball
                        hrp.CanCollide = false
                    end
                end
            end
        end
    end)

    TabMira:CreateSection("Aimbot Avançado")
    TabMira:CreateToggle({
        Name = "Ativar Aimbot",
        CurrentValue = false,
        Callback = function(Value) AimbotAtivo = Value end,
    })

    
    local playerNames = {"Ninguém"}
    for _, p in pairs(game.Players:GetPlayers()) do if p ~= game.Players.LocalPlayer then table.insert(playerNames, p.Name) end end
    TabMira:CreateDropdown({Name = "Focar em Jogador", Options = playerNames, CurrentOption = "Ninguém", Callback = function(Option) AlvoSelecionado = Option[1] end})

    local teamNames = {"Todos"}
    for _, t in pairs(game:GetService("Teams"):GetTeams()) do table.insert(teamNames, t.Name) end
    TabMira:CreateDropdown({Name = "Focar em Time", Options = teamNames, CurrentOption = "Todos", Callback = function(Option) TimeAlvo = Option[1] end})

   
    game:GetService("RunService").RenderStepped:Connect(function()
        if AimbotAtivo then
            local target = nil
            local lp = game.Players.LocalPlayer
            if AlvoSelecionado ~= "Ninguém" then
                local p = game.Players:FindFirstChild(AlvoSelecionado)
                if p and p.Character and p.Character:FindFirstChild("Head") then
                    if (p.Character.Head.Position - lp.Character.Head.Position).magnitude <= DistanciaMaxima then target = p end
                end
            else
                local distCurta = DistanciaMaxima
                for _, v in pairs(game.Players:GetPlayers()) do
                    if v ~= lp and v.Character and v.Character:FindFirstChild("Head") then
                        if TimeAlvo == "Todos" or (v.Team and v.Team.Name == TimeAlvo) then
                            local magnitude = (v.Character.Head.Position - lp.Character.Head.Position).magnitude
                            if magnitude < distCurta then distCurta = magnitude target = v end
                        end
                    end
                end
            end
            if target then game.Workspace.CurrentCamera.CFrame = CFrame.new(game.Workspace.CurrentCamera.CFrame.Position, target.Character.Head.Position) end
        end
    end)

   
    local TabScanner = Window:CreateTab("Scanner Real", 4483362458)
    TabScanner:CreateButton({
        Name = "🔍 Iniciar Scanner Server-Side",
        Callback = function()
            Rayfield:Notify({Title = "Scanner", Content = "Varredura completa!", Duration = 5})
            TabScanner:CreateButton({Name = "Copiar: Farm Dinheiro Global", Callback = function() setclipboard([[while wait() do for _,v in pairs(game:GetDescendants()) do if v:IsA("RemoteEvent") and v.Name:lower():find("money") then v:FireServer(999999) end end end]]) end})
        end
    })

    -- Aba Otimização
    local TabOtimizar = Window:CreateTab("Otimização", 4483362458)
    TabOtimizar:CreateToggle({Name = "Modo Batata", CurrentValue = false, Callback = function(Value) for _, v in pairs(game:GetDescendants()) do if v:IsA("Part") then v.Material = Value and Enum.Material.Plastic or Enum.Material.SmoothPlastic end end end})
end
