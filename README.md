
local function CoreGui()
    do
        if game:GetService("CoreGui"):FindFirstChild("NeroMT") then
           game:GetService("CoreGui"):FindFirstChild("NeroMT"):Destroy()
        else return CoreGui
        end
        if game:GetService("CoreGui"):FindFirstChild("NERO") then
           game:GetService("CoreGui"):FindFirstChild("NERO"):Destroy()
        else return CoreGui
        end
    end
end

pcall(function()
   CoreGui()
end)

local NeroMT = Instance.new("ScreenGui")
local NeroCorner = Instance.new("UICorner")
local NeroButton = Instance.new("TextButton")
NeroMT.Name = "NeroMT"
NeroMT.Parent = game.CoreGui
NeroMT.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
NeroCorner.Name = "NeroCorner"
NeroCorner.Parent = NeroButton
NeroButton.Name = "NeroButton"
NeroButton.Parent = NeroMT
NeroButton.BackgroundColor3 = Color3.fromRGB(30,20,20)
NeroButton.BackgroundTransparency = 0.1
NeroButton.BorderSizePixel = 0
NeroButton.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
NeroButton.Size = UDim2.new(0, 50, 0, 50)
NeroButton.Font = Enum.Font.SourceSans
NeroButton.TextColor3 = Color3.fromRGB(0, 0, 0)
NeroButton.Text = ""
NeroButton.TextSize = 14.000
NeroButton.Draggable = true
NeroButton.MouseButton1Click:Connect(function()
game.CoreGui:FindFirstChild("NERO").Enabled = not game.CoreGui:FindFirstChild("NERO").Enabled
end)




getgenv().Configui = {
 ["SchemeColor"] =  Color3.fromRGB(255,0,0),
 ["Background"] =  Color3.fromRGB(61, 61, 61),
 ["Header"] =  Color3.fromRGB(41,41, 41),
 ["TextColor"] =  Color3.fromRGB(255,255,255)
}

local PlusNero = {
	Themes = {
        Original = {
            SchemeColor = getgenv().Configui['SchemeColor'],
            Background = getgenv().Configui['Background'],
            Header = getgenv().Configui['Header'],
            TextColor = getgenv().Configui['TextColor']
        }
    }
}

local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local Mouse = LocalPlayer:GetMouse()

local function MakeTitle(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil

	local function Update(input)
		local Delta = input.Position - DragStart
		local pos =
			UDim2.new(
				StartPosition.X.Scale,
				StartPosition.X.Offset + Delta.X,
				StartPosition.Y.Scale,
				StartPosition.Y.Offset + Delta.Y
			)
		object.Position = pos
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if
				input.UserInputType == Enum.UserInputType.MouseMovement or
					input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = input
			end
		end
	)

	UserInputService.InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end
local function NeroEffect(object)
    spawn(function()
        local Types = Instance.new("ImageLabel")
        Types.Name = "Types"
        Types.Parent = object
        Types.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Types.BackgroundTransparency = 1.000
        Types.ZIndex = 8
        Types.Image = "rbxassetid://2708891598"
        Types.ImageTransparency = 0.800
        Types.ScaleType = Enum.ScaleType.Fit
        Types.Position = UDim2.new((Mouse.X - Types.AbsolutePosition.X) / object.AbsoluteSize.X, 0, (Mouse.Y - Types.AbsolutePosition.Y) / object.AbsoluteSize.Y, 0)
        TweenService:Create(Types, TweenInfo.new(1, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {Position = UDim2.new(-5.5, 0, -5.5, 0), Size = UDim2.new(12, 0, 12, 0)}):Play()
        wait(0.5)
        TweenService:Create(Types, TweenInfo.new(1, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {ImageTransparency = 1}):Play()
        wait(1)
        Types:Destroy()
    end)
end
local Nero = Instance.new("ScreenGui")
Nero.Name = "NERO"
Nero.Parent = game.CoreGui
Nero.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

local Toggled = false
UserInputService.InputBegan:Connect(function(X)
    if X.KeyCode == Enum.KeyCode.RightControl and bind then
        if Toggled == false then
            Nero.Enabled = false
            Toggled = true
        else
            Nero.Enabled = true
            Toggled = false
        end
    end
end)


function PlusNero:Mobile(title,theme,closebind)
    local tabs = {}
    local s = false
    local Main = Instance.new("Frame")
    local UICorner = Instance.new("UICorner")
    local Title = Instance.new("TextLabel")
    local MainFrame = Instance.new("Frame")
    local UICorner_2 = Instance.new("UICorner")
    local SectionBack = Instance.new("Frame")
    local UICorner_3 = Instance.new("UICorner")
    local search = Instance.new("ImageButton")
    local SearchBox = Instance.new("TextBox")
    local UICorner_25 = Instance.new("UICorner")

    Main.Name = "Main"
    Main.Parent = Nero
    Main.AnchorPoint = Vector2.new(0.5, 0.5)
    Main.BackgroundColor3 = theme.Header
    Main.BorderSizePixel = 0
    Main.Position = UDim2.new(0.5 ,0 ,0.5 ,0)
    Main.Size = UDim2.new(0, 556, 0, 366)
    Main.ZIndex = 3

    UICorner.CornerRadius = UDim.new(0, 5)
    UICorner.Parent = Main

    Title.Name = "Title"
    Title.Parent = Main
    Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    Title.BackgroundTransparency = 1.000
    Title.BorderSizePixel = 0
    Title.Position = UDim2.new(0, 13, 0, 0)
    Title.Size = UDim2.new(0, 556, 0, 19)
    Title.ZIndex = 7
    Title.Font = Enum.Font.SourceSansBold
    Title.Text = title
    Title.TextColor3 = theme.TextColor
    Title.TextSize = 20.000
    Title.TextWrapped = true
    Title.TextXAlignment = Enum.TextXAlignment.Left

    MainFrame.Name = "MainFrame"
    MainFrame.Parent = Main
    MainFrame.BackgroundColor3 = theme.Background
    MainFrame.BorderSizePixel = 0
    MainFrame.Position = UDim2.new(0, 0, 0, 19)
    MainFrame.Size = UDim2.new(0, 556, 0, 346)
    MainFrame.ZIndex = 3

    UICorner_2.CornerRadius = UDim.new(0, 5)
    UICorner_2.Parent = MainFrame

    SectionBack.Name = "SectionBack"
    SectionBack.Parent = MainFrame
    SectionBack.BackgroundColor3 = theme.Header
    SectionBack.BorderSizePixel = 0
    SectionBack.Position = UDim2.new(0, 6, 0, 35)
    SectionBack.Size = UDim2.new(0, 544, 0, 304)
    SectionBack.ZIndex = 5

    UICorner_3.CornerRadius = UDim.new(0, 3)
    UICorner_3.Parent = SectionBack
    MakeTitle(Title,Main)
    search.Name = "search"
    search.Parent = Main
    search.BackgroundColor3 = Color3.fromRGB(198, 197, 200)
    search.BackgroundTransparency = 1.000
    search.LayoutOrder = 1
    search.Position = UDim2.new(0, 530, 0, 0)
    search.Size = UDim2.new(0, 18, 0, 19)
    search.ZIndex = 9
    search.Image = "rbxassetid://3926305904"
    search.ImageRectOffset = Vector2.new(964, 324)
    search.ImageRectSize = Vector2.new(36, 36)

    SearchBox.Name = "SearchBox"
    SearchBox.Parent = Main
    SearchBox.BackgroundColor3 = theme.Background
    SearchBox.Position = UDim2.new(0.825999975, 50, 0, 2)
    SearchBox.Size = UDim2.new(0, 0, 0, 15)
    SearchBox.ZIndex = 10
    SearchBox.BorderSizePixel = 0
    SearchBox.Font = Enum.Font.SourceSans
    SearchBox.PlaceholderColor3 = Color3.fromRGB(239, 239, 239)
    SearchBox.Text = ""
    SearchBox.TextColor3 = theme.TextColor
    SearchBox.TextSize = 14.000
    SearchBox.Visible = true
    local SearchBoxTog = false

    search.MouseButton1Click:Connect(function()
        SearchBoxTog = not SearchBoxTog
        TweenService:Create(SearchBox,TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),{Size = SearchBoxTog and UDim2.new(0, 71, 0, 15) or UDim2.new(0, 0, 0, 15)}):Play()
        TweenService:Create(SearchBox,TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),{Position = SearchBoxTog and UDim2.new(0.825999975, 0, 0, 2) or UDim2.new(0.825999975, 50, 0, 2)}):Play()
    end)

    UICorner_25.Parent = SearchBox

    local TapBar = Instance.new("ScrollingFrame")
    local UICorner_16 = Instance.new("UICorner")
    local UIListLayout_3 = Instance.new("UIListLayout")

    TapBar.Name = "TapBar"
    TapBar.Parent = Main
    TapBar.BackgroundColor3 = Color3.fromRGB(41, 41, 41)
    TapBar.BorderSizePixel = 0
    TapBar.Position = UDim2.new(0, 6, 0, 28)
    TapBar.Size = UDim2.new(0, 544, 0, 21)
    TapBar.ZIndex = 5
    TapBar.ScrollBarThickness = 2
    TapBar.CanvasSize = UDim2.new(0,0,0,0)

    UICorner_16.CornerRadius = UDim.new(0, 3)
    UICorner_16.Parent = TapBar

    UIListLayout_3.Parent = TapBar
    UIListLayout_3.FillDirection = Enum.FillDirection.Horizontal
    UIListLayout_3.SortOrder = Enum.SortOrder.LayoutOrder

    function PlusNero:Notification(title,desc,button)
        for i,v in pairs(MainFrame:GetChildren())do
            if v.Name == "NotiBackFrame" then
                v:Destroy()
            end
        end
        local NotiBackFrame = Instance.new("Frame")
        local Notification = Instance.new("Frame")
        local Frame = Instance.new("Frame")
        local UICorner = Instance.new("UICorner")
        local Main = Instance.new("Frame")
        local UICorner_2 = Instance.new("UICorner")
        local Main_2 = Instance.new("Frame")
        local UICorner_3 = Instance.new("UICorner")
        local TextButton = Instance.new("TextButton")
        local UICorner_4 = Instance.new("UICorner")
        local Title = Instance.new("TextLabel")
        local UICorner_5 = Instance.new("UICorner")
        local Title_2 = Instance.new("TextLabel")
        local notifications = Instance.new("ImageButton")
        

        NotiBackFrame.Name = "NotiBackFrame"
        NotiBackFrame.Parent = MainFrame
        NotiBackFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
        NotiBackFrame.BackgroundTransparency = 1
        NotiBackFrame.Position = UDim2.new(-0.000238045119, 0, -0.0562442914, 0)
        NotiBackFrame.Size = UDim2.new(0, 556, 0, 366)
        NotiBackFrame.Visible = true
        NotiBackFrame.ZIndex = 100
        TweenService:Create(
            NotiBackFrame,
            TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
            {Position = UDim2.new(0, -500, -0.0562442914, 0)}
        ):Play()

        Notification.Name = "Notification"
        Notification.Parent = NotiBackFrame
        Notification.BackgroundColor3 = theme.Header
        Notification.BorderSizePixel = 0
        Notification.Position = UDim2.new(0, 83, 0, 55)
        Notification.Size = UDim2.new(0, 390, 0, 255)
        Notification.ZIndex = 10
        Notification.ClipsDescendants = true

        Frame.Parent = Notification
        Frame.BackgroundColor3 = theme.Background
        Frame.BorderColor3 = Color3.fromRGB(27, 42, 53)
        Frame.BorderSizePixel = 0
        Frame.Position = UDim2.new(0, 0, 0, 17)
        Frame.Size = UDim2.new(0, 390, 0, 236)
        Frame.ZIndex = 11
        
        UICorner.CornerRadius = UDim.new(0, 5)
        UICorner.Parent = Frame
        
        Main.Name = "Main"
        Main.Parent = Frame
        Main.BackgroundColor3 = theme.Header
        Main.BorderColor3 = Color3.fromRGB(27, 42, 53)
        Main.BorderSizePixel = 0
        Main.Position = UDim2.new(0, 8, 0, 7)
        Main.Size = UDim2.new(0, 373, 0, 220)
        Main.ZIndex = 11
        
        UICorner_2.CornerRadius = UDim.new(0, 5)
        UICorner_2.Parent = Main
        
        Main_2.Name = "Main"
        Main_2.Parent = Main
        Main_2.BackgroundColor3 = theme.Background
        Main_2.BorderColor3 = Color3.fromRGB(27, 42, 53)
        Main_2.BorderSizePixel = 0
        Main_2.Position = UDim2.new(0, 6, 0, 5)
        Main_2.Size = UDim2.new(0, 360, 0, 209)
        Main_2.ZIndex = 11
        
        UICorner_3.CornerRadius = UDim.new(0, 5)
        UICorner_3.Parent = Main_2
        
        TextButton.Parent = Main_2
        TextButton.BackgroundColor3 = theme.Header
        TextButton.Position = UDim2.new(0, 13, 0, 162)
        TextButton.Size = UDim2.new(0, 335, 0, 31)
        TextButton.ZIndex = 11
        TextButton.Font = Enum.Font.SourceSansBold
        TextButton.Text = button
        TextButton.TextColor3 = theme.TextColor
        TextButton.TextSize = 20.000
        
        UICorner_4.CornerRadius = UDim.new(0, 5)
        UICorner_4.Parent = TextButton
        TextButton.MouseButton1Click:Connect(function()

            NotiBackFrame:Destroy()

        end)
        Title.Name = "Title"
        Title.Parent = Main_2
        Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Title.BackgroundTransparency = 1.000
        Title.BorderSizePixel = 0
        Title.Position = UDim2.new(0, 14, 0, 8)
        Title.Size = UDim2.new(0, 335, 0, 113)
        Title.ZIndex = 11
        Title.Font = Enum.Font.SourceSansBold
        Title.Text = desc
        Title.TextColor3 = theme.TextColor
        Title.TextSize = 20.000
        Title.TextXAlignment = Enum.TextXAlignment.Left
        Title.TextYAlignment = Enum.TextYAlignment.Top
        
        UICorner_5.CornerRadius = UDim.new(0, 5)
        UICorner_5.Parent = Notification
        
        Title_2.Name = "Title"
        Title_2.Parent = Notification
        Title_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Title_2.BackgroundTransparency = 1.000
        Title_2.Position = UDim2.new(0, 28, 0, 1)
        Title_2.Size = UDim2.new(0, 191, 0, 19)
        Title_2.ZIndex = 10
        Title_2.Font = Enum.Font.SourceSansBold
        Title_2.Text = title
        Title_2.TextColor3 = theme.TextColor
        Title_2.TextSize = 20.000
        Title_2.TextXAlignment = Enum.TextXAlignment.Left
        
        notifications.Name = "notifications"
        notifications.Parent = Notification
        notifications.BackgroundTransparency = 1.000
        notifications.LayoutOrder = 1
        notifications.Position = UDim2.new(0, 7, 0, 0)
        notifications.Size = UDim2.new(0, 21, 0, 20)
        notifications.ZIndex = 11
        notifications.Image = "rbxassetid://3926305904"
        notifications.ImageRectOffset = Vector2.new(844, 564)
        notifications.ImageRectSize = Vector2.new(36, 36)
    end
    function tabs:Menu(title)
		local SectionContent = {}
		local Tab1 = Instance.new("TextButton")
		local UICorner_17 = Instance.new("UICorner")

		Tab1.Name = "Tab"
		Tab1.Parent = TapBar
		Tab1.BackgroundColor3 = theme.Header
		Tab1.Size = UDim2.new(0, 84, 0, 20)
		Tab1.ZIndex = 6
		Tab1.Font = Enum.Font.SourceSansBold
		Tab1.Text = title
		Tab1.TextColor3 = theme.TextColor
		Tab1.TextSize = 18.000
		Tab1.TextStrokeColor3 = Color3.fromRGB(255, 255, 255)
		Tab1.TextWrapped = true

		UICorner_17.CornerRadius = UDim.new(0, 3)
		UICorner_17.Parent = Tab1

		local ScrollingFrame = Instance.new("ScrollingFrame")
		local Left = Instance.new("Frame")
		local UIListLayout_2 = Instance.new("UIListLayout")
		local Right = Instance.new("Frame")
		local UIPadding_2 = Instance.new("UIPadding")

		ScrollingFrame.Parent = SectionBack
		ScrollingFrame.Active = true
		ScrollingFrame.BackgroundColor3 = theme.Header
		ScrollingFrame.BackgroundTransparency = 1.000
		ScrollingFrame.Position = UDim2.new(0, 0, 0.0197368413, 0)
		ScrollingFrame.Size = UDim2.new(0, 542, 0, 298)
		ScrollingFrame.ScrollBarThickness = 0
		ScrollingFrame.Visible = false
		Left.Name = "Left"
		Left.Parent = ScrollingFrame
		Left.BackgroundColor3 = Color3.fromRGB(63, 63, 63)
		Left.BackgroundTransparency = 1.000
		Left.BorderSizePixel = 0
		Left.Position = UDim2.new(0, 7, 0, 5)
		Left.Size = UDim2.new(0, 262, 0, 299)
		Left.ZIndex = 6

		UIListLayout_2.Parent = ScrollingFrame
		UIListLayout_2.FillDirection = Enum.FillDirection.Horizontal
		UIListLayout_2.SortOrder = Enum.SortOrder.LayoutOrder
		UIListLayout_2.Padding = UDim.new(0, 10)
		Right.Name = "Right"
		Right.Parent = ScrollingFrame
		Right.BackgroundColor3 = Color3.fromRGB(63, 63, 63)
		Right.BackgroundTransparency = 1.000
		Right.BorderSizePixel = 0
		Right.Position = UDim2.new(0, 7, 0, 5)
		Right.Size = UDim2.new(0, 262, 0, 299)
		Right.ZIndex = 6
        local RightList = Instance.new("UIListLayout")
        local LeftList = Instance.new("UIListLayout")
        LeftList.Parent = Left
        LeftList.SortOrder = Enum.SortOrder.LayoutOrder
        LeftList.Padding = UDim.new(0, 5)
        RightList.Parent = Right
        RightList.SortOrder = Enum.SortOrder.LayoutOrder
        RightList.Padding = UDim.new(0, 5)

		TapBar.CanvasSize = UDim2.new(0,UIListLayout_3.AbsoluteContentSize.X,0,0)

		UIPadding_2.Parent = ScrollingFrame
		UIPadding_2.PaddingLeft = UDim.new(0, 5)
        if s == false then
			s = true
			Tab1.TextColor3 = theme.Header
			ScrollingFrame.Visible = true
            Tab1.BackgroundColor3 = theme.SchemeColor
		end

		local function GetSide(Longest)
			if Longest then
				if LeftList.AbsoluteContentSize.Y > RightList.AbsoluteContentSize.Y then
					return Left
				else
					return Right
				end
			else
				if LeftList.AbsoluteContentSize.Y > RightList.AbsoluteContentSize.Y then
					return Right
				else
					return Left
				end
			end
		end

		LeftList:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
			if GetSide(true).Name == Left.Name then
				ScrollingFrame.CanvasSize = UDim2.new(0,0,0,LeftList.AbsoluteContentSize.Y + 5)
			else
				ScrollingFrame.CanvasSize = UDim2.new(0,0,0,RightList.AbsoluteContentSize.Y + 5)
			end
		end)
		RightList:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
			if GetSide(true).Name == Left.Name then
				ScrollingFrame.CanvasSize = UDim2.new(0,0,0,LeftList.AbsoluteContentSize.Y + 5)
			else
				ScrollingFrame.CanvasSize = UDim2.new(0,0,0,RightList.AbsoluteContentSize.Y + 5)
			end
		end)
		Tab1.MouseButton1Click:Connect(function()
			for i, v in next, SectionBack:GetChildren() do
				if v.Name == "ScrollingFrame" then
					v.Visible = false
				end
				ScrollingFrame.Visible = true

			end
			for i, v in next, TapBar:GetChildren() do
				if v.Name == "Tab" then
					TweenService:Create(
						v,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{TextColor3 = theme.TextColor}
					):Play()
					TweenService:Create(
						v,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = theme.Header}
					):Play()
					TweenService:Create(
						Tab1,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{TextColor3 = theme.Header}
					):Play()
					TweenService:Create(
						Tab1,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = theme.SchemeColor}
					):Play()
				end
			end
        end)



		function SectionContent:Section(title)
			local Content = {}
			local SectionHold = Instance.new("Frame")
			local UICorner_4 = Instance.new("UICorner")
			local UIListLayout = Instance.new("UIListLayout")
			local UIPadding = Instance.new("UIPadding")
			SectionHold.Name = "SectionHold"
			SectionHold.Parent = GetSide(false)
			SectionHold.BackgroundColor3 = theme.Background
			SectionHold.Position = UDim2.new(0, 1, 0, 0)
			SectionHold.Size = UDim2.new(0, 260, 0, 100)
			SectionHold.ZIndex = 7

			UICorner_4.CornerRadius = UDim.new(0, 5)
			UICorner_4.Parent = SectionHold


			UIListLayout.Parent = SectionHold
			UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
			UIListLayout.Padding = UDim.new(0, 5)
            UIListLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
				SectionHold.Size = UDim2.new(1,0,0,UIListLayout.AbsoluteContentSize.Y + 15)
			end)
			UIPadding.Parent = SectionHold
			UIPadding.PaddingLeft = UDim.new(0, 10)
			local Title_10 = Instance.new("TextLabel")

			Title_10.Name = "Title"
			Title_10.Parent = SectionHold
			Title_10.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Title_10.BackgroundTransparency = 1.000
			Title_10.Position = UDim2.new(0.0449448675, 0, -0.00182170793, 0)
			Title_10.Size = UDim2.new(0, 211, 0, 31)
			Title_10.ZIndex = 8
			Title_10.Font = Enum.Font.SourceSansBold
			Title_10.Text = title
			Title_10.TextColor3 = theme.SchemeColor
			Title_10.TextSize = 20.000
			Title_10.TextXAlignment = Enum.TextXAlignment.Left
			
			function Content:Line()
				local Line = Instance.new("Frame")
				local Frame_3 = Instance.new("Frame")
				local UICorner_8 = Instance.new('UICorner')

				Line.Name = "Line"
				Line.Parent = SectionHold
				Line.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Line.BackgroundTransparency = 1.000
				Line.BorderSizePixel = 0
				Line.Position = UDim2.new(0, 0, 0, 71)
				Line.Size = UDim2.new(0, 224, 0, 10)
				Line.ZIndex = 7

				Frame_3.Parent = Line
				Frame_3.BackgroundColor3 = Color3.fromRGB(37, 37, 37)
				Frame_3.BorderColor3 = Color3.fromRGB(255, 255, 255)
				Frame_3.BorderSizePixel = 0
				Frame_3.Position = UDim2.new(0, 10, 0, 5)
				Frame_3.Size = UDim2.new(0, 215, 0, 5)
				Frame_3.ZIndex = 7
				UICorner_8.CornerRadius = UDim.new(0, 10)
				UICorner_8.Parent = Frame_3
			end

			function Content:Label(title)
				local LabelFunc = {}
				local Label2 = Instance.new("Frame")
				local Title_4 = Instance.new("TextLabel")
				
				Label2.Name = title
				Label2.Parent = SectionHold
				Label2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Label2.BackgroundTransparency = 1.000
				Label2.BorderSizePixel = 0
				Label2.Position = UDim2.new(0, -11, 0, 191)
				Label2.Size = UDim2.new(0, 261, 0, 22)
				Label2.ZIndex = 7
				
				Title_4.Name = "Title"
				Title_4.Parent = Label2
				Title_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title_4.BackgroundTransparency = 1.000
				Title_4.Position = UDim2.new(0, 12, 0, -6)
				Title_4.Size = UDim2.new(0, 211, 0, 31)
				Title_4.ZIndex = 8
				Title_4.Text = title
				Title_4.Font = Enum.Font.SourceSansBold
				Title_4.TextColor3 = theme.TextColor
				Title_4.TextSize = 20.000
				function LabelFunc:Update(text)
					Label2.Name = tostring(text)

					Title_4.Text = tostring(text)
				end
				return LabelFunc
			end
			function Content:Setup(title)
				local LabelFunc = {}
				local Label1 = Instance.new("Frame")
				local Frame_8 = Instance.new("Frame")
				local UICorner_14 = Instance.new("UICorner")
				local Frame_9 = Instance.new("Frame")
				local UICorner_15 = Instance.new("UICorner")
				local Title_9 = Instance.new("TextLabel")
				
				Label1.Name = title
				Label1.Parent = SectionHold
				Label1.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Label1.BackgroundTransparency = 1.000
				Label1.BorderSizePixel = 0
				Label1.Position = UDim2.new(0, 0, 0, 30)
				Label1.Size = UDim2.new(0, 260, 0, 22)
				Label1.ZIndex = 7
				
				Frame_8.Parent = Label1
				Frame_8.BackgroundColor3 = Color3.fromRGB(37, 37, 37)
				Frame_8.BorderColor3 = Color3.fromRGB(255, 255, 255)
				Frame_8.BorderSizePixel = 0
				Frame_8.Position = UDim2.new(0, 24, 0, 7)
				Frame_8.Size = UDim2.new(0, 62, 0, 4)
				Frame_8.ZIndex = 7
				
				UICorner_14.CornerRadius = UDim.new(0, 10)
				UICorner_14.Parent = Frame_8
				
				Frame_9.Parent = Label1
				Frame_9.BackgroundColor3 = Color3.fromRGB(37, 37, 37)
				Frame_9.BorderColor3 = Color3.fromRGB(255, 255, 255)
				Frame_9.BorderSizePixel = 0
				Frame_9.Position = UDim2.new(0, 156, 0, 7)
				Frame_9.Size = UDim2.new(0, 62, 0, 4)
				Frame_9.ZIndex = 7
				
				UICorner_15.CornerRadius = UDim.new(0, 10)
				UICorner_15.Parent = Frame_9
				
				Title_9.Name = "Title"
				Title_9.Parent = Label1
				Title_9.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title_9.BackgroundTransparency = 1.000
				Title_9.Position = UDim2.new(0, 14, 0, -7)
				Title_9.Size = UDim2.new(0, 211, 0, 31)
				Title_9.ZIndex = 8
				Title_9.Text = title
				Title_9.Font = Enum.Font.SourceSansBold
				Title_9.TextColor3 = theme.TextColor
				Title_9.TextSize = 20.000
				function LabelFunc:Update(text)
					Label1.Name = tostring(text)
					Title_4.Text = tostring(text)
				end
				return LabelFunc
			end
			local focused = false
			SearchBox.Focused:Connect(function()
			
			end)
			SearchBox.FocusLost:Connect(function()
			
			end)

			function UpdateInputOfSearchText()
				local InputText = string.upper(SearchBox.Text)
				for _,button in pairs(SectionHold:GetChildren())do
					if button:IsA("Frame") then
								if InputText == "" or string.find(string.upper(button.Name),InputText) ~= nil then
									button.Visible = true
								else
									button.Visible = false
								end
					end
				end
			end

			SearchBox.Changed:Connect(UpdateInputOfSearchText)
			function Content:Button(title,callback)
				local Button = Instance.new("Frame")
				local TextButton = Instance.new("TextButton")
				local UICorner_5 = Instance.new("UICorner")
				local touch_app = Instance.new("ImageButton")

				Button.Name = title
				Button.Parent = SectionHold
				Button.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Button.BackgroundTransparency = 1.000
				Button.BorderSizePixel = 0
                Button.ClipsDescendants = true
				Button.Position = UDim2.new(0, 0, 0, 87)
				Button.Size = UDim2.new(0, 240, 0, 34)
				Button.ZIndex = 8

				TextButton.Parent = Button
				TextButton.BackgroundColor3 = theme.Header
				TextButton.BorderSizePixel = 0
				TextButton.Position = UDim2.new(0, 12, 0, 5)
				TextButton.Size = UDim2.new(0, 212, 0, 26)
				TextButton.ZIndex = 7
				TextButton.Font = Enum.Font.SourceSansBold
				TextButton.TextColor3 = theme.TextColor
				TextButton.TextSize = 20.000
                TextButton.Text = title
				UICorner_5.CornerRadius = UDim.new(0, 5)
				UICorner_5.Parent = TextButton

				touch_app.Name = "touch_app"
				touch_app.Parent = Button
				touch_app.BackgroundTransparency = 1.000
				touch_app.LayoutOrder = 9
				touch_app.Position = UDim2.new(0, 197, 0, 5)
				touch_app.Size = UDim2.new(0, 26, 0, 22)
				touch_app.ZIndex = 11

				touch_app.Image = "rbxassetid://3926305904"
				touch_app.ImageRectOffset = Vector2.new(84, 204)
				touch_app.ImageRectSize = Vector2.new(36, 36)

				TextButton.MouseButton1Down:Connect(function()
					NeroEffect(Button)               
					pcall(callback)
				end)
			end
			function Content:Toggle(title,default,callback)
				local Toggled = false
				local ToggleFunc = {}
				local Toggle = Instance.new("Frame")
				local Title = Instance.new("TextLabel")
				local ToggleBack = Instance.new("TextButton")
				local UICorner = Instance.new("UICorner")
				local ImageLabel = Instance.new("ImageLabel")
				local UICorner_2 = Instance.new("UICorner")

				Toggle.Name = title
				Toggle.Parent = SectionHold
				Toggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Toggle.BackgroundTransparency = 1.000
				Toggle.BorderSizePixel = 0
				Toggle.Position = UDim2.new(0, 0, 0, 187)
				Toggle.Size = UDim2.new(0, 231, 0, 30)
				Toggle.ZIndex = 7

				Title.Name = "Title"
				Title.Parent = Toggle
				Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title.BackgroundTransparency = 1.000
				Title.Position = UDim2.new(0, 43, 0, 6)
				Title.Size = UDim2.new(0, 168, 0, 22)
				Title.ZIndex = 8
				Title.Font = Enum.Font.SourceSansBold
				Title.Text = title
				Title.TextColor3 = theme.TextColor
				Title.TextSize = 20.000
				Title.TextXAlignment = Enum.TextXAlignment.Left

				ToggleBack.Name = "ToggleBack"
				ToggleBack.Parent = Toggle
				ToggleBack.BackgroundColor3 = theme.Header
				ToggleBack.Position = UDim2.new(0.0173160173, 0, 0.0666666701, 0)
				ToggleBack.Size = UDim2.new(0, 26, 0, 26)
				ToggleBack.ZIndex = 11
                ToggleBack.ClipsDescendants = true
				ToggleBack.Font = Enum.Font.SourceSans
				ToggleBack.Text = ""
				ToggleBack.TextColor3 = Color3.fromRGB(0, 0, 0)
				ToggleBack.TextSize = 14.000

				UICorner.CornerRadius = UDim.new(0, 5)
				UICorner.Parent = ToggleBack
				function ToggleFunc:Update(state)
					if state then
						Toggled = state
						TweenService:Create(
							ImageLabel,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Toggled and theme.SchemeColor or theme.Header}
						):Play()
						pcall(callback,Toggled)
					else
						Toggled = state
						TweenService:Create(
							ImageLabel,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{BackgroundColor3 = Toggled and theme.SchemeColor or theme.Header}
						):Play()
						pcall(callback,Toggled)
					end
				end
				
				ToggleBack.MouseButton1Down:Connect(function()
					Toggled = not Toggled
					TweenService:Create(
						ImageLabel,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Toggled and theme.SchemeColor or theme.Header}
					):Play()
					NeroEffect(ToggleBack)               

					pcall(callback,Toggled)
				end)
				ImageLabel.Parent = ToggleBack
				ImageLabel.BackgroundColor3 = theme.Header
				ImageLabel.Position = UDim2.new(0, 1, 0, 1)
				ImageLabel.Size = UDim2.new(0, 24, 0, 24)
				ImageLabel.ZIndex = 11
				ImageLabel.Image = "rbxassetid://3926305904"
				ImageLabel.ImageColor3 = Color3.fromRGB(41, 41, 41)
				ImageLabel.ImageRectOffset = Vector2.new(312, 4)
				ImageLabel.ImageRectSize = Vector2.new(24, 24)

				UICorner_2.CornerRadius = UDim.new(0, 5)
				UICorner_2.Parent = ImageLabel

				if default then
					Toggled = default
					TweenService:Create(
						ImageLabel,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundColor3 = Toggled and theme.SchemeColor or theme.Header}
					):Play()
					pcall(callback,Toggled)
				end
				return ToggleFunc
			end
			function Content:CreateKeybind(title,ori,callback)
				local Keybind = Instance.new("Frame")
				local Title_4 = Instance.new("TextLabel")
				local TextButton2323 = Instance.new("TextButton")
				local UICorner_5 = Instance.new("UICorner")
				Keybind.Name = title
				Keybind.Parent = SectionHold
				Keybind.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Keybind.BackgroundTransparency = 1.000
				Keybind.BorderSizePixel = 0
				Keybind.Position = UDim2.new(0, 0, 0, 223)
				Keybind.Size = UDim2.new(0, 231, 0, 30)
				Keybind.ZIndex = 7

				Title_4.Name = "Title"
				Title_4.Parent = Keybind
				Title_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title_4.BackgroundTransparency = 1.000
				Title_4.BorderSizePixel = 0
				Title_4.Position = UDim2.new(0, 10, 0, 4)
				Title_4.Size = UDim2.new(0, 98, 0, 22)
				Title_4.ZIndex = 8
				Title_4.Font = Enum.Font.SourceSansBold
				Title_4.Text = title
				Title_4.TextColor3 = theme.TextColor
				Title_4.TextSize = 18.000
				Title_4.TextXAlignment = Enum.TextXAlignment.Left

				TextButton2323.Parent = Keybind
				TextButton2323.BackgroundColor3 = theme.Header
				TextButton2323.Position = UDim2.new(0.744588733, 0, 0.13333334, 0)
				TextButton2323.Size = UDim2.new(0, 65, 0, 24)
				TextButton2323.ZIndex = 11
				TextButton2323.Font = Enum.Font.SourceSansBold
				TextButton2323.TextColor3 = theme.TextColor
				TextButton2323.TextSize = 15.000
				TextButton2323.Text = ori.Name or ""
				UICorner_5.CornerRadius = UDim.new(0, 5)
				UICorner_5.Parent = TextButton2323
				TextButton2323.MouseButton1Click:Connect(function()
                    
                TextButton2323.Text = "..."
                    local inputwait = UserInputService.InputBegan:wait()
                    if inputwait.KeyCode.Name ~= "Unknown" then
                        TextButton2323.Text = inputwait.KeyCode.Name
                        Key = inputwait.KeyCode.Name
                    end
                end)
                    
                UserInputService.InputBegan:connect(
                function(current, pressed)
                    if not pressed then
                        if current.KeyCode.Name == Key then
                            pcall(callback)
                        end
                    end
                end)
			end
			function Content:Slider(title,min,max,default,callback)
				local SliderFunc = {}
				local Slider = Instance.new("Frame")
				local Title_2 = Instance.new("TextLabel")
				local Frame = Instance.new("Frame")
				local UICorner_2 = Instance.new("UICorner")
				local Title_3 = Instance.new("TextLabel")
				local add = Instance.new("ImageButton")
				local remove = Instance.new("ImageButton")
				local SliderFrame = Instance.new("TextButton")
				local UICorner_3 = Instance.new("UICorner")
				local Sliderin = Instance.new("TextButton")
				local UICorner_4 = Instance.new("UICorner")
				Slider.Name = title
				Slider.Parent = SectionHold
				Slider.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Slider.BackgroundTransparency = 1.000
				Slider.BorderSizePixel = 0
				Slider.Position = UDim2.new(0, 0, 0, 61)
				Slider.Size = UDim2.new(0, 231, 0, 39)
				Slider.ZIndex = 7
				
				Title_2.Name = "Title"
				Title_2.Parent = Slider
				Title_2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title_2.BackgroundTransparency = 1.000
				Title_2.Position = UDim2.new(0.0519480482, 0, 0.128205135, 0)
				Title_2.Size = UDim2.new(0, 143, 0, 23)
				Title_2.ZIndex = 8
				Title_2.Font = Enum.Font.SourceSansBold
				Title_2.Text = title
				Title_2.TextColor3 = theme.TextColor
				Title_2.TextSize = 20.000
				Title_2.TextXAlignment = Enum.TextXAlignment.Left
				
				Frame.Parent = Slider
				Frame.BackgroundColor3 = theme.Header
				Frame.BorderColor3 = Color3.fromRGB(27, 42, 53)
				Frame.BorderSizePixel = 0
				Frame.Position = UDim2.new(0, 181, 0, 5)
				Frame.Size = UDim2.new(0, 30, 0, 19)
				Frame.ZIndex = 9
				
				UICorner_2.CornerRadius = UDim.new(0, 5)
				UICorner_2.Parent = Frame
				
				Title_3.Name = "Title"
				Title_3.Parent = Frame
				Title_3.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title_3.BackgroundTransparency = 1.000
				Title_3.BorderSizePixel = 0
				Title_3.Size = UDim2.new(0, 29, 0, 19)
				Title_3.ZIndex = 10
				Title_3.Font = Enum.Font.SourceSansBold
				Title_3.Text = "30"
				Title_3.TextColor3 = theme.TextColor
				Title_3.TextSize = 15.000
				
				add.Name = "add"
				add.Parent = Slider
				add.BackgroundTransparency = 1.000
				add.LayoutOrder = 3
				add.Position = UDim2.new(0, 210, 0, 4)
				add.Size = UDim2.new(0, 21, 0, 21)
				add.ZIndex = 9
                add.ClipsDescendants = true
				add.Image = "rbxassetid://3926307971"
				add.ImageRectOffset = Vector2.new(324, 364)
				add.ImageRectSize = Vector2.new(36, 36)
				
				remove.Name = "remove"
				remove.Parent = Slider
				remove.BackgroundTransparency = 1.000
				remove.LayoutOrder = 6
				remove.Position = UDim2.new(0, 156, 0, 4)
				remove.Size = UDim2.new(0, 21, 0, 21)
				remove.ZIndex = 9
                remove.ClipsDescendants = true
				remove.Image = "rbxassetid://3926307971"
				remove.ImageRectOffset = Vector2.new(884, 284)
				remove.ImageRectSize = Vector2.new(36, 36)
				
				SliderFrame.Name = "SliderFrame"
				SliderFrame.Parent = Slider
				SliderFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				SliderFrame.Position = UDim2.new(0.012987013, 0, 0.717948735, 0)
				SliderFrame.Size = UDim2.new(0, 225, 0, 6)
				SliderFrame.ZIndex = 11
				SliderFrame.Font = Enum.Font.SourceSans
				SliderFrame.Text = ""
				SliderFrame.TextColor3 = Color3.fromRGB(0, 0, 0)
				SliderFrame.TextSize = 14.000
				
				UICorner_3.CornerRadius = UDim.new(0, 5)
				UICorner_3.Parent = SliderFrame
				
				Sliderin.Name = "Sliderin"
				Sliderin.Parent = SliderFrame
				Sliderin.BackgroundColor3 = theme.SchemeColor
				Sliderin.Size = UDim2.new(0, 125, 0, 6)
				Sliderin.ZIndex = 11
				Sliderin.Font = Enum.Font.SourceSans
				Sliderin.Text = ""
				Sliderin.TextColor3 = Color3.fromRGB(0, 0, 0)
				Sliderin.TextSize = 14.000
				
				UICorner_4.CornerRadius = UDim.new(0, 5)
				UICorner_4.Parent = Sliderin

				local mouse = game:GetService("Players").LocalPlayer:GetMouse();  

                local Value = default
                SliderFrame.MouseButton1Down:Connect(function()
                    if not focusing then
                        Value = math.floor((((tonumber(max) - tonumber(min)) / 225) * Sliderin.AbsoluteSize.X) + tonumber(min)) or 0
                        pcall(function()
                            callback(Value)
                        end)
                        Sliderin:TweenSize(UDim2.new(0, math.clamp(mouse.X - Sliderin.AbsolutePosition.X, 0, 225), 0, 6), "InOut", "Linear", 0.01, true)
                        moveconnection = mouse.Move:Connect(function()
                            Value = math.floor((((tonumber(max) - tonumber(min)) / 225) * Sliderin.AbsoluteSize.X) + tonumber(min))
                            Title_3.Text = Value
                            pcall(function()
                                callback(Value)
                            end)
                            Sliderin:TweenSize(UDim2.new(0, math.clamp(mouse.X - Sliderin.AbsolutePosition.X, 0, 225), 0, 6), "InOut", "Linear", 0.01, true)
                        end)
                        releaseconnection = UserInputService.InputEnded:Connect(function(Mouse)
                            if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                                Value = math.floor((((tonumber(max) - tonumber(min)) / 225) * Sliderin.AbsoluteSize.X) + tonumber(min))
                                Title_3.Text = Value
    
                                pcall(function()
                                    callback(Value)
                                end)
    
                                Sliderin:TweenSize(UDim2.new(0, math.clamp(mouse.X - Sliderin.AbsolutePosition.X, 0, 225), 0, 6), "InOut", "Linear", 0.01, true)
                                moveconnection:Disconnect()
                                releaseconnection:Disconnect()
                            end
                        end)
                    end
                end)
                Sliderin.MouseButton1Down:Connect(function()
                    if not focusing then
                        Value = math.floor((((tonumber(max) - tonumber(min)) / 225) * Sliderin.AbsoluteSize.X) + tonumber(min)) or 0
                        pcall(function()
                            callback(Value)
                        end)
                        Sliderin:TweenSize(UDim2.new(0, math.clamp(mouse.X - Sliderin.AbsolutePosition.X, 0, 225), 0, 6), "InOut", "Linear", 0.01, true)
                        moveconnection = mouse.Move:Connect(function()
                            Value = math.floor((((tonumber(max) - tonumber(min)) / 225) * Sliderin.AbsoluteSize.X) + tonumber(min))
                            Title_3.Text = Value
                            pcall(function()
                                callback(Value)
                            end)
                            Sliderin:TweenSize(UDim2.new(0, math.clamp(mouse.X - Sliderin.AbsolutePosition.X, 0, 225), 0, 6), "InOut", "Linear", 0.01, true)
                        end)
                        releaseconnection = UserInputService.InputEnded:Connect(function(Mouse)
                            if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
                                Value = math.floor((((tonumber(max) - tonumber(min)) / 225) * Sliderin.AbsoluteSize.X) + tonumber(min))
                                Title_3.Text = Value
    
                                pcall(function()
                                    callback(Value)
                                end)
    
                                Sliderin:TweenSize(UDim2.new(0, math.clamp(mouse.X - Sliderin.AbsolutePosition.X, 0, 225), 0, 6), "InOut", "Linear", 0.01, true)
                                moveconnection:Disconnect()
                                releaseconnection:Disconnect()
                            end
                        end)
                    end
                end)
				add.MouseButton1Click:Connect(function()
					Value = math.clamp(Value + 1, 1, max)
					Sliderin.Size = UDim2.new(Value / max, 0, 0, 6)
                    Title_3.Text = Value
                    pcall(function()
                        callback(Value)
                    end)
					NeroEffect(add)               

				end)

				remove.MouseButton1Click:Connect(function()
					Value = math.clamp(Value - 1, min, max)
					Sliderin.Size = UDim2.new(Value / max, 0, 0, 6)
                    Title_3.Text = Value
                    pcall(function()
                        callback(Value)
                    end)
					NeroEffect(remove)               

				end)

                if default then
                    Sliderin.Size = UDim2.new((default or 0) / max, 0, 0, 6)
                    Title_3.Text = default
                    pcall(function()
                        callback(default)
                    end)
                end
                function SliderFunc:Update(value)
                    Sliderin.Size = UDim2.new((value or 0) / max, 0, 0, 6)
                    Title_3.Text = value
                    pcall(function()
                        callback(value)
                    end)
            	end
				return SliderFunc
			end
			function Content:TextBox(title,disapper,callback)
				local TextBox = Instance.new("Frame")
				local Title = Instance.new("TextLabel")
				local TextBox_2 = Instance.new("TextBox")
				local UICorner = Instance.new("UICorner")
				
				TextBox.Name = title
				TextBox.Parent = SectionHold
				TextBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				TextBox.BackgroundTransparency = 1.000
				TextBox.BorderSizePixel = 0
				TextBox.Position = UDim2.new(0, 0, 0, 187)
				TextBox.Size = UDim2.new(0, 231, 0, 30)
				TextBox.ZIndex = 7
				
				Title.Name = "Title"
				Title.Parent = TextBox
				Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title.BackgroundTransparency = 1.000
				Title.BorderSizePixel = 0
				Title.Position = UDim2.new(0, 20, 0, 5)
				Title.Size = UDim2.new(0, 98, 0, 22)
				Title.ZIndex = 8
				Title.Font = Enum.Font.SourceSansBold
				Title.Text = title
				Title.TextColor3 = theme.TextColor
				Title.TextSize = 20.000
				Title.TextXAlignment = Enum.TextXAlignment.Left
				
				TextBox_2.Parent = TextBox
				TextBox_2.BackgroundColor3 = theme.Header
				TextBox_2.Position = UDim2.new(0.597402573, 0, 0.166666672, 0)
				TextBox_2.Size = UDim2.new(0, 83, 0, 22)
				TextBox_2.ZIndex = 11
				TextBox_2.Font = Enum.Font.SourceSans
				TextBox_2.Text = ""
				TextBox_2.TextColor3 = theme.TextColor
				TextBox_2.TextSize = 14.000
				
				UICorner.CornerRadius = UDim.new(0, 5)
				UICorner.Parent = TextBox_2 
				TextBox_2.FocusLost:Connect(
                    function(ep)
                        if ep then
                            if #TextBox_2.Text > 0 then
                                pcall(callback, TextBox_2.Text)
                                if disapper then
                                    TextBox_2.Text = ""
                                end
                            end
                        end
                    end
                )
			end
            function Content:Dropdown(title,list,callback)
				local DropFunc = {}
				local Droptog = false
				local Dropdown = Instance.new("Frame")
				local Title_5 = Instance.new("TextLabel")
				local Frame_2 = Instance.new("Frame")
				local UICorner_6 = Instance.new("UICorner")
				local TextLabel = Instance.new("TextLabel")
				local expand_more = Instance.new("ImageButton")
				local DropHold = Instance.new("Frame")
				local Droplis = Instance.new("ScrollingFrame")
				local UIListLayout23423423423 = Instance.new("UIListLayout")
				local UIPadding = Instance.new("UIPadding")
				local UICorner_8 = Instance.new("UICorner")
							
				Dropdown.Name = title
				Dropdown.Parent = SectionHold
				Dropdown.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Dropdown.BackgroundTransparency = 1.000
				Dropdown.BorderSizePixel = 0
				Dropdown.Position = UDim2.new(0, 0, 0, 187)
				Dropdown.Size = UDim2.new(0, 231, 0, 30)
				Dropdown.ZIndex = 7

				Title_5.Name = "Title"
				Title_5.Parent = Dropdown
				Title_5.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Title_5.BackgroundTransparency = 1.000
				Title_5.BorderSizePixel = 0
				Title_5.Position = UDim2.new(0, 20, 0, 5)
				Title_5.Size = UDim2.new(0, 98, 0, 22)
				Title_5.ZIndex = 10
				Title_5.Font = Enum.Font.SourceSansBold
				Title_5.Text = title
				Title_5.TextColor3 = theme.TextColor
				Title_5.TextSize = 18.000
				Title_5.TextXAlignment = Enum.TextXAlignment.Left

				Frame_2.Parent = Dropdown
				Frame_2.BackgroundColor3 = theme.Header
				Frame_2.BorderColor3 = Color3.fromRGB(27, 42, 53)
				Frame_2.BorderSizePixel = 0
				Frame_2.Position = UDim2.new(0, 12, 0, 1)
				Frame_2.Size = UDim2.new(0, 212, 0, 31)
				Frame_2.ZIndex = 9

				UICorner_6.CornerRadius = UDim.new(0, 5)
				UICorner_6.Parent = Frame_2

				TextLabel.Parent = Frame_2
				TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				TextLabel.BackgroundTransparency = 1.000
				TextLabel.BorderColor3 = Color3.fromRGB(27, 42, 53)
				TextLabel.Size = UDim2.new(0, 59, 0, 24)
				TextLabel.ZIndex = 9
				TextLabel.Font = Enum.Font.SourceSansBold
				TextLabel.Text = ""
				TextLabel.TextColor3 = theme.TextColor
				TextLabel.TextSize = 20.000

				expand_more.Name = "expand_more"
				expand_more.Parent = Frame_2
				expand_more.BackgroundTransparency = 1.000
				expand_more.Position = UDim2.new(0.855562031, 0, 0.0551075041, 0)
				expand_more.Size = UDim2.new(0, 25, 0, 25)
				expand_more.ZIndex = 9
				expand_more.Image = "rbxassetid://3926305904"
				expand_more.ImageRectOffset = Vector2.new(564, 284)
				expand_more.ImageRectSize = Vector2.new(36, 36)
				expand_more.Rotation = 0
				
				DropHold.Name = "DropHold"
				DropHold.Parent = SectionHold
				DropHold.BackgroundColor3 = theme.Header
				DropHold.Position = UDim2.new(0, 0, 0.746887982, 0)
				DropHold.Size = UDim2.new(0, 500, 0, 0)
				DropHold.ZIndex = 10
				DropHold.Visible = false
				DropHold.BackgroundTransparency = 1

				Droplis.Name = "Droplis"
				Droplis.Parent = DropHold
				Droplis.Active = true
				Droplis.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Droplis.BackgroundTransparency = 1.000
				Droplis.Size = UDim2.new(0, 231, 0, 112)
				Droplis.ZIndex = 11
				Droplis.ScrollBarThickness = 0
				Droplis.Visible = false
				Droplis.Position = UDim2.new(0, 5, 0, 0)

				UIListLayout23423423423.Parent = Droplis
				UIListLayout23423423423.SortOrder = Enum.SortOrder.LayoutOrder

				UIPadding.Parent = Droplis
				UIPadding.PaddingTop = UDim.new(0, 3)
				
				expand_more.MouseButton1Click:Connect(function()
					Droptog = not Droptog
					DropHold.Visible = Droptog
					Droplis.Visible = Droptog
                    if expand_more.Rotation == 90 then
                        TweenService:Create(
                            expand_more,
                            TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                            {Rotation = 0}
                        ):Play()
                    else
                        TweenService:Create(
                            expand_more,
                            TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                            {Rotation = 90}
                        ):Play()
                    end
					TweenService:Create(
						DropHold,
						TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{Size = Droptog and UDim2.new(0, 500, 0, 80) or UDim2.new(0, 500, 0, 0)}
					):Play()
				end)
	
				UICorner_8.Parent = DropHold

				for i,v in next, list do

					local DrioBy = Instance.new("TextButton")
					local UICorner_7 = Instance.new("UICorner")
					DrioBy.Name = "DrioBy"
					DrioBy.Parent = Droplis
					DrioBy.BackgroundColor3 = Color3.fromRGB(71, 71, 71)
					DrioBy.Size = UDim2.new(0, 224, 0, 26)
					DrioBy.ZIndex = 12
					DrioBy.Text = v 
					DrioBy.Font = Enum.Font.SourceSansBold
					DrioBy.TextColor3 = theme.TextColor
					DrioBy.TextSize = 16.000
	
					UICorner_7.CornerRadius = UDim.new(0, 3)
					UICorner_7.Parent = DrioBy
	
    
                    DrioBy.MouseButton1Click:Connect(function()
                        pcall(callback, v)
                        Title_5.Text = title .. " : ".. v
                        Droptog = not Droptog
						DropHold.Visible = Droptog
						Droplis.Visible = Droptog
                        if expand_more.Rotation == 90 then
                            TweenService:Create(
                                expand_more,
                                TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                                {Rotation = 0}
                            ):Play()
                        end 
						TweenService:Create(
							DropHold,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Size = Droptog and UDim2.new(0, 500, 0, 80) or UDim2.new(0, 500, 0, 0)}
						):Play()
                    end)
                end

                function DropFunc:Clear()
                    for i, v in next, Droplis:GetChildren() do
                        if v.Name == "DrioBy" then
                            v:Destroy()
                        end
                    end
                    if Droptog == true then
                        Title_5.Text = Title
                    end
                end

                function DropFunc:Add(addtext)
					local DrioBy = Instance.new("TextButton")
					local UICorner_7 = Instance.new("UICorner")
					DrioBy.Name = "DrioBy"
					DrioBy.Parent = Droplis
					DrioBy.BackgroundColor3 = Color3.fromRGB(71, 71, 71)
					DrioBy.Size = UDim2.new(0, 224, 0, 26)
					DrioBy.ZIndex = 12
					DrioBy.Text = addtext 
					DrioBy.Font = Enum.Font.SourceSansBold
					DrioBy.TextColor3 = theme.TextColor
					DrioBy.TextSize = 16.000
	
					UICorner_7.CornerRadius = UDim.new(0, 3)
					UICorner_7.Parent = DrioBy
	
    
                    DrioBy.MouseButton1Click:Connect(function()
                        pcall(callback, addtext)
                        Title_5.Text = title .. " : ".. addtext
                        Droptog = not Droptog
						DropHold.Visible = Droptog
						Droplis.Visible = Droptog
                        if expand_more.Rotation == 90 then
                            TweenService:Create(
                                expand_more,
                                TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
                                {Rotation = 0}
                            ):Play()
                        end 
						TweenService:Create(
							DropHold,
							TweenInfo.new(.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
							{Size = Droptog and UDim2.new(0, 500, 0, 80) or UDim2.new(0, 500, 0, 0)}
						):Play()
                    end)
                end
            return DropFunc
            end
		return Content
	end
	return SectionContent
end
return tabs
end


local Mobile = PlusNero:Mobile("WATER X HUB",PlusNero.Themes.Original,Enum.KeyCode.RightControl)

local Return = {(nil)}

local Ultra = Mobile:Menu('Main1')
local Tab = Mobile:Menu('Main2')


local Ultra_left = Ultra:Section('Ultra left')

Ultra_left:Line()

Ultra_left:Label("Label")

Ultra_left:Toggle("AutoSetSpawn",false,function(Return)
      _G.AutoSetSpawn = Return
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if _G.AutoSetSpawn then
                    if game:GetService("Players").LocalPlayer.Character.Humanoid.Health > 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                    end
                end
            end
        end)
    end)


Ultra_left:Toggle("Redeem All Code",false,function(Return)
    function UseCode(Text)
			game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(Text)
		end
		UseCode("SUB2GAMERROBOT_EXP1")
		UseCode("StrawHatMaine")
		UseCode("Sub2OfficialNoobie")
		UseCode("FUDD10")
		UseCode("BIGNEWS")
		UseCode("THEGREATACE")
		UseCode("SUB2NOOBMASTER123")
		UseCode("Sub2Daigrock")
		UseCode("Axiore")
		UseCode("TantaiGaming")
		UseCode("STRAWHATMAINE")
	end)


local Ultra_right = Ultra:Section('PointStats')

Ultra_right:Line()

Ultra_right:Label("PointStats")

Ultra_right:Toggle("Melee",false,function(Return)
    _G.Auto_Melee = Return
    end)

Ultra_right:Toggle("Defense",false,function(Return)
    _G.Auto_Defense = Return
    end)
    
Ultra_right:Toggle("Sword",false,function(Return)
    _G.Auto_Sword = Return
    end)
    
Ultra_right:Toggle("Gun",false,function(Return)
    _G.Auto_Gun = Return
    end)

Ultra_right:Toggle("DevilFruit",false,function(Return)
    _G.Auto_DevilFruit = Return
    end)
    
     spawn(function()
        while wait() do
            pcall(function()
                if _G.Auto_Melee then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Melee",_G.PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if _G.Auto_Defense then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Defense",_G.PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if _G.Auto_Sword then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Sword",_G.PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if _G.Auto_Gun then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Gun",_G.PointStats)
                    end
                end
            end)
        end
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if _G.Auto_DevilFruit then
                    if game:GetService("Players")["LocalPlayer"].Data.Points.value ~= 0 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint","Devil Fruit",_G.PointStats)
                    end
                end
            end)
        end
    end)
