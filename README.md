# medidor_fluxo_agua
Medidor de fluxo de água usando ESPHome

## Lista de materiais

- Weemos D1 mini v3 (https://pt.aliexpress.com/item/32831353752.html?spm=a2g0o.order_list.order_list_main.58.66c0caa4Gt99Q5&gatewayAdapt=glo2bra) [3]
- medidor de fluxo de água com sensor de temperatura (https://pt.aliexpress.com/item/1005001982191762.html?spm=a2g0o.order_list.order_list_main.41.66c0caa4Gt99Q5&gatewayAdapt=glo2bra)
- fonte 5V 1A
- cabo usb - micro USB


A leitura da informação enviada pelo sensor é feita usando-se um pulse_counter no ESPHome. [1] [2]
  
    sensor:
      - platform: pulse_counter
        # GPIO5 = D1
        pin: GPIO5
        name: "fluxo de agua"
        update_interval: 5s

No código acima criamos um `sensor` chamado "fluxo de água" que vai indicar
a quantidade de pulsos do sensor (ainda não convertidos para uma métrica
do tipo "litros por minuto").


    sensor:
      - platform: pulse_counter
        # GPIO5 = D1
        pin: GPIO5
        name: "fluxo de agua"
        update_interval: 5s
        filters:
        - lambda: return (x / 27.0) * 60.0;
        unit_of_measurement: "L/hr"


## Referências:

[1] https://community.home-assistant.io/t/using-esphome-to-build-a-water-flow-rate-meter/119380/4

[2] Pulse counter sensor: https://esphome.io/components/sensor/pulse_counter.html?highlight=pulse

[3] Pinagem do Wemos D1 mini: https://i2.wp.com/www.teachmemicro.com/wp-content/uploads/2019/07/wemos-d1-mini-pinout.jpg?ssl=1


