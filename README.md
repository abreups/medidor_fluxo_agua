# medidor_fluxo_agua
Medidor de fluxo de água usando ESPHome

## Lista de materiais

- Weemos D1 mini v3 (https://pt.aliexpress.com/item/32831353752.html?spm=a2g0o.order_list.order_list_main.58.66c0caa4Gt99Q5&gatewayAdapt=glo2bra)
- medidor de fluxo de água com sensor de temperatura (https://pt.aliexpress.com/item/1005001982191762.html?spm=a2g0o.order_list.order_list_main.41.66c0caa4Gt99Q5&gatewayAdapt=glo2bra)
- fonte 5V 1A
- cabo usb - micro USB


A leitura da informação enviada pelo sensor é feita usando-se um pulse_counter no ESPHome. [1]

sensor:
  - platform: pulse_counter
    pin: GPIO5
    name: "Pulse Counter"
    update_interval: 5s
    filters:
    - lambda: return (x / 27.0) * 60.0;
    unit_of_measurement: "L/hr"  



## Referências:

[1] https://community.home-assistant.io/t/using-esphome-to-build-a-water-flow-rate-meter/119380/4

