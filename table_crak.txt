-- They can't even make configs auto save on GUI, so you gotta config in text manualy :joy_cat::thumbsdown:

_BuyFruitSinper = true -- true / false
_SelectDevil = {"Human-Human: Buddha","Rumble-Rumble","Dragon-Dragon","Soul-Soul","Quake-Quake","String-String","Venom-Venom",'Dark-Dark'}--,"Dragon-Dragon","Soul-Soul","Quake-Quake","String-String","Venom-Venom"
-- _BestSheetUrl= "https://sheet.best/api/sheets/25f4a337-64c0-4c3b-a403-6c47218098db"
_Team = "Pirates"
_FPS_Boost = true
_AutoFarm = true --"Level , Bone"   "Level"  "Bone"
_Fullystats = true
_AutoMeleeWeapon = true
_Make_Melee = {"Superhuman","Electric Claw","Dargon Talon","Sharkman Karate","Death Step"}
_AutoRedeem = true
_RedeemOnLv = 900
_BuyHaki = true
_RandomFruit = true
_StoreFruit = true
_BringFruit = true
_BuyBisento = true
_BuyCommon = true
_Mastery_Farm = true
_Mastery_Mode = "Fruit on 2300"
if game.PlaceId == 2753915549 then -- sea1
   _Farm_Mode = "Level"
   _autoSea2 = true
   _Open_Saber = true
   _Pole_v1 = true
elseif game.PlaceId == 4442272183 then -- sea2
   _AutoMeleeWeapon = true
   _Farm_Mode = "Level"
   _autoSea3 = true
   _Bartilo = true
   _AutoFlower = true
   _AutoDarkbeard = true
   _BuyEctoplasItem = true
   _BuyKabcha = true
   _AutoRaid = true
   _RaidMode = "Awake Skill"-- "Raid Normal" , "Awake Skill"
   _GetFruit_Method = "FruitInventory + BringFruit + Hop"-- "BringFruit" , "BringFruit + Hop" , "FruitInventory" , "FruitInventory + BringFruit" , "FruitInventory + BringFruit + Hop"
elseif game.PlaceId == 7449423635 then -- sea3
   _AutoMeleeWeapon = true
   _Farm_Mode = "Level"
   _BoneTrade = true
   _AutoRaid = true
   _RaidMode = "Awake Skill"-- "Raid Normal" , "Awake Skill"
   _GetFruit_Method = "FruitInventory + BringFruit + Hop"-- "BringFruit" , "BringFruit + Hop" , "FruitInventory" , "FruitInventory + BringFruit" , "FruitInventory + BringFruit + Hop"
   _BuyEctoplasItem = true
   _BuyKabcha = true
   _BuddySword = true
   _AutoScythe = true
   _AutoRipIndra = true
   _Canvander = true
   _AutoCakePrince = true
   _EliteHunt = true
   _Tushita = true
   _Elite_mode = "Yama"
end
_HideUI = true

repeat wait() until game:IsLoaded()

do
	getgenv().is_synapse_function = function()
		return false
	end

        getgenv().http_request = http_request or request or syn.request

	local ReqHook
	ReqHook = hookfunction(http_request, function(...)
		t = {...}
        if t[1].Url:find('auth') then
			return {
                Success = true,
                StatusMessage = "OK",
				StatusCode = 200,
                Cookies = {},
				Body = '{"error":true, "message":"di me may nhen con suc vat bucki nameki"}',
				Headers = game:GetService("HttpService"):JSONEncode({
					Authorization = 'vando123'
				}),
			}
		end
		return ReqHook(...)
	end)
	
	local SubHook
	SubHook = hookfunction(string.sub, function(...)
		t = {...}
		if checkcaller() then
			if #t[1] == 128 then
				return 'vando123vando123vando123vando123vando123vando123vando123vando123'
			end
		end
		return SubHook(...)
	end)

	local DecodeHook
	DecodeHook = hookfunction(game:GetService("HttpService").JSONDecode, function(...) 
		t = {...}
		if checkcaller() and t[2] and t[2]:find('"message":') then
			return {
				error = false,
				message = "vando123vando123vando123vando123vando123vando123vando123vando123"
			}
		end
		return DecodeHook(...)
	end)


	local DecodeHookV2
	DecodeHookV2 = hookmetamethod(game,"__namecall", function(...) 
		if checkcaller() then 
			t = {...}
			if getnamecallmethod() == "JSONDecode" and t[2] and t[2]:find('"message":') then 
				return {
					error = false,
					message = "vando123vando123vando123vando123vando123vando123vando123vando123"
				}
			end
		end    
		return DecodeHookV2(...)
	end)
end

-- Delete Xenon Hub's folder if you have, Table Hub won't let you execute the script if you got xenon folder in workspace, just like my sea hub <:troll:910751219465732117>
if isfolder("Xenon Hub Premium Scripts") then
    delfolder("Xenon Hub Premium Scripts")
end

local function Loader()
	getgenv().key = 'Table-1233-1234-1234-1234'
	getgenv().discord_id = '809804156956835841'

    local Status, Script = pcall(game.HttpGet, game, 'https://raw.githubusercontent.com/AltsegoD/scripts/egoD/TableHub.lua')
    -- You can change the above link to 'https://tablehub.net/v2/script' if you want to get the latest update of the script, will not gonna work if they patched this

    if Status ~= true then Loader() end
    loadstring(Script)()
end
Loader()

