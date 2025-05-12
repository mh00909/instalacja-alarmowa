### 1. Tytuł modelu
Model instalacji alarmowej 

### 2. Dane studenta
Monika Halek

E-mail: mhalek@student.agh.edu.pl
### 3. Opis modelowanego systemu
Instalacja alarmowa to system, którego zadaniem jest wykrywanie zagrożeń w budynku, takich jak: nieautoryzowany ruch, otwarcie drzwi, podwyższona temperatura lub pojawienie się dymu, oraz reagowanie na te zdarzenia poprzez aktywację alarmu dźwiękowego i świetlnego oraz wysyłanie powiadomień do użytkownika.

**Funkcjonalności systemu:**
- Wykrywanie ruchu
- Wykrywanie otwarcia drzwi
- Wykrywanie obecności dymu
- Wykrywanie podwyższonej temperatury
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
- **OverheatDetected** - informacja, czy wykryto przegrzanie
- **ControlSignal** - sygnał z panelu sterowania
- **AlarmDecision** - decyzja o aktywacji alarmu
- **NotificationSignal** - dane o powiadomieniu
- **LightAlarmSignal** – sygnał do aktywacji alarmu świetlnego
#### Device
- **MotionSensor** - czujnik ruchu
- **DoorSensor** - czujnik drzwi
- **SmokeSensor** - czujnik dymu
- **TemperatureSensor** – czujnik przegrzania
- **Siren** - syrena alarmowa
- **LightAlarm** – alarm świetlny (migająca lampa)
- **NetworkInterface** - moduł komunikacji
- **ControlPanel** - panel sterowania
#### Processor
- CPU_Main 
#### Memory
- RAM - pamięć systemowa używana przez kontroler do przechowywania danych.
#### Bus
- MainBus - magistrala komunikacyjna, przez którą przesyłane są dane.
#### Thread
- **ReadMotionThread** - odczyt MotionSensor
- **CheckDoorThread** - odczyt DoorSensor
- **ReadSmokeThread** - odczyt SmokeSensor
- **ReadTemperatureThread** – odczyt TemperatureSensor
- **EvaluateThreatThread** - analiza danych z SensorMonitorProc
- **HandleControlThread** - obsługa ControlPanel
- **SendNotificationThread** - przygotowanie i wysyłanie powiadomień
- **ActivateOutputsThread** - aktywacja syreny i alarmu świetlnego po wykryciu zagrożenia
#### Process
- **SensorMonitorProc** - zbiera dane z czujników
- **AlarmProc** - analizuje dane, decyduje o alarmie, aktywuje urządzenia wykonawcze
- **NotificationProc** - generuje i wysyła powiadomienia przez NetworkInterface
#### System
- **AlarmSystem** - cały system alarmowy
