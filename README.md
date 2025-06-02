### 1. Tytuł modelu
Model instalacji alarmowej 

### 2. Dane studenta
Imię i nazwisko: Monika Halek

E-mail: mhalek@student.agh.edu.pl

### 3. Opis modelowanego systemu
Instalacja alarmowa to system przeznaczony do wykrywania zagrożeń w budynku, takich jak nieautoryzowany ruch, otwarcie drzwi, wykrycie dymu lub przegrzania. System podejmuje decyzje w oparciu o dane z czujników oraz polecenia użytkownika. W odpowiedzi na zagrożenie aktywuje alarm dźwiękowy i świetlny, generuje powiadomienia sieciowe oraz zapisuje zdarzenia do logów.

Dane z czujników są odbierane przez dedykowane wątki przetwarzające, które działają w ramach procesu monitorującego. Logika alarmowa i podejmowanie decyzji realizowane są w osobnym procesie decyzyjnym. Obsługa użytkownika (komendy i status) oraz wysyłanie powiadomień są realizowane przez osobne procesy. Komunikacja między komponentami odbywa się poprzez dedykowane magistrale.



**Funkcjonalności systemu:**
- Wykrywanie ruchu
- Wykrywanie otwarcia drzwi
- Wykrywanie obecności dymu
- Wykrywanie podwyższonej temperatury
- Obsługa komend użytkownika (np. uzbrajanie/rozbrajanie systemu)
- Monitorowanie i przetwarzanie sygnałów z czujników
- Analiza danych i podejmowanie decyzji o uruchomieniu alarmu
- Aktywacja syreny alarmowej
- Aktywacja alarmu świetlnego
- Wysyłanie powiadomień do użytkownika
- Wyświetlanie statusu systemu
- Zapis zdarzeń do pamięci logów
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
- **SystemStatusData** – status systemu (np. „armed”, „disarmed”)
- **UserCommandData** – komendy użytkownika (np. „arm”, „disarm”)
- **LogData** – dane do zapisu w logach
#### Device
- **MotionSensor** - czujnik ruchu
- **DoorSensor** - czujnik drzwi
- **SmokeSensor** - czujnik dymu
- **TemperatureSensor** – czujnik przegrzania
- **Siren** - syrena alarmowa
- **LightAlarm** – alarm świetlny (migająca lampa)
- **NetworkInterface** - moduł odpowiedzialny za wysyłanie powiadomień
- **ControlPanel** - fizyczny panel sterowania
- **UserInterfacePanel** – interfejs użytkownika (do wprowadzania komend i wyświetlania statusu)
#### Processor
- **CPU_Main** – główny procesor odpowiedzialny za przetwarzanie danych, decyzje i logikę alarmu
- **CPU_UI** – procesor obsługujący interfejs użytkownika
#### Memory
- **RAM** – pamięć robocza dla głównych procesów
- **LogMemory** – pamięć dedykowana do przechowywania logów
#### Bus
- **MainBus** – magistrala główna do komunikacji między CPU a RAM i logami
- **I2CBus** – magistrala do komunikacji z czujnikami (ruchu, drzwi, dymu, temperatury)
- **SPIBus** – magistrala dla panelu sterowania, syreny, alarmu świetlnego i komunikacji sieciowej
- **UIBus** – magistrala dla interfejsu użytkownika
#### Thread
- **ReadMotionThread** - wątek przetwarzający dane z MotionSensor
- **CheckDoorThread** - wątek przetwarzający dane z DoorSensor
- **ReadSmokeThread** - wątek przetwarzający dane z SmokeSensor
- **ReadTemperatureThread** – wątek przetwarzający dane z TemperatureSensor
- **EvaluateThreatThread** - wątek analizujący dane z czujników i panelu sterowania, generujący decyzję alarmową, powiadomienie i sygnał świetlny
- **SendNotificationThread** - wątek przekazujący dane powiadomień do modułu komunikacyjnego
- **ReadUserCommandThread** – odczytuje komendy użytkownika
- **DisplaySystemStatusThread** – wyświetla status systemu
- **LogWriterThread** – zapisuje dane do logów
#### Process
- **SensorMonitorProc** - odbiera i przetwarza dane z czujników
- **AlarmProc** - logika decyzyjna (zawiera `EvaluateThreatThread`)
- **NotificationProc** - obsługuje wysyłanie powiadomień (`SendNotificationThread`)
- **UserInterfaceProc** – przetwarza komendy użytkownika i wyświetla status (`ReadUserCommandThread`, `DisplaySystemStatusThread`)
- **LogProc** – zapisuje zdarzenia do logów (`LogWriterThread`)
#### System
- **AlarmSystem** - główny system integrujący wszystkie komponenty

### 5. Diagram modelu
![diagram1](https://github.com/user-attachments/assets/0e6979fe-43d5-42a8-b534-3b0208f99e79)

### 6. Przeprowadzone analizy

### 7. Bibliografia

- https://insights.sei.cmu.edu/documents/788/2007_005_001_14891.pdf
- https://www.dipolnet.com/basic_information_on_intruder_alarm_systems_bib770.htm
- https://www.rapidalarms.com.au/alarm-system-components/
- https://reolink.com/blog/security-system-components/?srsltid=AfmBOoqDGheuvTGJQnjT0yzs-q5OulM6rrEHBxF4OdmJAeSBi3YUjKun

