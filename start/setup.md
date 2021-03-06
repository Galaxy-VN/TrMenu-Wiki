---
description: 'After installing the plugin, files will be generated in the plugins folder'
---

# Setup

## Files/Folders

{% tabs %}
{% tab title="/settings.yml" %}
Plugin's main configuration file.
{% endtab %}

{% tab title="/menus/" %}
Plugin's default menu loader folder
{% endtab %}

{% tab title="/lang/en\_US.yml" %}
You can edit most of the plugin's messages in the language file
{% endtab %}

{% tab title="/items.yml" %}
Storage for items created with the `/trmenu itemRepo` command
{% endtab %}
{% endtabs %}

## Setup

* The `settings.yml` file is the main configuration file of the plugin.
* The plugin will detect changes automatically and reload the file.

{% code title="settings.yml" %}
```yaml
#
# Configuration
#
Options:
  # Whether the debug mode should be enabled or not (more information will be sent to the console)
  Debug: false
  # Language of the plugin
  # Available： zh_CN, zh_TW, en_US, fr_FR, th_TH, es_MX
  Locale: en_US
  # Whether to hide the Logo of the plugin in the console on startup
  Hide-Logo: false
  # When enabled TrMenu will get the player heads datas from Mojang's API
  # [RECOMMENDED] If disabled, it will get them with https://github.com/Electroid/mojang-api
  Skull-Mojang-API: false

#
# Get menus from a path leading to a folder or directly a menu
# Supports ItemRepo files to get pre-made items for your menus
#
Load-Menu-Files:
  - 'plugins/CustomMenusFolder'

#
# Actions Configuration
#
Actions:
  # Customize the words used to cancel an input catcher, supports regex
  Catcher-Cancel-Words:
    - '(?i)cancel|quit|exit|end|stop'

#
# Menu Items Configuration
#
Item:
  # Default color for items' names
  Default-Color-Name: '&7'
  # Default color for items' lores
  Default-Color-Lore: '&7'

#
# Actions Shortcuts Configuration
#
Shortcuts:
  Offhand: 'open: Example'
  Sneaking-Offhand:
    - condition: 'hasPerm.trmenu.shortcut'
      execute: 'open: Example'
  Right-Click-Player: []
  Sneaking-Right-Click-Player: []
  PlayerInventory-Border-Left: []
  PlayerInventory-Border-Right: []
  PlayerInventory-Border-Middle: []

#
# Register commands with actions and arguments
# Supports tab-completition !
# (WARNING: A server restart is required to add, change or remove commands)
#
RegisterCommands:
  # Command name
  openMenus:
    # Command Aliases
    aliases: []
    # Required permission
    permission: null
    # Actions executed without any arguments
    execute:
      - 'tell: &7Argument `example` Required!'
    # Arguments with their actions
    arguments:
      example: 'open: example'

#
# When enabled, TrMenu will ignore cancelled events monitored by some plugins
# If you encouter compatibilities issues, try to toggle the option.
#
Events-Ignore-Cancelled:
  PlayerCommandPreprocessEvent: true
  InventoryOpenEvent: true
  InventoryClickEvent: true
```
{% endcode %}

