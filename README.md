# Galaxy Projector LED Nebula Light

Watch the full video tutorial here: https://youtu.be/YwHWbcuztuY



ESPHome Code:
```yaml
esphome:
  name: ${name}
  platform: ESP8266
  board: d1_mini

## Edit these for either your Wi-Fi SSID & Password - Or your 'secrets' entries ##
wifi:
  ssid: !secret ssid 
  password: !secret wifi_password

## Change this for your light's name ##
substitutions:
  name: nebula_lounge

logger:
  logs:
    light: none
api:
ota:

light:
  - platform: rgb
    name: ${name} Light
    id: rgb_light
    red: red
    green: green
    blue: blue
    effects:
      - flicker:
          name: Flicker
          alpha: 95%
          intensity: 2.5%
      - random:
          name: Random
          transition_length: 2.5s
          update_interval: 3s
      - random:
          name: Random Slow
          transition_length: 10s
          update_interval: 5s

  - platform: monochromatic
    name: ${name} Laser
    id: laser
    output: laser_pwm
  - platform: monochromatic
    name: ${name} Motor
    id: motor
    output: motor_pwm

output:
  - platform: esp8266_pwm
    id: red
    pin: D1
  - platform: esp8266_pwm
    id: green
    pin: D5
  - platform: esp8266_pwm
    id: blue
    pin: D6

  - platform: esp8266_pwm
    id: laser_pwm
    pin: D7
    frequency: 2000 Hz
  - platform: esp8266_pwm
    id: motor_pwm
    frequency: 8 Hz
    pin: D8
```

🎁 Found this useful or want to say 'thanks' and support my efforts...

[![BMC](https://www.buymeacoffee.com/assets/img/custom_images/white_img.png)](https://www.buymeacoffee.com/3ative) **And leave a me a message to let me know.**  ❤

🍺 CHEERS! 👍

