# Prairie Grass for FS22
This mod will add a paintable Prairie Grass texture to your Paintable -> Plants menu, allowing you to paint in a new type of specialized meadow grass that will mow directly into Hay.

## Prairie Grass Features
- Mowable with standard mowers directly into Hay
- 4 growth stages, mowable at 3rd stage just like Meadow grass
- Two variants Normal & Tall
- NOT Plantable as a crop

*Prairie Grass*
- Grows 20% taller than standard meadow grass
- Results in 10% more harvest than standard meadow grass.
- Costs 10% more to paint

*Tall Prairie Grass*
- Grows 50% taller than standard meadow grass
- Results in 20% more harvest than standard meadow grass.
- Costs 20% more to paint



## Mod Installation Instructions
If you'd like to use this prefab as a mod, you can - but unfortunately, due to in-game restrictions - this mod requires additional updates to both the `map.xml` and `map.i3d` files for the map being used, and as such cannot be used with base game maps. Follow the instructions below to use as a mod

To install:
1. Download this mod, add to your mod folder, and add as installed when you start the game.
2. Unzip the Map being used, locate the `map.xml` file. Open the file for editing.
3. Find this line:
    ```
    <paintableFoliage layerName="meadow" startChannel="0" numStateChannels="4" />
    ```
4. Add two lines following that line so that the block looks something like this:
    ```
    <paintableFoliages>
        <paintableFoliage layerName="grass" startChannel="0" numStateChannels="4" />
        <paintableFoliage layerName="meadow" startChannel="0" numStateChannels="4" />
        <paintableFoliage layerName="prairie" startChannel="0" numStateChannels="4" />
        <paintableFoliage layerName="prairieTall" startChannel="0" numStateChannels="4" />
        <paintableFoliage layerName="decoBush" startChannel="0" numStateChannels="4" />
        <paintableFoliage layerName="decoFoliage" startChannel="0" numStateChannels="4" />
    </paintableFoliages>
    ```
5. Open the `map.i3d` file in the same directory, in the same text-editor.
6. Find this line:  (or `meadowFR.xml` depending on the map, note that the `fileId` may not be the same in your map)
    ```
    <File fileId="335" filename="$data/map/mapUS/foliage/meadow/meadowUS.xml"/>`
    ```
7. Add these lines right blow that line; the `fileId` you use must be greater than the largest id used wthin the map.
It's easiest to initially pick a overly large number; if you open the `map.i3d` file in GE and save, it will automatically renumber these `Ids`.
    ```
    <File fileId="10336" filename="../../../FS22_PrairieGrass/prairie/prairieGrass.xml"/>
    <File fileId="10337" filename="../../../FS22_PrairieGrass/prairie/prairieGrassTall.xml"/>
    ```
    Note that the `../../../` must match the directory structure of the map you're using. If the `map.xml` file is located in `maps/mapUS/map.i3d`, your mod directory is _three levels_ above the `map.i3d` file; you one need `../` for each level.
8. Find this line:  (note that the `fileId` may not be the same in your map)
    ```
    <FoliageType name="meadow" foliageXmlId="335"/>
    ```
9. Add these lines right blow that line; the `foliageXmlId` for each line must match the related `fileId` created above for each foliage.
    ```
    <FoliageType name="prairie" foliageXmlId="10336"/>
    <FoliageType name="prairieTall" foliageXmlId="10337"/>
    ```
10. Save your changes.
11. (optional) Open the map.i3d file in GE and save - doing so will automatically renumber the `foliageXmlId` that you created.
12. Launch and test your map.
13. (optional) re-zip your map file.



## Map Making Instructions
To install the brushes included here as an integral part of your map ther are two versions of said instructions, both sharing the same data; You can either follow the 
XML based instructions: [README.xml](README.xml) or the step by step instructions below.

1. Download the mod and unzip it.
2. Copy the `prairie` folder from this mod into your `maps/mapUS/foliages/` directory
3. Update the icon paths in both `priarieBrush.xml` and `prairieBrushTall.xml` to match your map directory location. ie: 
    ```
    <image>maps/mapUS/foliage/prairie/store_prairieGrassTall.dds</image>
    ```
4. Follow steps 2-9 above, but update the paths used in step 7 to be local, and look like this: `foliages/prairie/prairieGrass.xml`
5. Open `storeItems.xml` and find this line: (it may not include the `$data/` depending on your map structure)
    ```
    <storeItem xmlFilename="$data/foliage/meadow/meadowBrush.xml" />
    ```
6. Add two lines following that line to add the two new brushes.
    ```
    <storeItem xmlFilename="maps/mapUS/foliage/prairie/prairieBrush.xml" />
    <storeItem xmlFilename="maps/mapUS/foliage/prairie/prairieBrushTall.xml" />
    ```
7. Open the mod file `maps_fruitTypes.xml` and merge the new `fruitTypes` with your map `maps_fruitTypes.xml` file, appending the new fruits after `meadow`, and adding the `fruitTypeConverter` to the `mower` section.
8. Open the mod file `maps_fillTypes.xml` and merge the new `fillTypes` with your map `maps_fillTypes.xml` file, appending the new types after `meadow`.
9. Open the mod file `maps_growth.xml` and merge the new `fruit` into your `maps_growth.xml` file, appending the new types after `meadow`.
10. Copy the `<l10n>` translations for the brush names from the mod `modDesc.xml` and merge into your map's `modDesc.xml` file.

_Note_ for all of the above files - if you do not have a custom version of the same file currently in your map and are referring to the basegame `$data/maps/` files... to use this mod, you will have to have map specific versions of each of those files. 

Once that is done, yous hould not only have the paintable meadow foliage in game, but you'll also have `prairie` and `prairieTall` in your foliage layers to use in-game.