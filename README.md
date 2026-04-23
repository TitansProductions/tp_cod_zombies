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

Inside the data where the comment is (-- your objects here) is where the objects are going to be placed.

You Have (3) ways:

1. Use modified spooni spooner that we provide and when placing getting the objectloader data as shown below in the screenshot (it will print on f8 the placed object, objectloader data to copy and laste automatically).


2. Use normal spooni spooner and manually take each placed object data (model, x,y,z,pitch,roll,yaw)

3. Create a ymap if its easier for you to do it. 

__How to use polyzone and why is it required?__

The reason for the polyzone requirement is because we want to prevent players to abuse the game and find way outs from the map. By having a zone, we will force the player to stay only inside that zone and once player attempts to go somewhere else, it wont be possible. 

*Keep in mind, the shape of the zone must be the one that players will be allowed to play inside, so dont make the zone bigger or not having any shape / design shape, because players will be getting out (for example, because barriers are open, we dont want them to get out of those barriers).*

Lets start making the map zone properly,

__X,Y,Z Explanation (Vector3 & Vector2)__

You need to understand how the configuration works related to the XYZ parts.

Through a `vector3` or a table form, you can get the X,Y,Z coordinates. 

1. If its a vector3, it will look like this:
`vector3(0, 0, 0) --0, 0, 0 (of vector3, represents X,Y,Z).`

2. If its a table form, it will look like this: `{ x = 0, y = 0, z = 0 .. } -- All that in a table form already represents everything we need without explanation.`

__Vector2__

In our configuration file, it requires a vector2, what is a vector2? vector2 is X,Y without the Z included (You get that also from vector3 or a table form).

So when getting the coords from a script, it will show you a vector3, you just change it into a vector2 with just X,Y inside only and not Z and the same if its a table form, you create a vector2 with X,Y that the table provides you. 

__MinZ & Max Z__

The **MinZ** and **MaxZ** that are included on the configuration when creating a zone, it means that it requires the Minimum Z position (lower point) and Maximum Z position (highest point) of a zone. 

To understand better, its like a building, you define the lowest point of the building like a point underneath the player and then the highest point of this building. This is how a zone works, you define the MinZ and MaxZ of the whole zone. You can also use the **Debug** to true to display into you the shape of the created zone and the height. 

__How to create a shape of the zone?__

To create a shape of a zone is actually very simple to understand, you have to think it as a paper drawing. Imagine drawing a town, a field, anything, you cannot draw it randomly can you? you need an order to draw a town or a field, because if you draw it in random spots, then the town or a field will not be called that way. This is also how to create a zone, it needs a specific order, like drawing on a paper in order to be made properly. 

I personally suggest (2) ways:

1. SPOONI SPOONER: A very great script that you can just place some barrels with the design you want and get their position one by one (in order like drawing) for the vector2 coords that are required.

2. Coords script: There are plenty of coords script that you can take your player current coords through a command, this is faster for those who have a bit more experience. 


# Development API
