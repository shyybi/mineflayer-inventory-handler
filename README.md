# mineflayer-inventory-handler

This is a Inventory Handler for Mineflayer (Minecraft bot) lib.
Because the original one was shitty

## Exemple of project structure :

```
.
├── README.md
├── index.js
├── package-lock.json
├── package.json
└── src
	└── chest.js
```

## Function List:

### Core Functions

**`sayItems(items)`**
- Lists all items in the bot's inventory or specified container
- Displays item names and quantities in chat
- Shows "empty" if no items are present

**`watchChest(minecart, blocks)`**
- Opens and monitors chest containers (regular chests, ender chests, trapped chests, or chest minecarts)
- Provides real-time updates when items are added or removed
- Supports chest minecarts when `minecart` parameter is true
- Allows filtering by block types through `blocks` parameter

**`watchFurnace()`**
- Opens and monitors furnace blocks (regular and lit furnaces)
- Displays current input, fuel, and output items
- Shows real-time fuel percentage and smelting progress
- Provides updates when furnace contents change

**`watchEnchantmentTable()`**
- Opens and monitors enchantment tables
- Shows available enchantment choices and levels
- Handles lapis lazuli placement for enchanting
- Manages the enchanting process from start to finish

**`useInvsee(username, showEquipment)`**
- Uses the `/invsee` command to view another player's inventory
- Can display either regular inventory items or equipped items
- Requires appropriate server permissions to function

### Utility Functions

**`itemToString(item)`**
- Converts item objects to readable string format
- Returns item name and count (e.g., "diamond sword x 1")
- Returns "(nothing)" for empty slots

**`itemByType(items, type)`**
- Searches through items array to find item by type ID
- Returns the first matching item found
- Returns null if no matching item exists

**`itemByName(items, name)`**
- Searches through items array to find item by name
- Returns the first matching item found  
- Returns null if no matching item exists

### Container Interaction Functions

**`withdrawItem(name, amount)`** *(within watchChest)*
- Withdraws specified amount of named item from chest to bot inventory
- Provides success/failure feedback in chat
- Handles errors gracefully with appropriate messages

**`depositItem(name, amount)`** *(within watchChest)*
- Deposits specified amount of named item from bot inventory to chest
- Provides success/failure feedback in chat
- Handles errors gracefully with appropriate messages

**`putInFurnace(where, name, amount)`** *(within watchFurnace)*
- Places items in furnace input or fuel slots
- `where` parameter specifies "input" or "fuel" slot
- Manages item placement with error handling

**`takeFromFurnace(what)`** *(within watchFurnace)*
- Removes items from furnace slots (input, fuel, or output)
- `what` parameter specifies which slot to take from
- Provides feedback on successful item retrieval

**`putItem(name)`** *(within watchEnchantmentTable)*
- Places target item in enchantment table for enchanting
- Searches bot inventory for specified item name
- Handles placement errors appropriately

**`addLapis()`** *(within watchEnchantmentTable)*
- Adds lapis lazuli to enchantment table for enchanting process
- Searches for various lapis item types (dye, purple_dye, lapis_lazuli)
- Required for enchantment operations

**`enchantItem(choice)`** *(within watchEnchantmentTable)*
- Performs enchantment using specified choice number
- Choice corresponds to available enchantment options
- Returns enchanted item upon successful completion

**`takeEnchantedItem()`** *(within watchEnchantmentTable)*
- Retrieves the enchanted item from enchantment table
- Completes the enchanting process
- Provides feedback on item retrieval

### Chat Commands Supported

- `list` - Display bot's inventory
- `chest` - Open nearby chest
- `furnace` - Open nearby furnace  
- `dispenser` - Open nearby dispenser
- `enchant` - Open nearby enchantment table
- `chestminecart` - Open nearby chest minecart
- `invsee <username>` - View another player's inventory
- `close` - Close current container
- `withdraw <amount> <item>` - Remove items from chest
- `deposit <amount> <item>` - Add items to chest
- `input <amount> <item>` - Add items to furnace input
- `fuel <amount> <item>` - Add fuel to furnace
- `take <input|fuel|output>` - Remove items from furnace
- `put <item>` - Place item in enchantment table
- `add lapis` - Add lapis to enchantment table
- `enchant <choice>` - Enchant item with specified option
- `take` - Remove item from enchantment table

## Usage

Run the bot with:
```bash
node chest.js <host> <port> [<name>] [<password>]
```

This comprehensive inventory handler provides full interaction capabilities with Minecraft's container systems, making it easy to automate storage, smelting, and enchanting operations. 