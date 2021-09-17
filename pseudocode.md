| Project | Author | Description |
|---|---|---|
| Pseudo Code | Michael Chinn | In this project I will be writing pseudo code for cooking chicken parmesan. |
<hr>

## Objective
To take a list of ingredients, perform various operation upon them, using various tools, in various workspaces, to create Chicken Parmesan.

Object Description

1. Workspace
    - Counter-Top
        - This workspace can receive all containers.
        - This is the starting location of all ingredients.
    - Stove-Top
        - This workspace can only receive Large Skillet containers.
        - Temperature can be set to "Low", "Medium" or "High".
    - Oven
        - This workspace can recieve Baking Dish containers.
        - Temperature can be set to an INT in the range of 0-500.
        - When the desired set temperature is reached BOOL preheat should = true.
        - Door can be open and shut.
2. Ingredients
    - ObjectArray
        - A list of ingredients which have names and quantities, from which we will take and add to containers then perform operations on.
        - When ingredients are removed quantities should be decremented.
        - When a quantity = 0, ingredient should be removed from the workspace.
3. Containers
    - Mixing Bowl
        - This container can recieve all ingredients.
        - Ingredients in this container can be...
            - Add
            - Remove
            - Mix
            - Pat
            - Flip
            - Check
    - Large Skillet
        - This container will recieve ingredients after they have been processed in the Counter-Top workspace.
        - Ingredients in this container can be...
            - Add
            - Remove
            - Flip
            - Check
    - Baking Dish
        - This container will recieve ingredients from both the Counter-Top and Large Skillet workspaces.
        - Ingredients in this container can be...
            - Add
            - Remove
            - Check
    - Plate
        - This container will recieve ingredients from the Oven workspace.
        - Ingredients in this container can be...
            - Add
    - Cutting Board
        - This container will receive ingredients from the Counter-Top workspace.
        - Ingredients in this container can be...
            - Add
            - Remove
            - Cut
            - Inscision
            - Pound
4. Tools
    - Hands
    - Eyes
    - Tongs
    - Meat Mallet
    - Butchers Knife
    - Meat Thermometer
    - Whisk
    - Plastic Sheet
5. Operations - *Functions*
    - Add
        - Add an ingredient to the specified container increasing its quantity.
    - Remove
        - Remove an ingredient from a specified container decreasing its quantity.
    - Move
        - Remove an ingredient from a specified container and Add it to another
    - Mix
        - Take multiple ingredients located in a specified container...
            - Use Eyes to Check whether the ingredients are mixed.
            - Remove ingredients.
            - Add new combined ingredient.
        - The tools used to perform this operation are..
            - Hands
            - Whisk
            - Eyes
    - Pat
        - Take an ingredient and apply it to the surface of another ingredient.
            - Use Eyes to Check whether the ingredients are patted.
            - Remove ingredients.
            - Add new combined ingredient.
        - The Tools used to peformed this operation are...
            - Hands
            - Eyes
    - Flip
        - Take an ingredient and turn it over so that the side of it that was down-facing is now it's upside.
        - The Tools used to perform this operation are...
            - Hands
            - Tongs
    - Check
        - Check the current state of a specific ingredient.
        - The tools used to perform this operation are...
            - Eyes
            - Meat Thermometer
    - Cut
        - Take an ingredient and split it into multiple pieces.
            - Remove ingredient from container.
            - Add x new ingredients back into container, where x = cuts + 1 and quantity = original quantity / cuts.
        - The tools used to perform this operation are..
            - Butchers Knife
    - Inscision
        - Take an ingredient and cut a slit into it, effectivly converting the ingredient into an ingredient & container.
            - Add a new property to the ingredient.
            - Specified ingredients can be added to this new insiscion property.
        - The tools used to perform this operation are..
            - Butchers Knife
    - Pound

# Pseudo Code

## Initialization

### Workspaces
```
INIT counterTop  = kitchen.workspace.counterTop
INIT stoveTop = kitchen.workspace.stoveTop
INIT oven = kitchen.workspace.oven
```

### Ingredients 
```
INIT counterTop.ingredients = ARRAY_START
    OBJECT_START
        name: "Chicken Breast", 
        qty: 4 
    OBJECT_END, 
    OBJECT_START
        name: "Flour", 
        qty: 2, 
        unit: "cup"
    OBJECT_END, 
    OBJECT_START 
        name: "Egg", 
        qty: 2
    OBJECT_END, 
    OBJECT_START 
        name: "Breadcrumbs", 
        qty: 1, 
        unit: "canister" 
    OBJECT_END, 
    OBJECT_START 
        name: "Shredded Mozzerella", 
        qty: 1, 
        unit: "lbs" 
    OBJECT_END, 
    OBJECT_START 
        name: "Grated Parmesan", 
        qty: 1, 
        unit: "shaker" 
    OBJECT_END, 
    OBJECT_START 
        name: "Salt", 
        qty: 1, 
        unit: "shaker" 
    OBJECT_END, 
    OBJECT_START 
        name: "Pepper", 
        qty: 1, 
        unit: "shaker" 
    OBJECT_END, 
    OBJECT_START 
        name: "Garlic Powder", 
        qty: 1, 
        unit: "shaker" 
    OBJECT_END, 
    OBJECT_START 
        name: "Onion Powder", 
        qty: 1, 
        unit: "shaker" 
    OBJECT_END, 
    OBJECT_START 
        name: "Ground Basil", 
        qty: 1, 
        unit: "shaker" 
    OBJECT_END, 
    OBJECT_START 
        name: "Ground Oregeno", 
        qty: 1, 
        unit: "shaker" 
    OBJECT_END, 
    OBJECT_START 
        name: "Tomato Sauce", 
        qty: 1, 
        unit: "Jar" 
    OBJECT_END, 
    OBJECT_START 
        name: "Ground Beef", 
        qty: 1, 
        unit: "shaker"  
    OBJECT_END
ARRAY_END
```

### Containers
```
INIT counterTop.containers = ARRAY_START ARRAY_END
INIT stoveTop.containers = ARRAY_START ARRAY_END
INIT oven.containers = ARRAY_START ARRAY_END
```

### Tools
```
INIT kitchen.tools = ARRAY_START
    Hands,
    Eyes,
    Tongs,
    Meat Mallet,
    Butchers Knife,
    Meat Thermometer,
    Whisk,
    Plastic Sheet
ARRAY_END
```

### Helper Functions
```
addContainer(workspace, containerType, containerName){
    workspace.containers.push(  OBJECT_START
        name: containerName,
        type: containerType,
        containerIngredients: ARRAY_START ARRAY_END
    OBJECT_END )
}
```
```
useTool(tool, container, action){
    container.tool.action.status = "used"
}
```
```
add(ingredient, container, quantity){
    IF ingredient.unit
        container.containerIngredients = OBJECT_START 
            name: ingredient.name
            quatity: ingredient.quantity
            unit: ingredient.unit
        OBJECT_END
    ELSE
        container.containerIngredients = OBJECT_START 
            name: ingredient.name
            quantity: ingredient.quantity 
        OBJECT_END
    ENDIF
}
```
```
remove(ingredient, container, removedQuantity){
    container.containerIngredient.ingredient.quantity = container.containerIngredient.ingredient.quantity - removedQuantity 
    IF container.containerIngredients.ingredient.quantity === 0 || removedQuantity === "all"
        container.containerIngredients.REMOVE(ingredient)
    ENDIF
    RETURN ingredient
}
```
```
move(ingredient, sourceConainer, targetContainer){
    remove(ingredient, sourceContainer)
    add(ingredient, targetContainer)
}
```
```
mix(ARRAY_START ingredients ARRAY_END, newIngredient, container, tool){
    useTool('kitchen.tools[tool]', container, 'mix')
    IF container.tool.action.status === "used" && check(container, eyes, "mixed")
        FOR ingredient IN ingredients
            remove(ingredient, container, "all")
        ENDFOR
        add(newIngredient, container, 1)
    ENDIF
}
```
```
pat(ingredient1, ingredient2, newIngredient, container){
    useTool(kitchen.tools[Hands], container)
    IF container.tool.action.status === "used" && check(container, ingredient, eyes, "patted")
        remove(ingredient1, container, "all")
        remove(ingredient2, container, "all")
        add(newIngredient, container, 1)
    ENDIF
}
```
```
flip(ingredient, container, tool){
    useTool(tool, container)
    IF container.tool.action.status === "used"
        ingredient.status = "flipped"
        RETURN true
    ENDIF
}
```
```
check(container, ingredient, tool, checkStatus){
    IF tool === kitchen.tools[eyes]
        useTool(container, kitchen.tools[tool], view)
        IF container.tool.action.status === "used" && ingredient.status === checkStatus
            RETURN true
        ENDIF
    ELSEIF tool === kitchen.tools[Meat Thermometer]
        useTool(container, kitchen.tools[tool], checkTemp)
        IF container.tool.action.status === "used" && ingredient.status === checkStatus
            RETURN true
        ENDIF
    ENDIF
}
```
```
cut(ingredient, container, pieces){
    remove(ingredient, container, 1)
    FOR i = 0; i < pieces; i++
        add(ingredient, container, 1)
    ENDFOR
}
```
```
inscision(ingredient, container){
    container.containerIngredient.ingredient.inscision = ARRAY_START ARRAY_END
}
```
```
pound(ingredient, container){
    useTool(Meat Mallet, container)
    IF container.tool.action.status === "used"
        ingredient.status = "pounded"
        RETURN true
    ENDIF
}
```
### The Process
```
addContainer(counterTop, "Cutting Board", cuttingBoard)
add("Chicken Breast", cuttingBoard, 4)
FOREACH "Chicken Breast" on cuttingBoard
    pound("Chicken Breast", cuttingBoard)
    add("Salt", cuttingBoard, "4 shakes")
    add("Pepper", cuttingBoard, "4 shakes")
    mix(cuttingBoard.containerIngredients, "Salted and Peppered Chicken Breast", kitchen.tools.Hand)
    inscision("Salted and Peppered Chicken Breast", cuttingBoard)
    add("Shredded Mozzerella", "Salted and Peppered Chicken Breast", "5 pinches")
ENDFOREACH

addContainer(counterTop, Mixing Bowl, mixBowl01)
add("Flour", mixBowl01, 2)
add("Flour", mixBowl01, 2)
```