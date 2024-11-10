# Подготовка окружения

## Установка образа ОС на микрокомпьютер

Для установки образа ОС (например DragonOS) на микрокомпьютер (например Raspberry Pi) необходимо
1. скачать образ с расширением .img со страницы разработчика ОС;
2. вставить SD-карту в ПК с установленной ОС семейства Linux;
3. командой `sudo lsblk -l` или `sudo fdisk -l` найти устройство SD-карты (одно из устройств `/dev/sdX`);
4. записать образ на SD-карты командой `sudo dd bs=4M conv=fsync status=progress if=<image_path> of=<device_name>`, где `<image_path>` — путь к образу ОС с расширением .img, `<device_name>` — устройство SD-карты вида `/dev/sdX`.

### Пример

Пусть требуется записать образ **DragonOS_Pi64_Beta37.img** на устройство `/dev/sdv`, тогда, полагая, что пользователь находится в той же директории, где расположен образ, необходимо ввести следующую команду.
```
sudo dd bs=4M conv=fsync status=progress if=DragonOS_Pi64_Beta37.img of=/dev/sdb
```


## Обновление ПО LimeSDR

Для обновления ПО LimeSDR необходимо
1. подключить LimeSDR к разьёму USB3.0 ПК;
2. проверить, что LimeSDR обнаруживается, выполнив команду `LimeUtil --find`, результат успешного выполнения которой имеет вид
```
  * [LimeSDR-USB, media=USB 3.0, module=FX3, addr=1d50:6108, serial=0009083401893821]
```
или пустую строку, если устройство не обнаружено;
3. обновить ПО LimeSDR, выполнив команду `LimeUtil --update`, результат успешного выполнения которой имеет вид
```
...
Connected to [LimeSDR-USB [USB 3.0] 9083401893821]
Existing firmware is same as update (4)
Existing gateware is same as update (2.23)
Firmware and Gateware update is not required.
```
