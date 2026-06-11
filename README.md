loadstring([[game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        local humanoid = character:WaitForChild("Humanoid")
        humanoid.MaxHealth = math.huge
        humanoid.Health = humanoid.MaxHealth
        humanoid.HealthChanged:Connect(function()
            if humanoid.Health < humanoid.MaxHealth then
                humanoid.Health = humanoid.MaxHealth
            end
        end)
        humanoid.Died:Connect(function()
            humanoid.Health = humanoid.MaxHealth
            humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
        end)
    end)
end)]])()
