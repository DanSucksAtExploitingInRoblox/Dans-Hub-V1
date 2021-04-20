-- Dans hub V1
-- This will have a lisence soon.
-- Script :


local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("ImageLabel")
local TextLabel = Instance.new("TextLabel")
local TextButton = Instance.new("TextButton")



ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

Frame.Name = "Frame"
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.BackgroundTransparency = 1.000
Frame.Position = UDim2.new(0.143782392, 0, 0.290836662, 0)
Frame.Size = UDim2.new(0, 386, 0, 281)
Frame.Image = "rbxassetid://3570695787"
Frame.ImageColor3 = Color3.fromRGB(43, 43, 43)
Frame.ScaleType = Enum.ScaleType.Slice
Frame.SliceCenter = Rect.new(100, 100, 100, 100)
Frame.SliceScale = 0.120

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.Position = UDim2.new(0, 0, 0.0427046269, 0)
TextLabel.Size = UDim2.new(0, 386, 0, 60)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "Dan's Hub V1"
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextSize = 70.000

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
TextButton.Position = UDim2.new(0.0725388601, 0, 0.302491099, 0)
TextButton.Size = UDim2.new(0, 325, 0, 163)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "ESP"
TextButton.TextColor3 = Color3.fromRGB(0, 0, 0)
TextButton.TextSize = 77.000
ESPButton.MouseButton1Down:connect(function()
	esp = true
	teamcheck = true
	-- esp options
	name = true

	function Esp()
		esp = true
		for i,v in pairs(game.Players:GetChildren()) do
			if v ~= game.Players.LocalPlayer then
				local base = Instance.new("BillboardGui", workspace.CurrentCamera)
				local esP = Instance.new("Frame", base)
				-- Billboard Stuff
				base.AlwaysOnTop = true
				base.Enabled = true
				base.Size = UDim2.new(4.5,0,6,0)
				base.Name = "ESP"
				base.Adornee = v.Character.Torso
				base.StudsOffset = Vector3.new(0, -0.6, 0)
				-- Frame Stuff
				esP.BackgroundColor3 = Color3.new(0,255,255)
				esP.BackgroundTransparency = 0.8
				esP.BorderColor3 = Color3.new(0,0,0)
				esP.BorderSizePixel = 1
				esP.Size = UDim2.new(1,0,1,0)
				if name ~= false then
					local name = Instance.new("TextLabel",base)
					name.Size = UDim2.new(1,0,1,0)
					name.BackgroundTransparency = 1
					name.Position = UDim2.new(0,0,0,0)
					name.Text = v.Name
					name.TextScaled = true
					name.TextXAlignment = "Left"
					name.TextYAlignment = "Top"
				end
			end
		end
	end
	function EspOff()
		esp = false
		for i,v in pairs(workspace.CurrentCamera:GetChildren()) do
			v:Destroy()
		end
	end
	game.Players.LocalPlayer.Chatted:connect(function(msg)
		if msg:lower():sub(1,4) == "/esp" then
			Esp()
		elseif msg:lower():sub(1,4) == "/off" then
			EspOff()
		end
	end)
	game.Players.PlayerAdded:connect(function(plr)
		if esp == true then
			if teamcheck == true then
				if plr.TeamColor ~= game.Players.LocalPlayer.TeamColor then
					Esp(tostring(plr.Name))
				end
			end
		else
			Esp(tostring(plr.Name))
		end
	end)
end)
