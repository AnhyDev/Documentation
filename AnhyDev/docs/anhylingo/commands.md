#### Commands for Language Management

##### Commands for All Players

###### Setting Preferred Languages

```shell
/lingo set <langs>
```

`<langs>` can be one or more languages, such as `en` or `en it es`. The plugin will search for translations in the specified order.

###### Resetting the Selected Language

```shell
/lingo reset
```

This command clears the selected languages list, and the plugin will retrieve the language from the Minecraft client.

###### Viewing Selected Languages

```shell
/lingo get
```

Displays the selected languages for translation.

##### Commands for Administrators

###### Reloading the Plugin

```shell
/lingo reload
```

Reloads the general configurations and language files.

###### Information on Available Item Localizations

```shell
/lingo items list <lang>
```

Displays a list of "keys" for all items that have translations in the specified language.

###### Viewing Localization by Key

```shell
/lingo items <lang> <key>
```

Shows the name and description in the specified language for the given key.
