# SHARC Firmwares

## Update Instructions

### OTA

[SHARC Over-The-Air Updates Diagram](./sharc_ota_diagram.pdf)

#### App Update Instructions

1. Connect your SHARC to an MQTT broker.
2. Identify your SHARC's serial number (eg. `48e7290b118c`).
3. Connect to your SHARC using MQTT on the [Sharc Studio App](https://apps.apple.com/us/app/sharc-studio/id6447310295)
4. Go the Settings Tab
5. Click on the `Upload Firmware` Button Located Near the Bottom
6. Paste Your New Firmware .bin Link into the Text Box
7. Click `Upload`
8. Wait and Watch Your SHARC Device's LEDs to Ensure the Upgrade Finished Successfully - [LED Status During Upgrade Process](https://github.com/SharcTech/sharc-support/blob/main/firmware/readme.md#led-status-during-upgrade-process)

#### [Sharc Tech](https://sharc.tech) Update Instructions

1. Connect your SHARC to an MQTT broker.
2. Identify your SHARC's serial number (eg. `48e7290b118c`).
3. Connect to your SHARC using MQTT on [Sharc Tech](https://sharc.tech)
4. Click the `Upload` Icon Located to the Right of the `Power` Icon 
6. Paste Your New Firmware .bin Link into the Text Box
7. Click `Update`
8. Wait and Watch Your SHARC Device's LEDs to Ensure the Upgrade Finished Successfully - [LED Status During Upgrade Process](https://github.com/SharcTech/sharc-support/blob/main/firmware/readme.md#led-status-during-upgrade-process)

#### Manual Update Instructions

1. Connect your SHARC to an MQTT broker.
2. Identify your SHARC's serial number (eg. `48e7290b118c`).
3. Set your MQTT publish topic to `sharc/{your-sharc-serial-number}/cmd/action` (eg. `sharc/48e7290b118c/cmd/action`).
4. Publish the following message with the appropriate firmware link.  Your SHARC must be able to access the URI without HTTP redirects.

```
{
  "id": "abc123",
  "v": {
    "device.ota": {
      "bin": "https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/{new-firmware-filename.bin}"
    }
  }
}
```

5. Your SHARC will reboot and begin the update process.
6. After a successful update, your SHARC will boot into its first boot protocol and then reboot into production mode.  

#### LED Status During Upgrade Process

Observe your SHARC's LED to determine the success or failure of the OTA update.

| Stage | LED Color | Description | Success Result | Failure Result |
| ---   | ---       | --- | --- | --- |
| 1     | Magenta   | Initialize hardware and read the OTA instructions. | LED turns white. | LED turns red and reboots. |
| 2     | White     | Compose software services. | LED turns cyan. | LED turns red and reboots. |
| 3     | Cyan      | Establish network connection. | LED turns blue. | LED turns red and reboots. |
| 4     | Blue      | Retrieve firmware binary and write to filesystem. | LED turns green and reboots. | LED turns red and reboots. 

## Firmware List

| id | date-time | board version | is OTA | is RTM | comments |
| --- | --- | --- | --- | --- | --- |
| [2b26eb2](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/2b26eb2_ota.bin) | 11/26/2024 00:00 | 106 | yes | no | MQTT SSL bug fix. |
| [cee1788](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/cee1788_ota.bin) | 11/23/2024 00:00 | 105 | yes | no | MQTT SSL bug fix. |
| [1ab1096](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/1ab1096_ota.bin) | 09/22/2024 00:00 | 105 | yes | no | I/O time delta higher resolution. |
| [763fe04](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/763fe04_ota.bin) | 09/22/2024 00:00 | 105 | yes | no | File logger. |
| [9478ff9](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/9478ff9_ota.bin) | 08/20/2024 00:00 | 105 | yes | no | MQTT SSL support. |
| [4469b72](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/4469b72_ota.bin) | 06/28/2024 00:00 | 105 | yes | no | I/O time delta reporting. |
| [8474e08](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/8474e08_ota.bin) | 04/08/2024 00:00 | 105 | yes | no | TCP socket improvements. |
| [2253329](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/2253329_ota.bin) | 02/29/2024 15:00 | 105 | yes | no | WLAN improvements. |
| [cb6c2a3](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/cb6c2a3_ota.bin) | 02/13/2024 22:00 | 105 | yes | no | Secure SHARC adoption bugfix. |
| [a488b9c](https://raw.githubusercontent.com/SharcTech/sharc-support/main/firmware/a488b9c_ota.bin) | 01/31/2024 09:00 | 105 | yes | no | Secure SHARC adoption. |


