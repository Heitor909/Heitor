

    -- Verificar se existe o grupo de NPCs no mapa
    local enemiesFolder = workspace:FindFirstChild("Enemies")
    if not enemiesFolder then
        warn("Não foi possível encontrar o grupo de NPCs no mapa!")
        return
    end

    -- Local onde os NPCs serão reunidos (posição do jogador, por exemplo)
    local targetPosition = humanoidRootPart.Position

    for _, npc in pairs(enemiesFolder:GetChildren()) do
        -- Verifica se o NPC é válido
        if npc:FindFirstChild("Humanoid") and npc:FindFirstChild("HumanoidRootPart") then
            local humanoid = npc.Humanoid
            local rootPart = npc.HumanoidRootPart

            -- NPC será teleportado para o local desejado (juntar)
            rootPart.CFrame = CFrame.new(targetPosition) + Vector3.new(math.random(-5, 5), 0, math.random(-5, 5))
            print("NPC movido:", npc.Name)
        end
    end
    print("NPCs reunidos!")
end
