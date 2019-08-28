# hass-momentary
### Momentary Switch Component for Home Assistant
A simple switch component that once turned on will turn itself off. 

## Table Of Contents
1. [Notes](#Notes)
1. [Thanks](#Thanks)
1. [Installation](#Installation)
   1. [Migrating from Old Layout](#Migrating-from-Old-Layout)
   1. [Manually](#Manually)
   1. [From Script](#From-Script)
1. [Component Configuration](#Component-Configuration)

## Notes
Wherever you see `/config` in this README it refers to your home-assistant configuration directory. For me, for example, it's `/home/steve/ha` that is mapped to `/config` inside my docker container.

## Thanks
Many thanks to:
* [![JetBrains](/images/jetbrains.svg)](https://www.jetbrains.com/?from=hass-aarlo) for the excellent **PyCharm IDE** and providing me with an open source license to speed up the project development.

## Installation

### HACS
[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)
Momentary is going to be part of the default HACS store. If you're not interested in development branches this is the easiest way to install.

### Manually
Copy the `momentary`directory into your `/config/custom_components` directory.

### From Script
Run the install script. Run it once to make sure the operations look sane and run it a second time with the `go` paramater to do the actual work. If you update just rerun the script, it will overwrite all installed files.

```sh
install /config
# check output looks good
install go /config
```

## Component Configuration
Add the following to your `configuration.yaml` to enable the component:

```yaml
momentary:
```

To create a switch use the following:

```yaml
switch:
  - platform: momentary
    name: Empty House Trigger
    on_for: 5
    allow_off: True
```

The following additional parameters can be specified against the switches:

| Field                 | Type     | Default          | Description                       
|-----------------------|----------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name                  | strings  |                  | Name of the switch. Has to be supplied.                                                                                                                                                                                                     |
| on_for                | seconds  | 1                | Amount of time to turn the switch on for.                                                                                                                                                                                                   |
| allow_off             | Boolean  | False            | Allow switched to be turned off manually.                                                                                                                                                                                                   |

To add multiple switches repeat the whole component configuration:

```yaml
switch:
  - platform: momentary
    name: Empty House Trigger
  - platform: momentary
    name: Bad Weather Trigger
```