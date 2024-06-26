# ESP32-COMMUNICATION_MODULE
Устройство на базе модуля ESP32-S3, будучи по одному из UART подключеным к другому устройству (далее Slave), является "прозрачным" переходником для связи между внешним устройствов (далее Мастер) и Slave. Мастер может читать данные из Slave и записывать в него данные с помощью команд в формате Modbus RTU, которые он передаёт на ESP32 по интерфейсам: UART, WIFi, BT.
  
ESP32 при получении данных от Мастера, анализирует их на предмет выполнения особых условий (например, требуется ли ждать ответа от Slave, или "очистка" команд от заголовков TCP/IP) и ретранслирует полученные данные на Slave, после чего ждёт ответа от Slave. Получив ответа от Slave, отпраляет его Мастеру.

Надо понимать:
1) что при работе через UART, BT соединение устанавливается "P2P" (точка-точка), т.е. один Мастер, один Slave.
2) При работе по WIFI, Мастеров может быть несколько и кадждый со своими запросами

При необходимости, Приложение на ESP32 должно содержать собственные настройки и возможность их посматривать и редактировать
