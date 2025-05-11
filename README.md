### 1. Tytuł modelu
Model instalacji alarmowej 

### 2. Dane studenta
Monika Halek

E-mail: mhalek@student.agh.edu.pl
### 3. Opis modelowanego systemu
Instalacja alarmowa to system, którego zadaniem jest wykrywanie zagrożeń w budynku, takich jak: nieautoryzowany ruch, otwarcie drzwi lub pojawienie się dymu, oraz reagowanie na te zdarzenia poprzez aktywację alarmu dźwiękowego i wysyłanie powiadomień do użytkownika.

**Funkcjonalności systemu:**
- Wykrywanie ruchu
- Wykrywanie otwarcia drzwi
- Wykrywanie obecności dymu
- Analiza danych i decyzja o uruchomieniu alarmu
- Aktywacja syreny alarmowej
- Wysyłanie powiadomień do użytkownika
- Obsługa panelu sterowania
- Ciągłe monitorowanie stanu czujników

### 4. Komponenty
#### Data
- **MotionDetected** - informacja, czy wykryto ruch
- **DoorOpened** - informacja, czy otwarto drzwi
- **SmokeDetected**- informacja, czy wykryto dym
- **ControlSignal** - sygnał z panelu sterowania
- **AlarmDecision** - decyzja o aktywacji alarmu
- **NotificationSignal** - dane o powiadomieniu
#### Device
- **MotionSensor** - czujnik ruchu
- **DoorSensor** - czujnik drzwi
- **SmokeSensor** - czujnik dymu
- **Siren** - syrena alarmowa
- **NetworkInterface** - moduł komunikacji
- **ControlPanel** - panel sterowania
#### Processor
- CPU_Main - obsługuje SensorsUnit i AlarmUnit  
#### Memory
- RAM - pamięć systemowa używana przez kontroler do przechowywania danych.
#### Bus
- MainBus - magistrala komunikacyjna, przez którą przesyłane są dane między komponentami.
#### Thread
- **ReadMotionThread** - odczyt MotionSensor
- **CheckDoorThread** - odczyt DoorSensor
- **ReadSmokeThread** - odczyt SmokeSensor
- **EvaluateThreatThread** - analiza danych z SensorMonitorProc
- **HandleControlThread** - obsługa ControlPanel
- **SendNotificationThread** - przygotowanie i wysyłanie powiadomień
#### Process
- **SensorMonitorProc** - zbiera dane z czujników, przesyła statusy do AlarmUnit
- **AlarmProc** - analizuje dane z SensorsUnit i ControlPanel, decyduje o alarmie
- **NotificationProc** - generuje i wysyła powiadomienia przez NetworkInterface
#### System
- **AlarmSystem** 
