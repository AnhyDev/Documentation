### Administrator Commands

#### Plugin Reload

##### Reloading Configurations

```shell
/shop reload
```

- Reloads the language files and trader configurations from the database.
- Requires permission: `anhyshop.reload`.
- This command is also available from the console.

#### Managing Traders

##### Trader Information

```shell
/shop list
```

- Displays a list of all traders with their details: `<key>`, `<name>`, and `<number of trades>`.
- Requires permission: `anhyshop.trader.view`.
- This command is also available from the console.

##### Creating a New Trader

```shell
/shop newt <name>
```

- Creates a new trader with the name `<name>`, generating a unique key for them.
- Requires permission: `anhyshop.trader.create`.
- This command is also available from the console.

##### Deleting a Trader

```shell
/shop delt <key>
```

- Deletes an existing trader by their unique key `<key>`.
- Requires permission: `anhyshop.trader.delete`.
- This command is also available from the console.

##### Renaming a Trader

```shell
/shop rename <key> <new_name>
```

- Finds a trader by their unique key `<key>` and assigns them a new name `<new_name>`.
- Requires permission: `anhyshop.trader.rename`.
- This command is also available from the console.

##### Opening the Trade Inventory

```shell
/shop open <key> <player_name>
```

- Opens the trade for player `<player_name>` with the trader `<key>`.
- Requires permission: `anhyshop.trader.open`.
- This command is also available from the console.

##### Trading on Behalf of a Player

```shell
/shop trade <key>
```

- Opens a trade with the trader `<key>`.
- Requires permission: `anhyshop.trader.trade`.