if game:GetService("RunService"):IsClient() then error("Script must be server-side in order to work; use h/ and not hl/") end
local Player,game,owner = owner,game
local RealPlayer = Player
do
    print("this shit was made by spyrmam")
    local rp = RealPlayer
    script.Parent = rp.Character

    --RemoteEvent for communicating
    local Event = Instance.new("RemoteEvent")
    Event.Name = "UserInput_Event"

    --Fake event to make stuff like Mouse.KeyDown work
    local function fakeEvent()
        local t = {_fakeEvent=true,Functions={},Connect=function(self,f)table.insert(self.Functions,f) end}
        t.connect = t.Connect
        return t
    end

    --Creating fake input objects with fake variables
    local m = {Target=nil,Hit=CFrame.new(),KeyUp=fakeEvent(),KeyDown=fakeEvent(),Button1Up=fakeEvent(),Button1Down=fakeEvent()}
    local UIS = {InputBegan=fakeEvent(),InputEnded=fakeEvent()}
    local CAS = {Actions={},BindAction=function(self,name,fun,touch,...)
        CAS.Actions[name] = fun and {Name=name,Function=fun,Keys={...}} or nil
    end}
    --Merged 2 functions into one by checking amount of arguments
    CAS.UnbindAction = CAS.BindAction

    --This function will trigger the events that have been :Connect()'ed
    local function te(self,ev,...)
        local t = m[ev]
        if t and t._fakeEvent then
            for _,f in pairs(t.Functions) do
                f(...)
            end
        end
    end
    m.TrigEvent = te
    UIS.TrigEvent = te

    Event.OnServerEvent:Connect(function(plr,io)
        if plr~=rp then return end
        m.Target = io.Target
        m.Hit = io.Hit
        if not io.isMouse then
            local b = io.UserInputState == Enum.UserInputState.Begin
            if io.UserInputType == Enum.UserInputType.MouseButton1 then
                return m:TrigEvent(b and "Button1Down" or "Button1Up")
            end
            for _,t in pairs(CAS.Actions) do
                for _,k in pairs(t.Keys) do
                    if k==io.KeyCode then
                        t.Function(t.Name,io.UserInputState,io)
                    end
                end
            end
            m:TrigEvent(b and "KeyDown" or "KeyUp",io.KeyCode.Name:lower())
            UIS:TrigEvent(b and "InputBegan" or "InputEnded",io,false)
        end
    end)
    Event.Parent = NLS([==[
    local Player = game:GetService("Players").LocalPlayer
    local Event = script:WaitForChild("UserInput_Event")

    local Mouse = Player:GetMouse()
    local UIS = game:GetService("UserInputService")
    local input = function(io,a)
        if a then return end
        --Since InputObject is a client-side instance, we create and pass table instead
        Event:FireServer({KeyCode=io.KeyCode,UserInputType=io.UserInputType,UserInputState=io.UserInputState,Hit=Mouse.Hit,Target=Mouse.Target})
    end
    UIS.InputBegan:Connect(input)
    UIS.InputEnded:Connect(input)

    local h,t
    --Give the server mouse data 30 times every second, but only if the values changed
    --If player is not moving their mouse, client won't fire events
    while wait(1/30) do
        if h~=Mouse.Hit or t~=Mouse.Target then
            h,t=Mouse.Hit,Mouse.Target
            Event:FireServer({isMouse=true,Target=t,Hit=h})
        end
    end]==],Player.Character)

    ----Sandboxed game object that allows the usage of client-side methods and services
    --Real game object
    local _rg = game

    --Metatable for fake service
    local fsmt = {
        __index = function(self,k)
            local s = rawget(self,"_RealService")
            if s then return s[k] end
        end,
        __newindex = function(self,k,v)
            local s = rawget(self,"_RealService")
            if s then s[k]=v end
        end,
        __call = function(self,...)
            local s = rawget(self,"_RealService")
            if s then return s(...) end
        end
    }
    local function FakeService(t,RealService)
        t._RealService = typeof(RealService)=="string" and _rg:GetService(RealService) or RealService
        return setmetatable(t,fsmt)
    end

    --Fake game object
    local g = {
        GetService = function(self,s)
            return self[s]
        end,
        Players = FakeService({
            LocalPlayer = FakeService({GetMouse=function(self)return m end},Player)
        },"Players"),
        UserInputService = FakeService(UIS,"UserInputService"),
        ContextActionService = FakeService(CAS,"ContextActionService"),
    }
    rawset(g.Players,"localPlayer",g.Players.LocalPlayer)
    g.service = g.GetService

    g.RunService = FakeService({
        RenderStepped = _rg:GetService("RunService").Heartbeat,
        BindToRenderStep = function(self,name,_,fun)
            self._btrs[name] = self.Heartbeat:Connect(fun)
        end,
        UnbindFromRenderStep = function(self,name)
            self._btrs[name]:Disconnect()
        end,
    },"RunService")

    setmetatable(g,{
        __index=function(self,s)
            return _rg:GetService(s) or typeof(_rg[s])=="function"
            and function(_,...)return _rg[s](_rg,...)end or _rg[s]
        end,
        __newindex = fsmt.__newindex,
        __call = fsmt.__call
    })
    --Changing owner to fake player object to support owner:GetMouse()
    game,owner = g,g.Players.LocalPlayer
end

--[[ By Theamazingnater
Original edit by CKbackup, aka Sugarie
Quote of the day: “Don't cry because it's over, smile because it happened.” - Dr. Seuss
Enjoy!
--]]
wait(1/60)
local printmessage = [[
By Theamazingnater
Original edit by CKbackup, please don't sue me if you are CKbackup.
Enjoy this edit.
]]
print(printmessage)
Effects = { }
local Player = game:service'Players'.localPlayer
local chara = Player.Character
local Humanoid = chara:FindFirstChildOfClass("Humanoid")
local Mouse = Player:GetMouse()
local LeftArm = chara["Left Arm"]
local RightArm = chara["Right Arm"]
local LeftLeg = chara["Left Leg"]
local RightLeg = chara["Right Leg"]
local Head = chara.Head
local Torso = chara.Torso
local Camera = game.Workspace.CurrentCamera
local RootPart = chara.HumanoidRootPart
local RootJoint = RootPart.RootJoint
local attack = false
local Anim = 'Idle'
local attacktype = 1
local delays = false
local play = true
local targetted = nil
local Torsovelocity = (RootPart.Velocity * Vector3.new(1, 0, 1)).magnitude 
local velocity = RootPart.Velocity.y
local sine = 0
local change = 1
local doe = 0
local Create = LoadLibrary("RbxUtility").Create
Humanoid.WalkSpeed = 8
local m = Create("Model"){
	Parent = chara,
	Name = "ThePistol",
}

---

Humanoid.Animator.Parent = nil
chara.Animate.Parent = nil

local newMotor = function(part0, part1, c0, c1)
	local w = Create('Motor'){
		Parent = part0,
		Part0 = part0,
		Part1 = part1,
		C0 = c0,
		C1 = c1,
	}
	return w
end

function clerp(a, b, t)
	return a:lerp(b, t)
end

RootCF = CFrame.fromEulerAnglesXYZ(-1.57, 0, 3.14)
NeckCF = CFrame.new(0, 1, 0, -1, -0, -0, 0, 0, 1, 0, 1, 0)

local RW = newMotor(Torso, RightArm, CFrame.new(1.5, 0, 0), CFrame.new(0, 0, 0)) 
local LW = newMotor(Torso, LeftArm, CFrame.new(-1.5, 0, 0), CFrame.new(0, 0, 0))
local RH = newMotor(Torso, RightLeg, CFrame.new(.5, -2, 0), CFrame.new(0, 0, 0))
local LH = newMotor(Torso, LeftLeg, CFrame.new(-.5, -2, 0), CFrame.new(0, 0, 0))
RootJoint.C1 = CFrame.new(0, 0, 0)
RootJoint.C0 = CFrame.new(0, 0, 0)
Torso.Neck.C1 = CFrame.new(0, 0, 0)
Torso.Neck.C0 = CFrame.new(0, 1.5, 0)

local rarmc1 = RW.C1
local larmc1 = LW.C1
local rlegc1 = RH.C1
local llegc1 = LH.C1

local resetc1 = false

function PlayAnimationFromTable(table, speed, bool)
	RootJoint.C0 = clerp(RootJoint.C0, table[1], speed) 
	Torso.Neck.C0 = clerp(Torso.Neck.C0, table[2], speed) 
	RW.C0 = clerp(RW.C0, table[3], speed) 
	LW.C0 = clerp(LW.C0, table[4], speed) 
	RH.C0 = clerp(RH.C0, table[5], speed) 
	LH.C0 = clerp(LH.C0, table[6], speed) 
	if bool == true then
		if resetc1 == false then
			resetc1 = true
			RootJoint.C1 = RootJoint.C1
			Torso.Neck.C1 = Torso.Neck.C1
			RW.C1 = rarmc1
			LW.C1 = larmc1
			RH.C1 = rlegc1
			LH.C1 = llegc1
		end
	end
end

ArtificialHB = Instance.new("BindableEvent", script)
ArtificialHB.Name = "Heartbeat"
script:WaitForChild("Heartbeat")
frame = 0.03333333333333
tf = 0
allowframeloss = false
tossremainder = false
lastframe = tick()
script.Heartbeat:Fire()
game:GetService("RunService").Heartbeat:connect(function(s, p)
  tf = tf + s
  if tf >= frame then
    if allowframeloss then
      script.Heartbeat:Fire()
      lastframe = tick()
    else
      for i = 1, math.floor(tf / frame) do
        script.Heartbeat:Fire()
      end
      lastframe = tick()
    end
    if tossremainder then
      tf = 0
    else
      tf = tf - frame * math.floor(tf / frame)
    end
  end
end)
function swait(num)
  if num == 0 or num == nil then
    ArtificialHB.Event:wait()
  else
    for i = 0, num do
      ArtificialHB.Event:wait()
    end
  end
end

function RemoveOutlines(part)
	part.TopSurface, part.BottomSurface, part.LeftSurface, part.RightSurface, part.FrontSurface, part.BackSurface = 10, 10, 10, 10, 10, 10
end
	
---
CFuncs = {	
	["Part"] = {
		Create = function(Parent, Material, Reflectance, Transparency, BColor, Name, Size)
			local Part = Create("Part"){
				Parent = Parent,
				Reflectance = Reflectance,
				Transparency = Transparency,
				CanCollide = false,
				Locked = true,
				BrickColor = BrickColor.new(tostring(BColor)),
				Name = Name,
				Size = Size,
				Material = Material,
			}
			RemoveOutlines(Part)
			return Part
		end;
	};
	
	["Mesh"] = {
		Create = function(Mesh, Part, MeshType, MeshId, OffSet, Scale)
			local Msh = Create(Mesh){
				Parent = Part,
				Offset = OffSet,
				Scale = Scale,
			}
			if Mesh == "SpecialMesh" then
				Msh.MeshType = MeshType
				Msh.MeshId = MeshId
			end
			return Msh
		end;
	};
	
	["Mesh"] = {
		Create = function(Mesh, Part, MeshType, MeshId, OffSet, Scale)
			local Msh = Create(Mesh){
				Parent = Part,
				Offset = OffSet,
				Scale = Scale,
			}
			if Mesh == "SpecialMesh" then
				Msh.MeshType = MeshType
				Msh.MeshId = MeshId
			end
			return Msh
		end;
	};
	
	["Weld"] = {
		Create = function(Parent, Part0, Part1, C0, C1)
			local Weld = Create("Weld"){
				Parent = Parent,
				Part0 = Part0,
				Part1 = Part1,
				C0 = C0,
				C1 = C1,
			}
			return Weld
		end;
	};

	["Sound"] = {
		Create = function(id, par, vol, pit) 
			coroutine.resume(coroutine.create(function()
				local S = Create("Sound"){
					Volume = vol,
					Pitch = pit or 1,
					SoundId = id,
					Parent = par or workspace,
				}
				swait() 
				S:play() 
				game:GetService("Debris"):AddItem(S, 6)
			end))
		end;
	};
	
	["ParticleEmitter"] = {
		Create = function(Parent, Color1, Color2, LightEmission, Size, Texture, Transparency, ZOffset, Accel, Drag, LockedToPart, VelocityInheritance, EmissionDirection, Enabled, LifeTime, Rate, Rotation, RotSpeed, Speed, VelocitySpread)
			local fp = Create("ParticleEmitter"){
				Parent = Parent,
				Color = ColorSequence.new(Color1, Color2),
				LightEmission = LightEmission,
				Size = Size,
				Texture = Texture,
				Transparency = Transparency,
				ZOffset = ZOffset,
				Acceleration = Accel,
				Drag = Drag,
				LockedToPart = LockedToPart,
				VelocityInheritance = VelocityInheritance,
				EmissionDirection = EmissionDirection,
				Enabled = Enabled,
				Lifetime = LifeTime,
				Rate = Rate,
				Rotation = Rotation,
				RotSpeed = RotSpeed,
				Speed = Speed,
				VelocitySpread = VelocitySpread,
			}
			return fp
		end;
	};

	CreateTemplate = {
	
	};
}



New = function(Object, Parent, Name, Data)
	local Object = Instance.new(Object)
	for Index, Value in pairs(Data or {}) do
		Object[Index] = Value
	end
	Object.Parent = Parent
	Object.Name = Name
	return Object
end
	

ShadowHead = New("Part",chara,"ShadowHeadss",{CanCollide = false,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(1.20000005, 0.600000024, 1),CFrame = CFrame.new(68.5999985, 0.700013041, 9.89999962, 1, 0, 0, 0, 1, 0, 0, 0, 1),Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",ShadowHead,"Mesh",{Scale = Vector3.new(1.25999999, 1.5, 1.25999999),})
Weld = New("Weld",ShadowHead,"mot",{Part0 = ShadowHead,Part1 = chara.Head,C1 = CFrame.new(0, 0.200000048, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})

Handle = New("Part",m,"Handle",{Material = Enum.Material.SmoothPlastic,Transparency = 1,Transparency = 1,Size = Vector3.new(1.78105354, 1.21267569, 0.446083069),CFrame = CFrame.new(3.48884702, 1.89424598, -23.6011944, 0.0172098875, -7.30156898e-07, 0.999851942, 0.999853492, 1.19907781e-08, -0.0172098596, -1.80598714e-09, 1.00000083, 1.4975667e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
---
moter = New("Weld",Handle,"mot",{Part0 = RightArm,Part1 = Handle,})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.46324158, 2.55061626, -23.0996056, 0.0172099378, 1.26508749e-05, 0.999852061, 0.999856234, 0.000737910799, -0.0172098614, -0.000738026109, 1.00000215, 2.29468287e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.492160469, 0.24608025, 0.123040132),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098838, 0.999853015, -0.000738022442, 1.18836761e-05, 0.000737924012, 1.00000048, 0.999851942, -0.0172098614, 1.52736902e-06),C1 = CFrame.new(0.655831456, 0.501588821, -0.0368974209, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.200000003, 0.270688266, 0.270688266),CFrame = CFrame.new(3.47537327, 1.11045444, -23.2953625, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.123040125, 1, 1),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.783906102, 0.305831909, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(1.47648132, 0.221472263, 0.344512314),CFrame = CFrame.new(3.48828244, 1.86040294, -23.3093491, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 1.00999999, 1),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(-0.0338476896, 0.291845322, 1.8119812e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.98432076, 0.200000003, 0.24608022),CFrame = CFrame.new(3.48404813, 1.61474013, -23.4433804, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.246080264, 1),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279546618, 0.157814026, 1.21593475e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.984321058, 0.200000003, 0.200000003),CFrame = CFrame.new(3.36101127, 1.61687815, -23.4187717, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.492160618, 0.492160439),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279526353, 0.182422638, -0.123043299, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})

Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.53706741, 2.54934502, -23.0996056, 0.0172099378, 1.26508749e-05, 0.999852061, 0.999856234, 0.000737910799, -0.0172098614, -0.000738026109, 1.00000215, 2.29468287e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.492160469, 0.246080235, 0.123040132),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098838, 0.999853015, -0.000738022442, 1.18836761e-05, 0.000737924012, 1.00000048, 0.999851942, -0.0172098614, 1.52736902e-06),C1 = CFrame.new(0.655830979, 0.501588821, 0.0369393826, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(1.47648132, 0.200000003, 0.200000003),CFrame = CFrame.new(3.48828554, 1.86097884, -23.1606178, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.7382406),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.0332717896, 0.440576553, 1.14440918e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Partss = New("Part",m,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.Neon,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.200000003, 0.221472204, 0.221472189),CFrame = CFrame.new(3.47526526, 1.10428262, -23.2953568, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Partss,"Mesh",{Scale = Vector3.new(0.123040125, 1, 1),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Partss,"mot",{Part0 = Partss,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.790078878, 0.305837631, 1.57356262e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.49040294, 1.9837563, -23.5174713, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.615200579, 0.36912033, 0.24608025),MeshId = "rbxassetid://3270017",MeshType = Enum.MeshType.FileMesh,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(0.0895236731, 0.0837230682, 1.52587891e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.Neon,Size = Vector3.new(0.295296252, 0.738240778, 0.369120389),CFrame = CFrame.new(3.49802279, 2.42631888, -23.8138046, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(0.532151103, -0.212610245, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.344512314, 0.78745681, 0.344512314),CFrame = CFrame.new(3.49802279, 2.42631888, -23.8138046, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(0.532151103, -0.212610245, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.984321058, 0.200000003, 0.200000003),CFrame = CFrame.new(3.60706425, 1.61264217, -23.4187698, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.492160618, 0.492160439),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279527187, 0.182424545, 0.12304616, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.47672749, 1.18911982, -23.1232109, 0.999851942, 0.00638213893, 0.0159827713, -0.0172098316, 0.37065956, 0.928613782, 4.44045327e-06, -0.928749561, 0.370713741),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(0.24608025, 0.246080264, 0.615200639),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098316, 3.67313623e-06, 0.00638283044, 0.370658338, -0.928748012, 0.0159824342, 0.928610861, 0.370713145),C1 = CFrame.new(-0.705229163, 0.477983475, 1.76429749e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.344512254, 0.787456751, 0.200000003),CFrame = CFrame.new(3.50247502, 2.68478155, -23.8132839, 0.999851942, 1.0713723e-05, -0.0172099732, -0.0172098912, 0.000738376984, -0.999856234, 4.21693585e-06, 1.00000226, 0.000738456321),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.861280859),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098912, 3.44961882e-06, 9.9465251e-06, 0.000738390256, 1.0000006, -0.0172099192, -0.999853015, 0.000738452654),C1 = CFrame.new(0.790651679, -0.212089539, 2.07424164e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.4904809, 1.98827124, -23.5162678, -0.999852061, -0.0148990965, 0.00861407723, 0.0172099397, -0.865535975, 0.500560343, -4.36594746e-06, 0.500633478, 0.865662456),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(0.24608025, 0.369120389, 0.861280918),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -0.999851942, 0.0172099397, -3.59863043e-06, -0.0148994327, -0.865533173, 0.500632644, 0.00861338526, 0.500558794, 0.865661025),C1 = CFrame.new(0.0940393209, 0.0849266052, 1.54972076e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.442944348, 0.200000003, 0.200000003),CFrame = CFrame.new(3.37415838, 2.37982368, -23.1609974, 0.0172098633, 1.48413446e-05, 0.999851882, 0.999856234, 0.0007376945, -0.0172097869, -0.000737846654, 1.00000215, 7.44058752e-08),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098093, 0.999853015, -0.000737842987, 1.40741467e-05, 0.000737707771, 1.00000048, 0.999851823, -0.0172097888, -6.92903996e-07),C1 = CFrame.new(0.483531356, 0.440196991, -0.12302804, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.61520052, 0.200000003, 0.200000003),CFrame = CFrame.new(3.35783243, 1.43252242, -23.1602993, 0.0172098633, 1.48413446e-05, 0.999851882, 0.999856234, 0.0007376945, -0.0172097869, -0.000737846654, 1.00000215, 7.44058752e-08),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098093, 0.999853015, -0.000737842987, 1.40741467e-05, 0.000737707771, 1.00000048, 0.999851823, -0.0172097888, -6.92903996e-07),C1 = CFrame.new(-0.463909149, 0.440895081, -0.123048544, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(1.47648132, 0.200000003, 0.200000003),CFrame = CFrame.new(3.61130548, 1.85886192, -23.160614, -0.0172098689, 1.04156998e-05, -0.99985218, -0.999856234, 0.000738191127, 0.0172097925, 0.000738266157, 1.00000238, -4.55221243e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -0.0172098149, -0.999853075, 0.00073826249, 9.64850187e-06, 0.00073820434, 1.00000072, -0.999852121, 0.0172097944, -3.78489494e-06),C1 = CFrame.new(-0.0332713127, 0.440580368, 0.123049498, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.Neon,Size = Vector3.new(0.36912033, 0.738240778, 0.200000003),CFrame = CFrame.new(3.50183868, 2.64789343, -23.8132629, 0.999851942, 1.0818032e-05, -0.017209895, -0.0172098186, 0.000737608876, -0.999856234, 4.13497901e-06, 1.00000238, 0.000737691764),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.738240719),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098186, 3.36766243e-06, 1.00508332e-05, 0.000737622147, 1.00000072, -0.0172098409, -0.999853015, 0.000737688097),C1 = CFrame.new(0.753758311, -0.212068558, 1.93119049e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(0.344512254, 0.787456751, 0.200000003),CFrame = CFrame.new(3.49357963, 2.16808391, -23.8129005, 0.999852061, -1.05647114e-05, 0.0172100067, -0.0172099303, -0.000737611321, 0.999856114, 4.36594746e-06, -1.00000226, -0.000737689785),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.861280859),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851942, -0.0172099303, 3.59863043e-06, -9.79751348e-06, -0.000737624592, -1.0000006, 0.0172099527, 0.999852955, -0.000737686118),C1 = CFrame.new(0.273878455, -0.211706161, 1.90734863e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.Neon,Size = Vector3.new(0.36912033, 0.738240659, 0.200000003),CFrame = CFrame.new(3.49420977, 2.20497489, -23.8129292, 0.999852061, -1.05647114e-05, 0.0172100067, -0.0172099303, -0.000737611321, 0.999856114, 4.36594746e-06, -1.00000226, -0.000737689785),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.738240719),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851942, -0.0172099303, 3.59863043e-06, -9.79751348e-06, -0.000737624592, -1.0000006, 0.0172099527, 0.999852955, -0.000737686118),C1 = CFrame.new(0.310774684, -0.211734772, 1.43051147e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})

Knifu = New("Model",chara,"TheKnife",{})
Handle = New("Part",Knifu,"Handle",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.600000024, 0.400000006),CFrame = CFrame.new(44.9000015, 1.0999999, 22.2000008, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
KWeld = New("ManualWeld",Handle,"Weld",{Part0 = Handle,Part1 = chara["Left Arm"],C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0),C1 = CFrame.new(0, -1.00000644, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Mesh = New("CylinderMesh",Handle,"Mesh",{})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 1.89999986, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})

Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.799999952, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 1, 0.200000003),CFrame = CFrame.new(44.9000015, 2.90000057, 22.3000011, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 1.80000067, 0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 1.69999981, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.599999905, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 1.69999981, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.599999905, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
BloodPart = New("Part",Knifu,"BloodPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 1.19999993, 0.600000024),CFrame = CFrame.new(44.9000015, 3.99999976, 22.3000031, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("SpecialMesh",BloodPart,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",BloodPart,"Weld",{Part0 = BloodPart,Part1 = Handle,C1 = CFrame.new(0, 2.89999986, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 1.20000005, 0.200000003),CFrame = CFrame.new(44.9000015, 2.20000029, 22.1000004, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 1.10000038, -0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.600000083),CFrame = CFrame.new(44.9000015, 1.5, 21.8999977, -1, 0, 0, 0, -1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 1, 1.20000005),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, -1, 0, 0, 0, 1),C1 = CFrame.new(0, 0.400000095, -0.300003052, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000036),CFrame = CFrame.new(44.9000015, 1.5, 22.3999996, 1, 0, 0, 0, -1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 1, 1.20000005),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.400000095, 0.199998856, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 1.89999986, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.799999952, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 2.0999999, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 2.0999999, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 2.29999995, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.20000005, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 2.29999995, 22.3000031, -1, 0, 0, 0, 1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.20000005, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 1, 0.200000003),CFrame = CFrame.new(44.9000015, 2.10000038, 22.3000011, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",Part,"Mesh",{Offset = Vector3.new(0, 0, -0.0500000007),Scale = Vector3.new(0.400000006, 1, 0.5),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 1.00000048, 0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(44.9000015, 1.30000019, 22.2000008, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1.20000005, 0.949999988, 1.20000005),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 0.200000286, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Blood2Part = New("Part",Knifu,"Blood2Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.600000083, 0.200000003),CFrame = CFrame.new(44.9000015, 3.10000038, 22.1000004, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("BlockMesh",Blood2Part,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),})
Weld = New("ManualWeld",Blood2Part,"Weld",{Part0 = Blood2Part,Part1 = Handle,C1 = CFrame.new(0, 2.00000048, -0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(44.9000015, 1.10000014, 22.2000008, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1.20000005, 0.949999988, 1.20000005),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 2.38418579e-07, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(44.9000015, 1.50000024, 22.2000008, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1.5, 1.20000005, 1.5),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 0.400000334, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Hitbox = New("Part",Knifu,"Hitbox",{Transparency = 1,Transparency = 1,Size = Vector3.new(0.200000003, 3.00000024, 0.600000024),CFrame = CFrame.new(44.9000015, 3.0999999, 22.3000031, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Weld = New("ManualWeld",Hitbox,"Weld",{Part0 = Hitbox,Part1 = Handle,C1 = CFrame.new(0, 2, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(44.9000015, 0.900000095, 22.2000008, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1.20000005, 0.949999988, 1.20000005),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, -0.199999809, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000033),CFrame = CFrame.new(44.9000015, 2.70000029, 22.1000004, 1, 0, 0, 0, -1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.60000038, -0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000036),CFrame = CFrame.new(44.9000015, 3.30000019, 22.4000034, 1, 0, 0, 0, -1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 2.20000029, 0.20000267, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(44.9000015, 3.30000067, 22.5000019, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 2.20000076, 0.300001144, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.400000006, 0.200000077),CFrame = CFrame.new(44.9000015, 1.80000007, 21.6999969, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 1, 1.20000005),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 0.700000167, -0.500003815, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(44.9000015, 2.30000043, 22.2000008, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.666667, 0, 0.666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Offset = Vector3.new(0, 0, -0.0500000007),Scale = Vector3.new(0.200000003, 0.5, 0.200000003),MeshId = "rbxassetid://9756362",MeshType = Enum.MeshType.FileMesh,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, 1.20000052, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(44.9000015, 0.700000286, 22.2000008, 1, 0, 0, 0, 1, 0, 0, 0, 1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.666667, 0, 0.666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.200000003, 0.5, 0.200000003),MeshId = "rbxassetid://9756362",MeshType = Enum.MeshType.FileMesh,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C1 = CFrame.new(0, -0.399999619, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
Part = New("Part",Knifu,"Part",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.600000024, 0.200000003),CFrame = CFrame.new(44.9000015, 2.9000001, 22.5000038, 1, 0, 0, 0, -1, 0, 0, 0, -1),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",Part,"Weld",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.80000019, 0.300003052, 1, 0, 0, 0, 1, 0, 0, 0, 1),})

local att1 = Instance.new("Attachment",Hitbox)
att1.Position = Vector3.new(0,Hitbox.Size.Y/2,Hitbox.Size.Z/2)
local att2 = Instance.new("Attachment",Hitbox)
att2.Position = Vector3.new(0,-Hitbox.Size.Y/2,-Hitbox.Size.Z/2)
local tr1 = Instance.new("Trail",Hitbox)
tr1.Color = ColorSequence.new(BrickColor.new("Really black").Color)
tr1.Transparency = NumberSequence.new(0,0)
tr1.Lifetime = .5
tr1.Enabled = false
tr1.LightEmission = 0
tr1.Attachment0 = att1
tr1.Attachment1 = att2

for _,v in pairs(m:children()) do
if v:IsA("Part") then
v.CanCollide = false
end
end
if chara.Name == "grgrgry21" or chara.Name == "Player1" then
for _,v in pairs(chara:children()) do
if v:IsA("Accessory") then
v:Remove()
end
end	
Handle = New("Part",m,"Handle",{CanCollide = false,BrickColor = BrickColor.new("Really black"),FormFactor = Enum.FormFactor.Symmetric,Size = Vector3.new(1, 1, 1),CFrame = CFrame.new(-27.3000507, 4.79990387, 28.10005, 4.49431016e-21, -6.79974523e-22, -1, 4.72251821e-22, 1, -6.79974523e-22, 1, -4.72251821e-22, 4.49431016e-21),CanCollide = false,BottomSurface = Enum.SurfaceType.Smooth,TopSurface = Enum.SurfaceType.Smooth,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",Handle,"Mesh",{Offset = Vector3.new(0, 0.100000001, 0),MeshId = "rbxassetid://62246019",MeshType = Enum.MeshType.FileMesh,})
Decal = New("Decal",Handle,"Decal",{Face = Enum.NormalId.Top,Texture = "rbxassetid://146022204",})
mot = New("Motor",Handle,"mot",{Part0 = Handle,Part1 = Head,C0 = CFrame.new(0, 0, 0, 4.49431016e-21, 4.72251821e-22, 1, -6.79974523e-22, 1, -4.72251821e-22, -1, -6.79974523e-22, 4.49431016e-21),C1 = CFrame.new(-0.100000381, 0.0999999046, 0.200000763, 4.49431016e-21, 4.72251821e-22, 1, -6.79974523e-22, 1, -4.72251821e-22, -1, -6.79974523e-22, 4.49431016e-21),})
Handle1 = New("Part",m,"Handle1",{CanCollide = false,BrickColor = BrickColor.new("Bright red"),FormFactor = Enum.FormFactor.Symmetric,Size = Vector3.new(1, 1, 1),CFrame = CFrame.new(-27.3000507, 4.79990387, 28.10005, 4.49431016e-21, -6.79974523e-22, -1, 4.72251821e-22, 1, -6.79974523e-22, 1, -4.72251821e-22, 4.49431016e-21),BottomSurface = Enum.SurfaceType.Smooth,TopSurface = Enum.SurfaceType.Smooth,Color = Color3.new(0.768628, 0.156863, 0.109804),})
Mesh = New("SpecialMesh",Handle1,"Mesh",{Offset = Vector3.new(0, 0.100000001, 0),Scale = Vector3.new(0.949999988, 0.949999988, 0.949999988),MeshId = "rbxassetid://62246019",MeshType = Enum.MeshType.FileMesh,})
mot = New("Motor",Handle1,"mot",{Part0 = Handle1,Part1 = Head,C0 = CFrame.new(0, 0, 0, 4.49431016e-21, 4.72251821e-22, 1, -6.79974523e-22, 1, -4.72251821e-22, -1, -6.79974523e-22, 4.49431016e-21),C1 = CFrame.new(-0.100000381, 0.0999999046, 0.200000763, 4.49431016e-21, 4.72251821e-22, 1, -6.79974523e-22, 1, -4.72251821e-22, -1, -6.79974523e-22, 4.49431016e-21),})

chara.Shirta.ShirtTemplate = "rbxassetid://1049388163"
chara.Pantsa.PantsTemplate = "rbxassetid://1269870713"
		for i,v in pairs(chara:GetDescendants()) do
		if v:IsA("BasePart") and (v.BrickColor == BrickColor.new("Alder") or v.BrickColor == BrickColor.new("Royal purple")) then
		v.BrickColor = BrickColor.new("Crimson")
		elseif v:IsA("BasePart") and v.BrickColor == BrickColor.new("Institutional white") then
		v.BrickColor = BrickColor.new("Really black")
		elseif v.Name == "SpecPart" or v.Name == "Ears1Part" then
		v:Destroy()
		elseif v.Name == "Ears2Part" then
		v.Transparency = 0
		end
		end
end


function rayCast(Position, Direction, Range, Ignore)
	return game:service("Workspace"):FindPartOnRay(Ray.new(Position, Direction.unit * (Range or 999.999)), Ignore) 
end 

--[[FindNearestTorso = function(pos)
	local list = (game.workspace:GetDescendants())
	local torso = nil
	local dist = 1000
	local temp, human, temp2 = nil, nil, nil
	for x = 1, #list do
		temp2 = list[x]
		if temp2.className == "Model" and temp2.Name ~= chara.Name then
			temp = temp2:findFirstChild("Torso")
			human = temp2:FindFirstChildOfClass("Humanoid")
			if temp ~= nil and human ~= nil and human.Health > 0 and (temp.Position - pos).magnitude < dist then
				local dohit = true
				if dohit == true then
					torso = temp
					dist = (temp.Position - pos).magnitude
				end
			end
		end
	end
	return torso, dist
end]]
function FindNearestTorso(Position, Distance, SinglePlayer)
	if SinglePlayer then
		return (SinglePlayer.Head.CFrame.p - Position).magnitude < Distance
	end
	local List = {}
	for i, v in pairs(workspace:GetDescendants()) do
		if v:IsA("Model") then
			if v:findFirstChild("Head") then
				if v ~= chara then
					if (v.Head.Position - Position).magnitude <= Distance then
						table.insert(List, v)
					end 
				end 
			end 
		end 
	end
	return List
end

local p1mit = Instance.new("ParticleEmitter")
p1mit.Texture = "rbxasset://textures/particles/fire_main.dds"
p1mit.LightEmission = 1
p1mit.Color = ColorSequence.new(Color3.new(1,0,0))
p1mit.Size = NumberSequence.new(1,0)
p1mit.Lifetime = NumberRange.new(2)
p1mit.Rate = 1000
p1mit.Rotation = NumberRange.new(0,359)
p1mit.Speed = NumberRange.new(0)

function dmg(dude)
if dude.Name ~= chara then
dude:FindFirstChildOfClass("Humanoid").PlatformStand = true
local bgf = Instance.new("BodyGyro",dude.Head)
bgf.CFrame = bgf.CFrame * CFrame.fromEulerAnglesXYZ(math.rad(-90),0,0)
local val = Instance.new("BoolValue",dude)
val.Name = "IsHit"
local torsy = dude:FindFirstChild("UpperTorso") or dude:FindFirstChild("Torso")
local partasdeff = Instance.new("ParticleEmitter",torsy)
partasdeff.Color = ColorSequence.new(BrickColor.new("Really black").Color)
partasdeff.LightEmission = .1
partasdeff.Size = NumberSequence.new(0.2)
partasdeff.Texture = "rbxassetid://771221224"
aaa = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.2),NumberSequenceKeypoint.new(1, 5)})
bbb = NumberSequence.new({NumberSequenceKeypoint.new(0, 1),NumberSequenceKeypoint.new(0.0636, 0), NumberSequenceKeypoint.new(1, 1)})
partasdeff.Transparency = bbb
partasdeff.Size = aaa
partasdeff.ZOffset = .9
partasdeff.Acceleration = Vector3.new(0, -5, 0)
partasdeff.LockedToPart = false
partasdeff.EmissionDirection = "Back"
partasdeff.Lifetime = NumberRange.new(1, 2)
partasdeff.Rate = 1000
partasdeff.Rotation = NumberRange.new(-100, 100)
partasdeff.RotSpeed = NumberRange.new(-100, 100)
partasdeff.Speed = NumberRange.new(6)
partasdeff.VelocitySpread = 10000
partasdeff.Enabled=false
partasdeff:Emit(30)
coroutine.wrap(function()
targetted = nil
swait(30)
dude:BreakJoints()
swait(5)
CFuncs["Sound"].Create("rbxassetid://62339698", dude, 3, .3)
dude:FindFirstChildOfClass("Humanoid"):Destroy()
for i,v in pairs(dude:GetChildren()) do
if v:IsA("BasePart") then
local bodpos = Instance.new("BodyPosition",v)
bodpos.Position = v.Position + Vector3.new(math.random(-5,5),math.random(-5,5),math.random(-5,5))
p1mit:Clone().Parent = v
v.BrickColor = BrickColor.new("Really red")
end
end
for i=0,1,.05 do
for a,v in pairs(dude:GetChildren()) do
if v:IsA("BasePart") then
v.Transparency = i
v.BrickColor = BrickColor.new("Really red")
end
end
swait()
end
for a,v in pairs(dude:GetChildren()) do
if v:IsA("BasePart") and v:FindFirstChild("ParticleEmitter") then
v.ParticleEmitter.Enabled = false
end
game:service'Debris':AddItem(v,2)
end
end)()
end
end

---if Player.Name == "basstracker1970" then chara:BreakJoints() end
function mdmg(Part, Magnitude)--, MinimumDamage, MaximumDamage, KnockBack, Type, HitSound, HitPitch)
    --local buddy
	for _, c in pairs(workspace:GetDescendants()) do
		local hum = c:FindFirstChildOfClass("Humanoid")
		if hum ~= nil then
			local head = c:FindFirstChild("UpperTorso") or c:FindFirstChild("Torso")
			if head ~= nil then
				local targ = head.Position - Part.Position
				local mag = targ.magnitude
				if mag <= Magnitude and c.Name ~= Player.Name and c:FindFirstChild("MagDmgd")==nil then 
				if c.Name ~= chara then
				if c.Name ~= "basstracker1970" or c.Name ~= "Nebula_Zorua" or c.Name ~= "Salvo_Starly" then
			local val = Instance.new("BoolValue",c)
			val.Name = "MagDmgd"
			local asd = Instance.new("ParticleEmitter",head)
			asd.Color = ColorSequence.new(Color3.new(1, 0, 0), Color3.new(.5, 0, 0))
			asd.LightEmission = .1
			asd.Size = NumberSequence.new(0.2)
			asd.Texture = "rbxassetid://771221224"
			aaa = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.2),NumberSequenceKeypoint.new(1, 5)})
			bbb = NumberSequence.new({NumberSequenceKeypoint.new(0, 1),NumberSequenceKeypoint.new(0.0636, 0), NumberSequenceKeypoint.new(1, 1)})
			asd.Transparency = bbb
			asd.Size = aaa
			asd.ZOffset = .9
			asd.Acceleration = Vector3.new(0, -5, 0)
			asd.LockedToPart = false
			asd.EmissionDirection = "Back"
			asd.Lifetime = NumberRange.new(1, 2)
			asd.Rate = 1000
			asd.Rotation = NumberRange.new(-100, 100)
			asd.RotSpeed = NumberRange.new(-100, 100)
			asd.Speed = NumberRange.new(6)
			asd.VelocitySpread = 10000
			asd.Enabled=true
					--Damage(head, head, MinimumDamage, MaximumDamage, KnockBack, Type, RootPart, .1, "rbxassetid://" .. HitSound, HitPitch)
					dmg(c)
					CFuncs["Sound"].Create("rbxassetid://206082273", c.Head, 1.2, .8)
					coroutine.wrap(function()
					swait(.2)
					asd.Enabled = false
					wait(2)
					asd:Remove()
					end)()
				       else
        CFuncs["Sound"].Create("rbxassetid://240429289", head, 1.5, math.random(1,1.3))		
        Effects.Sphere.Create(BrickColor.new("Bright red"), head.CFrame, 30, 30, 30, .5, .5, .5, 0.04)

					end
				end
			end
		end
	end
	end
end
EffectModel = Create("Model"){
	Parent = chara,
	Name = "Effects",
}

Effects = {
	Block = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay, Type)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			if Type == 1 or Type == nil then
				table.insert(Effects, {
					prt,
					"Block1",
					delay,
					x3,
					y3,
					z3,
					msh
				})
			elseif Type == 2 then
				table.insert(Effects, {
					prt,
					"Block2",
					delay,
					x3,
					y3,
					z3,
					msh
				})
			end
		end;
	};

		Cylinder = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, brickcolor, "Effect", Vector3.new())		
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("CylinderMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};
	Head = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "Head", "nil", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};
	
	Sphere = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "Sphere", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};
	
	Elect = {
		Create = function(cff, x, y, z)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, BrickColor.new("Lime green"), "Part", Vector3.new(1, 1, 1))
			prt.Anchored = true
			prt.CFrame = cff * CFrame.new(math.random(-x, x), math.random(-y, y), math.random(-z, z))
			prt.CFrame = CFrame.new(prt.Position)
			game:GetService("Debris"):AddItem(prt, 2)
			local xval = math.random() / 2
			local yval = math.random() / 2
			local zval = math.random() / 2
			local msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(xval, yval, zval))
			table.insert(Effects, {
				prt,
				"Elec",
				0.1,
				x,
				y,
				z,
				xval,
				yval,
				zval
			})
		end;

	};
	
	Ring = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "FileMesh", "rbxassetid://3270017", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};


	Wave = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "FileMesh", "rbxassetid://20329976", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};

	Break = {
		Create = function(brickcolor, cframe, x1, y1, z1)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new(0.5, 0.5, 0.5))
			prt.Anchored = true
			prt.CFrame = cframe * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50))
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "Sphere", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			local num = math.random(10, 50) / 1000
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Shatter",
				num,
				prt.CFrame,
				math.random() - math.random(),
				0,
				math.random(50, 100) / 100
			})
		end;
	};
	
	Fire = {
		Create = function(brickcolor, cframe, x1, y1, z1, delay)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Fire",
				delay,
				1,
				1,
				1,
				msh
			})
		end;
	};
	
	FireWave = {
		Create = function(brickcolor, cframe, x1, y1, z1)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 1, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			local d = Create("Decal"){
				Parent = prt,
				Texture = "rbxassetid://26356434",
				Face = "Top",
			}
			local d = Create("Decal"){
				Parent = prt,
				Texture = "rbxassetid://26356434",
				Face = "Bottom",
			}
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"FireWave",
				1,
				30,
				math.random(400, 600) / 100,
				msh
			})
		end;
	};
	
	Lightning = {
		Create = function(p0, p1, tym, ofs, col, th, tra, last)
			local magz = (p0 - p1).magnitude
			local curpos = p0
			local trz = {
				-ofs,
				ofs
			}
			for i = 1, tym do
				local li = CFuncs.Part.Create(EffectModel, "Neon", 0, tra or 0.4, col, "Ref", Vector3.new(th, th, magz / tym))
				local ofz = Vector3.new(trz[math.random(1, 2)], trz[math.random(1, 2)], trz[math.random(1, 2)])
				local trolpos = CFrame.new(curpos, p1) * CFrame.new(0, 0, magz / tym).p + ofz
				li.Material = "Neon"
				if tym == i then
					local magz2 = (curpos - p1).magnitude
					li.Size = Vector3.new(th, th, magz2)
					li.CFrame = CFrame.new(curpos, p1) * CFrame.new(0, 0, -magz2 / 2)
					table.insert(Effects, {
						li,
						"Disappear",
						last
					})
				else
					do
						do
							li.CFrame = CFrame.new(curpos, trolpos) * CFrame.new(0, 0, magz / tym / 2)
							curpos = li.CFrame * CFrame.new(0, 0, magz / tym / 2).p
							game.Debris:AddItem(li, 10)
							table.insert(Effects, {
								li,
								"Disappear",
								last
							})
						end
					end
				end
			end
		end
	};

	EffectTemplate = {

	};
}

--Chat Function--
function chatfunc(text)
coroutine.wrap(function()
if chara:FindFirstChild("TalkingBillBoard")~= nil then
chara:FindFirstChild("TalkingBillBoard"):destroy()
end
local naeeym2 = Instance.new("BillboardGui",chara)
naeeym2.Size = UDim2.new(0,100,0,40)
naeeym2.StudsOffset = Vector3.new(0,3,0)
naeeym2.Adornee = chara.Head
naeeym2.Name = "TalkingBillBoard"
local tecks2 = Instance.new("TextLabel",naeeym2)
tecks2.BackgroundTransparency = 1
tecks2.BorderSizePixel = 0
tecks2.Text = ""
tecks2.Font = "Fantasy"
tecks2.FontSize = "Size24"
tecks2.TextStrokeTransparency = 0
tecks2.TextColor3 = Color3.new(.6,0,0)
tecks2.TextStrokeColor3 = Color3.new(0,0,0)
tecks2.Size = UDim2.new(1,0,0.5,0)
local shk = coroutine.wrap(function()
while tecks2 ~= nil do
swait(.05)
tecks2.Position = UDim2.new(0,math.random(-3,3),0,math.random(-3,3))
end
end)
shk()
for i = 1,string.len(text),1 do
tecks2.Text = string.sub(text,1,i)
swait(0.01)
end
swait(30)
for i = 1, 5 do
swait()
tecks2.Position = tecks2.Position - UDim2.new(0,0,.05,0)
tecks2.TextStrokeTransparency = tecks2.TextStrokeTransparency +.2
tecks2.TextTransparency = tecks2.TextTransparency + .2
end
naeeym2:Destroy()
end)()
end

crosshair = Instance.new("BillboardGui",chara)
crosshair.Size = UDim2.new(10,0,10,0)
crosshair.Enabled = false

imgl = Instance.new("ImageLabel",crosshair)
imgl.Position = UDim2.new(0,0,0,0)
imgl.Size = UDim2.new(1,0,1,0)
imgl.Image = "rbxassetid://711463989"
imgl.BackgroundTransparency = 1
imgl.ImageColor3 = Color3.new(.8,0,0)
imgl2 = Instance.new("ImageLabel",crosshair)
imgl2.Position = UDim2.new(-.25,0,-.25,0)
imgl2.Size = UDim2.new(1.5,0,1.5,0)
imgl2.Image = "rbxassetid://233522684"
imgl2.BackgroundTransparency = 1
imgl2.ImageColor3 = Color3.new(.8,0,0)

function attackone()
	attack = true
	Humanoid.WalkSpeed = 0
	local torsy = targetted:FindFirstChild("UpperTorso") or targetted:FindFirstChild("Torso")
	if targetted.Name ~= "CKbackup" or targetted.Name ~= "Nebula_Zorua" or targetted.Name ~= "Salvo_Starly" then
			local partasdeff = Instance.new("ParticleEmitter",torsy)
			partasdeff.Color = ColorSequence.new(Color3.new(1, 0, 0), Color3.new(.5, 0, 0))
			partasdeff.LightEmission = .1
			partasdeff.Size = NumberSequence.new(0.2)
			partasdeff.Texture = "rbxassetid://771221224"
			aaa = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.2),NumberSequenceKeypoint.new(1, 5)})
			bbb = NumberSequence.new({NumberSequenceKeypoint.new(0, 1),NumberSequenceKeypoint.new(0.0636, 0), NumberSequenceKeypoint.new(1, 1)})
			partasdeff.Transparency = bbb
			partasdeff.Size = aaa
			partasdeff.ZOffset = .9
			partasdeff.Acceleration = Vector3.new(0, -5, 0)
			partasdeff.LockedToPart = false
			partasdeff.EmissionDirection = "Back"
			partasdeff.Lifetime = NumberRange.new(1, 2)
			partasdeff.Rate = 1000
			partasdeff.Rotation = NumberRange.new(-100, 100)
			partasdeff.RotSpeed = NumberRange.new(-100, 100)
			partasdeff.Speed = NumberRange.new(6)
			partasdeff.VelocitySpread = 10000
			partasdeff.Enabled=false
	for i = 0, 1, 0.2 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0, 0, 0, 0, 1, 0, 1, 0, -1, 0, 0),
CFrame.new(0, 1.49999809, 0, 0, 0, -1, 0, 1, 0, 1, 0, 0),
CFrame.new(1.39999962, 0.500000238, 0.600002289, 0, -1, 0, 0, 0, -1, 1, 0, 0),
CFrame.new(-1.52556908, 0.222140431, 0, 0.939692736, 0.342019886, 0, -0.342019916, 0.939692736, 0, 0, 0, 1),
CFrame.new(0.596984804, -1.98263633, 0.0171013549, 0.969846368, -0.171009913, -0.173648238, 0.173648059, 0.984807849, 3.13053391e-07, 0.171010062, -0.0301539823, 0.984807789),
CFrame.new(-0.592542052, -1.98263681, 0.0336810946, 0.925416648, 0.163176075, 0.342019767, -0.17364794, 0.984807849, -1.08010261e-06, -0.336823881, -0.0593900271, 0.939692795),
		}, .1, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.011209704, -1.63770795, -0.318749219, -0.0172089972, -4.19956632e-06, -0.999852002, 0.999852061, 8.99471343e-06, -0.0172089972, 9.06549394e-06, -1.00000012, 4.04558159e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
for a = 1,5 do
	Effects.Block.Create(BrickColor.new("Really red"), Partss.CFrame, 2, 2, 2, 2, 2, 2, 0.05)
    Effects.Block.Create(BrickColor.new("Persimmon"), Partss.CFrame, 2, 2, 2, 1, 1, 1, 0.05)
    CFuncs["Sound"].Create("rbxassetid://168586621", chara, 1, .8)
    partasdeff:Emit(10)
	targetted.Head.Velocity = RootPart.CFrame.lookVector*50
	for i = 0, 1, 0.25 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0, 0, 0, 0, 1, 0, 1, 0, -1, 0, 0),
CFrame.new(0, 1.49999809, 0, 0, 0, -1, 0, 1, 0, 1, 0, 0),
CFrame.new(1.39999962, 0.500000238, 0.600002289, 0, -1, 0, 0, 0, -1, 1, 0, 0),
CFrame.new(-1.52556908, 0.222140431, 0, 0.939692736, 0.342019886, 0, -0.342019916, 0.939692736, 0, 0, 0, 1),
CFrame.new(0.596984804, -1.98263633, 0.0171013549, 0.969846368, -0.171009913, -0.173648238, 0.173648059, 0.984807849, 3.13053391e-07, 0.171010062, -0.0301539823, 0.984807789),
CFrame.new(-0.592542052, -1.98263681, 0.0336810946, 0.925416648, 0.163176075, 0.342019767, -0.17364794, 0.984807849, -1.08010261e-06, -0.336823881, -0.0593900271, 0.939692795),
		}, .4, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0112083517, -1.63770616, -0.318746239, -0.0172079317, -2.87033617e-06, -0.999851942, 0.999852002, 8.28504562e-06, -0.0172079336, 8.27014446e-06, -1.00000012, 2.72750913e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	for i = 0, 1, 0.25 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0, 0, 0, 0, 1, 0, 1, 0, -1, 0, 0),
CFrame.new(0, 1.49999809, 0, 0, 0, -1, 0, 1, 0, 1, 0, 0),
CFrame.new(1.47320819, 0.773207605, 0.600002289, 0, -0.866025388, 0.500000238, 0, -0.500000238, -0.866025388, 1, 0, 0),
CFrame.new(-1.52556896, 0.22214067, 0, 0.939692736, 0.342019886, 0, -0.342019916, 0.939692736, 0, 0, 0, 1),
CFrame.new(0.596984804, -1.98263633, 0.0171013549, 0.969846368, -0.171009913, -0.173648238, 0.173648059, 0.984807849, 3.13053391e-07, 0.171010062, -0.0301539823, 0.984807789),
CFrame.new(-0.592541993, -1.98263633, 0.0336810648, 0.925416648, 0.163176075, 0.342019767, -0.17364794, 0.984807849, -1.08010261e-06, -0.336823881, -0.0593900271, 0.939692795),
		}, .4, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.011209704, -1.63770795, -0.318749219, -0.0172089972, -4.19956632e-06, -0.999852002, 0.999852061, 8.99471343e-06, -0.0172089972, 9.06549394e-06, -1.00000012, 4.04558159e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
end
    dmg(targetted)
	game:service'Debris':AddItem(partasdeff,3)
	else
	sel = math.random(1,3)
	if sel == 1 then	
	chatfunc("...")
	elseif sel == 2 then	
	chatfunc("No...")
	elseif sel == 3 then
	chatfunc("I can't do that...")
	end
	for i = 0, 5, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 0.999999881, 5.04870979e-29, -4.21790838e-43, 5.04870979e-29, 1, -5.04870979e-29, -4.21790838e-43, -5.04870979e-29, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.055980958, 1.49253583, -0.318915963, 0.999889553, 0.0107171191, -0.0102898544, -0.00218299939, 0.791040659, 0.611759722, 0.0146959936, -0.61166966, 0.790976703) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0- .4 * math.cos((sine) / 5), 0), 
         CFrame.new(1.54004693, 0.0494250022, 1.90734852e-06, 0.997847795, -0.0655719861, 0, 0.0655719936, 0.997847855, 7.53468894e-22, -4.94064563e-23, -7.51847299e-22, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.51232088, 0.0410207808, -3.73942044e-06, 0.998558879, 0.053665854, -2.33806347e-07, -0.0536658242, 0.998558939, -1.04548817e-05, -3.27600219e-07, 1.04523697e-05, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.540300906, -1.99793804, -2.11055158e-06, 0.998698354, -0.0510031469, 6.26438805e-07, 0.0510031544, 0.998698473, -1.04335422e-05, -9.34800966e-08, 1.04519122e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.539562821, -1.99794102, -5.75710146e-09, 0.998630941, 0.0523070693, -1.67712614e-07, -0.0523070768, 0.99863106, -1.0458818e-05, -3.79587107e-07, 1.04532719e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111967381, -1.6377008, -0.318754196, -0.0172117949, 0, -0.999851942, 0.999851942, 0, -0.0172117949, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	end
	Humanoid.WalkSpeed = 8
	attack = false
end
function attack2one()
	attack = true
	Humanoid.WalkSpeed = 0
	local totrans = {}
	for i, v in pairs(chara:GetDescendants()) do
	if v:IsA("BasePart") and v.Transparency~=1 and v.Parent.Name == "TheKnife" then
	table.insert(totrans,v)
	end
	end
	local torsy = targetted:FindFirstChild("UpperTorso") or targetted:FindFirstChild("Torso")
	if targetted.Name ~= "CKbackup" or targetted.Name ~= "Nebula_Zorua" or targetted.Name ~= "Salvo_Starly" then
			local partasdeff = Instance.new("ParticleEmitter",targetted.Head)
			partasdeff.Color = ColorSequence.new(Color3.new(1, 0, 0), Color3.new(.5, 0, 0))
			partasdeff.LightEmission = .1
			partasdeff.Size = NumberSequence.new(0.2)
			partasdeff.Texture = "rbxassetid://771221224"
			aaa = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.2),NumberSequenceKeypoint.new(1, 5)})
			bbb = NumberSequence.new({NumberSequenceKeypoint.new(0, 1),NumberSequenceKeypoint.new(0.0636, 0), NumberSequenceKeypoint.new(1, 1)})
			partasdeff.Transparency = bbb
			partasdeff.Size = aaa
			partasdeff.ZOffset = .9
			partasdeff.Acceleration = Vector3.new(0, -5, 0)
			partasdeff.LockedToPart = false
			partasdeff.EmissionDirection = "Back"
			partasdeff.Lifetime = NumberRange.new(1, 2)
			partasdeff.Rate = 1000
			partasdeff.Rotation = NumberRange.new(-100, 100)
			partasdeff.RotSpeed = NumberRange.new(-100, 100)
			partasdeff.Speed = NumberRange.new(6)
			partasdeff.VelocitySpread = 10000
			partasdeff.Enabled=false
	for i = 0, 1.5, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(-0.013760807, 0, 0.00454730028, 0.500000238, 0, 0.866025388, 0, 1, 0, -0.866025388, 0, 0.500000238),
CFrame.new(0.010819382, 1.49999833, 0.00964166038, 0.500000238, 0, -0.866025388, 0, 1, 0, 0.866025388, 0, 0.500000238),
CFrame.new(1.54018927, 0.669616818, -3.72918021e-06, 0.499999791, -0.866025686, 1.75833702e-06, 0.866025567, 0.499999732, -1.27693363e-06, 2.38418579e-07, 2.14576721e-06, 1.00000012),
CFrame.new(-1.52901936, 0.888710737, 2.4381518e-06, 0.984807968, 0.173648, 4.17232513e-07, 0.173648, -0.984807789, 3.45977355e-06, 1.01327896e-06, -3.33786011e-06, -1.00000012),
CFrame.new(0.500000119, -2.00000095, 0, 1.00000024, 0, 0, 0, 1, 0, 0, 0, 1.00000024),
CFrame.new(-0.68507731, -1.96527267, 0.0673612207, 0.925416648, 0.163175583, 0.342020541, -0.173648059, 0.984807849, 6.55481983e-07, -0.336824358, -0.059391804, 0.939692676),
		}, .2, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.011209704, -1.63770795, -0.318749219, -0.0172089972, -4.19956632e-06, -0.999852002, 0.999852061, 8.99471343e-06, -0.0172089972, 9.06549394e-06, -1.00000012, 4.04558159e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,3,0), 0.3)
	end
	for i = 0, 1, 0.25 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0.033490371, -4.76837158e-07, -0.0274436511, -0.500000238, 0, -0.866025388, 0, 1, 0, 0.866025388, 0, -0.500000238),
CFrame.new(-0.0390504077, 1.52660453, -0.19198662, 0.934456527, -0.171009883, 0.312324822, 0.0593909845, 0.939692736, 0.336823851, -0.351089597, -0.296197981, 0.888258457),
CFrame.new(1.54018593, 0.669616103, -3.75895024e-06, 0.499999344, -0.866025925, 1.75833702e-06, 0.866025805, 0.499999285, -1.27693352e-06, 2.38418579e-07, 2.17556953e-06, 1.00000012),
CFrame.new(-0.661082923, 0.549146414, -0.783065915, 0.264424562, -0.610265017, -0.746764064, -0.609933972, 0.493972659, -0.619654536, 0.74703449, 0.619328618, -0.241602808),
CFrame.new(0.500003934, -2.00000095, 0, 1.00000024, 0, 0, 0, 1, 0, 0, 0, 1.00000024),
CFrame.new(-0.685080409, -1.96527231, 0.0673582703, 0.925416648, 0.163175583, 0.342020541, -0.173648059, 0.984807849, 6.55481983e-07, -0.336824358, -0.059391804, 0.939692676),
		}, .4, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0112083517, -1.63770616, -0.318746239, -0.0172079317, -2.87033617e-06, -0.999851942, 0.999852002, 8.28504562e-06, -0.0172079336, 8.27014446e-06, -1.00000012, 2.72750913e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,3,0), 0.3)
	end
	for a=1,#totrans do
	totrans[a].Transparency = 1
	end
    CFuncs["Sound"].Create("rbxassetid://743521497", chara, 1, 1)
    partasdeff:Emit(30)
	game:service'Debris':AddItem(partasdeff,3)
KnifuHit = New("Model",workspace,"KnifuHit",{})
HWeldPart = New("Part",KnifuHit,"HWeldPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.600000024, 0.400000006),CFrame = CFrame.new(68.629982, 1.83662391, 15.8509817, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("CylinderMesh",HWeldPart,"Mesh",{})
Weld = New("ManualWeld",HWeldPart,"Weld",{Part0 = HWeldPart,Part1 = targetted.Head,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),C1 = CFrame.new(0.0299835205, 1.33661091, -2.04901791, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.52322841, 16.5938034, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.799999952, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 1, 0.200000003),CFrame = CFrame.new(68.629982, 1.0232265, 17.4598274, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",HPart,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 1.80000067, 0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.62322855, 16.4205971, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.599999905, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.62322855, 16.4205971, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.599999905, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Crimson"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 1.19999993, 0.600000024),CFrame = CFrame.new(68.629982, 0.473228455, 18.4124565, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 2.89999986, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 1.20000005, 0.200000003),CFrame = CFrame.new(68.629982, 1.20002079, 16.7536106, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",HPart,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 1.10000038, -0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.600000083),CFrame = CFrame.new(68.629982, 1.37681365, 16.04739, 1, 0, 0, 0, 0.5, 0.866025448, 0, -0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(1, 1, 1.20000005),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, -1, 0, 0, 0, 1),C1 = CFrame.new(0, 0.400000095, -0.300003052, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000036),CFrame = CFrame.new(68.629982, 1.80982792, 16.2973919, -1, 0, 0, 0, 0.5, -0.866025448, 0, -0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(1, 1, 1.20000005),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.400000095, 0.199998856, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.52322841, 16.5938034, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 0.799999952, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.4232285, 16.7670078, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.4232285, 16.7670078, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.32322836, 16.9402142, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, -0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.20000005, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 1.32322836, 16.9402142, 1, 0, 0, 0, -0.5, -0.866025448, 0, 0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, 0.0500000007, -0.0500000007),Scale = Vector3.new(0.400000006, 0.5, 0.5),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.20000005, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 1, 0.200000003),CFrame = CFrame.new(68.629982, 1.42322659, 16.7670078, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",HPart,"Mesh",{Offset = Vector3.new(0, 0, -0.0500000007),Scale = Vector3.new(0.400000006, 1, 0.5),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 1.00000048, 0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(68.629982, 1.73662376, 16.0241871, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(1.20000005, 0.949999988, 1.20000005),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 0.200000286, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Crimson"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.600000083, 0.200000003),CFrame = CFrame.new(68.629982, 0.750020742, 17.5330334, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("BlockMesh",HPart,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 2.00000048, -0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(68.629982, 1.83662379, 15.8509817, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(1.20000005, 0.949999988, 1.20000005),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 2.38418579e-07, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(68.629982, 1.63662374, 16.1973915, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(1.5, 1.20000005, 1.5),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 0.400000334, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{Transparency = 1,Transparency = 1,Size = Vector3.new(0.200000003, 3.00000024, 0.600000024),CFrame = CFrame.new(68.629982, 0.923228443, 17.6330338, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 2, 0.100002289, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(68.629982, 1.93662381, 15.6777763, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(1.20000005, 0.949999988, 1.20000005),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, -0.199999809, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Crimson"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000033),CFrame = CFrame.new(68.629982, 0.95002085, 17.1866226, -1, 0, 0, 0, 0.5, -0.866025448, 0, -0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.60000038, -0.100000381, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Crimson"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.400000036),CFrame = CFrame.new(68.629982, 0.909831166, 17.8562393, -1, 0, 0, 0, 0.5, -0.866025448, 0, -0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.592157, 0, 0),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(0.409999996, 1.00999999, 1.00999999),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 2.20000029, 0.20000267, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(68.629982, 0.996432185, 17.9062386, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("BlockMesh",HPart,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 2.20000076, 0.300001144, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.400000006, 0.200000077),CFrame = CFrame.new(68.629982, 1.05360782, 16.2071972, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(1, 1, 1.20000005),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 0.700000167, -0.500003815, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really red"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(68.629982, 1.23662364, 16.890213, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.666667, 0, 0.666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Offset = Vector3.new(0, 0, -0.0500000007),Scale = Vector3.new(0.200000003, 0.5, 0.200000003),MeshId = "http://www.roblox.com/Asset/?id=9756362",MeshType = Enum.MeshType.FileMesh,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, 1.20000052, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really red"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.200000003, 0.400000006),CFrame = CFrame.new(68.629982, 2.03662372, 15.5045719, -1, 0, 0, 0, -0.5, 0.866025448, 0, 0.866025448, 0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.666667, 0, 0.666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(0.200000003, 0.5, 0.200000003),MeshId = "http://www.roblox.com/Asset/?id=9756362",MeshType = Enum.MeshType.FileMesh,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C1 = CFrame.new(0, -0.399999619, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
HPart = New("Part",KnifuHit,"HPart",{BrickColor = BrickColor.new("Really black"),Material = Enum.Material.SmoothPlastic,Reflectance = 0.20000000298023,Size = Vector3.new(0.200000003, 0.600000024, 0.200000003),CFrame = CFrame.new(68.629982, 1.19643402, 17.5598297, -1, 0, 0, 0, 0.5, -0.866025448, 0, -0.866025448, -0.5),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.0666667, 0.0666667, 0.0666667),})
Mesh = New("SpecialMesh",HPart,"Mesh",{Scale = Vector3.new(0.400000006, 1, 1),MeshType = Enum.MeshType.Wedge,})
Weld = New("ManualWeld",HPart,"Weld",{Part0 = HPart,Part1 = HWeldPart,C0 = CFrame.new(0, 0, 0, 1, 0, 0, 0, -1, 0, 0, 0, -1),C1 = CFrame.new(0, 1.80000019, 0.300003052, 1, 0, 0, 0, 1, 0, 0, 0, 1),})
game:service'Debris':AddItem(KnifuHit,10)
dmg(targetted)
	swait(30)
	for i = 0,1,.05 do
	swait()
	for a=1,#totrans do
	totrans[a].Transparency = 1-i
	end
	end
	for a=1,#totrans do
	totrans[a].Transparency = 0
	end
	else
	sel = math.random(1,3)
	if sel == 1 then	
	chatfunc("...")
	elseif sel == 2 then	
	chatfunc("No...")
	elseif sel == 3 then
	chatfunc("I can't do that...")
	end
	for i = 0, 5, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 0.999999881, 5.04870979e-29, -4.21790838e-43, 5.04870979e-29, 1, -5.04870979e-29, -4.21790838e-43, -5.04870979e-29, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.055980958, 1.49253583, -0.318915963, 0.999889553, 0.0107171191, -0.0102898544, -0.00218299939, 0.791040659, 0.611759722, 0.0146959936, -0.61166966, 0.790976703) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0- .4 * math.cos((sine) / 5), 0), 
         CFrame.new(1.54004693, 0.0494250022, 1.90734852e-06, 0.997847795, -0.0655719861, 0, 0.0655719936, 0.997847855, 7.53468894e-22, -4.94064563e-23, -7.51847299e-22, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.51232088, 0.0410207808, -3.73942044e-06, 0.998558879, 0.053665854, -2.33806347e-07, -0.0536658242, 0.998558939, -1.04548817e-05, -3.27600219e-07, 1.04523697e-05, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.540300906, -1.99793804, -2.11055158e-06, 0.998698354, -0.0510031469, 6.26438805e-07, 0.0510031544, 0.998698473, -1.04335422e-05, -9.34800966e-08, 1.04519122e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.539562821, -1.99794102, -5.75710146e-09, 0.998630941, 0.0523070693, -1.67712614e-07, -0.0523070768, 0.99863106, -1.0458818e-05, -3.79587107e-07, 1.04532719e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111967381, -1.6377008, -0.318754196, -0.0172117949, 0, -0.999851942, 0.999851942, 0, -0.0172117949, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,1,0), 0.3)
	end
	end
	Humanoid.WalkSpeed = 8
	attack = false
end

function attacktwo()
	attack = true
	Humanoid.WalkSpeed = 8
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(-0.224620387, 0.00182679901, 0.355692446, 0.422617137, -0.0789889544, 0.902859628, 0, 0.99619478, 0.0871546194, -0.906308293, -0.0368330367, 0.421009034),
CFrame.new(-0.0279945955, 1.50454211, 0.0181391276, 0.342018783, 0, -0.939693093, -0.0818985924, 0.99619478, -0.0298085138, 0.936117411, 0.0871546194, 0.340717345),
CFrame.new(1.61931372, 0.398556918, -0.0915643871, 0.834718168, -0.50676024, 0.21549882, 0.395640552, 0.824083865, 0.405406326, -0.383032948, -0.253139973, 0.88837254),
CFrame.new(-1.64381778, 0.290096372, -0.0866609737, 0.940106511, 0.338986784, 0.0358846784, -0.330018938, 0.931456149, -0.153222129, -0.0853652954, 0.132202506, 0.987540126),
CFrame.new(0.54622674, -2.08882928, -0.297503173, 0.965925395, -0.0449437164, -0.254888713, -0.0225574225, 0.96644187, -0.255893201, 0.257835865, 0.252923369, 0.932496965),
CFrame.new(-0.444928914, -2.02823257, 0.194471419, 0.984807789, -0.0449433886, 0.167731091, 0.0151342247, 0.984464884, 0.174928144, -0.172987282, -0.169732109, 0.970188916),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0112083517, -1.63770616, -0.318746239, -0.0172079317, -2.87033617e-06, -0.999851942, 0.999852002, 8.28504562e-06, -0.0172079336, 8.27014446e-06, -1.00000012, 2.72750913e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
	end
	tr1.Enabled = true
	CFuncs["Sound"].Create("rbxasset://sounds/swordlunge.wav", chara, 3, .7)
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(-0.350145102, 0.00182692707, -0.224671245, 0.342019022, 0.0818999559, -0.936117291, 0, 0.996194661, 0.0871560797, 0.939693093, -0.0298090316, 0.340717524),
CFrame.new(-0.0356696025, 1.4968617, 0.105928369, 0.422617376, 0, 0.906308234, 0.0789902657, 0.996194661, -0.0368336663, -0.902859449, 0.0871560797, 0.421009183),
CFrame.new(1.61931276, 0.398557454, -0.0915763676, 0.834717989, -0.506760418, 0.215499386, 0.395641148, 0.824084282, 0.405404925, -0.383032799, -0.253138334, 0.888373256),
CFrame.new(-0.841956139, 1.08718979, -0.194648504, 0.451776862, -0.675602078, -0.582631707, -0.841145873, -0.540190697, -0.02584197, -0.297273308, 0.501753032, -0.812325478),
CFrame.new(0.384299219, -2.04907751, 0.312563866, 0.965925992, 0.109381422, -0.234569386, -0.0225576125, 0.93843776, 0.344711155, 0.257833749, -0.327674121, 0.908928871),
CFrame.new(-0.55455792, -1.93629444, -0.421594352, 0.984807789, 0.0733868033, 0.157378852, 0.0151345003, 0.866585255, -0.498799652, -0.172987461, 0.493603587, 0.852309287),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.011209704, -1.63770795, -0.318749219, -0.0172089972, -4.19956632e-06, -0.999852002, 0.999852061, 8.99471343e-06, -0.0172089972, 9.06549394e-06, -1.00000012, 4.04558159e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
		mdmg(Hitbox, 3)
	end
	swait(5)
	Humanoid.WalkSpeed = 8
	tr1.Enabled = false
	attack = false
end
function attack2two()
	attack = true
	Humanoid.WalkSpeed = 8
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(-0.118413232, -0.0999996662, -0.0162695143, 0.342019916, 0, 0.939692736, 0, 1, 0, -0.939692736, 0, 0.342019886),
CFrame.new(-0.0974596441, 1.42617989, -0.153679788, 0.698022485, 0.0783720315, -0.71177417, 0.241093084, 0.910238683, 0.33665964, 0.67426914, -0.406599849, 0.616472006),
CFrame.new(1.56614149, 0.675835967, -0.176545516, 0.635042489, -0.737752557, 0.229002833, 0.764718115, 0.558491647, -0.321392745, 0.109212175, 0.379220605, 0.91883868),
CFrame.new(-0.894028425, 0.449107349, -0.694228411, 0.777676225, -0.60256654, -0.179258019, -0.0868209973, 0.179467112, -0.979925394, 0.622641146, 0.777628005, 0.0872518644),
CFrame.new(0.732766688, -1.80342793, 0.0847177207, 0.88302201, -0.321393669, -0.34202078, 0.342020035, 0.939692736, 3.31529257e-08, 0.321394414, -0.116978005, 0.939692497),
CFrame.new(-0.534722447, -1.9000001, -0.196958184, 0.984807849, 0, 0.173648164, 0, 1, 0, -0.173648134, 0, 0.984807849),
		}, .3, false)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,-.5,0)*CFrame.Angles(math.rad(180),0,0), 0.3)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0112083517, -1.63770616, -0.318746239, -0.0172079317, -2.87033617e-06, -0.999851942, 0.999852002, 8.28504562e-06, -0.0172079336, 8.27014446e-06, -1.00000012, 2.72750913e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	tr1.Enabled = true
	CFuncs["Sound"].Create("rbxasset://sounds/swordlunge.wav", chara, 3, .7)
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(-0.08830598, -0.0999999046, -0.0618330762, 0.342019022, 0, -0.939693093, 0, 1, 0, 0.939693093, 0, 0.342018992),
CFrame.new(6.13927841e-06, 1.43159294, -0.187939167, 0.49999994, 3.87430191e-07, 0.866025567, -0.296198189, 0.939692616, 0.171009645, -0.813797832, -0.342019975, 0.469846368),
CFrame.new(1.52318263, 0.334726363, -0.285165101, 0.918839276, -0.321389288, 0.229005635, 0.38301909, 0.866026044, -0.321395814, -0.0950317085, 0.383024603, 0.918836951),
CFrame.new(-1.56829596, 0.236604273, 0.118294179, 0.433012068, 0.866026044, 0.2499993, 0.499999821, -1.78813863e-07, -0.866025567, -0.750000656, 0.499999046, -0.433012933),
CFrame.new(0.732768059, -1.80342686, 0.0847166926, 0.883022785, -0.321393728, -0.342019022, 0.342019916, 0.939692736, 0, 0.321392775, -0.116977297, 0.939693093),
CFrame.new(-0.534724653, -1.90000021, -0.196965426, 0.984807789, 0, 0.173648238, 0, 1, 0, -0.173648268, 0, 0.98480773),
		}, .3, false)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,-.5,0)*CFrame.Angles(math.rad(180),0,0), 0.3)
		moter.C0 = clerp(moter.C0, CFrame.new(0.011209704, -1.63770795, -0.318749219, -0.0172089972, -4.19956632e-06, -0.999852002, 0.999852061, 8.99471343e-06, -0.0172089972, 9.06549394e-06, -1.00000012, 4.04558159e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		mdmg(Hitbox, 3)
	end
	swait(5)
	Humanoid.WalkSpeed = 8
	tr1.Enabled = false
	attack = false
end
local Grabbed = false

function hedshoot()
	attack = true
	--local GGyro = Instance.new("BodyPosition")
	local grab = nil
	local torsy
	local partasdeff
    Effects.Wave.Create(BrickColor.new("White"), RootPart.CFrame * CFrame.Angles(0,math.rad(90),math.rad(90)), .5, .5, .5, 1, .2, 1, 0.07)
	CFuncs["Sound"].Create("rbxassetid://200632211", RootPart, 1.5, .5)
		for i = 0, 1, 0.1 do
		swait()
		if Grabbed == true then
			grab:FindFirstChildOfClass("Humanoid").PlatformStand = true
			--GGyro.position = Partss.Position
			--GGyro.Parent = grab.Head
			torsy.CFrame = Hitbox.CFrame * CFrame.Angles(math.rad(90),0,0)
		end
		PlayAnimationFromTable({
CFrame.new(0, 0.014960058, -0.00263785874, 0, 0, -1, 0.173647985, 0.984807849, 0, 0.984807849, -0.173647985, 0),
CFrame.new(0.0756459087, 1.47367561, 0, 0, 0.173647985, 0.984807849, 0, 0.984807849, -0.173647985, -1, 0, 0),
CFrame.new(1.61953926, 0.256342351, 0, 0.939692676, -0.342020601, 0, 0.342020601, 0.939692676, 0, 0, 0, 1),
CFrame.new(-1.41317761, 0.492402643, 0.500001907, 0, 0.984807849, -0.173647985, 0, -0.173647985, -0.984807849, -1, 0, 0),
CFrame.new(0.696965218, -2.03472972, 1.90734863e-06, 0.984807849, -0.173648134, 0, 0.173648164, 0.984807849, 0, 0, 0, 1),
CFrame.new(-0.303041309, -2.03472829, -1.90734863e-06, 0.965925813, -0.258818924, 0, 0.258818924, 0.965925813, 0, 0, 0, 1),
		}, .3, false)
		RootPart.Velocity = RootPart.CFrame.lookVector * 90
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111932121, -1.63769805, -0.318755955, -0.0172044784, -1.3951445e-05, -0.999852121, 0.999852002, 3.55020165e-06, -0.0172044784, 3.78862023e-06, -1.00000012, 1.38879986e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,-.5,0)*CFrame.Angles(math.rad(180),0,0), 0.3)
	if grab == nil then
	for i, v in pairs(FindNearestTorso(Hitbox.CFrame.p, 5)) do
		if v:FindFirstChild('Head') then
			Grabbed = true
			torsy = v:FindFirstChild("UpperTorso") or v:FindFirstChild("Torso")
			CFuncs["Sound"].Create("rbxassetid://444667824", torsy, 5, .8)
			partasdeff = Instance.new("ParticleEmitter",torsy)
			partasdeff.Color = ColorSequence.new(Color3.new(1, 0, 0), Color3.new(.5, 0, 0))
			partasdeff.LightEmission = .1
			partasdeff.Size = NumberSequence.new(0.2)
			partasdeff.Texture = "rbxassetid://771221224"
			aaa = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.2),NumberSequenceKeypoint.new(1, 5)})
			bbb = NumberSequence.new({NumberSequenceKeypoint.new(0, 1),NumberSequenceKeypoint.new(0.0636, 0), NumberSequenceKeypoint.new(1, 1)})
			partasdeff.Transparency = bbb
			partasdeff.Size = aaa
			partasdeff.ZOffset = .9
			partasdeff.Acceleration = Vector3.new(0, -5, 0)
			partasdeff.LockedToPart = false
			partasdeff.EmissionDirection = "Front"
			partasdeff.Lifetime = NumberRange.new(1, 2)
			partasdeff.Rate = 1000
			partasdeff.Rotation = NumberRange.new(-100, 100)
			partasdeff.RotSpeed = NumberRange.new(-100, 100)
			partasdeff.Speed = NumberRange.new(6)
			partasdeff.VelocitySpread = 10
			grab = v
		end
	end
	end
		end
		if Grabbed == true then
		Humanoid.WalkSpeed = 0
		for i = 0, 2, 0.1 do
		swait()
		if Grabbed == true then
			grab:FindFirstChildOfClass("Humanoid").PlatformStand = true
			--GGyro.position = Partss.Position
			--GGyro.Parent = grab.Head
			torsy.CFrame = Hitbox.CFrame * CFrame.Angles(math.rad(90),0,0)
		end
		PlayAnimationFromTable({
CFrame.new(0, 0.00631189346, 0.102432251, 0, 0, -1, 0, 1, 0, 1, 0, 0),
CFrame.new(0.0756477267, 1.47367513, 0, 0, 0.173647985, 0.984807849, 0, 0.984807849, -0.173647985, -1, 0, 0),
CFrame.new(1.6195389, 0.256341636, 0, 0.939692736, -0.342019886, 0, 0.342019916, 0.939692736, 0, 0, 0, 1),
CFrame.new(-1.41317773, 0.492402405, 0.500001907, 0, 0.984807849, -0.173647985, 0, -0.173647985, -0.984807849, -1, 0, 0),
CFrame.new(0.696966887, -2.03472996, 1.90734863e-06, 0.984807849, -0.173647985, 0, 0.173647985, 0.984807849, 0, 0, 0, 1),
CFrame.new(-0.696959853, -1.96527123, -1.90734863e-06, 0.984807849, 0.173647985, 0, -0.173647985, 0.984807849, 0, 0, 0, 1),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111932121, -1.63769805, -0.318755955, -0.0172044784, -1.3951445e-05, -0.999852121, 0.999852002, 3.55020165e-06, -0.0172044784, 3.78862023e-06, -1.00000012, 1.38879986e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		end
		if grab.Name ~= "CKbackup" or grab.Name ~= "Nebula_Zorua" or grab.Name ~= "Salvo_Starly" then
			local partasdeff = Instance.new("ParticleEmitter",torsy)
			partasdeff.Color = ColorSequence.new(Color3.new(1, 0, 0), Color3.new(.5, 0, 0))
			partasdeff.LightEmission = .1
			partasdeff.Size = NumberSequence.new(0.2)
			partasdeff.Texture = "rbxassetid://771221224"
			aaa = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.2),NumberSequenceKeypoint.new(1, 5)})
			bbb = NumberSequence.new({NumberSequenceKeypoint.new(0, 1),NumberSequenceKeypoint.new(0.0636, 0), NumberSequenceKeypoint.new(1, 1)})
			partasdeff.Transparency = bbb
			partasdeff.Size = aaa
			partasdeff.ZOffset = .9
			partasdeff.Acceleration = Vector3.new(0, -5, 0)
			partasdeff.LockedToPart = false
			partasdeff.EmissionDirection = "Back"
			partasdeff.Lifetime = NumberRange.new(1, 2)
			partasdeff.Rate = 1000
			partasdeff.Rotation = NumberRange.new(-100, 100)
			partasdeff.RotSpeed = NumberRange.new(-100, 100)
			partasdeff.Speed = NumberRange.new(10)
			partasdeff.VelocitySpread = 20
			partasdeff.Enabled=false
	sel = math.random(1,3)
	if sel == 1 then	
	chatfunc("Too weak.")
	elseif sel == 2 then	
	chatfunc("Die.")
	elseif sel == 3 then
	chatfunc("Worthless.")
	end
	for i = 0, 2, 0.1 do
		swait()
				if Grabbed == true then
			grab:FindFirstChildOfClass("Humanoid").PlatformStand = true
			--GGyro.position = Partss.Position
			--GGyro.Parent = grab.Head
			torsy.CFrame = Hitbox.CFrame * CFrame.Angles(math.rad(90),0,0)
		end
		PlayAnimationFromTable({
CFrame.new(0, 0.00631189346, 0.102432251, 0, 0, -1, 0, 1, 0, 1, 0, 0),
CFrame.new(0.0756477267, 1.47367513, 0, 0, 0.173647985, 0.984807849, 0, 0.984807849, -0.173647985, -1, 0, 0),
CFrame.new(0.177449316, 0.626879215, -0.79883039, -0.163171932, 0.896216869, -0.412516981, -0.0593889691, -0.426284939, -0.902637362, -0.984808505, -0.122786134, 0.122783162),
CFrame.new(-1.33671415, 0.478919148, 0.210226327, 0.254886955, 0.951251388, -0.173647881, -0.0449429974, -0.167731076, -0.984807849, -0.965925872, 0.258818924, -3.7422879e-07),
CFrame.new(0.696966887, -2.03472996, 1.90734863e-06, 0.984807849, -0.173647985, 0, 0.173647985, 0.984807849, 0, 0, 0, 1),
CFrame.new(-0.696959853, -1.96527123, -1.90734863e-06, 0.984807849, 0.173647985, 0, -0.173647985, 0.984807849, 0, 0, 0, 1),
		}, .1, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111939851, -1.63769794, -0.31875661, -0.0172049776, -1.39437616e-05, -0.999852121, 0.999852002, 5.96046448e-06, -0.0172049757, 6.16908073e-06, -1, 1.38394535e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	Effects.Block.Create(BrickColor.new("Really black"), Partss.CFrame, 2, 2, 2, 2, 2, 2, 0.05)
    Effects.Block.Create(BrickColor.new("Persimmon"), Partss.CFrame, 2, 2, 2, 1, 1, 1, 0.05)
    CFuncs["Sound"].Create("rbxassetid://168586621", chara, 1, .8)
    dmg(grab)
		grab.Head.Velocity = grab.Head.CFrame.lookVector * -60
	partasdeff.Enabled=true
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0.00631189346, 0.102432251, 0, 0, -1, 0, 1, 0, 1, 0, 0),
CFrame.new(0.0756477267, 1.47367513, 0, 0, 0.173647985, 0.984807849, 0, 0.984807849, -0.173647985, -1, 0, 0),
CFrame.new(0.580128729, 0.911159813, -0.882691503, -0.163171932, 0.569887638, -0.805358887, -0.0593889691, -0.820492566, -0.568563819, -0.984808505, -0.0449442416, 0.167726412),
CFrame.new(-1.33671415, 0.478919148, 0.210226327, 0.254886955, 0.951251388, -0.173647881, -0.0449429974, -0.167731076, -0.984807849, -0.965925872, 0.258818924, -3.7422879e-07),
CFrame.new(0.696966887, -2.03472996, 1.90734863e-06, 0.984807849, -0.173647985, 0, 0.173647985, 0.984807849, 0, 0, 0, 1),
CFrame.new(-0.696959853, -1.96527123, -1.90734863e-06, 0.984807849, 0.173647985, 0, -0.173647985, 0.984807849, 0, 0, 0, 1),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111932531, -1.63769579, -0.318755656, -0.0172050633, -1.61863863e-05, -0.999852121, 0.999851882, 5.15580177e-06, -0.017205067, 5.453825e-06, -1, 1.60960481e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	partasdeff.Enabled=false
	for i = 0, 2.5, 0.1 do
		swait()	
		PlayAnimationFromTable({
CFrame.new(0, 0.00631189346, 0.102432251, 0, 0, -1, 0, 1, 0, 1, 0, 0),
CFrame.new(0.0756477267, 1.47367513, 0, 0, 0.173647985, 0.984807849, 0, 0.984807849, -0.173647985, -1, 0, 0),
CFrame.new(0.177449316, 0.626879215, -0.79883039, -0.163171932, 0.896216869, -0.412516981, -0.0593889691, -0.426284939, -0.902637362, -0.984808505, -0.122786134, 0.122783162),
CFrame.new(-1.33671415, 0.478919148, 0.210226327, 0.254886955, 0.951251388, -0.173647881, -0.0449429974, -0.167731076, -0.984807849, -0.965925872, 0.258818924, -3.7422879e-07),
CFrame.new(0.696966887, -2.03472996, 1.90734863e-06, 0.984807849, -0.173647985, 0, 0.173647985, 0.984807849, 0, 0, 0, 1),
CFrame.new(-0.696959853, -1.96527123, -1.90734863e-06, 0.984807849, 0.173647985, 0, -0.173647985, 0.984807849, 0, 0, 0, 1),
		}, .2, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111939851, -1.63769794, -0.31875661, -0.0172049776, -1.39437616e-05, -0.999852121, 0.999852002, 5.96046448e-06, -0.0172049757, 6.16908073e-06, -1, 1.38394535e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	coroutine.wrap(function()	
		wait(2)
	partasdeff:Remove()	
	end)()
		else
	grab:FindFirstChildOfClass("Humanoid").PlatformStand = false
	for i = 0, 3, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(0.104280457, -1.46030498e-22, -0.179343686, 0.249860913, 5.18448626e-22, 0.968281686, -5.82335151e-22, 1, -5.29395592e-22, -0.968281686, -3.70576914e-22, 0.249860913) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.00671941042, 1.48144531, -0.121562012, 0.0679168552, 0.388981611, -0.918738663, 0.158512011, 0.904961228, 0.394866198, 0.985018492, -0.172449201, -0.000196114182) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.5714488, -0.100437641, -0.219321564, 0.297819793, -0.653239965, -0.696118593, -0.0311920028, 0.722160041, -0.691022456, 0.954112411, 0.227513462, 0.194697708) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.5814501, 0.177012652, 5.41775626e-06, 0.939689815, 0.342028022, -2.68220901e-06, -0.342027992, 0.939689755, -6.1805149e-06, 4.17232513e-07, 6.72787428e-06, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.569012046, -1.89856982, -0.00933695585, 0.266445845, -0.0764764398, -0.960811257, 0.0135949478, 0.997046292, -0.075590536, 0.963754177, 0.00707861409, 0.266698539) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.849534154, -2.01595497, 0.241721377, 0.948572636, 0.308689058, 0.070150286, -0.312330276, 0.948733151, 0.0485308319, -0.0515729487, -0.067945078, 0.996355295) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .1, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111981034, -1.63767779, -0.318741798, -0.0172085222, -1.4077872e-05, -0.999851882, 0.999851942, 7.4505806e-06, -0.0172085222, 7.68899918e-06, -1.00000012, 1.39512122e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
sel = math.random(1,3)
if sel == 1 then	
chatfunc("I'm so silly...")
elseif sel == 2 then	
chatfunc("What am I doing..?")
elseif sel == 3 then
chatfunc("I can't...")
end
		for i = 0, 5, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 0.999999881, 5.04870979e-29, -4.21790838e-43, 5.04870979e-29, 1, -5.04870979e-29, -4.21790838e-43, -5.04870979e-29, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.0399715528, 1.42130852, -0.217550665, 0.985933542, -0.136098281, -0.097015582, 0.166522697, 0.849608123, 0.500436008, 0.0143167432, -0.509551942, 0.860320628) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0- .4 * math.cos((sine) / 5), 0), 
         CFrame.new(1.57258642, 0.0433240086, 3.83948304e-08, 0.990993857, -0.133906633, -2.60571618e-08, 0.133906662, 0.990993977, 5.96046341e-08, 1.78410318e-08, -6.25570422e-08, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.693957031, 0.999676406, -0.811627388, 0.817211449, -0.569911301, -0.0858340934, -0.499626935, -0.626295447, -0.598442137, 0.287295371, 0.531934083, -0.796558976) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.540301144, -1.99792778, 1.70425119e-06, 0.998698354, -0.0510031469, 6.26438805e-07, 0.0510031544, 0.998698473, -1.04335422e-05, -9.34800966e-08, 1.04519122e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.539563119, -1.99793291, 1.9016752e-06, 0.998630941, 0.0523070693, -1.67712614e-07, -0.0523070768, 0.99863106, -1.0458818e-05, -3.79587107e-07, 1.04532719e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111991819, -1.63769639, -0.318748534, -0.0172109455, -5.96046448e-08, -0.999852002, 0.999852061, -1.19209318e-07, -0.0172108412, 5.96046519e-08, -0.99999994, -1.19209275e-07) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	end
	end
	--GGyro.Parent = nil
	attack = false
	Grabbed = false
	Humanoid.WalkSpeed = 8

end
	local blpemit = Instance.new("ParticleEmitter")
	blpemit.Color = ColorSequence.new(Color3.new(.5,0,0))
	blpemit.Texture = "rbxassetid://233069772"
	blpemit.Transparency = NumberSequence.new(0,1)
	blpemit.Lifetime = NumberRange.new(1,3)
	blpemit.Acceleration = Vector3.new(0,-10,0)
	blpemit.Enabled = true
	blpemit.EmissionDirection = "Front"
	blpemit.Speed = NumberRange.new(1,3)
	blpemit.Size = NumberSequence.new(.5)
	blpemit.Rate = 1000
	blpemit.RotSpeed = NumberRange.new(50)
	blpemit.Rotation = NumberRange.new(0,360)
function moarblood()
	attack = true
	Humanoid.WalkSpeed = 0
	local torsy = targetted:FindFirstChild("UpperTorso") or targetted:FindFirstChild("Torso")
    Tele(torsy.CFrame * CFrame.new(0,0,1.3))
	local totrans = {}
	for i, v in pairs(chara:GetDescendants()) do
	if v:IsA("BasePart") and v.Transparency~=1 and (v.Parent.Name == "ThePistol" or v.Parent.Name == "TheKnife") then
	table.insert(totrans,v)
	end
	end
	local stu = Instance.new("Part",targetted)
	stu.Anchored = true
	stu.CanCollide = false
	stu.Transparency = 1
	stu.CFrame = torsy.CFrame
	local w = Instance.new("Weld",stu)
	w.Part0 = torsy
	w.Part1 = stu
	local stu2 = Instance.new("Part",chara)
	stu2.Anchored = true
	stu2.CanCollide = false
	stu2.Transparency = 1
	stu2.CFrame = chara.HumanoidRootPart.CFrame
	local w2 = Instance.new("Weld",stu2)
	w2.Part0 = chara.HumanoidRootPart
	w2.Part1 = stu2
		PlayAnimationFromTable({
CFrame.new(0, 0.00182705373, -0.0581560358, 1, 0, 0, 0, 0.996194661, 0.087155968, 0, -0.087155968, 0.996194661),
CFrame.new(0, 1.52556372, -0.222143173, 1, 0, 0, 0, 0.939692795, 0.342019618, 0, -0.342019618, 0.939692795),
CFrame.new(1.49999928, -1.34110451e-07, 1.58933972e-07, 0.99619478, -0.0871556178, -1.0595604e-07, 0.0871556178, 0.99619472, -3.35276127e-07, 1.35041773e-07, 3.27825546e-07, 1),
CFrame.new(-1.50000119, 2.68220901e-07, 1.58934313e-07, 0.99619478, 0.0871556178, 1.0595604e-07, -0.0871556178, 0.99619472, -3.35276127e-07, -1.35041773e-07, 3.27825546e-07, 1),
CFrame.new(0.499997675, -1.9992758, -0.116536342, 0.965925872, 0, -0.258818984, -0.02255762, 0.996194661, -0.0841862038, 0.257834077, 0.087155968, 0.962250173),
CFrame.new(-0.50000006, -1.99927592, -0.116537228, 0.984807849, 0, 0.173647985, 0.0151344584, 0.996194661, -0.0858318806, -0.172987193, 0.087155968, 0.981060326),
		}, 1, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111980997, -1.6377027, -0.318750381, -0.0172109306, 0, -0.999851882, 0.999851882, 0, -0.0172109306, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
	for i = 0,1,.1 do
	swait()
	for a=1,#totrans do
	totrans[a].Transparency = i
	end
	end
	for a=1,#totrans do
	totrans[a].Transparency = 1
	end
		swait(5)
		for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0.00182705373, -0.0581560358, 1, 0, 0, 0, 0.996194661, 0.087155968, 0, -0.087155968, 0.996194661),
CFrame.new(0, 1.49941719, 0.0767186508, 1, 0, 0, 0, 0.996194661, -0.087155968, 0, 0.087155968, 0.996194661),
CFrame.new(1.1733681, 1.00347483, -0.438556999, 0.834721148, 0.546610475, 0.0667646676, 0.395648003, -0.510977745, -0.763128042, -0.383018494, 0.663414538, -0.642789304),
CFrame.new(-1.19234979, 1.02193367, -0.467352033, 0.879184604, -0.471780479, -0.0667649657, -0.349608243, -0.543515444, -0.763128519, 0.323741287, 0.694272459, -0.642788768),
CFrame.new(0.499997675, -1.9992758, -0.116536342, 0.965925872, 0, -0.258818984, -0.02255762, 0.996194661, -0.0841862038, 0.257834077, 0.087155968, 0.962250173),
CFrame.new(-0.50000006, -1.99927592, -0.116537228, 0.984807849, 0, 0.173647985, 0.0151344584, 0.996194661, -0.0858318806, -0.172987193, 0.087155968, 0.981060326),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111932121, -1.63769805, -0.318755955, -0.0172044784, -1.3951445e-05, -0.999852121, 0.999852002, 3.55020165e-06, -0.0172044784, 3.78862023e-06, -1.00000012, 1.38879986e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,-.5,0)*CFrame.Angles(math.rad(180),0,0), 0.3)
		end
swait(10)
if targetted.Name ~= "CKbackup" or targetted.Name ~= "Nebula_Zorua" or targetted.Name ~= "Salvo_Starly" then
	sel = math.random(1,3)
	if sel == 1 then	
	chatfunc("Time's up.")
	elseif sel == 2 then	
	chatfunc("Your end is here.")
	elseif sel == 3 then
	chatfunc("It's over.")
	end
swait(5)
		local wel = Instance.new("Weld",targetted.Head)
		wel.Part0 = torsy
		wel.Part1 = targetted.Head
		wel.C0 = CFrame.new(0,1.5,0)
		local bledp = Instance.new("Part",targetted)
	bledp.Size = Vector3.new(0,0,0)
	bledp.Transparency = 1
	bledp.CanCollide = false
	local blpe = blpemit:Clone()
	blpe.Parent = bledp
	blpe.EmissionDirection = "Top"
	blpe.VelocitySpread = 5
	wel.C0 = CFrame.new(0,-1.5,0) * CFrame.fromEulerAnglesXYZ(math.rad(180),0,0)
	local bledw = Instance.new("Weld",bledp)
	bledw.Part0 = targetted.Head
	bledw.Part1 = bledp
	bledw.C0 = CFrame.new(0,-.7,0) * CFrame.Angles(0,0,math.rad(45))
	CFuncs["Sound"].Create("rbxassetid://314390675", chara, 5, .7)
		for i = 0, 1, 0.25 do
		swait()
		PlayAnimationFromTable({
CFrame.new(-0.37728107, 0.00182711286, -0.228351086, 0.707106352, 0.0616285279, -0.704416513, 0, 0.99619478, 0.0871558264, 0.707107365, -0.0616284423, 0.7044155),
CFrame.new(-9.90927219e-07, 1.49941754, 0.0767165273, 0.766044199, 0, 0.642788053, 0.0560227223, 0.99619478, -0.066765219, -0.640341938, 0.0871558264, 0.763129056),
CFrame.new(1.14925241, 0.936202288, -0.560600817, 0.834721982, 0.490812272, 0.249685481, 0.39564395, -0.219157442, -0.891872227, -0.383021295, 0.843251646, -0.377122372),
CFrame.new(-1.01654804, 1.22616923, -0.180458635, 0.525007069, -0.121539712, -0.8423751, -0.63483566, -0.715151966, -0.292475075, -0.566878796, 0.688320994, -0.452617407),
CFrame.new(0.499999106, -1.99927592, -0.116537355, 0.965925813, 0, -0.258819491, -0.0225576311, 0.99619478, -0.0841860622, 0.257834613, 0.0871558264, 0.962249994),
CFrame.new(-0.500003219, -1.99927604, -0.116538122, 0.984807849, 0, 0.173648447, 0.0151344724, 0.99619478, -0.0858317465, -0.17298761, 0.0871558264, 0.981060266),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111932121, -1.63769805, -0.318755955, -0.0172044784, -1.3951445e-05, -0.999852121, 0.999852002, 3.55020165e-06, -0.0172044784, 3.78862023e-06, -1.00000012, 1.38879986e-05) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0,-.5,0)*CFrame.Angles(math.rad(180),0,0), 0.3)
		wel.C0 = CFrame.new(.7*i,1.5,0) * CFrame.Angles(0,0,math.rad(-90*i))
		end
		swait(30)
		targetted:BreakJoints()
	else
	sel = math.random(1,3)
	if sel == 1 then	
	chatfunc("...")
	elseif sel == 2 then	
	chatfunc("No...")
	elseif sel == 3 then
	chatfunc("I can't do that...")
	end
	for i = 0, 5, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 0.999999881, 5.04870979e-29, -4.21790838e-43, 5.04870979e-29, 1, -5.04870979e-29, -4.21790838e-43, -5.04870979e-29, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.055980958, 1.49253583, -0.318915963, 0.999889553, 0.0107171191, -0.0102898544, -0.00218299939, 0.791040659, 0.611759722, 0.0146959936, -0.61166966, 0.790976703) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0- .4 * math.cos((sine) / 5), 0), 
         CFrame.new(1.54004693, 0.0494250022, 1.90734852e-06, 0.997847795, -0.0655719861, 0, 0.0655719936, 0.997847855, 7.53468894e-22, -4.94064563e-23, -7.51847299e-22, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.51232088, 0.0410207808, -3.73942044e-06, 0.998558879, 0.053665854, -2.33806347e-07, -0.0536658242, 0.998558939, -1.04548817e-05, -3.27600219e-07, 1.04523697e-05, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.540300906, -1.99793804, -2.11055158e-06, 0.998698354, -0.0510031469, 6.26438805e-07, 0.0510031544, 0.998698473, -1.04335422e-05, -9.34800966e-08, 1.04519122e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.539562821, -1.99794102, -5.75710146e-09, 0.998630941, 0.0523070693, -1.67712614e-07, -0.0523070768, 0.99863106, -1.0458818e-05, -3.79587107e-07, 1.04532719e-05, 0.999999881) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111967381, -1.6377008, -0.318754196, -0.0172117949, 0, -0.999851942, 0.999851942, 0, -0.0172117949, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
end
stu:Destroy()
stu2:Destroy()
coroutine.wrap(function()
	for i = 0,1,.05 do
	swait()
	for a=1,#totrans do
	totrans[a].Transparency = 1-i
	end
	end
	for a=1,#totrans do
	totrans[a].Transparency = 0
	end
end)()
	attack = false
         Humanoid.WalkSpeed = 8
end


function painlessrain()
attack = true
    Humanoid.WalkSpeed = 0
   local ref1 = New("Part",m,"ref",{Transparency = 1,Size = Vector3.new(.2,.2,.2),CFrame = Torso.CFrame,Anchored = true,CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
	local totrans = {}
	for i, v in pairs(chara:GetDescendants()) do
	if v:IsA("BasePart") and v.Transparency~=1 and (v.Parent.Name == "ThePistol" or v.Parent.Name == "TheKnife") then
	table.insert(totrans,v)
	end
	end
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0.00182705373, -0.0581560358, 1, 0, 0, 0, 0.996194661, 0.087155968, 0, -0.087155968, 0.996194661),
CFrame.new(0, 1.52556372, -0.222143173, 1, 0, 0, 0, 0.939692795, 0.342019618, 0, -0.342019618, 0.939692795),
CFrame.new(1.49999928, -1.34110451e-07, 1.58933972e-07, 0.99619478, -0.0871556178, -1.0595604e-07, 0.0871556178, 0.99619472, -3.35276127e-07, 1.35041773e-07, 3.27825546e-07, 1),
CFrame.new(-1.50000119, 2.68220901e-07, 1.58934313e-07, 0.99619478, 0.0871556178, 1.0595604e-07, -0.0871556178, 0.99619472, -3.35276127e-07, -1.35041773e-07, 3.27825546e-07, 1),
CFrame.new(0.499997675, -1.9992758, -0.116536342, 0.965925872, 0, -0.258818984, -0.02255762, 0.996194661, -0.0841862038, 0.257834077, 0.087155968, 0.962250173),
CFrame.new(-0.50000006, -1.99927592, -0.116537228, 0.984807849, 0, 0.173647985, 0.0151344584, 0.996194661, -0.0858318806, -0.172987193, 0.087155968, 0.981060326),
		}, .2, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.00354172289, -1.19249964, -0.318736732, -0.017209189, -1.8668361e-06, -0.999851942, 0.999851882, 1.90734863e-06, -0.0172091946, 1.93715096e-06, -1.00000012, 1.82725489e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, math.rad(doe * 22)), 0.3)
	end
swait(10)
	for i = 0,1,.05 do
	swait()
	for a=1,#totrans do
	totrans[a].Transparency = i
	end
	end
	for a=1,#totrans do
	totrans[a].Transparency = 1
	end
swait(10)
CFuncs["Sound"].Create("rbxassetid://985132972", chara, 4)		
	for i = 0, 7, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),
CFrame.new(0, 1.43159318, -0.187939137, 1, 0, 0, 0, 0.939692736, 0.342019886, 0, -0.342019916, 0.939692736),
CFrame.new(1.5, 0.199999809, 0, 0, -1, 0, -1, 0, 0, 0, 0, -1),
CFrame.new(-1.5, 0.199999809, 0, 0, 1, 0, 1, 0, 0, 0, 0, -1),
CFrame.new(0.500001848, -2, 1.62422657e-06, 0.939692736, 0, -0.342019886, 0, 1, 0, 0.342019916, 0, 0.939692736),
CFrame.new(-0.500000954, -2, 7.00354576e-07, 0.984807849, 0, 0.173647985, 0, 1, 0, -0.173647985, 0, 0.984807849),
		}, .07, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.00354172289, -1.19249964, -0.318736732, -0.017209189, -1.8668361e-06, -0.999851942, 0.999851882, 1.90734863e-06, -0.0172091946, 1.93715096e-06, -1.00000012, 1.82725489e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, math.rad(doe * 22)), 0.3)
Effects.Block.Create(BrickColor.new("Really black"), RightArm.CFrame*CFrame.new(0,-1,0), 2, 2, 2, 2, 2, 2, 0.05)
Effects.Block.Create(BrickColor.new("Really black"), LeftArm.CFrame*CFrame.new(0,-1,0), 2, 2, 2, 2, 2, 2, 0.05)
	end
for i = 0, 30 do
Effects.Block.Create(BrickColor.new("Really black"), RightArm.CFrame*CFrame.new(0,-1,0), 2, 2, 2, 2, 2, 2, 0.05)
Effects.Block.Create(BrickColor.new("Really black"), LeftArm.CFrame*CFrame.new(0,-1,0), 2, 2, 2, 2, 2, 2, 0.05)
swait(3)
mdmg(ref1, 10)
CFuncs["Sound"].Create("rbxassetid://224339201", chara, 1, .8)		
ref1.CFrame = Mouse.Hit
Effects.Cylinder.Create(BrickColor.new("Really black"), ref1.CFrame, .5, 9999, .5, 10, 0, 10, 0.05)
Effects.Block.Create(BrickColor.new("Really black"), ref1.CFrame, 1, 1, 1, 10, 10, 10, 0.05)
end
ref1:Destroy()
	for i = 0,1,.05 do
	swait()
	for a=1,#totrans do
	totrans[a].Transparency = 1-i
	end
	end
	for a=1,#totrans do
	totrans[a].Transparency = 0
	end
attack = false
Humanoid.WalkSpeed = 8
end

function killyourself()
	attack = true
	Humanoid.WalkSpeed = 0
	kkk:Destroy()
	for i = 0, 3, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0, 0, 0.999999881, 0, -4.47034836e-07, 0, 1, 0, -4.47034836e-07, 0, 1.00000024),
CFrame.new(-0.115837865, 1.50782096, -0.215681732, 0.984807611, -0.173648, -5.83465351e-07, 0.163175955, 0.925416708, 0.342019916, -0.0593914725, -0.33682391, 0.939692974),
CFrame.new(1.54293299, 0.123661026, 1.21202584e-06, 0.98480773, -0.173647955, -4.47034836e-07, 0.173647985, 0.984807849, 0, -4.43412773e-07, 8.23791027e-08, 1.00000024),
CFrame.new(-1.49999988, 0.984808981, 0.17364502, 0.999999881, 7.72039854e-08, 4.43865531e-07, 0, -0.984807849, 0.173647985, -4.47034836e-07, -0.173648015, -0.984808087),
CFrame.new(0.49999693, -1.99999797, 3.65078449e-06, 0.939692497, 0, -0.342020273, 0, 1, 0, 0.342019558, 0, 0.939693153),
CFrame.new(-0.499997526, -1.99999797, 2.32458115e-06, 0.939692736, 0, 0.342019409, 0, 1, 0, -0.342020422, 0, 0.939692795),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0112083517, -1.63770616, -0.318746239, -0.0172079317, -2.87033617e-06, -0.999851942, 0.999852002, 8.28504562e-06, -0.0172079336, 8.27014446e-06, -1.00000012, 2.72750913e-06) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
	end
	tr1.Enabled = true
	for i = 0, 1, 0.25 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, 0, 0, 1, 0, 2.38418579e-07, 0, 1, 0, 2.38418579e-07, 0, 1.00000024),
CFrame.new(-0.0666886047, 1.42028046, 0.35870862, 0.984808087, -0.0868246108, 0.15038164, 0.163175017, 0.758906007, -0.630424976, -0.0593888946, 0.645386159, 0.761544466),
CFrame.new(1.47452879, 0.311596215, -3.63892013e-06, 0.939692736, -0.342019886, 1.1920929e-07, 0.342019916, 0.939692736, 0, 1.12020103e-07, -4.07719476e-08, 1.00000012),
CFrame.new(-0.971452236, 0.0420972407, -0.727193654, 0.472706228, -0.864956677, 0.168519452, 0.874283433, 0.436382502, -0.212600186, 0.110351123, 0.247830987, 0.962498188),
CFrame.new(0.499999553, -1.99999785, -3.15904617e-06, 0.939692795, 0, -0.342019647, 0, 1, 0, 0.342020184, 0, 0.939692795),
CFrame.new(-0.499998242, -1.99999785, 1.78813934e-07, 0.939692616, 0, 0.342020124, 0, 1, 0, -0.342019767, 0, 0.939693034),
		}, .4, false)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
	end
local partasdeff = Instance.new("ParticleEmitter",Torso)
partasdeff.Color = ColorSequence.new(Color3.new(1, 0, 0), Color3.new(.5, 0, 0))
partasdeff.LightEmission = .1
partasdeff.Size = NumberSequence.new(0.2)
partasdeff.Texture = "rbxassetid://771221224"
aaa = NumberSequence.new({NumberSequenceKeypoint.new(0, 0.2),NumberSequenceKeypoint.new(1, 5)})
bbb = NumberSequence.new({NumberSequenceKeypoint.new(0, 1),NumberSequenceKeypoint.new(0.0636, 0), NumberSequenceKeypoint.new(1, 1)})
partasdeff.Transparency = bbb
partasdeff.Size = aaa
partasdeff.ZOffset = .9
partasdeff.Acceleration = Vector3.new(0, -5, 0)
partasdeff.LockedToPart = false
partasdeff.EmissionDirection = "Back"
partasdeff.Lifetime = NumberRange.new(1, 2)
partasdeff.Rate = 1000
partasdeff.Rotation = NumberRange.new(-100, 100)
partasdeff.RotSpeed = NumberRange.new(-100, 100)
partasdeff.Speed = NumberRange.new(6)
partasdeff.VelocitySpread = 10000
partasdeff.Enabled=false
partasdeff:Emit(30)
CFuncs["Sound"].Create("rbxassetid://186311262", chara, 10)
swait(10)
for i, v in pairs(chara:GetDescendants()) do
if v.Parent.Name == "ThePistol" or v.Parent.Name == "TheKnife" then
v.CanCollide = true
end
end
m.Parent = workspace
game:service'Debris':AddItem(m,20)
moter:Destroy()
swait(20)
Knifu.Parent = workspace
game:service'Debris':AddItem(Knifu,20)
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
CFrame.new(0, -1.39999962, 0, 1, 0, 2.38418852e-06, 0, 1, 0, 2.38418852e-06, 0, 1.00000238),
CFrame.new(-0.102913857, 1.42711043, -0.223223031, 0.984807372, -0.171011478, -0.0301612895, 0.163180962, 0.851966083, 0.497519821, -0.0593829304, -0.494883925, 0.866929054),
CFrame.new(1.40506089, -0.0823242813, 1.94649601e-07, 0.984807849, 0.173647985, 6.31810508e-06, -0.173647985, 0.984807849, 0, -3.87415957e-06, -6.83118003e-07, 1.00000119),
CFrame.new(-0.971458435, 0.0420978218, -0.727199256, 0.472706467, -0.864956141, 0.168521509, 0.874283433, 0.436382502, -0.212600186, 0.110352375, 0.247829661, 0.962500572),
CFrame.new(0.500002623, -1.26108539, 0.461084843, 0.939690471, -6.31810508e-06, -0.342026144, 0.342026144, 0, 0.939690471, -3.69667123e-06, -1.00000119, 1.34550498e-06),
CFrame.new(-0.499990612, -1.26108611, 0.461088777, 0.939694881, -6.31810508e-06, 0.342013985, -0.342013955, 0, 0.939694881, -3.69668851e-06, -1.00000119, -1.34545712e-06),
		}, .3, false)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
	end
swait(20)
KWeld:Destroy()
coroutine.wrap(function()
chara:BreakJoints()
swait(.2)
CFuncs["Sound"].Create("rbxassetid://62339698", chara, 3, .3)
chara:FindFirstChildOfClass("Humanoid"):Destroy()
for i,v in pairs(chara:GetChildren()) do
if v:IsA("BasePart") then
local bodpos = Instance.new("BodyPosition",v)
bodpos.Position = v.Position + Vector3.new(math.random(-5,5),math.random(-5,5),math.random(-5,5))
p1mit:Clone().Parent = v
v.BrickColor = BrickColor.new("Really red")
end
end
for i=0,1,.05 do
for a,v in pairs(chara:GetChildren()) do
if v:IsA("BasePart") then
v.Transparency = i
end
end
swait()
end
for a,v in pairs(chara:GetChildren()) do
if v:IsA("BasePart") and v:FindFirstChild("ParticleEmitter") then
v.ParticleEmitter.Enabled = false
end
game:service'Debris':AddItem(v,2)
end
end)()
end

function Tele(pos)
	CFuncs["Sound"].Create("rbxassetid://743521656", chara, 1, .8)
    for _, v in pairs(chara:children()) do
      if v:IsA("BasePart") and v.Name ~= "HumanoidRootPart" then
        do
          local p = v:clone()
          p.Name = "trail"
          p.Parent = EffectModel
          p.Transparency = 0.5
          p.Anchored = true
          p.BrickColor = BrickColor.new("Really black")
          p.Material = "Neon"
          p:BreakJoints()
          p.CanCollide = false
		  if v == Head then
		  for a, b in pairs(p:children()) do
		  if b:IsA("Sound") then
		  b:Destroy()
		  end
		  end
		  end
          coroutine.resume(coroutine.create(function()
            for i = 1, 50 do
              swait()
              p.Transparency = i / 50
            end
            p:Destroy()
          end))
        end
      end
      if v.className == "Accessory" then
      end
    end
RootPart.CFrame = pos
end

function TargetSelect(person)
local dd=coroutine.wrap(function()
if targetted ~= person then
targetted = person
for i=0,1,.05 do
swait()
crosshair.Size = UDim2.new(40-30*i,0,40-30*i,0)
imgl.ImageTransparency = 1-i
imgl2.ImageTransparency = 1-i
end
crosshair.Size = UDim2.new(10,0,10,0)
imgl.ImageTransparency = 0
imgl2.ImageTransparency = 0
end
end)
dd()
end

function LockOn()
if Mouse.Target.Parent ~= chara and Mouse.Target.Parent.Parent ~= chara and Mouse.Target.Parent:FindFirstChildOfClass("Humanoid") ~= nil then
TargetSelect(Mouse.Target.Parent)
CFuncs["Sound"].Create("rbxassetid://743521450", chara, 1, .8)
end
end


function ofmoosic() -- 2 lazi hoh
delays = true
while kkk and kkk.Volume >= 0.02 do
	swait(.5)
	kkk.Volume = kkk.Volume - 0.05
end
swait(0.1)
kkk.Pitch = 0
kkk.PlaybackSpeed = 0
play = false
delays = false
end
function onmoosic()
delays = true
kkk.Pitch = 1
kkk.PlaybackSpeed = 1
while kkk and kkk.Volume <= 1 do
	swait(.5)
	kkk.Volume = kkk.Volume + 0.05
end
swait(0.1)
play = true
delays = false
end
Mouse.Button1Down:connect(function()
	if attack == false then
	local cho = math.random(1,2)
	if cho == 1 then
	attacktwo()
	elseif cho == 2 then
	attack2two()	
	end
	end
end)


Mouse.KeyDown:connect(function(k)
	k = k:lower()
	if attack == false and k == 'q' then
	LockOn()
	end
	if attack == false and k == 'p' then
	killyourself()
	end
	if k == 'z' and attack == false then	
	hedshoot()
	elseif k == 'e' and attack == false and targetted ~= nil then
    Tele(targetted.Head.CFrame * CFrame.new(0,-1.5,3))
	elseif k == 'x' and attack == false and targetted ~= nil then
	local cho = math.random(1,2)
	if cho == 1 then
	attackone()
	elseif cho == 2 then
	attack2one()	
	end
	elseif k == 'c' and attack == false and targetted ~= nil then
	moarblood()
	elseif k == 'v' and attack == false then
	painlessrain()
	elseif k == 'g' and delays == false then
	delays = true
	chatfunc("The only choice, is death.")
	delays = false
    elseif k == 'm' and play == true and delays == false then
	ofmoosic()
	elseif k == 'm' and play == false and delays == false then
	onmoosic()
	end
end)

kkk = Instance.new("Sound",chara)
kkk.Volume = 2
kkk.PlaybackSpeed = 1
kkk.Pitch = 1
kkk.SoundId = "rbxassetid://845268894"
kkk:Play()
kkk.Name = "a"
kkk.Looped = true

	for i, v in pairs(chara:GetDescendants()) do
	if v:IsA("BasePart") then
	v.CanCollide = false
	end
	end

coroutine.wrap(function()
while true do
	swait()
	for i, v in pairs(chara:GetDescendants()) do
		if v:IsA("BasePart") and (v.Parent.Name == "ThePistol" or v.Parent.Name == "TheKnife") then
		v.Anchored = false
		end
	end
	chara.Torso.Anchored = false
end
end)()
coroutine.wrap(function()
while 1 do
swait()
if doe <= 360 then
	doe = doe + 2
else
	doe = 0
end
end
end)()
while true do
	swait()
	for i, v in pairs(chara:GetChildren()) do
		if v:IsA("Part") then
			v.Material = "SmoothPlastic"
		elseif v:IsA("Accessory") then
			v:WaitForChild("Handle").Material = "SmoothPlastic"
		end
	end
while true do
swait()
Humanoid.MaxHealth = math.huge
Humanoid.Health = math.huge
Humanoid.Name = "asfopwejfopewkpfkwepfkp"
imgl.Rotation = imgl.Rotation + 3
imgl2.Rotation = imgl2.Rotation - 3
if targetted ~= nil then
crosshair.Adornee = targetted:FindFirstChild("Torso") or targetted:FindFirstChild("UpperTorso")
crosshair.Enabled = true
elseif targetted == nil then
crosshair.Adornee = nil
crosshair.Enabled = false
targetted = nil
end
if targetted ~= nil and targetted:FindFirstChildOfClass("Humanoid").Health<1 then
crosshair.Adornee = nil
crosshair.Enabled = false
targetted = nil
end
while true and imgl.Rotation >= 360 do
imgl.Rotation = 0
imgl2.Rotation = 0
end
	Torsovelocity = (RootPart.Velocity * Vector3.new(1, 0, 1)).magnitude 
	velocity = RootPart.Velocity.y
	sine = sine + change
	local hit, pos = rayCast(RootPart.Position, (CFrame.new(RootPart.Position, RootPart.Position - Vector3.new(0, 1, 0))).lookVector, 4, chara)
		if RootPart.Velocity.y > 1 and hit == nil then 
			Anim = "Jump"
			if attack == false then
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 1, -2.21689355e-12, -5.11591203e-13, -2.21689355e-12, 1, 7.74860496e-07, -5.11591203e-13, 7.74860496e-07, 1.00000048) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.0579944476, 1.48445117, -0.000906195492, 0.999631822, -0.0259140469, -0.00804444961, 0.0262291897, 0.998776913, 0.0419151038, 0.0069484422, -0.0421099029, 0.999089062) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.68067598, 0.167780995, 5.50026158e-08, 0.965881884, -0.258982956, -3.41060513e-13, 0.258982956, 0.965881884, 4.47034836e-07, 8.49010675e-08, 3.16640808e-07, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.67620921, 0.188169807, -3.04922651e-07, 0.95698452, 0.290146649, -2.61441073e-07, -0.290146649, 0.95698452, -1.0069979e-05, -2.89639524e-06, 1.04542296e-05, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.537238836, -1.93797374, 0.176598221, 0.998698533, -0.0506777391, -0.00574572897, 0.0510024093, 0.992341697, 0.112511501, -6.35704041e-08, -0.112657718, 0.993634105) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.536944568, -1.94808352, 0.126473114, 0.998626292, 0.0520468242, 0.00521374354, -0.0523067154, 0.993665218, 0.0995327011, -3.84102691e-07, -0.099668026, 0.995023906) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111988392, -1.63769972, -0.318750381, -0.0172117054, 0, -0.999851942, 0.999851942, 0, -0.0172116756, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
					end
		elseif RootPart.Velocity.y < -1 and hit == nil then 
			Anim = "Fall"
			if attack == false then
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 1, -2.21689355e-12, -5.11591203e-13, -2.21689355e-12, 1, 7.74860496e-07, -5.11591203e-13, 7.74860496e-07, 1.00000048) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.0576509275, 1.50532985, -0.129091382, 0.999631822, -0.0231846143, -0.0140984114, 0.0262298863, 0.958684564, 0.283279002, 0.00694822101, -0.283544153, 0.958935201) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.68622994, 0.21415168, 7.02040666e-08, 0.881990671, -0.471266806, -3.41060513e-13, 0.471266806, 0.881990671, 4.47034836e-07, 1.54493137e-07, 2.89139166e-07, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.72513735, 0.240890861, 2.54038241e-07, 0.814108491, 0.58071363, -2.61430017e-07, -0.580713034, 0.814108849, -1.00698489e-05, -6.08482924e-06, 8.98058715e-06, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.536720514, -1.92783141, 0.223740995, 0.998698533, -0.0498600565, -0.0107376017, 0.0510031059, 0.976314366, 0.210260883, -3.04512355e-07, -0.210534185, 0.977587521) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.535922825, -1.92850935, 0.222419083, 0.99863112, 0.0512506701, 0.0104565797, -0.0523065142, 0.978474379, 0.199629858, -3.7062793e-07, -0.199902818, 0.97981596) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0112015437, -1.63769758, -0.318750381, -0.0172110498, 0, -0.999851942, 0.999851942, 0, -0.0172110498, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
					end
		elseif Torsovelocity < 1 and hit ~= nil then
			Anim = "Idle"
			if attack == false then
				change = 1
		PlayAnimationFromTable({
CFrame.new(0.0315842479, -0.0265286062, -0.152690947, 0.906307876, 0.109381199, -0.408217728, 0, 0.965926111, 0.25881815, 0.422617942, -0.234568939, 0.875426471),
CFrame.new(8.40146095e-06, 1.4825958, -0.0984789878, 0.939692557, -0.059389703, 0.336824298, 0.0298068672, 0.995281875, 0.0923336893, -0.340718806, -0.0767255723, 0.937029362),
CFrame.new(1.10245335, 0.636036694, -0.730026484, 0.875466704, 0.48325485, 0.00478051743, 0.116469122, -0.201375037, -0.972565234, -0.469034195, 0.852005303, -0.232581407),
CFrame.new(-0.395449817, 0.579820335, -0.690471053, -0.341808617, -0.515997887, -0.785438061, -0.896480024, 0.429773033, 0.107790381, 0.28194046, 0.740973234, -0.609481931),
CFrame.new(0.499991119, -2.02235937, -0.229938298, 0.982728899, -0.0649467632, 0.173279479, 0.106723413, 0.963886976, -0.243992254, -0.15117538, 0.258271217, 0.954170942),
CFrame.new(-0.59830004, -2.02112007, -0.211634785, 0.983016431, 0.0602907613, 0.173330963, -0.0124089085, 0.964169204, -0.26499784, -0.183097318, 0.258346409, 0.948542297),
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111980997, -1.6377027, -0.318750381, -0.0172109306, 0, -0.999851882, 0.999851882, 0, -0.0172109306, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
			end
		elseif Torsovelocity > 2 and hit ~= nil then
			Anim = "Walk"
			if attack == false then
		PlayAnimationFromTable({		
         CFrame.new(0, 0, 0, 1, -2.21689355e-12, -5.11591203e-13, -2.21689355e-12, 1, 7.74860496e-07, -5.11591203e-13, 7.74860496e-07, 1.00000048) * CFrame.new(0, 0- .08 * math.cos((sine) / 5), 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.0595112406, 1.55331731, -0.0425721854, 0.999631822, -0.0248252042, -0.010953242, 0.0262294486, 0.987443328, 0.155781403, 0.00694842171, -0.156010598, 0.987731278) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.54809988, 0.041232653, 1.35168499e-08, 0.996376455, -0.0850530341, -3.41060513e-13, 0.0850530341, 0.996376455, 4.47034836e-07, 2.78823862e-08, 3.26637689e-07, 1.00000024) * CFrame.new(0, 0, 0- .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 + 30 * math.cos((sine) / 10)), 0, 0), 
         CFrame.new(-1.53598976, 0.0413191095, -1.86092848e-06, 0.995650649, 0.0931596532, -2.61508148e-07, -0.0931649953, 0.995651186, -1.00695124e-05, -7.49969331e-07, 1.08217946e-05, 1.00000024) * CFrame.new(0, 0, 0+ .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 - 30 * math.cos((sine) / 10)), 0, 0), 
         CFrame.new(0.540300786, -1.99793816, -9.82598067e-07, 0.998698533, -0.0510031395, 6.36324955e-07, 0.0510031395, 0.998698533, -1.00461093e-05, -8.35937328e-08, 1.08393433e-05, 1.00000024) * CFrame.new(0, 0, 0+ .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 - 30 * math.cos((sine) / 10)), 0, 0), 
         CFrame.new(-0.539563596, -1.99794078, 1.12228372e-06, 0.998635888, 0.0523072146, -1.77852357e-07, -0.0523072146, 0.998635888, -1.00715051e-05, -3.89727461e-07, 1.08406466e-05, 1.00000024) * CFrame.new(0, 0, 0- .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 + 30 * math.cos((sine) / 10)), 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.0111980997, -1.6377027, -0.318750381, -0.0172109306, 0, -0.999851882, 0.999851882, 0, -0.0172109306, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		KWeld.C0 = clerp(KWeld.C0, CFrame.new(0, 0, 0, -1, 0, 0, 0, 0, 1, 0, 1, 0), 0.3)
			end
		end
	if 0 < #Effects then
		for e = 1, #Effects do
			if Effects[e] ~= nil then
				local Thing = Effects[e]
				if Thing ~= nil then
					local Part = Thing[1]
					local Mode = Thing[2]
					local Delay = Thing[3]
					local IncX = Thing[4]
					local IncY = Thing[5]
					local IncZ = Thing[6]
					if Thing[2] == "Shoot" then
						local Look = Thing[1]
						local move = 30
						if Thing[8] == 3 then
							move = 10
						end
						local hit, pos = rayCast(Thing[4], Thing[1], move, m)
						if Thing[10] ~= nil then
							da = pos
							cf2 = CFrame.new(Thing[4], Thing[10].Position)
							cfa = CFrame.new(Thing[4], pos)
							tehCF = cfa:lerp(cf2, 0.2)
							Thing[1] = tehCF.lookVector
						end
						local mag = (Thing[4] - pos).magnitude
						Effects["Head"].Create(Torso.BrickColor, CFrame.new((Thing[4] + pos) / 2, pos) * CFrame.Angles(1.57, 0, 0), 1, mag * 5, 1, 0.5, 0, 0.5, 0.2)
						if Thing[8] == 2 then
							Effects["Ring"].Create(Torso.BrickColor, CFrame.new((Thing[4] + pos) / 2, pos) * CFrame.Angles(1.57, 0, 0) * CFrame.fromEulerAnglesXYZ(1.57, 0, 0), 1, 1, 0.1, 0.5, 0.5, 0.1, 0.1, 1)
						end
						Thing[4] = Thing[4] + Look * move
						Thing[3] = Thing[3] - 1
						if 2 < Thing[5] then
							Thing[5] = Thing[5] - 0.3
							Thing[6] = Thing[6] - 0.3
						end
						if hit ~= nil then
							Thing[3] = 0
							if Thing[8] == 1 or Thing[8] == 3 then
								Damage(hit, hit, Thing[5], Thing[6], Thing[7], "Normal", RootPart, 0, "", 1)
							else
								if Thing[8] == 2 then
									Damage(hit, hit, Thing[5], Thing[6], Thing[7], "Normal", RootPart, 0, "", 1)
									if (hit.Parent:FindFirstChildOfClass("Humanoid")) ~= nil or (hit.Parent.Parent:FindFirstChildOfClass("Humanoid")) ~= nil then
										ref = CFuncs.Part.Create(workspace, "Neon", 0, 1, BrickColor.new("Really red"), "Reference", Vector3.new())
										ref.Anchored = true
										ref.CFrame = CFrame.new(pos)
										CFuncs["Sound"].Create("161006093", ref, 1, 1.2)
										game:GetService("Debris"):AddItem(ref, 0.2)
										Effects["Block"].Create(Torso.BrickColor, CFrame.new(ref.Position) * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50)), 1, 1, 1, 10, 10, 10, 0.1, 2)
										Effects["Ring"].Create(BrickColor.new("Bright yellow"), CFrame.new(ref.Position) * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50)), 1, 1, 0.1, 4, 4, 0.1, 0.1)
										MagnitudeDamage(ref, 15, Thing[5] / 1.5, Thing[6] / 1.5, 0, "Normal", "", 1)
									end
								end
							end
							ref = CFuncs.Part.Create(workspace, "Neon", 0, 1, BrickColor.new("Really red"), "Reference", Vector3.new())
							ref.Anchored = true
							ref.CFrame = CFrame.new(pos)
							Effects["Sphere"].Create(Torso.BrickColor, CFrame.new(pos), 5, 5, 5, 1, 1, 1, 0.07)
							game:GetService("Debris"):AddItem(ref, 1)
						end
						if Thing[3] <= 0 then
							table.remove(Effects, e)
						end
					end
					do
						do
							if Thing[2] == "FireWave" then
								if Thing[3] <= Thing[4] then
									Thing[1].CFrame = Thing[1].CFrame * CFrame.fromEulerAnglesXYZ(0, 1, 0)
									Thing[3] = Thing[3] + 1
									Thing[6].Scale = Thing[6].Scale + Vector3.new(Thing[5], 0, Thing[5])
								else
									Part.Parent = nil
									table.remove(Effects, e)
								end
							end
							if Thing[2] ~= "Shoot" and Thing[2] ~= "Wave" and Thing[2] ~= "FireWave" then
								if Thing[1].Transparency <= 1 then
									if Thing[2] == "Block1" then
										Thing[1].CFrame = Thing[1].CFrame * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50))
										Mesh = Thing[7]
										Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
										Thing[1].Transparency = Thing[1].Transparency + Thing[3]
									else
										if Thing[2] == "Block2" then
											Thing[1].CFrame = Thing[1].CFrame
											Mesh = Thing[7]
											Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
											Thing[1].Transparency = Thing[1].Transparency + Thing[3]
										else
											if Thing[2] == "Fire" then
												Thing[1].CFrame = CFrame.new(Thing[1].Position) + Vector3.new(0, 0.2, 0)
												Thing[1].CFrame = Thing[1].CFrame * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50))
												Thing[1].Transparency = Thing[1].Transparency + Thing[3]
											else
												if Thing[2] == "Cylinder" then
													Mesh = Thing[7]
													Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
													Thing[1].Transparency = Thing[1].Transparency + Thing[3]
												else
													if Thing[2] == "Blood" then
														Mesh = Thing[7]
														Thing[1].CFrame = Thing[1].CFrame * CFrame.new(0, 0.5, 0)
														Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
														Thing[1].Transparency = Thing[1].Transparency + Thing[3]
													else
														if Thing[2] == "Elec" then
															Mesh = Thing[10]
															Mesh.Scale = Mesh.Scale + Vector3.new(Thing[7], Thing[8], Thing[9])
															Thing[1].Transparency = Thing[1].Transparency + Thing[3]
														else
															if Thing[2] == "Disappear" then
																Thing[1].Transparency = Thing[1].Transparency + Thing[3]
															else
																if Thing[2] == "Shatter" then
														Thing[1].Transparency = Thing[1].Transparency + Thing[3]
														Thing[4] = Thing[4] * CFrame.new(0, Thing[7], 0)
														Thing[1].CFrame = Thing[4] * CFrame.fromEulerAnglesXYZ(Thing[6], 0, 0)
														Thing[6] = Thing[6] + Thing[5]
																end
															end
														end
													end
												end
											end
										end
									end
								else
									Part.Parent = nil
									table.remove(Effects, e)
								end
							end
						end
					end
				end
			end
		end
	end
end
end
