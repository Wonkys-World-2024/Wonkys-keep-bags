# Wonky’s Keep Bags — Dev Bag Edition
Preview https://youtu.be/ss9Gh1RdKcI
A customized fork of [Swkeep’s keep-bags](https://github.com/swkeep/keep-bags), based on version 2.2.0. Adds the `devbag` alongside the existing backpacks, duffle, briefcase and service bags.

The Dev Bag has **50 slots** and a configured capacity of **100,000,000 grams** on ox_inventory. The item has no built-in staff permission check. Restrict how it is issued if it is intended for staff only.

## Setup for Qbox and ox_inventory

1. Install oxmysql, ox_inventory and [keep-harmony](https://swkeep.tebex.io/package/5592482). Configure keep-harmony for your framework and inventory. For clothing integration, use the appearance resource supported by your keep-harmony setup, such as [illenium-appearance](https://github.com/iLLeniumStudios/illenium-appearance).
2. Import `sql.sql` into your server database to create the retrieval table.
3. Copy the supplied inventory images into `ox_inventory/web/images`. Add item definitions for the bags enabled in `config.lua`. The upstream examples are in [UPSTREAM-README.md](UPSTREAM-README.md). If enabling `backpack3`, register it using the same item format as the other backpacks.
4. Add this entry inside the returned table in `ox_inventory/data/items.lua`:

   ```lua
   ['devbag'] = {
       label = 'Dev Bag',
       weight = 15,
       stack = false,
       close = true,
       description = 'High-capacity development bag',
       client = { image = 'duffle1.png' },
   },
   ```

5. Keep the resource folder named `keep-bags`. Start it after oxmysql, ox_inventory and keep-harmony with `ensure keep-bags`. Restart the inventory or server after adding items. Test opening the Dev Bag and storing and retrieving an item.

## Credits and license

Original resource by Swkeep. Dev Bag configuration by Wonky’s World. The original notices and [GPL-3.0 license](LICENSE) are included.
