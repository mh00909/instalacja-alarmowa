### 1. Tytuł modelu
Model instalacji alarmowej 

### 2. Dane studenta
Imię i nazwisko: Monika Halek

E-mail: mhalek@student.agh.edu.pl
### 3. Opis modelowanego systemu
Instalacja alarmowa to system przeznaczony do wykrywania zagrożeń w budynku, takich jak nieautoryzowany ruch, otwarcie drzwi, wykrycie dymu lub przegrzania. System reaguje na zdarzenia poprzez aktywację alarmu dźwiękowego i świetlnego oraz wysyłanie powiadomień do użytkownika. Dane z czujników są przetwarzane przez odpowiednie wątki, a decyzje podejmowane przez procesy przetwarzające.



**Funkcjonalności systemu:**
- Wykrywanie ruchu
- Wykrywanie otwarcia drzwi
- Wykrywanie obecności dymu
- Wykrywanie podwyższonej temperatury
- Obsługa panelu sterowania
- Monitorowanie i przetwarzanie sygnałów z czujników
- Analiza danych i podejmowanie decyzji o uruchomieniu alarmu
- Aktywacja syreny alarmowej
- Aktywacja alarmu świetlnego
- Wysyłanie powiadomień do użytkownika

### 4. Komponenty
#### Data
- **MotionDetected** - informacja o wykryciu ruchu
- **DoorOpened** - informacja o otwarciu drzwi
- **SmokeDetected**- informacja o wykryciu dymu
- **OverheatDetected** - informacja o wykryciu przegrzania
- **ControlSignal** - sygnał z panelu sterowania
- **AlarmDecision** - decyzja o aktywacji alarmu
- **NotificationSignal** - dane powiadomienia wysyłane do użytkownika
- **LightAlarmSignal** – sygnał do aktywacji alarmu świetlnego
#### Device
- **MotionSensor** - czujnik ruchu
- **DoorSensor** - czujnik drzwi
- **SmokeSensor** - czujnik dymu
- **TemperatureSensor** – czujnik przegrzania
- **Siren** - syrena alarmowa
- **LightAlarm** – alarm świetlny (migająca lampa)
- **NetworkInterface** - moduł odpowiedzialny za wysyłanie powiadomień
- **ControlPanel** - panel sterowania
#### Processor
- CPU_Main - główny procesor systemu
#### Memory
- RAM - pamięć wykorzystywana przez procesy
#### Bus
- MainBus - główna magistrala komunikacyjna łącząca komponenty systemu
#### Thread
- **ReadMotionThread** - wątek przetwarzający dane z MotionSensor
- **CheckDoorThread** - wątek przetwarzający dane z DoorSensor
- **ReadSmokeThread** - wątek przetwarzający dane z SmokeSensor
- **ReadTemperatureThread** – wątek przetwarzający dane z TemperatureSensor
- **EvaluateThreatThread** - wątek analizujący dane z czujników i panelu sterowania, generujący decyzję alarmową, powiadomienie i sygnał świetlny
- **SendNotificationThread** - wątek przekazujący dane powiadomień do modułu komunikacyjnego
- **ActivateOutputsThread** - aktywacja syreny i alarmu świetlnego po wykryciu zagrożenia
#### Process
- **SensorMonitorProc** - proces odpowiedzialny za odbiór i przekazywanie danych z czujników
- **AlarmProc** - proces decyzyjny analizujący dane i sterujący alarmem
- **NotificationProc** - proces odpowiedzialny za przekazanie powiadomień do użytkownika
#### System
- **AlarmSystem** - główny system integrujący wszystkie komponenty

### 5. Architektura
![diagram1](https://github.com/user-attachments/assets/e9ed4e07-cdda-408e-861c-8368f8387717)

