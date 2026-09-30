# Add-on: Bluetooth

## Description

This add-on enables your panel to provide Bluetooth Proxy and BLE Tracker services to 
Home Assistant, which is useful for connecting other devices and for tracking mobile
devices from room to room.

<!-- blockquote separator - to avoid markdown lint 028 error -->

## Installation

You will need to add the reference to the `addon_bluetooth_proxy` file in your ESPHome
settings in the `package` section and after the `remote_package` (base code),
as shown below:

```yaml
packages:
  remote_package:
    url: https://github.com/edwardtfn/NSPanel-Easy
    ref: latest
    refresh: 300s
    files:
      - nspanel_esphome.yaml # Basic package
      # Optional advanced and add-on configurations
      # - esphome/nspanel_esphome_addon_climate_cool.yaml
      # - esphome/nspanel_esphome_addon_climate_heat.yaml
      # - esphome/nspanel_esphome_addon_climate_dual.yaml
      - esphome/nspanel_esphome_addon_bluetooth_proxy.yaml
      # - esphome/nspanel_esphome_addon_cover.yaml
      # - esphome/nspanel_esphome_addon_display_light.yaml  # Show the display as a light in Home Assistant
```

### UI entities

The bluetooth device should appear in the Bluetooth section in Home Assistant
(**Settings** > **Devices & services** > **Bluetooth**)
