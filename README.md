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

3. go to you qb-core\shared\item/lua and copy and past the [items.lua.md](items.lua.md) at the buttome
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-- Define food items in Lua
local foodItems = {
    ['atom_junkie'] = {
        ['name'] = 'atom_junkie',
        ['label'] = 'Atom Junkie',
        ['weight'] = 100,
        ["decay"] = nil,
        ['type'] = 'item',
        ['image'] = 'atom_junkie.png',
        ["created"] = nil,
        ["delete"] = true,
        ['unique'] = false,
        ['useable'] = true,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = ''
    },
    ['bacon_eggs'] = {
        ['name'] = 'bacon_eggs',
        ['label'] = 'Bacon n Eggs',
        ['weight'] = 100,
        ["decay"] = nil,
        ['type'] = 'item',
        ['image'] = 'bacon_eggs.png',
        ["created"] = nil,
        ["delete"] = true,
        ['unique'] = false,
        ['useable'] = true,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = ''
    },
    -- Add more food items here
}

-- Output the Lua code defining the food items
print("-- Define food items in Lua")
print("local foodItems = {")
for itemName, itemInfo in pairs(foodItems) do
    print("\t['" .. itemName .. "'] = {")
    for key, value in pairs(itemInfo) do
        if type(value) == "string" then
            print("\t\t['" .. key .. "'] = '" .. value .. "',")
        else
            print("\t\t['" .. key .. "'] = " .. tostring(value) .. ",")
        end
    end
    print("\t},")
end
print("}")

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Contributing

If you'd like to contribute to the development of this script, feel free to fork the repository and submit a pull request with your changes. Bug fixes, feature enhancements, and documentation improvements are all welcome!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

