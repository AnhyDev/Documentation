#### Adding a New Trade

```shell
/shop add <key>
```

- To add a trade, you need to place items in slots 1, 2, and 3 of your inventory, as shown in the screenshot below.
- Slots 1 and 2 represent the price of the item; one of these slots can be left empty.
- Slot 3 is the item being sold for the specified price.
- `<key>` is the unique identifier for the trader.
- Requires the permission: `anhyshop.product.add`.

<div align="center">
    <img src="../assets/addtrade.png">
</div>

#### Replacing an Existing Trade

```shell
/shop replace <key>
```

- To replace a trade, the placement of items in the slots is the same as when adding a new trade.
- If the item in slot 3 is found, its price will be updated to the values in slots 1 and 2.
- If the item in slot 3 is not found, it will be added as a new trade.
- `<key>` is the unique identifier for the trader.
- Requires the permission: `anhyshop.product.replace`.

#### Removing an Existing Trade

```shell
/shop remove <key>
```

- To remove a trade, place the specified item in slot 3; slots 1 and 2 are not required.
- `<key>` is the unique identifier for the trader.
- Requires the permission: `anhyshop.product.remove`.