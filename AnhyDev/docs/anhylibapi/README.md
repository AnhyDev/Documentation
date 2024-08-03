<div align="center">
    <img src="assets/logo_maxy.png" alt="AnhyFamily">
</div>

### AnhyLibAPI: For Minecraft Plugins

**AnhyLibAPI** is a library designed for integration into Minecraft plugins, developed to enhance their capabilities on servers running on Spigot, Paper, Purpur, and other Spigot forks.

**ProtocolLib** plugin version 5.0.0 or higher is required for operation.

**AnhyLibAPI** must be loaded on the server as a plugin. It's crucial to understand that **AnhyLibAPI**, in its role as a plugin, does not monitor any events, have timers, or interact with the world or players, ensuring no additional load on the server's operation and performance. The primary purpose of **AnhyLibAPI** is to provide its API to other plugins, serving as a robust foundation for extending their functionality. This design ensures that **AnhyLibAPI** enhances plugin capabilities without compromising server efficiency.

#### Key Features:

*   **Multilingual Support**: Easy integration of language packs for plugins.
*   **NBT Tags Handling**: Advanced management of NBT tags for flexible data interaction.
*   **Player Persistent Data**: Efficient use of persistent data for players.
*   **Customizing Messages**: Individual customization of message delivery to players.
*   **Logging**: Unique methods for event logging.