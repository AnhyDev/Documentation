#### Конфигурационный файл
Плагин AnhyFamily позволяет настраивать различные аспекты плагина, от баз данных до семейных функций. Ниже приведено детальное описание каждого параметра конфигурации.

#### Основные Настройки

- **language**: Язык по умолчанию, который будет использоваться, если перевод не найден на желаемом языке.
```yaml
  language: en
```

- **plugin_name**: Название плагина, которое будет отображаться пользователям в чате.
```yaml
  plugin_name: AnhyFamily
```

#### Настройки Базы Данных

- **database**: Настройки для подключения к базе данных. Возможные типы баз данных: 'SQLite' или 'MySQL'.
```yaml
  database:
    type: 'SQLite'
    mysql:
      host: 'db4free.net'
      port: 3306
      database: 'anhyfamily'
      username: 'anhydev'
      password: 'HE5rYZb2hygDf4FW'
      prefix: 'anhy_'
      useSSL: false
      autoReconnect: true
```

#### Настройки Цен

- **prices**: Настройки валюты и цен на различные действия в плагине.
```yaml
  prices:
    currency: VIRTUAL
    marriage: 0
    divorce: 0
    adoption: 0
```

#### Настройки Пола

- **gender**: Настройки, позволяющие выбор небинарного пола и соответствующие права для усыновления и заключения брака.
```yaml
  gender:
    non_binary: false
    non_binary_adoption: false
    non_binary_marriage: false
```

#### Настройки Церемоний

- **ceremonyRadius**: Максимальное расстояние от священника до жениха и невесты. Если 0, то ограничений нет.
```yaml
  ceremonyRadius: 20
```

- **ceremonyHearingRadius**: Радиус, в котором сообщение о браке будет видно в чате. Если 0, то все игроки, которые онлайн.
```yaml
  ceremonyHearingRadius: 200
```

- **marriedSymbol**: Символ, который используется для обозначения женатых игроков.
```yaml
  marriedSymbol: "⚭"
```

#### Настройки Частной Церемонии

- **privateCeremony**: Локация для проведения частной церемонии заключения брака.
```yaml
  privateCeremony:
    world: "world"
    x: 100
    y: 64
    z: -200
```

#### Настройки Семейного Дома

- **home**: Настройки для семейного дома.
```yaml
  home:
    timeout: 1440
    world: false
```

#### Настройки Семейного Сундука

- **chest**: Настройки для семейного сундука.
```yaml
  chest:
    command: true
    distance: 0
    world: false
    click: true
    material:
      - CHEST
      - BARREL
    distance_to_home: 20
```

#### Настройки Имен и Фамилий

- **languages_limitation**: Настройки ограничений для имен и фамилий с помощью регулярных выражений.
```yaml
  languages_limitation: "^(?!.*[-']{2})(?!.*--)(?!.*'')\\p{L}['-]*[\\p{L}]+$"
```

### Пример Конфигурационного Файла

```yaml
#
# ░█████╗░███╗░░██╗██╗░░██╗██╗░░░██╗███████╗░█████╗░███╗░░░███╗██╗██╗░░██╗░░░██╗
# ██╔══██╗████╗░██║██║░░██║╚██╗░██╔╝██╔════╝██╔══██╗████╗░████║██║██║░░╚██╗░██╔╝
# ███████║██╔██╗██║███████║░╚████╔╝░█████╗░░███████║██╔████╔██║██║██║░░░╚████╔╝░
# ██╔══██║██║╚████║██╔══██║░░╚██╔╝░░██╔══╝░░██╔══██║██║╚██╔╝██║██║██║░░░░╚██╔╝░░
# ██║░░██║██║░╚███║██║░░██║░░░██║░░░██║░░░░░██║░░██║██║░╚═╝░██║██║███████╗██║░░░
# ╚═╝░░╚═╝╚═╝░░╚══╝╚═╝░░╚═╝░░░╚═╝░░░╚═╝░░░░░╚═╝░░╚═╝╚═╝░░░░░╚═╝╚═╝╚══════╝╚═╝░░░
#
language: en
plugin_name: AnhyFamily

database:
  type: 'SQLite'
  mysql:
    host: 'db4free.net'
    port: 3306
    database: 'anhyfamily'
    username: 'anhydev'
    password: 'HE5rYZb2hygDf4FW'
    prefix: 'anhy_'
    useSSL: false
    autoReconnect: true

prices:
  currency: VIRTUAL
  marriage: 0
  divorce: 0
  adoption: 0

gender:
  non_binary: false
  non_binary_adoption: false
  non_binary_marriage: false

ceremonyRadius: 20
ceremonyHearingRadius: 200
marriedSymbol: "⚭"

privateCeremony:
  world: "world"
  x: 100
  y: 64
  z: -200

home:
  timeout: 1440
  world: false

chest:
  command: true
  distance: 0
  world: false
  click: true
  material:
    - CHEST
    - BARREL
  distance_to_home: 20

languages_limitation: "^(?!.*[-']{2})(?!.*--)(?!.*'')\\p{L}['-]*[\\p{L}]+$"
```

Этот конфигурационный файл позволяет настроить плагин AnhyFamily в соответствии с вашими потребностями, обеспечивая гибкое управление базой данных, ценами, гендерными параметрами, церемониями, семейными локациями и ограничениями для имен и фамилий.