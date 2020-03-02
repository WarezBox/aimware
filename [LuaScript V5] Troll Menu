--[Onyx] TrollMenu for AIMWARE V5 by OurmineOGTv#6846
local OnyxSilentName = 0
local OnyxDisconnect = 0
local OnyxTimer = 0
local OnyxCurTime = globals.CurTime()
local OnyxMsgType, OnyxWeapons, OnyxRarity, OnyxText, box1, box2, box3, box4, OnyxSlider, OnyxTrollMenuEnable, OnyxEnableType, OnyxUseOwnName, OnyxBanText, OnyxBanDisconnect, OnyxFakeText, OnyxFakeKickText, OnyxKickSelf
local OnyxOriginalName = "[Onyx] Troll Menu for V5 broken"

local function OnyxGetOriginalName()

	OnyxOriginalName = client.GetConVar("Name")

end

OnyxGetOriginalName()

local function table_contains(tbl, item)
    for i=1, #tbl do
        if tbl[i] == item then
            return true
        end
    end
    return false
end

local function OnyxSetName(name)
    client.SetConVar("name", name);
end

local OnyxKnives = {
    "Bayonet", "Bowie Knife", "Butterfly Knife", 
    "Falchion Knife", "Flip Knife", "GutKnife", 
    "Huntsman Knife", "Karambit", "M9 Bayonet", "Navaja", 
    "Shadow Daggers", "Stiletto", "Talon", "Ursus"
}

local OnyxWeaponsTable = {
    "Bayonet", "Bowie Knife", "Butterfly Knife", "Falchion Knife", 
    "Flip Knife", "GutKnife", "Huntsman Knife", "Karambit", 
    "M9 Bayonet", "Navaja", "Shadow Daggers", "Stiletto", 
    "Talon", "Ursus", "AWP", "AK-47", "Desert Eagle", 
    "Glock-18", "M4A4", "M4A1-S", "USP-S"
}

local OnyxTeamColors = {
   "\x01",
   "\x09",
   "\x0B"
}

local OnyxRarityColors = {
   "\x0B",
   "\x0C",
   "\x03",
   "\x0E",
   "\x07",
   "\x10"
}

local OnyxTypeMessages = {
    " has opened a container and found:",
    " received in a trade:"
}
	local OnyxReference = gui.Reference("MISC")
	local OnyxTrollMenuTab = gui.Tab(OnyxReference, "onyx.troll.menu.tab", "[Onyx] Troll Menu")

	local OnyxMainGroupbox = gui.Groupbox(OnyxTrollMenuTab, "Main", 15, 15, 200, 100)
	OnyxTrollMenuEnable = gui.Checkbox(OnyxMainGroupbox, OnyxTrollMenuEnable, "Enable", 0)
	OnyxEnableType = gui.Combobox(OnyxMainGroupbox, OnyxEnableType, "Active Type", "Fake Skin", "Fake Ban", "Fake Vote", "Fake Kick")
	
	local OnyxSetResetName = gui.Groupbox(OnyxTrollMenuTab, "Set Name / Reset Name", 460, 15, 160, 100)
		local OnyxResetNameButton = gui.Button(OnyxSetResetName, "Reset Name", function()
		if OnyxTrollMenuEnable:GetValue() then
			OnyxSetName(OnyxOriginalName)
			end
		end)
	local OnyxFakeSkinGroupbox = gui.Groupbox(OnyxTrollMenuTab, "Fake Skin Settings", 230, 15, 215, 100)
	OnyxMsgType = gui.Combobox(OnyxFakeSkinGroupbox, OnyxMsgType, "Message Type", "Unbox", "Trade")
	OnyxWeapons = gui.Combobox(OnyxFakeSkinGroupbox, OnyxWeapons, "Weapon", "Bayonet", "Bowie Knife", "Butterfly Knife", "Falchion Knife", 
			"Flip Knife", "GutKnife", "Huntsman Knife", "Karambit", 
			"M9 Bayonet", "Navaja", "Shadow Daggers", "Stiletto", 
			"Talon", "Ursus", "AWP", "AK-47", "Desert Eagle", 
			"Glock-18", "M4A4", "M4A1-S", "USP-S")
			OnyxRarity = gui.Combobox(OnyxFakeSkinGroupbox, OnyxRarity, "Rarity/Color", "Industrial (LightBlue)", "Mil spec (DarkBlue)", "Restricted (Pruple)", "Classified (PinkishPurple)", "Covert (Red)", "Contraband (Orangeish)" )
		gui.Text(OnyxFakeSkinGroupbox, "Skin Name")
		OnyxText = gui.Editbox(OnyxFakeSkinGroupbox, OnyxText, "")
		local OnyxMultiBox = gui.Multibox( OnyxFakeSkinGroupbox, "Modifiers")
			box1 = gui.Checkbox(OnyxMultiBox, check1, "Auto-Disconnect", 0)
			box2 = gui.Checkbox(OnyxMultiBox, check2, "StatTrak Weapon", 0)
			box3 = gui.Checkbox(OnyxMultiBox, check3, "White Name Color", 0)
			box4 = gui.Checkbox(OnyxMultiBox, check4, "Use Custom Gap Value", 0)
			OnyxSlider = gui.Slider(OnyxFakeSkinGroupbox, OnyxSlider, "Gap Value", 1, 1, 35)
		
	local OnyxFakeBanGroupbox = gui.Groupbox(OnyxTrollMenuTab, "Fake Ban Settings", 15, 170, 200, 100)
		gui.Text(OnyxFakeBanGroupbox, "Banned Player Name")
		OnyxBanText = gui.Editbox(OnyxFakeBanGroupbox,OnyxBanText, "")
		OnyxUseOwnName = gui.Checkbox(OnyxFakeBanGroupbox, ownname, "Use Own Name Instead", 1)
		OnyxBanDisconnect = gui.Checkbox(OnyxFakeBanGroupbox, OnyxBanDisconnect, "Auto-Disconnect", 0)
		
	local OnyxFakeVoteGroupbox = gui.Groupbox(OnyxTrollMenuTab, "Fake Vote Settings", 15, 375, 200, 100)
		gui.Text(OnyxFakeVoteGroupbox, "Vote Text")
		OnyxFakeText = gui.Editbox(OnyxFakeVoteGroupbox,OnyxFakeText, "")
		
	local OnyxFakeKickGroupbox = gui.Groupbox(OnyxTrollMenuTab, "Fake Kick Settings", 230, 425, 215, 100)
		gui.Text(OnyxFakeKickGroupbox, "Player Name")
		OnyxFakeKickText = gui.Editbox(OnyxFakeKickGroupbox,OnyxFakeKickText, "")
		OnyxKickSelf = gui.Checkbox(OnyxFakeKickGroupbox, OnyxKickSelf, "Use Own Name Instead", 1)
		
		local OnyxSetNameButton = gui.Button(OnyxSetResetName, "Set Name", function()
	if OnyxTrollMenuEnable:GetValue() then
		if OnyxEnableType:GetValue() == 0 then
		local local_player  = entities.GetLocalPlayer()
		if local_player ~= nil then
			local itemn = OnyxWeapons:GetValue() + 1
			local item          = OnyxWeaponsTable[itemn]
			local weapon_name   = table_contains(OnyxKnives, item) and "★ " or ""
			weapon_name         = box2:GetValue() and weapon_name .. "StatTrak™ " .. item or weapon_name .. item
			local team_color    = nil
			local rarn = OnyxRarity:GetValue() + 1
			local rarity_color  = OnyxRarityColors[rarn]
			local msgn = OnyxMsgType:GetValue() + 1
			local message       = OnyxTypeMessages[msgn]
			local skinname      = OnyxText:GetValue()
			if box3:GetValue() then team_color = "\x01" else team_color = OnyxTeamColors[local_player:GetTeamNumber()] end
			local char = ""
			local char2 = ""
			local number = OnyxSlider:GetValue()
			local name = string.len("" .. OnyxOriginalName .. "" .. message .. "" .. weapon_name .. "" .. skinname .. "")
			print("[Onyx] Total name length: " .. name)

			if name == 25 then char = "" for _ = 1, 19 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 26 then char = "" for _ = 1, 19 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 27 then char = "" for _ = 1, 19 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 28 then char = "" for _ = 1, 18 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 29 then char = "" for _ = 1, 18 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 30 then char = "" for _ = 1, 18 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 31 then char = "" for _ = 1, 17 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 32 then char = "" for _ = 1, 17 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 33 then char = "" for _ = 1, 16 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 34 then char = "" for _ = 1, 16 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 35 then char = "" for _ = 1, 15 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 36 then char = "" for _ = 1, 15 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 37 then char = "" for _ = 1, 14 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 38 then char = "" for _ = 1, 14 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 39 then char = "" for _ = 1, 13 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 40 then char = "" for _ = 1, 12 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 41 then char = "" for _ = 1, 12 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 👌 "
			elseif name == 42 then char = "" for _ = 1, 11 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 43 then char = "" for _ = 1, 10 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 44 then char = "" for _ = 1,  9 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 45 then char = "" for _ = 1,  9 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 46 then char = "" for _ = 1,  9 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 47 then char = "" for _ = 1,  9 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 48 then char = "" for _ = 1,  8 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 49 then char = "" for _ = 1,  8 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 50 then char = "" for _ = 1,  7 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 51 then char = "" for _ = 1,  7 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 52 then char = "" for _ = 1,  6 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 53 then char = "" for _ = 1,  5 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 54 then char = "" for _ = 1,  5 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 55 then char = "" for _ = 1,  4 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 👌 "
			elseif name == 56 then char = "" for _ = 1,  4 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 "
			elseif name == 57 then char = "" for _ = 1,  3 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 "
			elseif name == 58 then char = "" for _ = 1,  2 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 "
			elseif name == 59 then char = "" for _ = 1,  2 do char = char .. "ᅠ" end char2 = "" char2 = " 👌 👌 👌 "
			elseif name == 60 then char = "ᅠᅠ" char2 = "" char2 = " 👌 👌 "
			elseif name == 61 then char = "ᅠ" char2 = "" char2 = " 👌 👌 "
			elseif name == 62 then char = "" char2 = "" char2 = " 👌 👌 "
			elseif name == 63 then char = "" char2 = "" char2 = " 👌 👌 "
			elseif name == 64 then char = "" char2 = "" char2 = " 👌 👌 "
			elseif name == 65 then char = "" char2 = "" char2 = " "
			elseif name == 66 then char = "" char2 = "" char2 = " "
			elseif name  > 66 then char = "" char2 = "" print("[Onyx] Values above 66 Don't work properly.")
			end
				
			if table_contains(OnyxKnives, OnyxWeapons:GetValue()) then state = 1 else state = nil end
			if state == 1 then for _ = 1, 2 do char = char .. "ᅠ" end end
				
			if box1:GetValue() then state = 2 end
			if state == 2 then char2 = "" for _ = 1, 6 do char = char .. "ᅠ" end end  

			if box2:GetValue() then state = 3 end
			if state == 3 then for _ = 1, 3 do char = char .. "ᅠ" end end

			if box4:GetValue() then state = 4 end
			if state == 4 then char = "" for _ = 1, number do char = char .. "ᅠ" end end

				if box1:GetValue() then
					OnyxSetName("👌" .. team_color .. "" .. OnyxOriginalName .. "\x01" .. message .. "" .. rarity_color .. " " .. weapon_name .. " | " .. skinname .. "\n" .. char ..  "👌 \x01")
					OnyxDisconnect = 1
				else
					OnyxSetName("👌" .. team_color .. "" .. OnyxOriginalName .. "\x01" .. message .. "" .. rarity_color .. " " .. weapon_name .. " | " .. skinname .. "\n" .. char ..  "" .. char2 .. "\x01You")
				end
		end
		
		elseif OnyxEnableType:GetValue() == 1 then
			local name = 0
			if OnyxUseOwnName:GetValue() then
				name = string.len(OnyxOriginalName)
			else
				name = string.len(OnyxBanText:GetValue())
			end
			local meme = ""
			if(name < 2) and (name > 0)  then
					meme =" 👌 👌 👌 👌 👌 👌 👌 👌 👌 👌 👌 👌 "
			elseif(name < 3) and (name > 1)  then
					meme =" 👌 👌 👌 👌 👌 👌 👌 👌 👌 👌 👌 "
			elseif(name < 4) and (name > 2)  then
					meme =" 👌 👌 👌 👌 👌 👌 👌 👌 👌 👌 "
			elseif(name < 5) and (name > 3)  then
					meme =" 👌 👌 👌 👌 👌 👌 👌 👌 👌 "
			elseif(name < 6) and (name > 4)  then
					meme =" 👌 👌 👌 👌 👌 👌 👌 👌 "
			elseif(name < 7) and (name > 5)  then
					meme =" 👌 👌 👌 👌 👌 👌 👌 "
			elseif(name < 8) and (name > 6)  then
					meme =" 👌 👌 👌 👌 👌 👌 "
			elseif(name < 9) and (name > 7)  then
					meme =" 👌 👌 👌 👌 👌 "
			elseif(name < 10) and (name > 8) then
					meme =" 👌 👌 👌 👌 "
			elseif(name < 99) and (name > 9) then
					print("[Onyx] Names above 9 characters don't work properly")
			end
			if OnyxBanDisconnect:GetValue() then  
				if OnyxUseOwnName:GetValue() then
					OnyxSetName(" \x07" .. OnyxOriginalName .. " has been permanently banned from official CS:GO servers." .. meme .. "\x01 👌 ")
					OnyxDisconnect = 1
				else
					OnyxSetName(" \x07" .. OnyxBanText:GetValue() .. " has been permanently banned from official CS:GO servers." .. meme .. "\x01 👌 ")
					OnyxDisconnect = 1
				end
			else
				if OnyxUseOwnName:GetValue() then
					OnyxSetName(" \x07" .. OnyxOriginalName .. " has been permanently banned from official CS:GO servers." .. meme .. "\x01You");
				else
					OnyxSetName(" \x07" .. OnyxBanText:GetValue() .. " has been permanently banned from official CS:GO servers." .. meme .. "\x01You");
				end
			end
		
		elseif OnyxEnableType:GetValue() == 2 then
		
			local currentName = ''
			local tempName = ''
			for _ = 1, 28 do
				tempName = tempName .. "\n";
			end
			
			tempName = tempName .. OnyxFakeText:GetValue();
			
			for _ = 1, 60 do
				tempName = tempName .. "\n";
			end
			
			currentName = tempName;
			OnyxSetName(currentName);
		
		elseif OnyxEnableType:GetValue() == 3 then
		
			if OnyxKickSelf:GetValue() then
			
				local currentName = ''
				local tempName = ''
				for _ = 1, 28 do
					tempName = tempName .. "\n";
				end
				
				tempName = tempName .. "Kick player: " .. OnyxOriginalName .. "?";
				
				for _ = 1, 60 do
					tempName = tempName .. "\n";
				end
				
				currentName = tempName;
				OnyxSetName(currentName);

			else
			
				local currentName = ''
				local tempName = ''
				for _ = 1, 28 do
					tempName = tempName .. "\n";
				end
				
				tempName = tempName .. "Kick player: " .. OnyxFakeKickText:GetValue() .. "?";
				
				for _ = 1, 60 do
					tempName = tempName .. "\n";
				end
				
				currentName = tempName;
				OnyxSetName(currentName);
			
			end
			
		end
	end
end)

local function OnyxDisconnectFunction()
	if OnyxDisconnect == 1 then
		OnyxTimer = globals.CurTime()
		OnyxDisconnect = 2
	end
	if OnyxDisconnect == 2 and globals.CurTime() >= OnyxTimer + 0.8 then
		client.Command("disconnect", true)
		OnyxDisconnect = 3
	end
	if OnyxDisconnect == 3 and globals.CurTime() >= OnyxTimer + 3.6 then
		client.Command("name" .. OnyxOriginalName, true)
		print("[Onyx] Automatically disconnected from the server after setting name.")
		OnyxDisconnect = 0
	end
end

callbacks.Register("Draw",OnyxDisconnectFunction)

local function OnyxNameSilentFunction()
	local lp = entities.GetLocalPlayer()
	if OnyxSilentName == 0 and lp ~= nil and OnyxTrollMenuEnable:GetValue() then
		OnyxSetName("\n\xAD\xAD\xAD\xAD")
		OnyxTimer = globals.CurTime()
		OnyxSilentName = 1
	end
	if OnyxSilentName == 1 and globals.CurTime() >= OnyxTimer + 0.1 then
		OnyxSetName(OnyxOriginalName)
		OnyxSilentName = 2
	end

	if lp == nil then
		OnyxSilentName = 0
	end
end

callbacks.Register("Draw",OnyxNameSilentFunction)
