JavaDoc for AnhyLibAPI are available at the following link: [AnhyLibAPI Documentation](https://dev.anh.ink/anhylibapi/javadoc/).


### Integration with Gradle and Maven:

#### Gradle:

```groovy
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}
```
```groovy
dependencies {
    implementation 'com.github.AnhyDev:AnhyLibAPI:v1.3.3'
}
```

#### Maven:

```xml
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>
```
```xml
<dependency>
    <groupId>com.github.AnhyDev</groupId>
    <artifactId>AnhyLibAPI</artifactId>
    <version>v1.3.3</version>
</dependency>
```

### Plugin Writing Examples:

For a comprehensive, ready-to-use plugin example that implements AnhyLibAPI, visit the following link: [AnhyLibAPI Plugin Examples](https://github.com/AnhyDev/ResourcesHub/tree/main/AnhyLibAPI/examples/ExampleLangPlugin). This example is more than just sample code; it is a fully functional plugin featuring multilingual support, configurable settings, and player commands. Developers can use this plugin as a foundation, renaming and repackaging as needed, while also adding their own code to extend its functionality. It serves as an excellent starting point for understanding and applying AnhyLibAPI in a practical, real-world plugin project.

#### See below for some examples from this code:

```java
package ink.anh.example;

import java.io.File;
import java.io.IOException;
import org.bukkit.Bukkit;
import org.bukkit.configuration.file.YamlConfiguration;
import org.bukkit.plugin.Plugin;

import ink.anh.api.LibraryManager;
import ink.anh.api.lingo.Translator;
import ink.anh.api.lingo.lang.LanguageManager;
import ink.anh.api.messages.Logger;
import net.kyori.adventure.platform.bukkit.BukkitAudiences;
import net.md_5.bungee.api.ChatColor;

public class GlobalManager extends LibraryManager {

    private static GlobalManager instance;
	private ExampleLangPlugin plugin;

	private LanguageManager langManager;
    private String pluginName;
    private String defaultLang;
    private static BukkitAudiences bukkitAudiences;
    private boolean debug;

	private GlobalManager(ExampleLangPlugin plugin) {
		super(plugin);
		this.plugin = plugin;
		this.saveDefaultConfig();
		this.loadFields(plugin);
	}

    public static synchronized GlobalManager getManager(ExampleLangPlugin plugin) {
        if (instance == null) {
            instance = new GlobalManager(plugin);
        }
        return instance;
    }

	@Override
	public Plugin getPlugin() {
		return plugin;
	}

	@Override
	public String getPluginName() {
		return pluginName;
	}

	@Override
	public BukkitAudiences getBukkitAudiences() {
		return bukkitAudiences;
	}

	@Override
	public LanguageManager getLanguageManager() {
		return this.langManager;
	}

	@Override
	public String getDefaultLang() {
		return defaultLang;
	}

	@Override
	public boolean isDebug() {
		return debug;
	}

    private void loadFields(ExampleLangPlugin plugin) {
        bukkitAudiences = BukkitAudiences.create(plugin);
        defaultLang = plugin.getConfig().getString("language", "en");
        pluginName = ChatColor.translateAlternateColorCodes('&',plugin.getConfig().getString("plugin_name", "ExampleLangPlugin"));
        debug = plugin.getConfig().getBoolean("debug", false);
        setLanguageManager();
    }

    private void saveDefaultConfig() {
    	File configFile = new File(plugin.getDataFolder(), "config.yml");
        if (!configFile.exists()) {
            YamlConfiguration defaultConfig = new YamlConfiguration();
            defaultConfig.set("plugin_name", "ExampleLangPlugin");
            defaultConfig.set("language", "en");
            defaultConfig.set("debug", false);
            try {
                defaultConfig.save(configFile);
                Logger.warn(plugin, "Default configuration created. ");
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }

    private void setLanguageManager() {
        if (this.langManager == null) {
            this.langManager = LangMessage.getInstance(this);;
        } else {
        	this.langManager.reloadLanguages();
        }
    }

	public boolean reload() {
		Bukkit.getScheduler().runTaskAsynchronously(plugin, () -> {
	        try {
	        	saveDefaultConfig();
	            plugin.reloadConfig();
	            loadFields(plugin);
	            Logger.info(plugin, Translator.translateKyeWorld(instance, "configuration_reloaded" , new String[] {defaultLang}));
	        } catch (Exception e) {
	            e.printStackTrace();
	            Logger.error(plugin, Translator.translateKyeWorld(instance, "err_reloading_configuration ", new String[] {defaultLang}));
	        }
		});
        return true;
    }
}
```

```java
package ink.anh.example;

import ink.anh.api.lingo.lang.LanguageManager;

public class LangMessage extends LanguageManager {

    private static LangMessage instance = null;
    private static final Object LOCK = new Object();

    private LangMessage(GlobalManager manager) {
        super(manager, "lang");
    }

    public static LangMessage getInstance(GlobalManager manager) {
        if (instance == null) {
            synchronized (LOCK) {
                if (instance == null) {
                    instance = new LangMessage(manager);
                }
            }
        }
        return instance;
    }
}
```

