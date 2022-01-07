--script Lifting Simulator




getgenv().auto = false;
getgenv().sell = false;


function doTap()
spawn(function()
    while getgenv().auto == true do
     local args = {
    [1] = {
        [1] = "GainMuscle"
    }
}

game:GetService("ReplicatedStorage").RemoteEvent:FireServer(unpack(args))
wait()
end
end)
end

function doSell()
    spawn(function()
    while sell == true do
    local args = {
    [1] = {
        [1] = "SellMuscle"
    }
}

game:GetService("ReplicatedStorage").RemoteEvent:FireServer(unpack(args))
wait()
end
end)
end

local library = loadstring(game:HttpGet(('https://raw.githubusercontent.com/AikaV3rm/UiLib/master/Lib.lua')))()

local w = library:CreateWindow("Lifting Simulator") -- Creates the window

local b = w:CreateFolder("Auto Farm") -- Creates the folder(U will put here your buttons,etc)

local c = w:CreateFolder("Teleport")

b:DestroyGui()

b:Toggle("Auto Farming",function(bool)
    getgenv().auto = bool
    print(shared.toggle)
    if bool then
    doTap();
    end
end)

b:Toggle("Auto Sell",function(bool)
    getgenv().sell = bool
    print(shared.toggle)
    if bool then
    doSell();
    end
end)

b:Button("Anti AFK",function()
    local vu = game:GetService("VirtualUser")
game:GetService("Players").LocalPlayer.Idled:connect(function()
   vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
   wait(1)
   vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
end)
end)




c:Button("Sell Zone",function()
       game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-634.35, -40, 1858.41)
end)

c:Button("Buy Zone",function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-646.88, -40, 1785.9)
end)
