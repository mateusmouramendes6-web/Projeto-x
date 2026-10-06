# Projeto-x

-- ADMIN MODE
-- Coloque em ServerScriptService

local Players = game:GetService("Players")

local ADMINS = {
	[123456789] = true, -- troque pelo seu UserId
}

local function isAdmin(player)
	return ADMINS[player.UserId] == true
end

Players.PlayerAdded:Connect(function(player)
	if not isAdmin(player) then return end

	player.CharacterAdded:Connect(function(character)
		local humanoid = character:WaitForChild("Humanoid")

		-- Invencível
		humanoid.MaxHealth = math.huge
		humanoid.Health = math.huge

		humanoid.HealthChanged:Connect(function()
			if humanoid.Health < humanoid.MaxHealth then
				humanoid.Health = humanoid.MaxHealth
			end
		end)
	end)
end)
