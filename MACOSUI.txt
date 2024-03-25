-- horrible variable naming tysm oSkid im never letting you name stuff ever again i haad to struggle with these horrible names 
local uis = game:GetService("UserInputService")
local rs = game:GetService("RunService")
local ts = game:GetService("TweenService")
local plrs = game:GetService("Players")
local getService = game.GetService;
local players = getService(game, "Players");
--local lighting = getService(game, "Lighting")
local runService = getService(game, "RunService");
local guiService = getService(game, "GuiService");
local inputService = getService(game, "UserInputService");
--local replicatedStorage = getService(game, "ReplicatedStorage")
local starterGUI = getService(game, "StarterGui");
local workspace, debug = workspace, debug;
local math, string = math, string;
local table, Instance = table, Instance;
local Vector3, Vector2 = Vector3, Vector2
local Color3, CFrame = Color3, CFrame;
local Enum, type = Enum, type;
local mathFloor, mathCeil, mathMax, mathHuge, mathRandom, mathClamp, mathRound = math.floor,math.ceil,math.max,math.huge,math.random,math.clamp,math.round;
local vector2New, vector3New, udim2New, cframeNew = Vector2.new, Vector3.new, UDim2.new, CFrame.new;
local colorNew, color3RGB = Color3.new, Color3.fromRGB;
local tableInsert, tableFind = table.insert, table.find;
local instanceNew = Instance.new;
local camera = workspace.CurrentCamera;
local worldToViewportPoint = camera.WorldToViewportPoint;
local findFirstChild = game.FindFirstChild;
local localPlayer = players.LocalPlayer;
local Mouse = localPlayer:GetMouse();
local findFirstChildOfClass = game.FindFirstChildOfClass;
local QwFolder = "QwUIS";
local ConfigurationFolder = QwFolder.."/Configs";
local ConfigurationExtension = ".Qw";
local Library = {connections = {}} 

local utility = {}
function utility:Connect(connection, func) -- this will help disable any connections with keybind 
	local con = connection:Connect(func)
	table.insert(Library.connections, con)
	return con
end

function utility:ToRGB(color)  
	return color.R*255,color.G*255,color.B*255
end

function Library:Window(Info)
	Info = Info or {}
	local window = {first_tab = nil, tabcount = 0}

	local grabielscsgocheat = Instance.new("ScreenGui")
	grabielscsgocheat.Name = "Grabiel'scsgocheat"
	grabielscsgocheat.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	grabielscsgocheat.Parent = game:GetService("CoreGui")

	local mainFrame = Instance.new("Frame")
	mainFrame.Parent = grabielscsgocheat
	mainFrame.Name = "MainFrame"
	mainFrame.BackgroundColor3 = Color3.fromRGB(6, 6, 6)
	mainFrame.BackgroundTransparency = 0.11
	mainFrame.BorderColor3 = Color3.fromRGB(0, 0, 0)
	mainFrame.BorderSizePixel = 0
	mainFrame.Position = UDim2.fromScale(0.257, 0.14)
	mainFrame.Size = UDim2.fromOffset(784, 577)
	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.Parent = mainFrame
	local holdingSections = Instance.new("Frame")
	holdingSections.Parent = mainFrame
	holdingSections.Name = "HoldingSections"
	holdingSections.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	holdingSections.BackgroundTransparency = 1
	holdingSections.BorderColor3 = Color3.fromRGB(0, 0, 0)
	holdingSections.BorderSizePixel = 0
	holdingSections.Position = UDim2.fromScale(0.276, 0.0116)
	holdingSections.Size = UDim2.fromOffset(570, 560)
	local uIListLayout = Instance.new("UIListLayout")
	uIListLayout.Name = "UIListLayout"
	uIListLayout.Padding = UDim.new(0, 1)
	uIListLayout.FillDirection = Enum.FillDirection.Horizontal
	uIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	uIListLayout.Parent = holdingSections
	local tabBorder = Instance.new("Frame")
	tabBorder.Parent = mainFrame
	tabBorder.Name = "TabBorder"
	tabBorder.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	tabBorder.BorderColor3 = Color3.fromRGB(0, 0, 0)
	tabBorder.BorderSizePixel = 0
	tabBorder.Position = UDim2.fromScale(0.271, 0)
	tabBorder.Size = UDim2.new(0, 1, 1, 0)

	--side bar holder 
	local sidebarHolder = Instance.new("Frame")
	sidebarHolder.Parent = mainFrame
	sidebarHolder.Name = "SidebarHolder"
	sidebarHolder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	sidebarHolder.BackgroundTransparency = 1
	sidebarHolder.BorderColor3 = Color3.fromRGB(0, 0, 0)
	sidebarHolder.BorderSizePixel = 0
	sidebarHolder.Position = UDim2.fromScale(0, 0.00161)
	sidebarHolder.Size = UDim2.new(0.271, 1, -0.00161, 577)
	local close = Instance.new("TextButton")
	close.Name = "Close"
	close.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
	close.Text = ""
	close.TextColor3 = Color3.fromRGB(0, 0, 0)
	close.TextSize = 14
	close.AutoButtonColor = false
	close.BackgroundColor3 = Color3.fromRGB(254, 94, 87)
	close.Position = UDim2.fromOffset(39.984, 8.0203)
	close.Size = UDim2.fromOffset(10, 10)
	close.Parent = mainFrame
	close.MouseButton1Click:Connect(function()
		game:GetService("CoreGui")["Grabiel'scsgocheat"]:Destroy()
		for i, v in pairs(Library.connections) do
			v:Disconnect()
		end
	end)
	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.CornerRadius = UDim.new(0, 50)
	uICorner.Parent = close

	local minimize = Instance.new("TextButton")
	minimize.Name = "Minimize"
	minimize.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
	minimize.Text = ""
	minimize.TextColor3 = Color3.fromRGB(0, 0, 0)
	minimize.TextSize = 14
	minimize.AutoButtonColor = false
	minimize.BackgroundColor3 = Color3.fromRGB(250, 188, 56)
	minimize.Position = UDim2.fromOffset(24, 8)
	minimize.Size = UDim2.fromOffset(10, 10)
	minimize.Parent = mainFrame
	minimize.MouseButton1Click:Connect(function()

		game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.HoldingSections.Visible = false 
		game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.SidebarHolder.Visible = false 
		game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.TabBorder.Visible = false 
		ts:Create(mainFrame, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Size =udim2New(0, 784,0,43)}):Play()

	end)

	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.CornerRadius = UDim.new(0, 50)
	uICorner.Parent = minimize

	local open = Instance.new("TextButton")
	open.Name = "Open"
	open.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
	open.Text = ""
	open.TextColor3 = Color3.fromRGB(0, 0, 0)
	open.TextSize = 14
	open.AutoButtonColor = false
	open.BackgroundColor3 = Color3.fromRGB(116, 170, 92)
	open.Position = UDim2.fromOffset(9, 8)
	open.Size = UDim2.fromOffset(10, 10)
	open.Parent = mainFrame
	open.MouseButton1Click:Connect(function()

		ts:Create(mainFrame, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Size =UDim2.fromOffset(784, 577)}):Play()
		wait(0.10)

		game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.HoldingSections.Visible = true 
		game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.SidebarHolder.Visible = true 
		game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.TabBorder.Visible = true 
	end)
	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.CornerRadius = UDim.new(0, 50)
	uICorner.Parent = open


	local line1 = Instance.new("Frame")
	line1.Name = "line1"
	line1.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	line1.BorderColor3 = Color3.fromRGB(0, 0, 0)
	line1.BorderSizePixel = 0
	line1.Position = UDim2.fromOffset(0, 40)
	line1.Size = UDim2.fromOffset(214, 1)
	line1.Parent = sidebarHolder

	local line2 = Instance.new("Frame")
	line2.Name = "Line2"
	line2.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	line2.BorderColor3 = Color3.fromRGB(0, 0, 0)
	line2.BorderSizePixel = 0
	line2.Position = UDim2.fromScale(0, 0.154)
	line2.Size = UDim2.fromOffset(214, 1)
	line2.Parent = sidebarHolder

	local tabHolder = Instance.new("ScrollingFrame")

	tabHolder.Name = "TabHolder"
	tabHolder.ScrollBarImageColor3 = Color3.fromRGB(42, 42, 42)
	tabHolder.ScrollBarThickness = 5
	tabHolder.ScrollingDirection = Enum.ScrollingDirection.Y
	tabHolder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	tabHolder.BackgroundTransparency = 1
	tabHolder.BorderColor3 = Color3.fromRGB(0, 0, 0)
	tabHolder.BorderSizePixel = 0
	tabHolder.Position = UDim2.fromScale(0, 0.17)
	tabHolder.Selectable = false
	tabHolder.Size = UDim2.fromOffset(209, 412)
	tabHolder.SelectionGroup = false

	local uIListLayout = Instance.new("UIListLayout")
	uIListLayout.Name = "UIListLayout"
	uIListLayout.Padding = UDim.new(0, 8)
	uIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
	uIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
	uIListLayout.Parent = tabHolder
		--[[
		local frame = Instance.new("Frame")
		frame.Name = "Frame"
		frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		frame.BackgroundTransparency = 1
		frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
		frame.BorderSizePixel = 0
		frame.Position = UDim2.fromOffset(6, 180)
		frame.Size = UDim2.fromOffset(5, 5)
		frame.Parent = tabHolder
		]]
	tabHolder.Parent = sidebarHolder

	local usernameSeparator = Instance.new("Frame")
	usernameSeparator.Name = "UsernameSeparator"
	usernameSeparator.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	usernameSeparator.BorderSizePixel = 0
	usernameSeparator.Position = UDim2.fromScale(0, 0.888)
	usernameSeparator.Size = UDim2.new(1, 0, 0, 1)
	usernameSeparator.Parent = sidebarHolder
	-- end
	-- section 



	-- end
	-- search frame 
	local searchFrame = Instance.new("Frame")
	searchFrame.Parent = sidebarHolder
	searchFrame.Name = "Search_Frame"
	searchFrame.BackgroundColor3 = Color3.fromRGB(29, 29, 29)
	searchFrame.BackgroundTransparency = 0.6
	searchFrame.Position = UDim2.new(0.06, 2, 0.085, 0)
	searchFrame.Size = UDim2.fromOffset(184, 32)
	searchFrame.ZIndex = 8

	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.Parent = searchFrame

	local uICorner1 = Instance.new("UICorner")
	uICorner1.Name = "UICorner"
	uICorner1.Parent = searchFrame

	local search = Instance.new("ImageButton")
	search.Name = "search"
	search.Image = "rbxassetid://3926305904"
	search.ImageColor3 = Color3.fromRGB(171, 171, 171)
	search.ImageRectOffset = Vector2.new(964, 324)
	search.ImageRectSize = Vector2.new(36, 36)
	search.BackgroundTransparency = 1
	search.Position = UDim2.fromScale(0.0815, 0.219)
	search.Size = UDim2.fromOffset(18, 18)
	search.ZIndex = 2
	search.Parent = searchFrame

	local SearchInput = Instance.new("TextBox")
	SearchInput.Name = "TextLabel"
	SearchInput.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
	SearchInput.Text = "Search Element"
	SearchInput.TextColor3 = Color3.fromRGB(193, 193, 193)
	SearchInput.TextSize = 14
	SearchInput.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	SearchInput.BackgroundTransparency = 1
	SearchInput.BorderColor3 = Color3.fromRGB(27, 42, 53)
	SearchInput.BorderSizePixel = 0
	SearchInput.Size = UDim2.fromScale(1, 1)
	SearchInput.Parent = searchFrame

		--[[
		SearchInput:GetPropertyChangedSignal('Text'):Connect(function()
			local InputText=string.upper(SearchInput.Text)

					for _,v in pairs(game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.SidebarHolder.TabHolder:GetChildren())do
						if v:IsA("Frame") and v.Name ~= 'Placeholder' and v.Name ~= 'UIListLayout' then
							if InputText==""or string.find(string.upper(v.TextLabel.Text),InputText)~=nil then
								v.Visible=true
							else
								v.Visible=false
							
						
					end
				end
			end
		end)
]]
	SearchInput:GetPropertyChangedSignal('Text'):Connect(function()
		local InputText=string.upper(SearchInput.Text)
		for _,page in ipairs(game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.HoldingSections:GetChildren()) do
			if page ~= 'UIListLayout' then
				for _,side in pairs(page:GetChildren()) do
					if side ~= "UIListLayout" then 
						for _,Section in pairs(side:GetChildren()) do
							if Section:IsA("Frame") and Section ~= "PlaceHolder" then  
								for _,Element in pairs(Section:GetChildren()) do

									if Element:IsA("Frame") and Element.Name ~= 'Placeholder'  then
										if InputText==""or string.find(string.upper(Element.Name),InputText)~=nil then
											Element.Visible=true

										else
											Element.Visible=false
										end 
									end 
								end 
							end 
						end
					end 
				end
			end
		end
	end)
	local uIStroke = Instance.new("UIStroke")
	uIStroke.Name = "UIStroke"
	uIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
	uIStroke.Color = Color3.fromRGB(42, 42, 42)
	uIStroke.Parent = searchFrame
	-- end 

	-- username_frame 
	local usernameFrame = Instance.new("Frame")
	usernameFrame.Parent = sidebarHolder
	usernameFrame.Name = "Username_frame"
	usernameFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	usernameFrame.BackgroundTransparency = 0.75
	usernameFrame.Position = UDim2.fromScale(0.09, 0.907)
	usernameFrame.Size = UDim2.fromOffset(171, 44)

	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.Parent = usernameFrame

	local imageLabel = Instance.new("ImageLabel")
	imageLabel.Name = "ImageLabel"
	imageLabel.Image = "rbxthumb://type=AvatarHeadShot&id=" .. game.Players.LocalPlayer.UserId .."&w=420&h=420" 

	imageLabel.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
	imageLabel.Position = UDim2.fromScale(0.0409, 0.148)
	imageLabel.Size = UDim2.fromOffset(30, 30)

	local uICorner1 = Instance.new("UICorner")
	uICorner1.Name = "UICorner"
	uICorner1.CornerRadius = UDim.new(0, 50)
	uICorner1.Parent = imageLabel

	local uIStroke = Instance.new("UIStroke")
	uIStroke.Name = "UIStroke"
	uIStroke.Color = Color3.fromRGB(50, 50, 50)
	uIStroke.Parent = imageLabel

	imageLabel.Parent = usernameFrame

	local textLabel = Instance.new("TextLabel")
	textLabel.Name = "TextLabel"
	textLabel.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
	textLabel.Text =game.Players.LocalPlayer.Name
	textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
	textLabel.TextSize = 11
	textLabel.TextXAlignment = Enum.TextXAlignment.Left
	textLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	textLabel.BackgroundTransparency = 1
	textLabel.Position = UDim2.fromScale(0.281, 0)
	textLabel.Size = UDim2.fromOffset(115, 44)
	textLabel.Parent = usernameFrame

	local uIStroke1 = Instance.new("UIStroke")
	uIStroke1.Name = "UIStroke"
	uIStroke1.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
	uIStroke1.Color = Color3.fromRGB(42, 42, 42)
	uIStroke1.Parent = usernameFrame
	usernameFrame = Instance.new("Frame")
	usernameFrame.Name = "Username_frame"
	usernameFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	usernameFrame.BackgroundTransparency = 0.75
	usernameFrame.Position = UDim2.fromScale(0.09, 0.907)
	usernameFrame.Size = UDim2.fromOffset(171, 44)

	local uICorner = Instance.new("UICorner")
	uICorner.Name = "UICorner"
	uICorner.Parent = usernameFrame

	local imageLabel = Instance.new("ImageLabel")
	imageLabel.Name = "ImageLabel"
	imageLabel.Image = "rbxassetid://12042414074"
	imageLabel.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
	imageLabel.Position = UDim2.fromScale(0.0409, 0.148)
	imageLabel.Size = UDim2.fromOffset(30, 30)

	local uICorner1 = Instance.new("UICorner")
	uICorner1.Name = "UICorner"
	uICorner1.CornerRadius = UDim.new(0, 50)
	uICorner1.Parent = imageLabel

	local uIStroke = Instance.new("UIStroke")
	uIStroke.Name = "UIStroke"
	uIStroke.Color = Color3.fromRGB(50, 50, 50)
	uIStroke.Parent = imageLabel

	imageLabel.Parent = usernameFrame

	local textLabel = Instance.new("TextLabel")
	textLabel.Name = "TextLabel"
	textLabel.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
	textLabel.Text = "we're the best ngl"
	textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
	textLabel.TextSize = 11
	textLabel.TextXAlignment = Enum.TextXAlignment.Left
	textLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	textLabel.BackgroundTransparency = 1
	textLabel.Position = UDim2.fromScale(0.281, 0)
	textLabel.Size = UDim2.fromOffset(115, 44)
	textLabel.Parent = usernameFrame

	local uIStroke1 = Instance.new("UIStroke")
	uIStroke1.Name = "UIStroke"
	uIStroke1.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
	uIStroke1.Color = Color3.fromRGB(42, 42, 42)
	uIStroke1.Parent = usernameFrame

	--end


	function window:Tab(Info) 
		local tab = {}
		Info = Info or {}
		Title = Info.Title or Info.title or Info.name or Info.Name or Info.text or Info.Text or "Tab"
		ImageId = Info.Image or Info.image or Info.ID or Info.id or "rbxassetid://3926305904"
		self.tabcount = self.tabcount + 1
		if self.tabcount == 1 then 
			self.first_tab = Title
		end

		local sectionHolders = Instance.new("ScrollingFrame")
		sectionHolders.Parent = holdingSections
		sectionHolders.Name =  Title--"SectionHolders"
		sectionHolders.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
		sectionHolders.ScrollBarImageTransparency = 1
		sectionHolders.ScrollBarThickness = 1
		sectionHolders.Active = true
		sectionHolders.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		sectionHolders.BackgroundTransparency = 1
		sectionHolders.BorderColor3 = Color3.fromRGB(0, 0, 0)
		sectionHolders.BorderSizePixel = 0
		sectionHolders.Position = UDim2.fromScale(0, 0,0, 0)
		sectionHolders.Size = UDim2.fromOffset(572, 567)
		sectionHolders.Visible = true 

		local uIListLayout = Instance.new("UIListLayout")
		uIListLayout.Name = "UIListLayout"
		uIListLayout.Padding = UDim.new(0, 1)
		--uIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
		uIListLayout.FillDirection = Enum.FillDirection.Horizontal
		uIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		uIListLayout.Parent = sectionHolders

		local tab1 = Instance.new("Frame")
		tab1.Name = "Tab1"
		tab1.Parent = tabHolder
		tab1.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
		tab1.BackgroundTransparency = 1 --0.5 
		tab1.Position = UDim2.fromScale(0.0983, 0.0291)
		tab1.Size = UDim2.fromOffset(180, 38)

		local Tab_detector = Instance.new("TextButton")
		Tab_detector.Parent = tab1
		Tab_detector.Name = "TextButton"
		Tab_detector.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
		Tab_detector.Text = ""
		Tab_detector.TextColor3 = Color3.fromRGB(0, 0, 0)
		Tab_detector.TextSize = 14
		Tab_detector.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		Tab_detector.BackgroundTransparency = 1
		Tab_detector.BorderColor3 = Color3.fromRGB(0, 0, 0)
		Tab_detector.BorderSizePixel = 0
		Tab_detector.Size = UDim2.fromScale(1, 1)

		local uICorner = Instance.new("UICorner")
		uICorner.Name = "UICorner"
		uICorner.Parent = tab1

		local textLabel = Instance.new("TextLabel")
		textLabel.Name = "TextLabel"
		textLabel.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
		textLabel.Text = Title
		textLabel.TextColor3 = Color3.fromRGB(151, 152, 152)
		textLabel.TextSize = 14
		textLabel.TextXAlignment = Enum.TextXAlignment.Left
		textLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		textLabel.BackgroundTransparency = 1
		textLabel.BorderColor3 = Color3.fromRGB(27, 42, 53)
		textLabel.BorderSizePixel = 0
		textLabel.Position = UDim2.fromScale(0.185, 0)
		textLabel.Size = UDim2.fromScale(0.815, 1)
		textLabel.Parent = tab1

		-- blame the retard oShy for these retarded naming too lazy and unnessecary to change 
		local home = Instance.new("ImageButton")
		home.Name = "home"
		home.Image = ImageId
		home.ImageColor3 = Color3.fromRGB(188, 188, 188)

		home.ImageRectOffset = Vector2.new(964, 204)
		home.ImageRectSize = Vector2.new(36, 36)
		home.BackgroundTransparency = 1
		home.Position = UDim2.fromScale(0.0566, 0.257)
		home.Size = UDim2.fromOffset(18, 18)
		home.ZIndex = 2
		home.Parent = tab1

		local left = Instance.new("Frame")
		left.Name = "Left"
		left.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		left.BackgroundTransparency = 1
		left.BorderColor3 = Color3.fromRGB(0, 0, 0)
		left.BorderSizePixel = 0
		--left.Position = UDim2.fromScale(-0.00179, -5.38e-08)
		left.Size = UDim2.fromOffset(287, 517)


		local placeholder = Instance.new("Frame")
		placeholder.Name = "Placeholder"
		placeholder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		placeholder.BackgroundTransparency = 1
		placeholder.BorderColor3 = Color3.fromRGB(0, 0, 0)
		placeholder.BorderSizePixel = 0
		placeholder.Size = UDim2.fromOffset(6, 6)
		placeholder.Parent = left

		local uIListLayout1 = Instance.new("UIListLayout")
		uIListLayout1.Name = "UIListLayout"
		uIListLayout1.Padding = UDim.new(0, 10)
		uIListLayout1.HorizontalAlignment = Enum.HorizontalAlignment.Center
		uIListLayout1.SortOrder = Enum.SortOrder.LayoutOrder
		uIListLayout1.Parent = left

		left.Parent = sectionHolders

		local right = Instance.new("Frame")
		right.Name = "Right"
		right.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		right.BackgroundTransparency = 1
		right.BorderColor3 = Color3.fromRGB(0, 0, 0)
		right.BorderSizePixel = 0
		--right.Position = UDim2.fromScale(0.494, -5.38e-08)
		right.Size = UDim2.fromOffset(278, 517)

		local placeholder = Instance.new("Frame")
		placeholder.Name = "Placeholder"
		placeholder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		placeholder.BackgroundTransparency = 1
		placeholder.BorderColor3 = Color3.fromRGB(0, 0, 0)
		placeholder.BorderSizePixel = 0
		placeholder.Size = UDim2.fromOffset(6, 6)
		placeholder.Parent = right

		local uIListLayout2 = Instance.new("UIListLayout")
		uIListLayout2.Name = "UIListLayout"
		uIListLayout2.Padding = UDim.new(0, 10)
		uIListLayout2.HorizontalAlignment = Enum.HorizontalAlignment.Left
		uIListLayout2.SortOrder = Enum.SortOrder.LayoutOrder
		uIListLayout2.Parent = right

		right.Parent = sectionHolders


		for i,v in pairs(holdingSections:GetChildren()) do 
			if v:IsA("ScrollingFrame") then 
				if v.Name == Title and self.first_tab == Title then 
					v.Visible = true
					ts:Create(home, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {ImageColor3 =color3RGB(255,255,255)}):Play()
					ts:Create(tab1, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency =0.5}):Play()
					ts:Create(textLabel, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(255,255,255)}):Play()

				elseif v.Name == Title and self.first_tab ~= Title then 
					v.Visible = false
					ts:Create(home, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {ImageColor3 =color3RGB(188,188,188)}):Play()
					ts:Create(textLabel, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(188,188,188)}):Play()
					ts:Create(tab1, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency =1}):Play()

				end
			end

		end

		Opened = false 

		Tab_detector.MouseButton1Click:Connect(function()

			--ts:Create(home, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {ImageColor3 =color3RGB(188,188,188)}):Play()
			--ts:Create(textLabel, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(188,188,188)}):Play()
			--ts:Create(tab1, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency =1}):Play()

			for _,v in pairs(game:GetService("CoreGui")["Grabiel'scsgocheat"].MainFrame.SidebarHolder.TabHolder:GetChildren()) do 
				if v.Name == "Tab1"  then 

					ts:Create(v.home, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {ImageColor3 =color3RGB(188,188,188)}):Play()
					ts:Create(v.TextLabel, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(188,188,188)}):Play()
					ts:Create(v, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency =1}):Play()


				end 
				ts:Create(home, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {ImageColor3 =color3RGB(255,255,255)}):Play()
				ts:Create(tab1, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency =0.5}):Play()
				ts:Create(textLabel, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(255,255,255)}):Play()


			end 
			for _,v in pairs(holdingSections:GetChildren()) do 
				if v:IsA("ScrollingFrame") then 
					v.Visible = false 

				end

			end
			sectionHolders.Visible = true

			--ts:Create(home, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {ImageColor3 =color3RGB(255,255,255)}):Play()
			--ts:Create(tab1, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundTransparency =0.5}):Play()
			--ts:Create(textLabel, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(255,255,255)}):Play()

			--home.ImageColor3 = color3RGB(255,255,255)
			--textLabel.TextColor3 = color3RGB(255,255,255)
			--tab1.BackgroundTransparency = 0.5
		end)
		tabTitle = Title
		function tab:Section(Info) 
			sec = {}
			Info = Info or {}
			local Side = Info.side or Info.Side or 1
			Title = Info.text or Info.Text or Info.Title or Info.title or Info.Name or Info.name or "Section"
			local side = Side == 1 and left or right

			local section = Instance.new("Frame")
			section.Name = "Section"
			section.BackgroundColor3 = Color3.fromRGB(36, 36, 36)
			section.BackgroundTransparency = 0.6
			section.BorderColor3 = Color3.fromRGB(27, 42, 53)
			--section.Position = UDim2.fromScale(0.041, 0.0175)
			section.Size = UDim2.fromOffset(270, 550)
			section.Parent = side
			local uICorner = Instance.new("UICorner")
			uICorner.Name = "UICorner"
			uICorner.Parent = section

			local placeHolder = Instance.new("Frame")
			placeHolder.Name = "PlaceHolder"
			placeHolder.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			placeHolder.Parent = section

			local sectionTitle = Instance.new("TextLabel")
			sectionTitle.Name = "SectionTitle"
			sectionTitle.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
			sectionTitle.Text =Title
			sectionTitle.TextColor3 = Color3.fromRGB(200,200,200)
			sectionTitle.TextSize = 14
			sectionTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			sectionTitle.BackgroundTransparency = 1
			sectionTitle.BorderColor3 = Color3.fromRGB(35, 35, 35)
			sectionTitle.BorderSizePixel = 0
			sectionTitle.Position = UDim2.fromScale(0.13, 0)
			sectionTitle.Size = UDim2.fromOffset(200, 29)

			local searchTopSeparator = Instance.new("Frame")
			searchTopSeparator.Name = "SearchTopSeparator"
			searchTopSeparator.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
			searchTopSeparator.BorderSizePixel = 0
			searchTopSeparator.Position = UDim2.fromScale(0, 1.01)
			searchTopSeparator.Size = UDim2.new(1, 0, 0, 1)
			searchTopSeparator.Parent = sectionTitle

			sectionTitle.Parent = section

			local uIStroke = Instance.new("UIStroke")
			uIStroke.Name = "UIStroke"
			uIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
			uIStroke.Color = Color3.fromRGB(42, 42, 42)
			uIStroke.Parent = section

			local uIListLayout_section = Instance.new("UIListLayout")
			uIListLayout_section.Name = "UIListLayout"
			uIListLayout_section.Padding = UDim.new(0, 10)
			uIListLayout_section.HorizontalAlignment = Enum.HorizontalAlignment.Center
			uIListLayout_section.SortOrder = Enum.SortOrder.LayoutOrder
			uIListLayout_section.Parent = section 

			uIListLayout_section:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
				section.Size = UDim2.new(0,270,0,uIListLayout_section.AbsoluteContentSize.Y + 10)
			end)


			function sec:Button(Info)
				local BUtton = {}
				Info = Info or {} 
				Button_title = Info.Title or Info.title or Info.Text or Info.text or Info.Name or Info.name or "Incorrect title value"
				callback = Info.Callback or Info.callback or function () end 
				local button = Instance.new("Frame")
				button.Name = Button_title
				button.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				button.BackgroundTransparency = 1
				button.BorderColor3 = Color3.fromRGB(0, 0, 0)
				button.BorderSizePixel = 0
				button.Position = UDim2.fromScale(0.337, 0.15)
				button.Size = UDim2.fromOffset(246, 28)
				button.Parent = section
				local uIStroke = Instance.new("UIStroke")
				uIStroke.Name = "UIStroke"
				uIStroke.Color = Color3.fromRGB(42, 42, 42)
				uIStroke.Parent = button

				local uICorner = Instance.new("UICorner")
				uICorner.Name = "UICorner"
				uICorner.CornerRadius = UDim.new(0, 6)
				uICorner.Parent = button

				local buttoNText = Instance.new("TextLabel")
				buttoNText.Name = "ButtoNText"
				buttoNText.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				buttoNText.Text = Button_title
				buttoNText.TextColor3 = Color3.fromRGB(182, 188, 188)
				buttoNText.TextSize = 12
				buttoNText.TextXAlignment = Enum.TextXAlignment.Left
				buttoNText.BackgroundColor3 = Color3.fromRGB(151, 152, 152)
				buttoNText.BackgroundTransparency = 1
				buttoNText.BorderColor3 = Color3.fromRGB(0, 0, 0)
				buttoNText.BorderSizePixel = 0
				buttoNText.Position = UDim2.fromScale(0.0488, 0)
				buttoNText.Size = udim2New(0, 233,0, 31)
				buttoNText.Parent = button

				local buttonImmage = Instance.new("ImageLabel")
				buttonImmage.Name = "ButtonImmage"
				buttonImmage.Image = "rbxassetid://8498776661"
				buttonImmage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				buttonImmage.BackgroundTransparency = 1
				buttonImmage.BorderColor3 = Color3.fromRGB(0, 0, 0)
				buttonImmage.BorderSizePixel = 0
				buttonImmage.Position = UDim2.fromScale(0.87, 0.143)
				buttonImmage.Size = UDim2.fromOffset(20, 20)
				buttonImmage.Parent = button

				local Button_Detector = Instance.new("TextButton")
				Button_Detector.Name = "Button_Detector"
				Button_Detector.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
				Button_Detector.Text = ""
				Button_Detector.TextColor3 = Color3.fromRGB(0, 0, 0)
				Button_Detector.TextSize = 14
				Button_Detector.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Button_Detector.BackgroundTransparency = 1
				Button_Detector.BorderColor3 = Color3.fromRGB(0, 0, 0)
				Button_Detector.BorderSizePixel = 0
				Button_Detector.Size = UDim2.fromScale(1, 1)
				Button_Detector.Parent = button

				Button_Detector.MouseButton1Click:Connect(function()
					callback()
					Button_Detector.BackgroundTransparency = 0.9
					wait(0.1)
					Button_Detector.BackgroundTransparency = 1
				end)
				return BUtton 

			end
			function sec:Toggle(Info)
				local TOGGLE = {}
				Value = Info.Default or Info.default or Info.Def or Info.def or false
				Info = Info or {}
				Toggle_Title = Info.Title or Info.title or Info.Text or Info.text or Info.Name or Info.name or "Incorrect title value"
				Callback = Info.callback or Info.Callback or function() end 
				local toggle = Instance.new("Frame")
				toggle.Name = Toggle_Title
				toggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				toggle.BackgroundTransparency = 1
				toggle.BorderColor3 = Color3.fromRGB(0, 0, 0)
				toggle.BorderSizePixel = 0
				toggle.Position = UDim2.fromScale(0.337, 0.15)
				toggle.Size = UDim2.fromOffset(246, 28)
				toggle.Parent = section


				local uICorner = Instance.new("UICorner")
				uICorner.Name = "UICorner"
				uICorner.CornerRadius = UDim.new(0, 6)
				uICorner.Parent = toggle

				local toggleText = Instance.new("TextLabel")
				toggleText.Name = "Toggle+1Text"
				toggleText.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				toggleText.Text = Toggle_Title
				toggleText.TextColor3 = Color3.fromRGB(151, 152, 152)
				toggleText.TextSize = 12
				toggleText.TextXAlignment = Enum.TextXAlignment.Left
				toggleText.BackgroundColor3 = Color3.fromRGB(151, 152, 152)
				toggleText.BackgroundTransparency = 1
				toggleText.BorderColor3 = Color3.fromRGB(0, 0, 0)
				toggleText.BorderSizePixel = 0
				toggleText.Position = UDim2.fromScale(0.0407, 0)
				toggleText.Size = UDim2.fromOffset(248, 28)
				toggleText.Parent = toggle

				local sWITC2HOLHD = Instance.new("Frame")
				sWITC2HOLHD.Name = "SWITC2HOLHD"
				sWITC2HOLHD.BackgroundColor3 = Color3.fromRGB(65, 66, 67)
				sWITC2HOLHD.BorderColor3 = Color3.fromRGB(0, 0, 0)
				sWITC2HOLHD.BorderSizePixel = 0
				sWITC2HOLHD.Position = udim2New(0.829, 0,0.107, 0)
				sWITC2HOLHD.Size = UDim2.fromOffset(41, 22)

				local uICorner1 = Instance.new("UICorner")
				uICorner1.Name = "UICorner"
				uICorner1.CornerRadius = UDim.new(0.5, 0)
				uICorner1.Parent = sWITC2HOLHD

				sWITC2HOLHD.Parent = toggle

				local cirlc12e2 = Instance.new("Frame")
				cirlc12e2.Name = "Cirlc12e2"
				cirlc12e2.BackgroundColor3 = Color3.fromRGB(95, 96, 96)
				cirlc12e2.BorderColor3 = Color3.fromRGB(0, 0, 0)
				cirlc12e2.BorderSizePixel = 0
				cirlc12e2.Position = udim2New(0, 2,0, 2)
				cirlc12e2.Size = UDim2.fromOffset(18, 18)

				local uICorner2 = Instance.new("UICorner")
				uICorner2.Name = "UICorner"
				uICorner2.CornerRadius = UDim.new(0.5, 0)
				uICorner2.Parent = cirlc12e2

				cirlc12e2.Parent = sWITC2HOLHD

				local Toggle_Detector = Instance.new("TextButton")
				Toggle_Detector.Name = "Toggle_Detector"
				Toggle_Detector.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
				Toggle_Detector.Text = ""
				Toggle_Detector.TextColor3 = Color3.fromRGB(0, 0, 0)
				Toggle_Detector.TextSize = 14
				Toggle_Detector.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Toggle_Detector.BackgroundTransparency = 1
				Toggle_Detector.BorderColor3 = Color3.fromRGB(0, 0, 0)
				Toggle_Detector.BorderSizePixel = 0
				Toggle_Detector.Size = UDim2.fromScale(1, 1)
				Toggle_Detector.Parent = toggle
				function TOGGLE:ToggleSwitch(Value)
					Callback(Value)
					ToggleIndicatorColor = Value == true and Color3.fromRGB(208, 206, 203) or Color3.fromRGB(95, 96, 96) 
					ToggleIndicatorPos = Value == true and  udim2New(1, -21,0.091, 0) or udim2New(0,2, 0.091, 0)
					Toggleframe_Color = Value == true and  Color3.fromRGB(88, 87, 86) or Color3.fromRGB(65, 66, 67) 
					toggletextcolor = Value == true and  Color3.fromRGB(255, 255, 255) or Color3.fromRGB(151, 152, 152) 
					ts:Create(toggleText, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =toggletextcolor}):Play()

					ts:Create(cirlc12e2, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundColor3 =ToggleIndicatorColor}):Play()
					ts:Create(cirlc12e2, TweenInfo.new(0.14, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Position =ToggleIndicatorPos}):Play()
					ts:Create(sWITC2HOLHD, TweenInfo.new(0.26, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {BackgroundColor3 =Toggleframe_Color}):Play()

				end
				Toggle_Detector.MouseButton1Click:Connect(function()
					Value = not Value 

					TOGGLE:ToggleSwitch(Value)
				end)

				TOGGLE:ToggleSwitch(Value)
				return TOGGLE
			end 

			function sec:Dropdown(Info) 
				local DropDown = {}
				local Info = Info or {}
				Dropdown_visible = false 
				local list = Info.List or Info.list or Info.Table or Info.table or {"option 1","option2"}
				dropdown_Title = Info.Title or Info.title or Info.text or Info.Text or Info.Name or Info.name or "Dropdown"
				Default = Info.Default or Info.default or list 
				Multi_dropdown = Info.Multi or Info.multi or false  
				local callback = Info.Callback or Info.callback or function() end
				local dropdown = Instance.new("Frame")
				dropdown.Name = dropdown_Title
				dropdown.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				dropdown.BackgroundTransparency = 1
				dropdown.BorderColor3 = Color3.fromRGB(0, 0, 0)
				dropdown.BorderSizePixel = 0
				dropdown.Position = UDim2.fromScale(0.0444, 0.384)
				dropdown.Size = UDim2.fromOffset(246, 28) -- 148 = y
				dropdown.Visible = true 
				dropdown.Parent = section

				local uIStroke = Instance.new("UIStroke")
				uIStroke.Name = "UIStroke"
				uIStroke.Color = Color3.fromRGB(42, 42, 42)
				uIStroke.Parent = dropdown

				local uICorner = Instance.new("UICorner")
				uICorner.Name = "UICorner"
				uICorner.CornerRadius = UDim.new(0, 6)
				uICorner.Parent = dropdown

				local dropdownText = Instance.new("TextLabel")
				dropdownText.Name = "DropdownText"
				dropdownText.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				dropdownText.Text = dropdown_Title .. ": " --.. Default
				dropdownText.TextColor3 = Color3.fromRGB(151, 152, 152)
				dropdownText.TextSize = 12
				dropdownText.TextXAlignment = Enum.TextXAlignment.Left
				dropdownText.BackgroundColor3 = Color3.fromRGB(151, 152, 152)
				dropdownText.BackgroundTransparency = 1
				dropdownText.BorderColor3 = Color3.fromRGB(0, 0, 0)
				dropdownText.BorderSizePixel = 0
				dropdownText.Position = UDim2.new(0, 12, 0, 0)
				dropdownText.Size =UDim2.new(233, 0, 0, 28) 
				dropdownText.Parent = dropdown

				local dropdownImage = Instance.new("ImageLabel")
				dropdownImage.Name = "DropdownImage"
				dropdownImage.Image = "rbxassetid://14395970362"
				dropdownImage.ImageColor3 = Color3.fromRGB(47, 47, 47)
				dropdownImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				dropdownImage.BackgroundTransparency = 1
				dropdownImage.BorderColor3 = Color3.fromRGB(0, 0, 0)
				dropdownImage.BorderSizePixel = 0
				dropdownImage.Position = UDim2.new(0.886, 0, 0, 6)
				dropdownImage.Size = UDim2.fromOffset(16, 16)
				dropdownImage.Parent = dropdown

				local dropdown_scrollingFrame = Instance.new("ScrollingFrame")
				dropdown_scrollingFrame.Name = "ScrollingFrame"
				dropdown_scrollingFrame.ScrollBarImageColor3 = Color3.fromRGB(0, 0, 0)
				dropdown_scrollingFrame.ScrollBarImageTransparency = 1
				dropdown_scrollingFrame.Active = true
				dropdown_scrollingFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				dropdown_scrollingFrame.BackgroundTransparency = 1
				dropdown_scrollingFrame.BorderColor3 = Color3.fromRGB(0, 0, 0)
				dropdown_scrollingFrame.BorderSizePixel = 0
				dropdown_scrollingFrame.Position = UDim2.fromOffset(0, 28)
				dropdown_scrollingFrame.Size = UDim2.new(1, 0, 0,110)
				dropdown_scrollingFrame.Parent = dropdown
				dropdown_scrollingFrame.Visible = false
				local uIListLayout = Instance.new("UIListLayout")
				uIListLayout.Name = "UIListLayout"
				uIListLayout.Padding = UDim.new(0, 4)
				uIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
				uIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
				uIListLayout.Parent = dropdown_scrollingFrame

				local frame = Instance.new("Frame")
				frame.Name = "Frame"
				frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				frame.BackgroundTransparency = 1
				frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
				frame.BorderSizePixel = 0
				frame.Size = UDim2.fromOffset(1, 1)
				frame.Parent = dropdown_scrollingFrame



				for i,v in pairs(list) do 
					local dropdownOption1 = Instance.new("Frame")
					dropdownOption1.Name = tostring(v)
					dropdownOption1.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
					dropdownOption1.BackgroundTransparency = 1
					dropdownOption1.BorderColor3 = Color3.fromRGB(0, 0, 0)
					dropdownOption1.BorderSizePixel = 0
					dropdownOption1.Position = UDim2.fromScale(0.0488, 0.286)
					dropdownOption1.Size = UDim2.fromOffset(211, 28)
					local Dropdown_option_detector = Instance.new("TextButton")
					Dropdown_option_detector.Name = "Dropdown_option_detector"
					Dropdown_option_detector.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
					Dropdown_option_detector.Text = ""
					Dropdown_option_detector.TextColor3 =color3RGB(151, 152, 152)
					Dropdown_option_detector.TextSize = 14
					Dropdown_option_detector.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					Dropdown_option_detector.BackgroundTransparency = 1
					Dropdown_option_detector.BorderColor3 = Color3.fromRGB(0, 0, 0)
					Dropdown_option_detector.BorderSizePixel = 0
					Dropdown_option_detector.Size = UDim2.fromScale(1, 1)
					Dropdown_option_detector.Parent = dropdownOption1
					local uIStroke = Instance.new("UIStroke")
					uIStroke.Name = "UIStroke"
					uIStroke.Color = Color3.fromRGB(42, 42, 42)
					uIStroke.Parent = dropdownOption1

					local uICorner = Instance.new("UICorner")
					uICorner.Name = "UICorner"
					uICorner.CornerRadius = UDim.new(0, 6)
					uICorner.Parent = dropdownOption1

					local optionText = Instance.new("TextLabel")
					optionText.Name = "option_text"
					optionText.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
					optionText.Text = tostring(v)
					optionText.TextColor3 = color3RGB(151, 152, 152)
					optionText.TextSize = 12
					optionText.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
					optionText.BackgroundTransparency = 1
					optionText.BorderColor3 = Color3.fromRGB(0, 0, 0)
					optionText.BorderSizePixel = 0
					optionText.Size = UDim2.fromScale(1, 1)
					optionText.Parent = dropdownOption1

					dropdownOption1.Parent = dropdown_scrollingFrame
					if Multi_dropdown then 
						Dropdown_option_detector.MouseButton1Click:Connect(function()
							if table.find(Default, v) then				
								table.remove(Default, table.find(Default, v))
								dropdownText.Text = dropdown_Title .. " : " .. table.concat(Default, ", ")
								--DropMain.Btn.Title.Text = text .. " - " .. table.concat(Dropdown.Value, ", ")
								callback(Default)
							else
								table.insert(Default, v)
								dropdownText.Text = dropdown_Title .. " : " .. table.concat(Default, ", ")

								--DropMain.Btn.Title.Text = text .. " - " .. table.concat(Dropdown.Value, ", ")
								callback(Default)

							end;			
						end)
					else 
						Dropdown_option_detector.MouseButton1Click:Connect(function()
							callback(v)
							dropdownText.Text = dropdown_Title .. ": " .. v

						end)


					end
				end 
				local Dropdown_Detector = Instance.new("TextButton")
				Dropdown_Detector.Name = "Dropdown_Detector"
				Dropdown_Detector.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
				Dropdown_Detector.Text = ""
				Dropdown_Detector.TextColor3 = Color3.fromRGB(0, 0, 0)
				Dropdown_Detector.TextSize = 14
				Dropdown_Detector.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Dropdown_Detector.BackgroundTransparency = 1
				Dropdown_Detector.BorderColor3 = Color3.fromRGB(0, 0, 0)
				Dropdown_Detector.BorderSizePixel = 0
				Dropdown_Detector.Size = UDim2.new(1, 0, 0,032, 116)
				Dropdown_Detector.Parent = dropdown
				function DropDown:DropdownState()
					Dropdown_visible = not Dropdown_visible
					dropdown_scrollingFrame.Visible = Dropdown_visible

					ts:Create(dropdown, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Size = Dropdown_visible == true and UDim2.fromOffset(246, 148) or UDim2.fromOffset(246, 28) }):Play()
					ts:Create(dropdownImage, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.InOut), {ImageColor3 = Dropdown_visible == true and color3RGB(255,255,255) or color3RGB(47,47,47) }):Play()
					ts:Create(dropdownText, TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.InOut), {TextColor3 = Dropdown_visible == true and color3RGB(200,200,200) or color3RGB(151, 152, 152) }):Play()

				end

				Dropdown_Detector.MouseButton1Click:Connect(function()
					DropDown:DropdownState()

				end)
				return DropDown 

				--	callback(Default)
			end



			function sec:Slider(Info) 
				local SLider = {}
				local Info = Info or {}
				local Slider_title = Info.Title or Info.title or Info.text or Info.Text or Info.Name or Info.name or "Walkspeed"
				local SliderValue = Info.Value or Info.value or Info.Val or Info.val or 0
				local Min = Info.Min or Info.min or 0
				local Max = Info.Max or Info.max or 100
				local Increment = Info.Increment or Info.increment or 1
				local Increment = 1 / Increment
				local CaLLBACAK = Info.Callback or Info.callback or function() end

				local slider = Instance.new("Frame")
				slider.Name = Slider_title
				slider.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				slider.BackgroundTransparency = 1
				slider.BorderColor3 = Color3.fromRGB(0, 0, 0)
				slider.BorderSizePixel = 0
				slider.Position = UDim2.fromScale(0.337, 0.15)
				slider.Size = UDim2.fromOffset(246, 28)
				slider.Parent = section
				local uICorner_slider = Instance.new("UICorner")
				uICorner_slider.Name = "UICorner"
				uICorner_slider.CornerRadius = UDim.new(0, 6)
				uICorner_slider.Parent = slider

				local sliderEXT = Instance.new("TextLabel")
				sliderEXT.Name = "Slider_tEXT"
				sliderEXT.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				sliderEXT.Text = Slider_title
				sliderEXT.TextColor3 = Color3.fromRGB(151, 152, 152)
				sliderEXT.TextSize = 12
				sliderEXT.TextXAlignment = Enum.TextXAlignment.Left
				sliderEXT.BackgroundColor3 = Color3.fromRGB(151, 152, 152)
				sliderEXT.BackgroundTransparency = 1
				sliderEXT.BorderColor3 = Color3.fromRGB(0, 0, 0)
				sliderEXT.BorderSizePixel = 0
				sliderEXT.Position = UDim2.fromScale(0.0407, 0)
				sliderEXT.Size = UDim2.fromOffset(248, 28)
				sliderEXT.Parent = slider

				local sliderBar = Instance.new("Frame")
				sliderBar.Name = "SliderBar"
				sliderBar.BackgroundColor3 = Color3.fromRGB(65, 66, 67)
				sliderBar.BackgroundTransparency = 0.2
				sliderBar.BorderColor3 = Color3.fromRGB(0, 0, 0)
				sliderBar.BorderSizePixel = 0
				sliderBar.Position = UDim2.fromScale(0.337, 0.426)
				sliderBar.Size = UDim2.fromOffset(112, 3)

				local uICorner_slider1 = Instance.new("UICorner")
				uICorner_slider1.Name = "UICorner"
				uICorner_slider1.CornerRadius = UDim.new(0, 6)
				uICorner_slider1.Parent = sliderBar

				local indicator_slider = Instance.new("Frame")
				indicator_slider.Name = "Indicator"
				indicator_slider.AnchorPoint = Vector2.new(0, 0.5)
				indicator_slider.BackgroundColor3 = Color3.fromRGB(240, 240, 240)
				indicator_slider.BorderSizePixel = 0
				indicator_slider.Position = UDim2.new(1.07, -20, 0.5, 0)
				indicator_slider.Size = UDim2.fromOffset(12, 12)

				local uICorner_slider2 = Instance.new("UICorner")
				uICorner_slider2.Name = "UICorner"
				uICorner_slider2.CornerRadius = UDim.new(1, 0)
				uICorner_slider2.Parent = indicator_slider

				indicator_slider.Parent = sliderBar

				sliderBar.Parent = slider

				local frame = Instance.new("Frame")
				frame.Name = "Frame"
				frame.BackgroundColor3 = Color3.fromRGB(36, 36, 36)
				frame.BorderColor3 = Color3.fromRGB(0, 0, 0)
				frame.BorderSizePixel = 0
				frame.BackgroundTransparency = 1
				frame.Position = UDim2.fromScale(0.844, 0.0143)
				frame.Size = UDim2.fromOffset(38, 27)

				local uICorner3 = Instance.new("UICorner")
				uICorner3.Name = "UICorner"
				uICorner3.CornerRadius = UDim.new(0, 5)
				uICorner3.Parent = frame

				local Slider_Value_Text = Instance.new("TextBox")
				Slider_Value_Text.Name = "Slider_Value_Text"
				Slider_Value_Text.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				Slider_Value_Text.Text = "100%"
				Slider_Value_Text.TextColor3 = Color3.fromRGB(240, 240, 240)
				Slider_Value_Text.TextSize = 12
				Slider_Value_Text.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Slider_Value_Text.BackgroundTransparency = 1
				Slider_Value_Text.Size = UDim2.fromScale(1, 1)
				Slider_Value_Text.Parent = frame

				local uIStroke_slider = Instance.new("UIStroke")
				uIStroke_slider.Name = "UIStroke"
				uIStroke_slider.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
				uIStroke_slider.Color = Color3.fromRGB(42, 42, 42)
				uIStroke_slider.Parent = frame

				frame.Parent = slider

				local Slider_Detector = Instance.new("TextButton")
				Slider_Detector.Name = "Slider_Detector"
				Slider_Detector.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
				Slider_Detector.Text = ""
				Slider_Detector.TextColor3 = Color3.fromRGB(0, 0, 0)
				Slider_Detector.TextSize = 14
				Slider_Detector.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Slider_Detector.BackgroundTransparency = 1
				Slider_Detector.BorderColor3 = Color3.fromRGB(0, 0, 0)
				Slider_Detector.BorderSizePixel = 0
				Slider_Detector.Size = udim2New(1,2,1,12)--UDim2.fromScale(1, 1)
				Slider_Detector.Parent = sliderBar

				function SLider:UpdateValue()
					Slider_Value_Text.Text = tostring(SliderValue)  --slider.suf

					local percent = 1- (Max - SliderValue) / (Max - Min) 
					ts:Create(indicator_slider, TweenInfo.new(0.15, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), {Position =udim2New(0, percent   * sliderBar.AbsoluteSize.X  ,0.5, 0)}):Play()
					--indicator_slider.Position = udim2New(0, percent  * sliderBar.AbsoluteSize.X,0.5, 0)
				end

				function SLider:SetValue(value)
					if typeof(value) ~= "number" then return end 
					SliderValue =  math.clamp(math.round(value * Increment) / Increment, Min, Max)

					SLider:UpdateValue()
					CaLLBACAK(SliderValue)
				end
				SLider:SetValue(SliderValue)



				Holding = false
				Slider_Detector.InputBegan:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then 
						Holding = true

						local pos =UDim2.new(math.clamp((input.Position.X - sliderBar.AbsolutePosition.X) / sliderBar.AbsoluteSize.X, 0, 1),-6,-1.30499995,0)

						local SliderV = math.floor(((pos.X.Scale * Max) / Max) * (Max - Min) + Min)

						SLider:SetValue(SliderV)
					end 
				end)
				Slider_Detector.InputChanged:Connect(function(input)
					if  input.UserInputType == Enum.UserInputType.MouseMovement and Holding == true   then 
						local pos =UDim2.new(math.clamp((input.Position.X - sliderBar.AbsolutePosition.X) / sliderBar.AbsoluteSize.X, 0, 1),-6,-1.30499995,0)


						local SliderV = math.floor(((pos.X.Scale * Max) / Max) * (Max - Min) + Min)
						SLider:SetValue(SliderV)
					end 
				end) 
				Slider_Detector.InputEnded:Connect(function(input)
					if  input.UserInputType == Enum.UserInputType.MouseButton1 and Holding == true then 
						Holding = false 
						local pos =UDim2.new(math.clamp((input.Position.X - sliderBar.AbsolutePosition.X) / sliderBar.AbsoluteSize.X, 0, 1),-6,-1.30499995,0)


						local SliderV = math.floor(((pos.X.Scale * Max) / Max) * (Max - Min) + Min)
						SLider:SetValue(SliderV)

					end
				end)


				Slider_Value_Text.FocusLost:Connect(function()

					SLider:SetValue(tonumber(Slider_Value_Text.Text))
				end)
				return SLider 
			end
			function sec:TextLabel(Info)
				local Info = Info or {} 
				local Text = Info.Text or Info.text or Info.Title or Info.title or "Label"


				local label = Instance.new("Frame")
				label.Name = "Label"
				label.AutomaticSize = Enum.AutomaticSize.Y
				label.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				label.BackgroundTransparency = 1
				label.BorderColor3 = Color3.fromRGB(0, 0, 0)
				label.BorderSizePixel = 0
				label.Position = UDim2.fromScale(0.337, 0.15)
				label.Size = UDim2.fromOffset(246, 28)
				label.Parent = section 
				local uIStroke = Instance.new("UIStroke")
				uIStroke.Name = "UIStroke"
				uIStroke.Color = Color3.fromRGB(42, 42, 42)
				uIStroke.Parent = label

				local uICorner = Instance.new("UICorner")
				uICorner.Name = "UICorner"
				uICorner.CornerRadius = UDim.new(0, 6)
				uICorner.Parent = label

				local title = Instance.new("TextLabel")
				title.Name = "Title"
				title.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				title.LineHeight = 1.08
				title.RichText = true
				title.Text =Text

				title.TextColor3 = Color3.fromRGB(200, 200, 200)
				title.TextSize = 13
				title.TextWrapped = true
				title.TextXAlignment = Enum.TextXAlignment.Left
				title.AnchorPoint = Vector2.new(0.5, 0.5)
				title.AutomaticSize = Enum.AutomaticSize.Y
				title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				title.BackgroundTransparency = 1
				title.BorderColor3 = Color3.fromRGB(27, 42, 53)
				title.Position = UDim2.new(0.508, 0,0.5, 0)
				title.Size = UDim2.new(0.934, 0,1, 0)
				title.Parent = label

			end 
			function sec:Keybind(Info)
				local kEybind = {}
				local Info = Info or {}
				local Mode = Info.Mode or Info.mode or "Toggle"
				local keybind_default = Info.Default or Info.default or Info.Def or Info.def or Enum.KeyCode.Q
				local Keybind_Title = Info.Title or Info.title or Info.Text or Info.text or Info.Name or Info.name or "Textbox"
				local Keybind_callback = Info.Callback or Info.callback or function() end 
				local Keybinding,Holding,keybindValue = false,false,false 
				local holdmode =   Mode == "Hold" and true or false 
				local togglemode = Mode == "Toggle" and true or false 
				local short_keybind_names = {["MouseButton1"] = "MB1", ["MouseButton2"] = "MB2", ["MouseButton3"] = "MB3", ["Insert"] = "INS", ["LeftAlt"] = "LALT", ["LeftControl"] = "LC", ["LeftShift"] = "LS", ["RightAlt"] = "RALT", ["RightControl"] = "RC", ["RightShift"] = "RS", ["CapsLock"] = "CAPS", ["Return"] = "RET", ["Backspace"] = "BSP", ["BackSlash"] = "BS"}

				local WhitelistedMouse = {Enum.UserInputType.MouseButton1, Enum.UserInputType.MouseButton2,Enum.UserInputType.MouseButton3}
				local BlacklistedKeys = {Enum.KeyCode.Unknown,Enum.KeyCode.W,Enum.KeyCode.A,Enum.KeyCode.S,Enum.KeyCode.D,Enum.KeyCode.Up,Enum.KeyCode.Left,Enum.KeyCode.Down,Enum.KeyCode.Right,Enum.KeyCode.Slash,Enum.KeyCode.Tab,Enum.KeyCode.Backspace,Enum.KeyCode.Escape}

				local keybind = Instance.new("Frame")
				keybind.Name = Keybind_Title
				keybind.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				keybind.BackgroundTransparency = 1
				keybind.BorderColor3 = Color3.fromRGB(0, 0, 0)
				keybind.BorderSizePixel = 0
				keybind.Position = UDim2.fromScale(0.0444, 0.251)
				keybind.Size = UDim2.fromOffset(246, 28)
				keybind.Parent = section 

				local keybindText = Instance.new("TextLabel")
				keybindText.Name = "Keybind_text"
				keybindText.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				keybindText.Text = Keybind_Title
				keybindText.TextColor3 =Color3.fromRGB(151, 152, 152)
				keybindText.TextSize = 12
				keybindText.TextXAlignment = Enum.TextXAlignment.Left
				keybindText.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				keybindText.BackgroundTransparency = 1
				keybindText.BorderColor3 = Color3.fromRGB(0, 0, 0)
				keybindText.BorderSizePixel = 0
				keybindText.Position = UDim2.fromScale(0.0488, 0.0875)
				keybindText.Size = UDim2.fromOffset(233, 25)
				keybindText.Parent = keybind

				local keybindFrame = Instance.new("Frame")
				keybindFrame.Name = "KeybindFrame"
				keybindFrame.AutomaticSize = Enum.AutomaticSize.X
				keybindFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				keybindFrame.BackgroundTransparency = 1
				keybindFrame.BorderColor3 = Color3.fromRGB(0, 0, 0)
				keybindFrame.BorderSizePixel = 0
				keybindFrame.Position = UDim2.fromScale(0.80, 0.1)
				keybindFrame.Size = UDim2.fromOffset(40, 20)

				local uICorner = Instance.new("UICorner")
				uICorner.Name = "UICorner"
				uICorner.CornerRadius = UDim.new(0, 6)
				uICorner.Parent = keybindFrame

				local uIStroke = Instance.new("UIStroke")
				uIStroke.Name = "UIStroke"
				uIStroke.Color = Color3.fromRGB(42, 42, 42)
				uIStroke.Parent = keybindFrame

				local keybindbutotn = Instance.new("TextButton")
				keybindbutotn.Name = "Keybindbutotn"
				keybindbutotn.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				keybindbutotn.Text = "iooppoop"
				keybindbutotn.TextColor3 = Color3.fromRGB(216, 216, 216)
				keybindbutotn.TextSize = 12
				keybindbutotn.TextWrapped = true
				keybindbutotn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				keybindbutotn.BackgroundTransparency = 1
				keybindbutotn.BorderColor3 = Color3.fromRGB(0, 0, 0)
				keybindbutotn.BorderSizePixel = 0
				keybindbutotn.Size = UDim2.fromScale(1, 1)
				keybindbutotn.Parent = keybindFrame

				keybindFrame.Parent = keybind

				local uIStroke1 = Instance.new("UIStroke")
				uIStroke1.Name = "UIStroke"
				uIStroke1.Color = Color3.fromRGB(42, 42, 42)
				uIStroke1.Parent = keybind

				local uICorner1 = Instance.new("UICorner")
				uICorner1.Name = "UICorner"
				uICorner1.CornerRadius = UDim.new(0, 6)
				uICorner1.Parent = keybind
				function kEybind:CheckKey(tab, key)
					for i, v in next, tab do
						if v == key then
							return true
						end
					end
				end
				function kEybind:Setkey(Key)
					Keybinding = false
					keybind_default_text = tostring(Key.Name) or tostring(keybind_default.Name)
					keybind_default = Key.Name
					keybindbutotn.Text = short_keybind_names[keybind_default_text] or keybind_default_text:upper() 
				end
				kEybind:Setkey(keybind_default)
				keybindbutotn.MouseButton1Click:Connect(function()
					if Keybinding ~= true then 
						Keybinding = true
						keybindbutotn.Text = "..."

					end
				end)

				utility:Connect(uis.InputBegan, function(input)

					if (Input.KeyCode.Name == keybind_default or Input.UserInputType.Name == keybind_default) and not Keybinding then
						if holdmode then
							Holding = true
							Keybind_callback(Holding)
						elseif not Keybinding and togglemode then 
							keybindValue = not keybindValue
							Keybind_callback(keybindValue)
						end
					elseif Keybinding then
						local key 
						pcall(function()
							if not kEybind:CheckKey(BlacklistedKeys, Input.KeyCode) then
								key = Input.KeyCode
							end
						end)
						pcall(function()
							if kEybind:CheckKey(WhitelistedMouse, Input.UserInputType) and not Key then

								key = Input.UserInputType
							end
						end)
						key = key or keybind_default
						kEybind:Setkey(key)
					end
				end)

				utility:Connect(uis.InputEnded, function(input)
					if Input.KeyCode.Name ==keybind_default or Input.UserInputType.Name ==keybind_default then
						if holdmode and Holding then
							Holding = false
							Keybind_callback(Holding)
						end
					end
				end)
				return kEybind 
			end
			function sec:Textbox(Info)
				local tExtbox = {}
				local Info = Info or {}
				local Textbox_default = Info.Default or Info.default or Info.Def or Info.def or "Text"
				local Textbox_Title = Info.Title or Info.title or Info.Text or Info.text or Info.Name or Info.name or "Textbox"
				local Textbox_callback = Info.Callback or Info.callback or function() end 


				local textbox = Instance.new("Frame")
				textbox.Name = Textbox_Title
				textbox.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				textbox.BackgroundTransparency = 1
				textbox.BorderColor3 = Color3.fromRGB(0, 0, 0)
				textbox.BorderSizePixel = 0
				textbox.Position = UDim2.fromScale(0.337, 0.15)
				textbox.Size = UDim2.fromOffset(246, 28)
				textbox.Parent = section 
				local textboxtext = Instance.new("TextLabel")
				textboxtext.Name = "Textboxtext"
				textboxtext.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				textboxtext.Text = Textbox_Title
				textboxtext.TextColor3 =Color3.fromRGB(151, 152, 152)
				textboxtext.TextSize = 12
				textboxtext.TextXAlignment = Enum.TextXAlignment.Left
				textboxtext.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				textboxtext.BackgroundTransparency = 1
				textboxtext.BorderColor3 = Color3.fromRGB(0, 0, 0)
				textboxtext.BorderSizePixel = 0
				textboxtext.Position = UDim2.fromScale(0.0488, 0)
				textboxtext.Size = UDim2.fromOffset(237, 28)
				textboxtext.Parent = textbox

				local textboxinput = Instance.new("Frame")
				textboxinput.Name = "textboxinput"
				textboxinput.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				textboxinput.BackgroundTransparency = 1
				textboxinput.BorderColor3 = Color3.fromRGB(0, 0, 0)
				textboxinput.BorderSizePixel = 0
				textboxinput.Position = UDim2.fromScale(0.431, 0.14)
				textboxinput.Size = UDim2.fromOffset(131, 20)

				local uICorner_textbox = Instance.new("UICorner")
				uICorner_textbox.Name = "UICorner"
				uICorner_textbox.CornerRadius = UDim.new(0, 6)
				uICorner_textbox.Parent = textboxinput

				local uIStroke_textbox = Instance.new("UIStroke")
				uIStroke_textbox.Name = "UIStroke"
				uIStroke_textbox.Color = Color3.fromRGB(42, 42, 42)
				uIStroke_textbox.Parent = textboxinput

				local textTextbox = Instance.new("TextBox")
				textTextbox.Name = "TextTextbox"
				textTextbox.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				textTextbox.Text = Textbox_default
				textTextbox.TextColor3 = Color3.fromRGB(216, 216, 216)
				textTextbox.TextSize = 12
				textTextbox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				textTextbox.BackgroundTransparency = 1
				textTextbox.BorderColor3 = Color3.fromRGB(0, 0, 0)
				textTextbox.BorderSizePixel = 0
				textTextbox.Size = UDim2.fromScale(1, 1)
				textTextbox.Parent = textboxinput
				textTextbox.ClearTextOnFocus = false 

				textboxinput.Parent = textbox

				local uIStroke_textbox1 = Instance.new("UIStroke")
				uIStroke_textbox1.Name = "UIStroke"
				uIStroke_textbox1.Color = Color3.fromRGB(42, 42, 42)
				uIStroke_textbox1.Parent = textbox

				local uICorner_textbox1 = Instance.new("UICorner")
				uICorner_textbox1.Name = "UICorner"
				uICorner_textbox1.CornerRadius = UDim.new(0, 6)
				uICorner_textbox1.Parent = textbox

				textTextbox.FocusLost:Connect(function()
					local text = textTextbox.Text

					return Textbox_callback(text)
				end)
				return tExtbox 
			end


			function sec:Colorpicker(Info) 

				local Info = Info or {}
				Val = Info.Value or Info.value or Info.Val or Info.val or color3RGB(255,255,255)
				colorpicker_title = Info.Title or Info.title or Info.text or Info.Text or Info.Name or Info.name or "Invalid"
				CallBack = Info.Callback or Info.callback or function() end 

				local colorpicker = Instance.new("Frame")
				colorpicker.Name = colorpicker_title
				colorpicker.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
				colorpicker.BackgroundTransparency = 1
				colorpicker.BorderColor3 = Color3.fromRGB(0, 0, 0)
				colorpicker.BorderSizePixel = 0
				colorpicker.Position = UDim2.fromScale(0.337, 0.15)
				colorpicker.Size = UDim2.fromOffset(246, 28)--UDim2.fromOffset(246, 32)
				colorpicker.Parent = section

				local uIStroke = Instance.new("UIStroke")
				uIStroke.Name = "UIStroke"
				uIStroke.Color = Color3.fromRGB(42, 42, 42)
				uIStroke.Parent = colorpicker

				local uICorner = Instance.new("UICorner")
				uICorner.Name = "UICorner"
				uICorner.CornerRadius = UDim.new(0, 6)
				uICorner.Parent = colorpicker

				local colorpickerText = Instance.new("TextLabel")
				colorpickerText.Name = "Colorpicker_text"
				colorpickerText.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				colorpickerText.Text = colorpicker_title
				colorpickerText.TextColor3 = Color3.fromRGB(151, 152, 152)
				colorpickerText.TextSize = 12
				colorpickerText.TextXAlignment = Enum.TextXAlignment.Left
				colorpickerText.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				colorpickerText.BackgroundTransparency = 1
				colorpickerText.BorderColor3 = Color3.fromRGB(0, 0, 0)
				colorpickerText.BorderSizePixel = 0
				colorpickerText.Position = UDim2.new(0.041, 0, 0, 1)
				colorpickerText.Size = UDim2.fromOffset(233, 28)
				colorpickerText.Parent = colorpicker

				local Colorpicker_image = Instance.new("ImageLabel")
				Colorpicker_image.Name = "Colorpicker_image"
				Colorpicker_image.Image = "rbxassetid://8604555937"
				Colorpicker_image.ImageColor3 = Val
				Colorpicker_image.BackgroundColor3 = Val
				Colorpicker_image.BackgroundTransparency = 1
				Colorpicker_image.BorderColor3 = Color3.fromRGB(0, 0, 0)
				Colorpicker_image.BorderSizePixel = 0
				Colorpicker_image.Position = UDim2.fromOffset(214, 5)
				Colorpicker_image.Size = UDim2.fromOffset(20, 20)
				Colorpicker_image.Parent = colorpicker


				local Colorpicker_Detector = Instance.new("TextButton")
				Colorpicker_Detector.Name = "Colorpicker_Detector"
				Colorpicker_Detector.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json")
				Colorpicker_Detector.Text = ""
				Colorpicker_Detector.TextColor3 = Color3.fromRGB(0, 0, 0)
				Colorpicker_Detector.TextSize = 14
				Colorpicker_Detector.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Colorpicker_Detector.BackgroundTransparency = 1
				Colorpicker_Detector.BorderColor3 = Color3.fromRGB(0, 0, 0)
				Colorpicker_Detector.BorderSizePixel = 0
				Colorpicker_Detector.Size = UDim2.new(1, 0, 0,032, 116)
				Colorpicker_Detector.Parent = colorpicker
				-- colorpicker >> 
				local colorpickerMain = Instance.new("Frame")
				colorpickerMain.Name = "Colorpicker_Main"
				colorpickerMain.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				colorpickerMain.BackgroundTransparency = 1
				colorpickerMain.BorderColor3 = Color3.fromRGB(0, 0, 0)
				colorpickerMain.BorderSizePixel = 0
				colorpickerMain.Position = UDim2.fromOffset(0, 28)
				colorpickerMain.Size = UDim2.fromOffset(245, 156)
				colorpickerMain.Parent = colorpicker
				colorpickerMain.Visible = false 
				local colorValue = Instance.new("Frame")
				colorValue.Name = "Color_value"
				colorValue.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				colorValue.BackgroundTransparency = 1
				colorValue.BorderColor3 = Color3.fromRGB(0, 0, 0)
				colorValue.BorderSizePixel = 0
				colorValue.Position = UDim2.fromScale(0.354, 0.81)
				colorValue.Size = UDim2.fromOffset(72, 26)

				local textLabel = Instance.new("TextLabel")
				textLabel.Name = "TextLabel"
				textLabel.FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json")
				textLabel.Text = "1,1,1"
				textLabel.TextColor3 = Color3.fromRGB(216, 216, 216)
				textLabel.TextSize = 12
				textLabel.BackgroundColor3 = Color3.fromRGB(27, 27, 27)
				textLabel.BackgroundTransparency = 1
				textLabel.BorderColor3 = Color3.fromRGB(0, 0, 0)
				textLabel.BorderSizePixel = 0
				textLabel.Size = UDim2.fromScale(1, 1)
				textLabel.Parent = colorValue

				local uICorner = Instance.new("UICorner")
				uICorner.Name = "UICorner"
				uICorner.CornerRadius = UDim.new(0, 6)
				uICorner.Parent = colorValue

				local uIStroke = Instance.new("UIStroke")
				uIStroke.Name = "UIStroke"
				uIStroke.Color = Color3.fromRGB(42, 42, 42)
				uIStroke.Parent = colorValue

				colorValue.Parent = colorpickerMain

				local sVSeEction = Instance.new("ImageButton")
				sVSeEction.Name = "SV_se;ection"
				sVSeEction.Image = "rbxassetid://11970108040"
				sVSeEction.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
				sVSeEction.BorderColor3 = Color3.fromRGB(50, 50, 50)
				sVSeEction.Position = UDim2.fromScale(0.0952, 0.0771)
				sVSeEction.Size = UDim2.fromOffset(180, 107)
				sVSeEction.AutoButtonColor = false

				local sVSlider = Instance.new("Frame")
				sVSlider.Name = "SV_slider"
				sVSlider.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				sVSlider.BackgroundTransparency = 1
				sVSlider.Position = UDim2.fromScale(0.961, 0.0187)
				sVSlider.Size = UDim2.fromOffset(7, 7)

				local uICorner1 = Instance.new("UICorner")
				uICorner1.Name = "UICorner"
				uICorner1.CornerRadius = UDim.new(0, 100)
				uICorner1.Parent = sVSlider

				local uIStroke1 = Instance.new("UIStroke")
				uIStroke1.Name = "UIStroke"
				uIStroke1.Color = Color3.fromRGB(255, 255, 255)
				uIStroke1.Parent = sVSlider

				sVSlider.Parent = sVSeEction

				sVSeEction.Parent = colorpickerMain

				local hUESelection = Instance.new("ImageButton")
				hUESelection.Name = "HUE_selection"
				hUESelection.ImageColor3 = color3RGB(255,255,255)
				hUESelection.Image = "rbxassetid://11970136481"
				hUESelection.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				hUESelection.BorderColor3 = Color3.fromRGB(50, 50, 50)
				hUESelection.Position = UDim2.fromScale(0.868, 0.0771)
				hUESelection.Size = UDim2.fromOffset(15, 107)

				local Hslider = Instance.new("Frame")
				Hslider.Name = "Slider"
				Hslider.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
				Hslider.BorderColor3 = Color3.fromRGB(0, 0, 0)
				Hslider.Position = UDim2.fromScale(-0.133, -0.00935)
				Hslider.Size = UDim2.fromOffset(19, 3)
				Hslider.Parent = hUESelection

				hUESelection.Parent = colorpickerMain

				local Colorpic = {}

				function Colorpic:openColorpicker()
					colorpickerMain.Visible = true 
					--colorpicker.Size = UDim2.fromOffset(246, 187)--UDim2.fromOffset(246, 32)
					--colorpickerText.TextColor3 = Color3.fromRGB(255, 255, 255)
					ts:Create(colorpickerText, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(255,255,255)}):Play()
					ts:Create(colorpicker, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Size = UDim2.fromOffset(246, 187)}):Play()

				end 

				function Colorpic:Closecolorpicker()
					colorpickerMain.Visible = false  
					--colorpicker.Size = UDim2.fromOffset(246, 28)--UDim2.fromOffset(246, 32)
					--colorpickerText.TextColor3 = Color3.fromRGB(151, 152, 152)
					ts:Create(colorpickerText, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {TextColor3 =color3RGB(151, 152, 152)}):Play()
					ts:Create(colorpicker, TweenInfo.new(0.2, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {Size = UDim2.fromOffset(246, 28)}):Play()

				end 

				Colorpicker_Detector.MouseButton1Click:Connect(function()
					if colorpickerMain.Visible == false then 
						Colorpic:openColorpicker()
					else
						Colorpic:Closecolorpicker()		
					end
				end)
				function Colorpic:UpdateColorPicker()
					if colorpickerMain.Visible == true then 
						Colorpicker_image.ImageColor3 = Color3.fromHSV(ColorH, ColorS, ColorV)
						R,G,B = utility:ToRGB(Colorpicker_image.ImageColor3)
						sVSeEction.BackgroundColor3 = Color3.fromHSV(ColorH, 1, 1)
						textLabel.Text = tostring(math.floor(R)) .. "," .. tostring(math.floor(G)) ..  "," ..tostring(math.floor(B))
						-- sVSeEction.BackgroundColor3 =  Color3.fromHSV(ColorH, ColorS, 1 )
						-- local R,G,B = ColorH:ToHex()
						--  local HEX = Colorpickerpreview.BackgroundColor3:ToHex()

						CallBack(Colorpicker_image.ImageColor3)
					end
				end 
				ColorH = 1 - (math.clamp(Hslider.AbsolutePosition.Y - hUESelection.AbsolutePosition.Y, 0, hUESelection.AbsoluteSize.Y) / hUESelection.AbsoluteSize.Y)
				ColorS = (math.clamp(sVSlider.AbsolutePosition.X - sVSeEction.AbsolutePosition.X, 0, sVSeEction.AbsoluteSize.X) / sVSeEction.AbsoluteSize.X)
				ColorV = 1 - (math.clamp(sVSlider.AbsolutePosition.Y - sVSeEction.AbsolutePosition.Y, 0, sVSeEction.AbsoluteSize.Y) / sVSeEction.AbsoluteSize.Y)


				sVSeEction.InputBegan:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if ColorInput then
							ColorInput:Disconnect()
						end
						ColorInput = rs.RenderStepped:Connect(function()
							local ColorX = (math.clamp(Mouse.X - sVSeEction.AbsolutePosition.X, 0, sVSeEction.AbsoluteSize.X) / sVSeEction.AbsoluteSize.X)
							local ColorY = (math.clamp(Mouse.Y - sVSeEction.AbsolutePosition.Y, 0, sVSeEction.AbsoluteSize.Y) / sVSeEction.AbsoluteSize.Y)
							sVSlider.Position = UDim2.new(ColorX, 0, ColorY, 0)
							ColorS = ColorX
							ColorV = 1 - ColorY
							Colorpic:UpdateColorPicker()
						end)
					end
				end)

				sVSeEction.InputEnded:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if ColorInput then
							ColorInput:Disconnect()
						end
					end
				end)




				hUESelection.InputBegan:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if HueInput then
							HueInput:Disconnect()
						end

						HueInput = rs.RenderStepped:Connect(function()
							local HueY = (math.clamp(Mouse.Y - hUESelection.AbsolutePosition.Y, 0, hUESelection.AbsoluteSize.Y) / hUESelection.AbsoluteSize.Y)

							Hslider.Position =  UDim2.new(-0.133, 0, HueY, 0)

							ColorH =  HueY


							Colorpic:UpdateColorPicker()
						end)
					end
				end)

				hUESelection.InputEnded:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						if HueInput then
							HueInput:Disconnect()
						end
					end



				end)
				Colorpicker_image.ImageColor3 =Val
				CallBack(Colorpicker_image.ImageColor3)
			end
			return sec
		end
		return tab  
	end
	return window
	--return window,tab,sec
end

local Window = Library:Window()
--local Tab2 = Window:Tab()
local Tab2 = Window:Tab({Name = "Home"})
local Tab4 = Window:Tab({Name = "Aiming"})
local section4 = Tab4:Section({side = 2, title = "Section"})
local section42 = Tab4:Section({side = 2, title = "Section"})

local section1 = Tab4:Section({side = 1, title = "Section"})
local toggle = section1:Toggle({def = false, callback = function(a)
	print(a)
end})
local toggle = section1:Toggle({def = false, callback = function(a)
	print(a)
end})
section1:Colorpicker({callback = function(a)
	print(a)
end})
section1:Colorpicker({callback = function(a)
	print(a)
end})
local Dropdown = section1:Dropdown({Title = "MultiDropdown", Table = {"1","2"}, Default = {"1","2"},Multi = true, callback = function(a)
	print(a)
end})

section1:Dropdown({Title = "Dropdown", Table = {"1","2"},Default = {"1"}, Multi = false,  callback = function(a)
	print(a)
end})
section1:Slider({callback = function(a)
	print(a)
end})
section1:Slider({callback = function(a)
	print(a)
end})
section1:TextLabel({Text = "adwadwaszdczxc"})
section1:Button({callback = function()
	print("aa")
end})
section1:Textbox({callback = function(e)
	print(e)
end})
section1:Keybind({ mode = "Hold", callback = function(e)
	print(e)
end})
