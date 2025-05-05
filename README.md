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
- MotionDetected – sygnał logiczny informujący, czy wykryto ruch.
- DoorOpened – sygnał logiczny wskazujący, czy drzwi zostały otwarte.
- AlarmSignal – sygnał logiczny aktywujący lub dezaktywujący alarm.
#### Device
- MotionSensor – czujnik ruchu, który generuje dane o wykrytym ruchu.
- DoorSensor – czujnik drzwi, który wykrywa otwarcie lub zamknięcie drzwi.
- Siren – urządzenie alarmowe, które emituje dźwięk ostrzegawczy.
#### Processor
- CPU_Controller - analiza danych i podejmowanie decyzji alarmowych
- CPU_Alarm	- zarządzanie sygnałami alarmowymi
#### Memory
- RAM - pamięć systemowa używana przez kontroler do przechowywania danych.
#### Bus
- MainBus - magistrala komunikacyjna, przez którą przesyłane są dane między komponentami.
#### Thread
- ReadMotionThread – wątek cykliczny odczytujący dane z czujnika ruchu.
- CheckDoorThread – wątek reagujący na zdarzenia związane z otwarciem drzwi.
- TriggerAlarmThread – wątek analizujący dane z czujników i decydujący o uruchomieniu alarmu.
#### Process
- SensorProc -	Przetwarza dane z czujników i przygotowuje je do przesłania do głównego kontrolera.
- MonitorProc	- Główna logika decyzji (czy włączyć alarm) na podstawie danych z SensorProc.
- AlarmProc	- Zarządza wszystkimi akcjami alarmowymi (syrena, światła, powiadomienia).
#### System
- SensorsUnit – jednostka zbierająca dane z czujników i przekazująca je do kontrolera.
- AlarmUnit – jednostka alarmowa odpowiedzialna za uruchomienie syreny.
- AlarmSystem – kompletny system alarmowy.
