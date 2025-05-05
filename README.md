## Tytuł modelu
Model instalacji alarmowej 

### Dane studenta
Monika Halek

E-mail: mhalek@student.agh.edu.pl
### Opis modelowanego systemu
Model przedstawia architekturę instalacji alarmowej zaprojektowanej w języku AADL. System składa się z czujników (ruchu i drzwi), kontrolera przetwarzającego sygnały z sensorów, modułu alarmowego z syreną oraz komponentów sprzętowych, 
takich jak procesor, pamięć i magistrala danych. 

### Opis ogólny
System alarmowy został podzielony na trzy główne jednostki:
- SensorsUnit – zbiera dane o otoczeniu (czy wykryto ruch, czy otwarto drzwi).
- Controller – analizuje dane z sensorów i podejmuje decyzję, czy włączyć alarm.
- AlarmUnit – syrena aktywująca się, gdy kontroler wykryje zagrożenie.

Komunikacja między komponentami odbywa się przez porty danych i połączenia, przy użyciu wspólnej magistrali (MainBus). Wątkami w procesie kontrolera zarządza procesor, a dane są przetwarzane w pamięci RAM. 

### Opis dla użytkownika
Czujniki systemu ciągle monitorują otoczenie. Gdy wykryją ruch lub otwarcie drzwi, dane trafiają do jednostki kontrolnej, która podejmuje decyzję o aktywacji alarmu. Jeśli wykryte zostanie zagrożenie, włącza się syrena alarmowa. 
Użytkownik nie musi ręcznie sterować systemem.

### Komponenty
#### Data
- MotionDetected
- DoorOpened
- AlarmSignal
#### Device
- MotionSensor
- DoorSensor
- Siren
#### Processor
- CPU
#### Memory
- RAM
#### Bus
- MainBus
#### Thread
- ReadMotionThread
- CheckDoorThread
- TriggerAlarmThread
#### Process
- MonitorProc
#### System
- SensorsUnit
- AlarmUnit
- AlarmSystem
