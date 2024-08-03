### Using the Plugin as a Library

AnhyLingo provides an API that allows developers of other plugins to create multilingual functionality.

##### Adding via Gradle

```groovy
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}

dependencies {
    implementation 'com.github.AnhyDev:AnhyLingo:v0.1.2'
}
```

##### Adding via Maven

```xml
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>

<dependency>
    <groupId>com.github.AnhyDev</groupId>
    <artifactId>AnhyLingo</artifactId>
    <version>v0.1.2</version> 
</dependency>
```

##### Example Usage

###### Language Management Class

```java
package myplugin.lang;

import myplugin.MyPlugin;
import ink.anh.lingo.api.lang.LanguageManager;

public class LangMessage extends LanguageManager {

    private static LangMessage instance = null;
    private static final Object LOCK = new Object();

    private LangMessage(MyPlugin plugin) {
        super(plugin, "lang"); // 'lang' is the folder name for language files
    }

    public static LangMessage getInstance(MyPlugin plugin) {
        if (instance == null) {
            synchronized (LOCK) {
                if (instance == null) {
                    instance = new LangMessage(plugin);
                }
            }
        }
        return instance;
    }
}
```

###### Initialization in the Main Plugin Class

```java
import myplugin.lang.LangMessage;
import ink.anh.lingo.api.lang.LanguageManager;

public class MyPlugin extends JavaPlugin {

    private static MyPlugin instance;
    private LanguageManager languageManager;

    @Override
    public void onEnable() {
        instance = this;
        languageManager = LangMessage.getInstance(this);
    }

    public static MyPlugin getInstance() {
        return instance;
    }

    public LanguageManager getLanguageManager() {
        return languageManager;
    }
}
```