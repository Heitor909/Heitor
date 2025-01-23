-- Script em Lua (Exemplo Genérico)

-- Função para pegar a fruta (simula pegar a fruta)
function pegarFruta()
    -- Aqui deve ser colocada a lógica que detecta se há uma fruta no chão
    -- e então faz o jogador pegar essa fruta.
    -- Exemplo genérico:
    if game.Workspace:FindFirstChild("Fruit") then
        local fruta = game.Workspace.Fruit
        fruta:Destroy()  -- Remove a fruta do chão
        print("Fruta pega com sucesso!")
    end
end

-- Função para upar de level
function upaLevel()
    -- Exemplo genérico para upar nível: interagir com inimigos ou outros objetos.
    -- Isso depende das interações que o jogo permite.
    local player = game.Players.LocalPlayer
    if player and player.Character then
        -- Simula atacar inimigos e ganhar XP
        local inimigos = game.Workspace:FindPartsInRegion3(workspace.CurrentCamera.CFrame.Position, Vector3.new(50, 50, 50), nil)
        for _, inimigo in ipairs(inimigos) do
            if inimigo:FindFirstChild("Humanoid") then
                -- Simula dano no inimigo
                inimigo.Humanoid:TakeDamage(50)  -- Dano fictício, ajustável
                print("Inimigo derrotado! XP ganho.")
            end
        end
    end
end

-- Função de teleporte
function teleporteParaSea(sea)
    local player = game.Players.LocalPlayer
    local destino
    -- Define os destinos para cada Sea
    if sea == 1 then
        destino = CFrame.new(100, 50, 100) -- Exemplo de posição no Sea 1
    elseif sea == 2 then
        destino = CFrame.new(200, 50, 200) -- Exemplo de posição no Sea 2
    elseif sea == 3 then
        destino = CFrame.new(300, 50, 300) -- Exemplo de posição no Sea 3
    end

    -- Teleporta o jogador para o destino
    if player and player.Character then
        player.Character:SetPrimaryPartCFrame(destino)
        print("Teleportando para o Sea " .. sea)
    end
end

-- Função principal
function main()
    while true do
        -- Simula o up de level (essa função pode ser chamada de tempos em tempos)
        upaLevel()
        
        -- Simula pegar a fruta (essa função pode ser chamada se o jogador estiver próximo de uma fruta)
        pegarFruta()
        
        -- Simula teleporte para o Sea 2 (exemplo de uso)
        teleporteParaSea(2)
        
        -- Atraso entre as execuções das funções
        wait(5)  -- Espera 5 segundos entre cada ação (ajustável)
    end
end

-- Inicia o script
main()
