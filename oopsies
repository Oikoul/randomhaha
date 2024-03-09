local info = {}
local names = {}
local enabled = false
local fling = false
local mouse = false
local plr = game.Players.LocalPlayer
local head = plr.Character.Head
local m = plr:GetMouse()
local height = 6
local side = 0
local uis = game:GetService("UserInputService")
local throwstre = 1
local anchormode = false
local plrNAME = string.lower(game.Players.LocalPlayer.Name)
local spinmode = false
local spinsp = .2
local spinspp = 0
local Magic = Instance.new("ScreenGui")
local Main = Instance.new("Frame")
local TextBox = Instance.new("TextBox")
local dm = 50
local noclip = false
if game.CoreGui:FindFirstChild("Magic") then
	game.CoreGui["Magic"]:Destroy()
end
spawn(function()
	while true do
		game.Players.LocalPlayer.MaximumSimulationRadius = math.pow(math.huge,math.huge)*math.huge
		sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.pow(math.huge,math.huge)*math.huge)
		game:GetService("RunService").Heartbeat:Wait()
	end
end)
Magic.Name = "Magic"
Magic.Parent = game.CoreGui
Magic.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
Main.Name = "Main"
Main.Parent = Magic
Main.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Main.BackgroundTransparency = 0.500
Main.BorderColor3 = Color3.fromRGB(85, 255, 0)
Main.Position = UDim2.new(0.411487013, 0, 0.0336700343, 0)
Main.Size = UDim2.new(0, 224, 0, 30)
TextBox.Parent = Main
TextBox.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
TextBox.BorderColor3 = Color3.fromRGB(85, 255, 0)
TextBox.Position = UDim2.new(0.0223214291, 0, 0.0666666701, 0)
TextBox.Size = UDim2.new(0, 214, 0, 25)
TextBox.ClearTextOnFocus = false
TextBox.Font = Enum.Font.SourceSans
TextBox.PlaceholderColor3 = Color3.fromRGB(85, 255, 0)
TextBox.PlaceholderText = "Enter"
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(85, 255, 0)
TextBox.TextSize = 14.000
TextBox.TextXAlignment = Enum.TextXAlignment.Left
local function move()
	local script = Instance.new('LocalScript', Main)
	local UIS = game:GetService('UserInputService')
	local frame = script.Parent
	local dragToggle = nil
	local dragSpeed = 0.25
	local dragStart = nil
	local startPos = nil
	local function updateInput(input)
		local delta = input.Position - dragStart
		local position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
		game:GetService('TweenService'):Create(frame, TweenInfo.new(dragSpeed), {Position = position}):Play()
	end
	frame.InputBegan:Connect(function(input)
		if (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch) then 
			dragToggle = true
			dragStart = input.Position
			startPos = frame.Position
			input.Changed:Connect(function()
				if input.UserInputState == Enum.UserInputState.End then
					dragToggle = false
				end
			end)
		end
	end)
	UIS.InputChanged:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
			if dragToggle then
				updateInput(input)
			end
		end
	end)
end
coroutine.wrap(move)()
local function main()
	while enabled == true do
		if mouse ~= true then
			for _, v in pairs(info) do
				if v ~= nil and v:FindFirstChild("BodyPosition") ~= nil then
					if noclip == true then
						for _, nc in pairs(info) do
							nc.CanCollide = false
						end
					else
						for _, nc in pairs(info) do
							nc.CanCollide = true
						end
					end
					if spinmode == false then
						local target1 = v.BodyPosition
						local target2 = v.BodyGyro
						for _, v in pairs(game.Players:GetPlayers()) do
							if plrNAME ~= nil and plrNAME == string.lower(v.Name) then
								local fut = v.Character:FindFirstChild("HumanoidRootPart").CFrame + (v.Character:FindFirstChild("HumanoidRootPart").Velocity * .4)
								local xx = fut * CFrame.new(side, 0, 0)
								local zz = fut * CFrame.new(side, 0, 0)
								target1.Position = Vector3.new(xx.x, fut.y + height, zz.z)
								target2.CFrame = v.Character:FindFirstChild("Head").CFrame
							end
						end
					else
						for _, v in pairs(game.Players:GetPlayers()) do
							if plrNAME ~= nil and plrNAME == string.lower(v.Name) then
								if v.Character:FindFirstChild("Humanoid").Health > 0 then
									local set = 0
									for _, v in pairs(info) do
										if v ~= nil then
											set += 1
										end
									end
									local setup = 360 / set
									local items = 0
									for _, m in pairs(info) do
										if m ~= nil and m:FindFirstChild("BodyPosition") ~= nil and m:FindFirstChild("BodyGyro") and v.Character:FindFirstChild("Humanoid").Health > 0 then
											local fut = v.Character:FindFirstChild("HumanoidRootPart").Position + (v.Character:FindFirstChild("HumanoidRootPart").Velocity * .4)
											local ea = spinsp * 50
											local xx = fut.x + dm * math.cos(math.rad(spinspp + setup * items))
											local yy = fut.y
											local zz = fut.z - dm * math.sin(math.rad(spinspp + setup * items))
											spinspp += spinsp
											items += 1
											m.BodyPosition.Position = Vector3.new(xx + side, yy + height, zz)
											m.BodyGyro.CFrame = v.Character:FindFirstChild("Head").CFrame
										end
									end
								end
							end
						end
					end
				end
			end
		end
		if mouse == true then
			for _, v in pairs(info) do
				if v ~= nil and v:FindFirstChild("BodyPosition") ~= nil then
					local target1 = v.BodyPosition
					local target2 = v.BodyGyro
					target1.Position = Vector3.new(m.Hit.X + side, m.Hit.Y + side + height, m.Hit.Z + side)
					target2.CFrame = plr.Character:FindFirstChild("Head").CFrame
				end
			end
		end
		if enabled ~= true then
			break
		end
		game:GetService("RunService").Heartbeat:Wait()
	end
end
uis.InputEnded:Connect(function(pp)
	if pp.KeyCode == Enum.KeyCode.F1 then
		if enabled == false then
			for _, v in pairs(game:GetService("Workspace").Grabable:GetChildren()) do
				if v ~= nil and v:FindFirstChild("Part") ~= nil and (v.Part.Position - head.Position).magnitude < 30 and v.Name ~= "USED PART" then
					
							if v.Part:FindFirstChild("BodyPosition") ~= nil then
									v.Part.BodyPosition:Destroy()
								end
								if v.Part:FindFirstChild("BodyGyro") ~= nil then
									v.Part.BodyGyro:Destroy()
								end
								local bp = Instance.new("BodyPosition")
								bp.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
								bp.Position = v.Part.Position
								bp.Parent = v.Part
								local p = Instance.new("BodyGyro")
								p.Parent = v.Part
								p.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
					table.insert(info, v.Part)
					table.insert(names, v.Name)
					v.Name = "USED PART"
					
				end
			end
			enabled = true
			print("Started!")
			main()
		else
			for _, v in pairs(info) do
				if v ~= nil then
					if v:FindFirstChild("BodyPosition") ~= nil then
						v.BodyPosition:Destroy()
						v.BodyGyro:Destroy()
						v.CanCollide = true
						v.Parent.Name = names[1]
						table.remove(names, 1)
						table.remove(info, 1)
						wait(.1)
					end
				else
					table.remove(names, 1)
				end
			end
			print("Ended!")
			enabled = false
		end
	end
	if pp.KeyCode == Enum.KeyCode.F2 then
		if mouse == false then
			mouse = true
			print("Mouse mode enabled!")
		else
			mouse = false
			print("Mouse mode disabled!")
		end
	end
	if pp.KeyCode == Enum.KeyCode.F3 then
		height += 3
		print("Height: "..height)
	end
	if pp.KeyCode == Enum.KeyCode.F4 then
		height -= 3
		print("Height: "..height)
	end
	if pp.KeyCode == Enum.KeyCode.F5 then
		side += 3
		print("Side: "..side)
	end
	if pp.KeyCode == Enum.KeyCode.F6 then
		side -= 3
		print("Side: "..side)
	end
	if pp.KeyCode == Enum.KeyCode.F7 then
		if fling == false then
			print("Fling enabled")
			fling = true
			for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
				if v:IsA("BasePart") and v.Name ~="HumanoidRootPart" then 
					game:GetService("RunService").Heartbeat:connect(function()
						v.Velocity = Vector3.new(-30,0,0)
					end)
				end
			end
			for _, v in pairs(info) do
				if v ~= nil then
					local bt = Instance.new("BodyThrust")
					bt.Parent = v
					bt.Force = Vector3.new(5000, 5000, 5000)
					bt.Location = v.Position
					bt.Parent = v
				end
			end
		else
			fling = false
			print("Fling disabled")
			for _, v in pairs(info) do
				if v ~= nil and v:FindFirstChild("BodyThrust") then
					v.BodyThrust:Destroy()
				end
			end
		end
	end
	if pp.KeyCode == Enum.KeyCode.Minus then
		throwstre -= .25
		print("Throw strength: "..throwstre)
	end
	if pp.KeyCode == Enum.KeyCode.Equals then
		throwstre += .25
		print("Throw strength: "..throwstre)
	end
	if pp.KeyCode == Enum.KeyCode.F8 then
		if anchormode == true then
			anchormode = false
			print("Anchor mode disabled")
		else
			anchormode = true
			print("Anchor mode enabled")
		end
	end
	if pp.KeyCode == Enum.KeyCode.End then
		if TextBox.Text ~= "" then
			local text = TextBox.Text
			for _, v in pairs(game.Players:GetPlayers()) do
				if string.lower(text) == string.lower(v.Name) then
					plrNAME = string.lower(text)
				end
			end
			if string.lower(text) == "spin" then
				if spinmode == false then
					spinmode = true
					print("Spin mode activated!")
				else
					spinmode = false
					print("Spin mode deactivated!")
				end
			end
			if string.lower(text) == "unfollow" then
				enabled = false
			end
			if string.lower(text) == "follow" then
				enabled = true
				main()
			end
			local tt = game.CoreGui.Magic.Main.TextBox.Text:split(" ")
			if string.lower(tt[1]) == "speed" and tonumber(tt[2]) then
				spinsp = tonumber(tt[2])
				print("Spin speed set: "..spinsp)
			end
			if string.lower(tt[1]) == "dm" and tonumber(tt[2]) then
				dm = tonumber(tt[2])
				print("Spin diameter set: "..dm)
			end
			if string.lower(text) == "noclip" then
				noclip = true
			end
			if string.lower(text) == "clip" then
				noclip = false
			end
			if string.lower(text) == "uranium value" then
				local val = 0
				for _, v in pairs(info) do
					if v ~= nil then
						local va = v.Size.X * v.Size.Y * v.Size.z
						local ve = 159.982174688057 * va
						val += ve
					end
				end
				print("Refined uranium value ~ $"..val)
			end
		end
	end
end)
m.KeyDown:Connect(function(k)
	if k == "f" and m.Hit and enabled then
		for _, v in pairs(game:GetService("Workspace").Grabable:GetChildren()) do
			if v ~= nil and v:FindFirstChild("Part") ~= nil and (v.Part.Position - m.Hit.Position).magnitude < 10 and v.Name ~= "USED PART" then


							if v.Part:FindFirstChild("BodyPosition") ~= nil then
								v.Part.BodyPosition:Destroy()
							end
							if v.Part:FindFirstChild("BodyGyro") ~= nil then
								v.Part.BodyGyro:Destroy()
							end
							local bp = Instance.new("BodyPosition")
							bp.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
							bp.Position = v.Part.Position
							bp.Parent = v.Part
							local p = Instance.new("BodyGyro")
							p.Parent = v.Part
							p.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
				table.insert(info, v.Part)
				table.insert(names, v.Name)
				v.Name = "USED PART"

			end
		end
	end
	if k == "g" and m.Hit and enabled then
		if info[1] ~= nil then
			local target = info[1]
			info[1].Parent.Name = names[1]
			table.remove(info, 1)
			table.remove(names, 1)
			target.BodyPosition.P = target.BodyPosition.P * throwstre
			target.BodyPosition.Position = Vector3.new(m.Hit.X, m.Hit.Y, m.Hit.Z)
			target.CanCollide = true
			if anchormode == false then
				wait()
				target:FindFirstChild("BodyPosition"):Destroy()
				target:FindFirstChild("BodyGyro"):Destroy()
			end
		else
			table.remove(names, 1)
		end
	end
end)
