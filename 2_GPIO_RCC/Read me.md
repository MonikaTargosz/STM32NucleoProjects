# STM MCU Finder

Aplikacja umożliwia eksplorację i łączenie się z pełnym portfolio mikrokontrolerów STM32 ARM Cortex-M i STM 8 oraz płyt programistycznych z dowolnego urządzenia mobilnego 
lub bezpośrednio ze środowiska programisty.

## Składowe opisu mikrokontrolera

- Rdzeń
- Seria mikrokontrolera
- Linie
- Wielkość obudowy
- Zaawansowane wybory
- Wybór peryferii

# ST Link Utility

Program pozwala programować mikrokontroler z pliku binarnego oraz ustawić jego bity konfiguracyjne pozwalające na zablokowanie pamięci przed odczytem lub zapisem. 
Program pozwala na wykasowanie pamięci i uruchomienie mikrokontrolera.

# STM32 Cube Programmer

Program umożliwia wybór interfejsu przez jaki chcemy się połączyć. Umożliwia wgranie pliku binarnego do mikrokontrolera oraz kasowanie pamięci zewnętrznej Flash.

## Zakładka CPU w option bytes

Umożliwia debugowanie.

## Zakładka SWV w option bytes

Umożliwia podgląd zmiennych.

# Biblioteka HAL

Aplikacja nie wnika w działanie sprzętu pod spodem, ponieważ jest to abstrakcyjna warstwa sprzętowa. 
Przykładowo używając I2C nie musimy wiedzieć jakie rejestry możemy używać i jak je skonfigurować.
Obsługa mikrokontrolerów jest jednolita: APP -> MIDW -> HAL -> HW.

Funkcje zaczynają się od przedrosta HAL_ .
Składowe nazwy funkcji to:
- peryferium np. GPIO,
- nazwa, co funkcja robi np. TogglePin i argumenty w ().

Funkcja __ IT() współpracuje z trybem przerwaniowym.
Funkcja __ DMA() współpracuje z trybem DMA.

Funkcje zaczynające się od __ HAL znajdują się w HAL'owym API. Są to definicje, które operują na operacjach atomowych, wykorzystujące najmniejszą rzecz 
np. zmiana flagi, zmiana bitu lub wyliczenie numeru portu.

# Zegary MCU

## Częstotliwość główna mikrokontrolara

Ustawia się ja w pliku .ioc w zakładce Clock Configuration

## Maksymalna częstotliwość główna mikrokontrolera

Jest to 100 MHz.

## Domyślna częstotliwość główna w Nucleo

Jest to 84 MHz.

## Dostępny wybór rezonatora

- PLLCLK z pętlą PLL z mnożnikami i dzielnikami
- HSE (High Speed External) - rezonator zewnętrzny
- HSI (High Speed Internal) - rezonator wewnętrzny

## APB2 są bezpośrednio podawane z mikrokontrolera na timery

## Konfiguracja LSE

Low Speed External - rezonator niskiej częstotliowści dla zegara RTC (czasu rzeczywistego)

## Konfiguracja LSI

Low Speed Internal - wewnętrzny rezonator niskiej częstotliwości, mniej dokładny, ale z dużą ilością feature.

# GPIO

General Purpose Input Output - porty wejścia wyjścia

## Konfiguracja wyjścia

Możemy ustawić stan wysoki lub niski.

## Konfiguracja wejścia

Czytamy z zewnątrz czy to stan wysoki czy niski.

## Tryb Push Pull

Stan wysoki i niski jest wymuszany przez mikrokontroler, tranzystory na wyjściu pinu (komplementarne). Otwarty tranzystor Vcc -> 1, GND -> 0.

## Tryb Open Drain

Należy zastosować rezystory podciągające. Na wyjściu powinien pojawić się rezystor podciągający do zasilana. Kiedy tranzystor jest zamknięty, "0" kiedy przeważa brak oporu.

## Działanie rezystora ściągającego

Działa tak samo jak podciągający, ale w drugą stronę do masy. Również może eliminować stany nieustalone.

## Połączenie rezystorów podciągających i ściągających (wbudowanych) w STM32 na wyjściu

Odbywa się poprzez odpowiednie bity. Wartości tych rezystorów są podane w dokumentacji.

## Pinout Configuration

Znajduje się w zakładce System Core -> GPIO. Klikając na dany pin wybieramy czym może on być.

## Parametry GPIO Output Configuration

- GPIO Output Level
- GPIO Mode: output Push-Pull
- GPIO Pull-up/Pull-down: no pull-up/pull-down (brak rezystorów)
- Maximum output speed: low - very high (szybkość narastania zbocza na pinie, UWAGA! very high dla wyświetlacza powoduje pływaniem napisów)
- User Label

# GPIO Input Configuration

## Wybór czytania pinu ręcznie

Polling

## Generowanie przerwania przez pin

## Większa ilość pinów

Jest potrzebna do portów równoległych np. wyświetlaczy.

## Parametry wejścia

- GPIO Mode (tryby przerwaniowe: external interrupt/ external mode)
- GPIO pull-up/pull-down
- User label

## GPIO w dokumentacji

Manual R.8 GPIO - schemat z rezystorami.
Datasheet str. 98 - wartość rezystorów pull-up i pull-down.

# Funkcja TogglePin()

Zmienia stan na pinie, który mu podamy. Nie przyjmuje wartości stanu jaki ma być. Po prostu zmienia aktualny stan na przeciwny.


# Callbacki

To funkcje, które wywołują się w trakcie przerwania, __Callback().



