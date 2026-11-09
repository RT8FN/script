local TweenService = game:GetService('TweenService')
local inputService = game:GetService("UserInputService")
local userSettings = UserSettings and UserSettings() or function() end
local RunService = game:GetService('RunService')
local Mouse = game.Players.LocalPlayer:GetMouse()
local MarketplaceService = game:GetService("MarketplaceService")
local par = game.CoreGui -- game.Players.LocalPlayer.PlayerGui game.CoreGui and game.CoreGui or game.Players.LocalPlayer.PlayerGui
for i,v in next, par:GetChildren() do if v.Name == "Ui Lossless" then v:Destroy() end end
for i,v in next, game.Lighting:GetChildren() do if v:GetAttribute("NormolHub2") then v:Destroy() end end
if _G.LoadBackground then task.cancel(_G.LoadBackground) end
local getBlur = function()
	for i,v in next, game:GetService('Lighting'):GetChildren() do if v:GetAttribute('NormolHub') then return v end end
	return nil
end

local removeBlur = function()
	for i,v in next, game:GetService('Lighting'):GetChildren() do if v:GetAttribute('NormolHub') then v:Destroy() end end
end

local function getMapName()
	local placeId = game.PlaceId
	local success, info = pcall(function()
		return MarketplaceService:GetProductInfo(placeId)
	end)

	if success then
		return info.Name
	else
		return "Unknown Map"
	end
end

local function getMapIcon()
	local placeId = game.PlaceId
