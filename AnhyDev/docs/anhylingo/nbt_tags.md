#### Adding or Modifying Data

```
/lingo data set <data_key> <params...>
```
Sets the key `data_key` with parameters `params`, specifying the data type (e.g., `string:value, int:10`). This command stores data in the `PersistentDataContainer` for the item in the player's hand.

#### Viewing Data List

```
/lingo data list
```
Displays a list of all data stored in the `PersistentDataContainer` for the item in the player's hand.

#### Viewing Specific Data Values

```
/lingo data info <data_key>
```
Shows the value of a specific key `data_key` stored in the `PersistentDataContainer` for the item in the player's hand.

These changes ensure that data management is done using the safer and more convenient `PersistentDataContainer`, while maintaining similar functionality to the previous NBT-based system.