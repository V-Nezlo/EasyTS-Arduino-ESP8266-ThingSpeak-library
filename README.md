# EasyTS - Arduino + ESP8266  + ThingSpeak + NTP

Легкая и быстрая библиотека для работы с ThingSpeak и NTP сервером с помощью ESP8266. 

 [ThingSpeak](https://thingspeak.com/) - это облачная платформа интернета вещей (IoT), которая позволяет собирать, отображать и анализировать потоковые данные. Сервис поддерживает работу по протоколу MQTT, а так же через REST API. Данная библиотека работает через REST API.

Библиотека позволяет:
- подключать ESP8266 к WI-FI стандартно через SSID и пароль
- подключать ESP8266 к WI-FI с помощью WPS
- отправлять данные на ThingSpeak сервер
- получать данные с ThingSpeak сервера, парсить полученные данные
- конфигурировать NTP и запрашивать текущее время

Методы, используемые в библиотеке:
```sh
reset() - перезапуск модуля
```
```sh
wps_connect() - вызов функции инициализации подключения по WPS (параллельно нажимается кнопка WPS на роутере)
```
```sh
std_connect(String ssid, String pass) - запрос на подключение по SSID и паролю (ssid это ssid. pass это пароль)
```
```sh
sntp_config(int state, int timezone) - конфигурирование ntp (state - 1 это активировать, 0 - выключить, timezone - часовой пояс)
```
```sh
sntp_get() - получить текущее время (возвращает в виде Mon Nov 30 16:02:15 2020 )
```
```sh
send(String api_w, int field, String data) - отправить данные на TS поле и канал (api_w это API WRITE, field - поле, data - строка с записываемым значением)
```
```sh
request(String api_r, int field, String channel) - запросить данные с TS (возвращает одно число, и возвращает 9 в случае ошибки)(api_r - API READ, field - нужное поле, channel - id канала)
```

Функции связанные с ThingSpeak находятся на этапе доработки функционала.

ВНИМАНИЕ! Библиотека использует Hardware Serial! Монитор порта и загрузка прошивки через бутлоадер будет недоступна при подключенном ESP!
Для отладки кода используйте отдельный USB-TTL конвертер и подключите его к RX порту Ардуино

Используемая версия прошивки ESP8266:
AT version:1.7.4.0(May 11 2020 19:13:04)
SDK version:3.0.4(9532ceb)
compile time:May 27 2020 10:12:22
Bin version(Wroom 02):1.7.4
