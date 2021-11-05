## Important notes about ESP8266
some important information for making initial setup of esp8266

### Notes

CHIP_ENABLE (EN) / CHIP_POWERDOWN (CH_PD)
HIGH - chip works properly
LOW -> off, small current consumed

GPIO2, GPIO0, and MTDO are used to select booting mode and the SDIO mode;

U0TXD should not be pulled externally to a low logic level during the powering-up.

![observations](https://raw.githubusercontent.com/ViniciusGambi/esp8266-important-notes/main/esp.png)

**About power modes**

The low-power architecture operates in the following modes:
- Active mode: The chip radio is powered on. The chip can receive, transmit, or listen.
- Modem-sleep mode: The CPU is operational. The Wi-Fi and radio are disabled.
- Light-sleep mode: The CPU and all peripherals are paused. Any wake-up events
(MAC, host, RTC timer, or external interrupts) will wake up the chip.
- Deep-sleep mode: Only the RTC is operational and all other part of the chip are
powered off.

### Practical rules

- GPIO0 should be LOW on boot to UART programing
- GPIO2 should be always HIGH on boot
- if RESET goes LOW it reboots
- GPIO15 should be  LOW
