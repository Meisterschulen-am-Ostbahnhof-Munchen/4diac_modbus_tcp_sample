# 4diac_modbus_tcp_sample

Dieses Beispiel zeigt die Ansteuerung eines **akYtec MK210-301/311** Digital I/O Moduls über Modbus TCP mit Eclipse 4diac.

## Hardware-Details (akYtec MK210-301/311)
Das Modul verfügt über 6 digitale Eingänge und 8 Relais-Ausgänge. Die Standard-IP ist `192.168.1.99`, die Modbus-Unit-ID (Slave ID) ist `1`.

## Modbus Konfiguration
Die Modbus-Parameter sind in der Datei `modbus_const.gcf` als globale Konstanten definiert. Der Zugriff erfolgt über Gruppen-Register, was effizienter ist als das Lesen einzelner Bits.

### Verbindungs-Strings erklärt
Die Syntax in 4diac FORTE folgt dem Schema:
`modbus[protocol:ip:port:slaveId:pollFrequency:readAddresses:sendAddresses]`

#### 1. ID_01_TCP (Ausgänge steuern & lesen)
`modbus[tcp:192.168.1.99:502:1:500:h468:h470]`
* **h468 (0x01D4)**: `Output bitmask`. Liest den aktuellen physikalischen Status der 8 Relais-Ausgänge (Feedback).
* **h470 (0x01D6)**: `New output bitmask`. Schreibt die Bitmaske für die Ansteuerung der Ausgänge DO1 bis DO8.

#### 2. ID_02_TCP (Eingänge lesen)
`modbus[tcp:192.168.1.99:502:1:500:h51:]`
* **h51 (0x0033)**: `Input bitmask`. Liest den Status der 6 digitalen Eingänge (DI1 bis DI6) gesammelt in einem Register.

## Weiterführende Links
* Gateway RTU to TCP: [4diac_modbus_rtu_tcp_sample](https://github.com/franz-ms-muc/4diac_modbus_rtu_tcp_sample)
* Pure RTU Sample: [4diac_modbus_rtu_sample](https://github.com/Meisterschulen-am-Ostbahnhof-Munchen/4diac_modbus_rtu_sample)

![image](https://github.com/user-attachments/assets/1c56c030-2ad8-4f50-9d4b-dc929eb3726d)

![image](https://github.com/user-attachments/assets/5d4c0c65-dc57-40e3-92b5-5b06ca9a6f0c)

