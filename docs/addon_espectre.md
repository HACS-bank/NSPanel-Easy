# Add-on: ESPectre

## Description

This add-on enables the use of your panel's Wi-Fi traffic to act as a motion sensor using the
ESPectre module - see (ESPectre.dev)[https://espectre.dev] for the details of how the module works.

If the display is blank, and motion is detected, the display wakes up.

For best results 

### Attention

1. The NSPanel is only just capable of running this addon in addition to everything else it is doing. Be kind to it and keep an eye on the image size when building. If you have too many addons, you might need to choose.
2. It is also asking a lot to use Bluetooth at the same time as WiFi motion detection as they use the same airspace. The `addon_espectre_and_bluetooth` combination makes some necessary compromises.
3. The addon makes use of the display item normally reserved for RELAY 2. If _you are also using the second relay_, expect the unexpected 😃

## Installation

You will need to add the reference to `addon_espectre`, or `addon_espectre_and_bluetooth` files on your ESPHome settings in the `package` section after the `remote_package` (base code), as shown below (for `espectre` in this example):

> [!NOTE]
> `addon_espectre_and_bluetooth` includes `addon_espectre` and `addon_bluetooth_proxy`, so don't try to add them as well yourself.

```yaml
substitutions:
  # Settings - Editable values
  device_name: "YOUR_NSPANEL_NAME"
  friendly_name: "Your panel's friendly name"
  wifi_ssid: !secret wifi_ssid
  wifi_password: !secret wifi_password
  language: en      # Language code - see docs/localization.md for all supported codes

  # Add-on configuration (if needed)
  ## force active scan at your own risk
  upload_tft_automatically: true

##### My customization - Start #####
##### My customization - End #####

# Basic and optional configurations
packages:
  remote_package:
    url: https://github.com/edwardtfn/NSPanel-Easy
    ref: latest
    refresh: 300s
    files:
      - nspanel_esphome.yaml # Basic package
      # Optional advanced and add-on configurations
      # pick no more than one of these
      - esphome/nspanel_esphome_addon_espectre_and_bluetooth.yaml  # both
      # - esphome/nspanel_esphome_addon_espectre.yaml  # just ESPectre
      # - esphome/nspanel_esphome_addon_bluetooth_proxy.yaml  # just Bluetooth

```

## Configuration

The following keys are available to be used in your `substitutions`:

<!-- markdownlint-disable MD013 MD033 -->
| Key | Required | Supported values | Default | Description |
| :- | :-: | :-: | :-: | :- |
| cooler_relay | Mandatory for *cool* and *dual* | `1` or `2` | `0` (disabled) | Relay used to control the cooler. Use `1` for "Relay 1" or `2` for "Relay 2". |

<!-- markdownlint-enable MD013 MD033 -->

- All values must be delimited with `""`

