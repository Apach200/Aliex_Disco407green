# Aliex_Disco407green
EvolutionBoard STM32F4X-DISCOVERY from Aliexpress Green color.
CANOpen at STM32F407

Проект выполнен в среде STM32CubeIDE


Реализовано CAN-устройство на STM32F4X-DISCOVERY from Aliexpress Green color.
Сеть состоит из устройств из проектов Disco407_Blue, Aliex_Disco407green.



CAN-устройство на STM32F407 считывает запись с индексом 0x6047 из OD CAN-устройства 0_CAN_F103 посредством SDO.
1. Чтение с удалённого узла записи 0x6047.
2. Новое значение в  0x6047.
3. Чтение с удалённого узла записи 0x6047.

До инициализации CANOpen есть участок кода для физической проверки классического CAN-интерфейса. 
До начала передачи сообщений вводится задержка 1500ms для начала работы CAN на обоих устройствах.
Код отключен при помощи #if 0.

OD отредактирован с помощью EDSEditorGUI
Для просмотра открыть DS301_profile.xpd
Перетащить из проводника файл DS301_profile.xdd (CANopen XML Device Description File )
Так как файлы OD.h и OD.c не редактируются, а перезаписываются, то для контроля версий их следует добавлять в репозиторий при каждом commit.

Каждые 750ms инкрементруется запись OD_PERSIST_COMM.x6000_nucleo_VAR32_6000.
Каждые 750ms инкрементруется член массива  OD_PERSIST_COMM.x6038_nucleo_VAR32_6038.

Поочерёдно 4 TPDO принудительно передаются на шину CAN.
Значение дублируется в терминал через TerminalInterface.
