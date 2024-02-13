
# uj-qbfood

# QBcore Food Addon Script

Welcome to the QBcore Food Addon Script! This script adds a variety of food-related features to your QBcore FiveM server, enhancing the roleplaying experience for your players. From hunger mechanics to restaurants and food items, this addon provides a comprehensive system for managing food in your server.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Features

- **Food Items**: A wide range of food items are available for purchase or consumption, including snacks, meals, and drinks.
- **Inventory Integration**: Seamlessly integrates with QBcore's inventory system, allowing players to store and manage their food items.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Installation

1. Ensure you have a working installation of [QBcore](https://github.com/qbcore-framework/qb-core).
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2. go to you qb-core\shared\item/lua and copy and past the [items.lua.md](items.lua.md) at the buttome
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Add to shared.lua example !!!
```
	QBShared = QBShared or {}
    QBShared.Items = {
        -- Other Tools
    casinochips                  = { name = 'casinochips', label = 'Casino Chips', weight = 0, type = 'item', image = 'casinochips.png', unique = false, useable = false, shouldClose = false, combinable = nil, description = 'Chips For Casino Gambling' },
    stickynote                   = { name = 'stickynote', label = 'Sticky note', weight = 0, type = 'item', image = 'stickynote.png', unique = true, useable = false, shouldClose = false, combinable = nil, description = 'Sometimes handy to remember something :)' },
    moneybag                     = { name = 'moneybag', label = 'Money Bag', weight = 0, type = 'item', image = 'moneybag.png', unique = true, useable = true, shouldClose = true, combinable = nil, description = 'A bag with cash' },
    parachute                    = { name = 'parachute', label = 'Parachute', weight = 30000, type = 'item', image = 'parachute.png', unique = true, useable = true, shouldClose = true, combinable = nil, description = 'The sky is the limit! Woohoo!' },
    binoculars                   = { name = 'binoculars', label = 'Binoculars', weight = 600, type = 'item', image = 'binoculars.png', unique = false, useable = true, shouldClose = true, combinable = nil, description = 'Sneaky Breaky...' },
    lighter                      = { name = 'lighter', label = 'Lighter', weight = 0, type = 'item', image = 'lighter.png', unique = false, useable = false, shouldClose = true, combinable = nil, description = 'On new years eve a nice fire to stand next to' },
    certificate                  = { name = 'certificate', label = 'Certificate', weight = 0, type = 'item', image = 'certificate.png', unique = false, useable = false, shouldClose = true, combinable = nil, description = 'Certificate that proves you own certain stuff' },
    markedbills                  = { name = 'markedbills', label = 'Marked Money', weight = 1000, type = 'item', image = 'markedbills.png', unique = true, useable = false, shouldClose = true, combinable = nil, description = 'Money?' },
    labkey                       = { name = 'labkey', label = 'Key', weight = 500, type = 'item', image = 'labkey.png', unique = true, useable = true, shouldClose = true, combinable = nil, description = 'Key for a lock...?' },
    printerdocument              = { name = 'printerdocument', label = 'Document', weight = 500, type = 'item', image = 'printerdocument.png', unique = true, useable = true, shouldClose = true, combinable = nil, description = 'A nice document' },
    newscam                      = { name = 'newscam', label = 'News Camera', weight = 100, type = 'item', image = 'newscam.png', unique = true, useable = true, shouldClose = true, combinable = nil, description = 'A camera for the news' },
    newsmic                      = { name = 'newsmic', label = 'News Microphone', weight = 100, type = 'item', image = 'newsmic.png', unique = true, useable = true, shouldClose = true, combinable = nil, description = 'A microphone for the news' },
    newsbmic                     = { name = 'newsbmic', label = 'Boom Microphone', weight = 100, type = 'item', image = 'newsbmic.png', unique = true, useable = true, shouldClose = true, combinable = nil, description = 'A Useable BoomMic' },
    ---add you food items below here 
    ['atom_junkie'] 		 		= {['name'] = 'atom_junkie', 	    		['label'] = 'Atom Junkie', 				['weight'] = 100, 	["decay"] = nil,	['type'] = 'item', 		['image'] = 'atom_junkie.png', 			["created"] = nil, 	["delete"] = true,		['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,		['combinable'] = nil,   ['description'] = ''},
    ---add more food items here
    }
```
3. go to you qb-smallresources\server\consumables.lua and copy and past the [consumables.md](consumables.md) ----------- / Eat
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Add to consumables.lua example !!!
```
	local QBCore = exports['qb-core']:GetCoreObject()
----------- / alcohol

for k, _ in pairs(Config.Consumables.alcohol) do
    QBCore.Functions.CreateUseableItem(k, function(source, item)
        TriggerClientEvent('consumables:client:DrinkAlcohol', source, item.name)
    end)
end

----------- / Eat

for k, _ in pairs(Config.Consumables.eat) do
    QBCore.Functions.CreateUseableItem(k, function(source, item)
        local Player = QBCore.Functions.GetPlayer(source)
        if not Player.Functions.RemoveItem(item.name, 1, item.slot) then return end
        TriggerClientEvent('consumables:client:Eat', source, item.name)
    end)
end
---Add your Food Items Belowe here
QBCore.Functions.CreateUseableItem("atom_junkie", function(source, item)
    local Player = QBCore.Functions.GetPlayer(source)
	if Player.Functions.RemoveItem(item.name, 1, item.slot) then
        TriggerClientEvent("consumables:client:Eat", source, item.name)
    end
end)

---Add More Food items here
```
4. go to you qb-smallresources\config/lua and copy and past the [consumables.md](consumables.md) at Config.Consumables = {
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Add to config.lua example !!!
```
Config.Consumables = {
    eat = { 
        -- default food items
        ['sandwich'] = math.random(35, 54),
        ['tosti'] = math.random(40, 50),
        ['twerks_candy'] = math.random(35, 54),
        ['snikkel_candy'] = math.random(40, 50),
        --add your config code here
        --uj-qbfood
        ["atom_junkie"] = math.random(35, 54),
        ---add the reste here 
    },
}
```
5. Add all the images in [pic](pic) to your inventory\html\images
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Contributing

If you'd like to contribute to the development of this script, feel free to fork the repository and submit a pull request with your changes. Bug fixes, feature enhancements, and documentation improvements are all welcome!

# License

 This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.