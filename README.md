# Tutorials

## How to create a new map

Lets start from basics, to create a new map, you need an area, not small but similar to valentine, so you can create some stages and for the players to be able to walk around. 

Next, in that map, you have to design it, where the barriers are going to be, the vending machines, mystery boxes, doors (blockways) and all that which are highly required to have a good and interesting map. 

Once you design it and you dont have knowledge about ymaps and xmls, in that script we provide you a map builder which is called **object loader**. The object loader purpose is to avoid ymaps and xmls and create the desired areas from a configuration 

__How to use objectloader:__

By default, on the `config/map_creator` you will find the **valentine** map which is an example.  All the objects firstly placed through spooni spooner script ( we personally use spooni-spooner of our version - modified) and then, we are getting the placed object data (model, x,y,z,pitch,roll,yaw) and we add them on the new map configuration file. 

Ofcourse, since you are making a new map, select template.lua file, copy and paste it and rename it to the new map name, then, inside is where you are going to place all objects. 

1. Go to `config/map_creator` directory folder.
2. Copy `template.lua` file.
3. Paste and rename it to the new map name (ex: rhodes.lua)
4. Open `rhodes.lua` and its going to be similar as this:

```lua
---------------------------------------------------------------
--[[ Functions ]]--
---------------------------------------------------------------

-- (!) DO NOT RENAME THE `data` variable, it must always be as `data`.
-- Checkout the examples below how we create objects to the specified locations.

local data = { 
    -- your objects here
}
--------------------------------------------------------------
--[[ DO NOT TOUCH ]]--
---------------------------------------------------------------

Citizen.CreateThread(function()
    local objCount = 0
    for _, v in pairs (data) do
        objCount = objCount + 1
        InsertObjectData(v)
    end

    if Config.Debug then
 ------
    end
end)

```

# Development API
