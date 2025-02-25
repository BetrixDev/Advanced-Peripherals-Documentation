# Inventory Manager

!!! picture inline end
    ![Header](https://intelligence-modding.de/wp-content/uploads/2021/04/Inventory-Manager.png){ align=right }

The Inventory Manager can communicate with the player's inventory. You need to right click a [Memory Card](../items/memory_card.md) and put the card into the manager to use it.

!!! info
    Only one Memory Card can be linked by Inventory Manager.

<br><br>

## Overview

| Peripheral Name  | Interfaces with  | Events | Introduced in |
| ---------------- | ---------------- | ------ | ------------- |
| inventoryManager | Player Inventory | No     | 0.5b          |

## Functions

```lua
local manager = peripheral.find("inventoryManager") -- Finds the peripheral if one is connected

if manager == nil then error("inventoryManager not found") end

manager.addItemToPlayer("UP", 63, 4, "minecraft:dirt") --Will add 63 dirt to the players inventory from the chest above. 4 Is the slot

manager.removeItemFromPlayer("UP", 114, -1, "minecraft:stone") --Will remove 114 stone blocks from the players inventory to the chest above. -1 Says it will ignore the slot

manager.removeItemFromPlayer("UP", 400) --Will remove 400 items from the players inventory to the chest above
```

| Function                                                                | Returns    | Description                                                                                                                                                                                                                                                |
| ----------------------------------------------------------------------- | ---------- | -------------------------------------------- |
| addItemToPlayer(string direction, int count\[, int slot\, string item])      | int amount | Adds an item to the player's inventory. `direction` is the direction for the chest/inventory block. The Inventory Manager will add a random item to the player's inventory if the argument `item` is null.|
| getArmor()                                                              | table      | Returns the content of the player's armor. |
| getItems()                                                              | table      | Returns the content of the player's. |
| getOwner()                                                              | string     | Returns the owner of the memory card, nil if the memory card is. |
| isPlayerEquipped()                                                      | boolean    | Returns true if the player is wearing one or more armor. |
| isWearing(int slot)                                                     | boolean    | Returns true if the player is wearing a armor piece on the given slot. Slots: 103(Helmet)-100(Boots). |
| removeItemFromPlayer(string direction, int count\[, int slot\, string item]) | int amount | Removes an item from the player's inventory to the given inventory direction. `direction` is the direction for the chest/inventory block. The Inventory Manager will remove a random item from the player's inventory if the argument `item` is null. |
| getItemInHand()                                                         | table      | Returns the item in the hand. |
| getFreeSlot()                                                           | int        | Returns the nearest free slot of the player(-1 if inventory is full). |
| isSpaceAvailable()                                                      | boolean    | Returns true if space is available in the player inventory. |
| getEmptySpace()                                                         | int        | the amount of empty slots. |

## Changelog/Trivia

0.7.4r
Added `getItemInHand`, `getFreeSlot`, `isSpaceAvailable` and `getEmptySpace` to the inventory manager.
Added support for armor items. You can use the slots 100-103 to access armor items.

0.7r
Added the slot parameter
Also changed the direction parameter to computercraft directions.

0.5.2b
Fixed a bug, that the inventory manager does not drop the contents.

0.5b
Added the Inventory Manager and Memory Card
