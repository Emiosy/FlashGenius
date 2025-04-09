# Dokument wymagań produktu (PRD) - FlashGenius

## 1. Przegląd produktu

FlashGenius to aplikacja webowa wspierająca efektywną naukę poprzez automatyczne generowanie fiszek edukacyjnych przy użyciu sztucznej inteligencji. Produkt rozwiązuje problem czasochłonnego procesu tworzenia wysokiej jakości fiszek, umożliwiając użytkownikom szybkie generowanie materiałów do nauki metodą powtórek rozłożonych w czasie (spaced repetition).

Główne funkcjonalności aplikacji to:
- Generowanie fiszek przez AI na podstawie wprowadzonego tekstu
- Możliwość manualnego tworzenia fiszek
- Zarządzanie fiszkami (przeglądanie, edycja, usuwanie)
- System kont użytkowników
- Integracja z gotowym algorytmem powtórek (SM-2)

Aplikacja zostanie zbudowana jako Single Page Application (SPA) w technologii React z backendem opartym na PHP i bazie danych PostgreSQL, wdrożona przy użyciu kontenerów Docker na platformie DigitalOcean.

## 2. Problem użytkownika

Manualne tworzenie wysokiej jakości fiszek edukacyjnych jest procesem czasochłonnym, co zniechęca wielu uczących się do korzystania z efektywnej metody nauki jaką jest spaced repetition. Użytkownicy potrzebują narzędzia, które:

- Przyspieszy proces tworzenia fiszek
- Zapewni wysoką jakość generowanych materiałów edukacyjnych
- Będzie łatwe w obsłudze
- Umożliwi efektywne zarządzanie stworzonymi materiałami
- Zintegruje proces tworzenia fiszek z systemem powtórek

Użytkownicy tracą znaczną ilość czasu na manualne przygotowanie fiszek, co często prowadzi do rezygnacji z tej metody nauki pomimo jej udowodnionej skuteczności. FlashGenius automatyzuje ten proces, zachowując wysoką jakość materiałów edukacyjnych.

## 3. Wymagania funkcjonalne

### 3.1 Generowanie fiszek przez AI
- Użytkownik może wprowadzić tekst (kopiuj-wklej) do systemu od 1000 do 10000 znaków
- Użytkownik może również poprosić AI o samodzielne wygenerowanie fiszek na dany temat bez wprowadzania tekstu źródłowego
- System analizuje tekst i generuje zestaw fiszek przy użyciu AI
- Generowane fiszki zawierają informację o źródle pochodzenia
- System prezentuje fiszki do akceptacji przez użytkownika (zaakceptuj/odrzuć)
- Fiszki zaakceptowane są zapisywane w bazie danych użytkownika

### 3.2 Manualne tworzenie fiszek
- Użytkownik może ręcznie tworzyć własne fiszki
- System umożliwia wprowadzenie przód (pytanie) i tyłu (odpowiedź) fiszki
- Przód fiszki ograniczony jest do 200 znaków
- Tył fiszki ograniczony jest do 500 znaków
- System przeprowadza walidację wprowadzanych danych
- System wykrywa potencjalne duplikaty fiszek

### 3.3 Zarządzanie fiszkami
- Użytkownik może przeglądać wszystkie swoje fiszki
- Użytkownik może edytować istniejące fiszki
- Użytkownik może usuwać fiszki
- System umożliwia filtrowanie fiszek według kategorii
- System wyróżnia fiszki utworzone manualnie od tych wygenerowanych przez AI

### 3.4 Zarządzanie kategoriami
- Użytkownik może tworzyć nowe kategorie
- Użytkownik może edytować istniejące kategorie
- Użytkownik może usuwać kategorie
- Fiszki mogą być przypisane do wielu kategorii
- Fiszki mogą również nie być przypisane do żadnej kategorii, ale wtedy nie biorą udziału w procesie powtórkowym, chyba ze uzytkownik chce by powtórka objęła wszystkie fiszki jakie ma zapisane przy swoim

### 3.5 System kont użytkowników
- Rejestracja nowych użytkowników
- Logowanie do systemu
- Wylogowywanie z systemu
- Zmiana hasła
- Rozróżnienie ról (użytkownik i administrator)
- Użytkownicy mają dostęp tylko do swoich danych
- Administratorzy mają dostęp do wszystkich danych w systemie

### 3.6 Integracja z algorytmem powtórek
- System integruje się z gotowym algorytmem SM-2
- Konfiguracja algorytmu odbywa się poprzez plik konfiguracyjny
- Użytkownik może korzystać z systemu powtórek dla swoich fiszek
- System śledzi postępy użytkownika w nauce

### 3.7 Infrastruktura i bezpieczeństwo
- System wykorzystuje hashowanie haseł
- Komunikacja odbywa się przez HTTPS
- Wdrożenie przy użyciu kontenerów Docker
- CI/CD realizowane przez GitHub Actions
- Podstawowy mechanizm logowania błędów

## 4. Granice produktu

MVP (Minimum Viable Product) nie będzie zawierał następujących funkcjonalności:

- Własny, zaawansowany algorytm powtórek (wykorzystamy gotowy algorytm SM-2)
- Import wielu formatów (PDF, DOCX, itp.) - na początek tylko zwykły tekst
- Współdzielenie zestawów fiszek między użytkownikami
- Integracje z innymi platformami edukacyjnymi
- Aplikacje mobilne (na początek tylko wersja webowa)
- Zaawansowane formaty fiszek (audio, wideo, kod) - tylko format tekstowy
- Personalizacja parametrów algorytmu SM-2 poza konfiguracją plikową
- Zaawansowany system logowania błędów i raportowania przez użytkowników

## 5. Historyjki użytkowników

### US-001: Rejestracja konta
**Opis:** Jako nowy użytkownik, chcę utworzyć konto w systemie, aby móc korzystać z funkcjonalności aplikacji.

**Kryteria akceptacji:**
- Użytkownik może wprowadzić dane rejestracyjne (e-mail, hasło, potwierdzenie hasła)
- System waliduje poprawność danych (format e-mail, złożoność hasła)
- System weryfikuje unikalność adresu e-mail
- Po udanej rejestracji użytkownik otrzymuje powiadomienie o sukcesie
- Po udanej rejestracji użytkownik jest automatycznie zalogowany do systemu

### US-002: Logowanie do aplikacji
**Opis:** Jako zarejestrowany użytkownik, chcę zalogować się do aplikacji, aby uzyskać dostęp do moich fiszek.

**Kryteria akceptacji:**
- Użytkownik może wprowadzić swoje dane logowania (e-mail, hasło)
- System waliduje poprawność danych logowania
- Po udanym logowaniu użytkownik jest przekierowany do głównego ekranu aplikacji
- W przypadku błędnych danych system wyświetla odpowiedni komunikat
- Dostępna jest opcja przypomnienia hasła

### US-003: Wylogowanie z aplikacji
**Opis:** Jako zalogowany użytkownik, chcę się wylogować z aplikacji, aby zabezpieczyć moje konto przed nieautoryzowanym dostępem.

**Kryteria akceptacji:**
- Użytkownik może kliknąć przycisk wylogowania
- Po wylogowaniu użytkownik jest przekierowany do ekranu logowania
- Po wylogowaniu poprzednia sesja jest zakończona i niedostępna

### US-004: Zmiana hasła
**Opis:** Jako zarejestrowany użytkownik, chcę zmienić moje hasło, aby zwiększyć bezpieczeństwo mojego konta.

**Kryteria akceptacji:**
- Użytkownik może przejść do ustawień konta
- Użytkownik musi podać aktualne hasło
- Użytkownik wprowadza nowe hasło i jego potwierdzenie
- System waliduje złożoność nowego hasła
- Po udanej zmianie system wyświetla potwierdzenie

### US-005: Generowanie fiszek przez AI
**Opis:** Jako zalogowany użytkownik, chcę wkleić tekst do systemu i wygenerować fiszki przy użyciu AI, aby zaoszczędzić czas na manualnym tworzeniu.

**Kryteria akceptacji:**
- Użytkownik może wprowadzić tekst w dedykowane pole
- System oferuje przycisk do generowania fiszek
- Po wygenerowaniu system prezentuje listę proponowanych fiszek
- Każda fiszka zawiera przód, tył oraz informację o źródle
- Użytkownik może zaakceptować lub odrzucić każdą fiszkę indywidualnie
- Zaakceptowane fiszki są zapisywane w bazie danych użytkownika

### US-006: Generowanie fiszek przez AI bez tekstu źródłowego
**Opis:** Jako zalogowany użytkownik, chcę by AI samodzielnie wygenerowało fiszki na wybrany temat bez konieczności wprowadzania tekstu źródłowego, wykorzystując swoją wiedzę i przeszukując dostępne źródła.

**Kryteria akceptacji:**
- Użytkownik może wprowadzić temat lub dziedzinę dla generowanych fiszek
- System oferuje przycisk do generowania fiszek bez tekstu źródłowego
- AI wykorzystuje swoją wiedzę do wygenerowania tematycznych fiszek
- Po wygenerowaniu system prezentuje listę proponowanych fiszek
- Każda fiszka zawiera przód, tył oraz informację, że została wygenerowana autonomicznie przez AI
- Użytkownik może zaakceptować lub odrzucić każdą fiszkę indywidualnie
- Zaakceptowane fiszki są zapisywane w bazie danych użytkownika

### US-007: Przeglądanie wygenerowanych fiszek przed zapisaniem
**Opis:** Jako użytkownik generujący fiszki przez AI, chcę przejrzeć wygenerowane fiszki przed ich zapisaniem, aby ocenić ich jakość i przydatność.

**Kryteria akceptacji:**
- System prezentuje listę wygenerowanych fiszek
- Dla każdej fiszki wyświetlany jest przód i tył
- Użytkownik może zapoznać się z treścią każdej fiszki
- Użytkownik może zaakceptować lub odrzucić każdą fiszkę
- System informuje o liczbie zaakceptowanych i odrzuconych fiszek

### US-008: Ręczne tworzenie fiszki
**Opis:** Jako zalogowany użytkownik, chcę ręcznie utworzyć fiszkę, aby dodać konkretną informację do mojego zestawu.

**Kryteria akceptacji:**
- Użytkownik może przejść do formularza tworzenia fiszki
- Użytkownik wprowadza treść przodu fiszki (max 200 znaków)
- Użytkownik wprowadza treść tyłu fiszki (max 500 znaków)
- System waliduje wprowadzone dane
- Po zapisaniu fiszka jest dodawana do bazy danych użytkownika
- System sprawdza i informuje o potencjalnych duplikatach

### US-009: Przeglądanie fiszek
**Opis:** Jako zalogowany użytkownik, chcę przeglądać moje fiszki, aby zapoznać się z ich treścią.

**Kryteria akceptacji:**
- Użytkownik widzi listę swoich fiszek
- Lista może być filtrowana według kategorii
- Użytkownik może zobaczyć zarówno przód jak i tył fiszki
- System wyróżnia fiszki utworzone manualnie od wygenerowanych przez AI
- Dostępna jest paginacja dla dużych zbiorów fiszek

### US-010: Edycja fiszki
**Opis:** Jako zalogowany użytkownik, chcę edytować istniejącą fiszkę, aby zaktualizować jej treść.

**Kryteria akceptacji:**
- Użytkownik może wybrać fiszkę do edycji
- System prezentuje formularz z aktualnymi danymi fiszki
- Użytkownik może zmienić przód i tył fiszki
- System waliduje wprowadzone zmiany (limity znaków)
- Po zapisaniu zmiany są aktualizowane w bazie danych

### US-011: Usuwanie fiszki
**Opis:** Jako zalogowany użytkownik, chcę usunąć niepotrzebne fiszki, aby utrzymać porządek w moim zestawie.

**Kryteria akceptacji:**
- Użytkownik może wybrać fiszkę do usunięcia
- System wyświetla prośbę o potwierdzenie operacji
- Po potwierdzeniu fiszka jest usuwana z bazy danych
- System wyświetla potwierdzenie udanego usunięcia

### US-012: Tworzenie kategorii
**Opis:** Jako zalogowany użytkownik, chcę utworzyć nową kategorię, aby lepiej organizować moje fiszki.

**Kryteria akceptacji:**
- Użytkownik może przejść do zarządzania kategoriami
- Użytkownik może wprowadzić nazwę nowej kategorii
- System waliduje unikalność nazwy kategorii
- Po zapisaniu nowa kategoria jest dostępna do użycia

### US-013: Edycja kategorii
**Opis:** Jako zalogowany użytkownik, chcę edytować istniejącą kategorię, aby zmienić jej nazwę.

**Kryteria akceptacji:**
- Użytkownik może wybrać kategorię do edycji
- System prezentuje formularz z aktualną nazwą kategorii
- Użytkownik może zmienić nazwę kategorii
- System waliduje unikalność nowej nazwy
- Po zapisaniu zmiany są aktualizowane w bazie danych

### US-014: Usuwanie kategorii
**Opis:** Jako zalogowany użytkownik, chcę usunąć niepotrzebną kategorię, aby utrzymać porządek w organizacji fiszek.

**Kryteria akceptacji:**
- Użytkownik może wybrać kategorię do usunięcia
- System wyświetla prośbę o potwierdzenie operacji
- System informuje o wpływie usunięcia na fiszki (nie będą usunięte, tylko odłączone od kategorii)
- Po potwierdzeniu kategoria jest usuwana z bazy danych

### US-015: Przypisywanie fiszek do kategorii
**Opis:** Jako zalogowany użytkownik, chcę przypisać fiszki do kategorii, aby lepiej organizować moje materiały.

**Kryteria akceptacji:**
- Użytkownik może wybrać fiszkę lub zestaw fiszek
- Użytkownik może wybrać jedną lub więcej kategorii do przypisania
- System zapisuje powiązania między fiszkami a kategoriami
- Użytkownik otrzymuje potwierdzenie udanej operacji

### US-016: Korzystanie z systemu powtórek
**Opis:** Jako zalogowany użytkownik, chcę korzystać z systemu powtórek, aby efektywnie się uczyć.

**Kryteria akceptacji:**
- Użytkownik może rozpocząć sesję powtórek
- System prezentuje fiszki według algorytmu SM-2
- Użytkownik może ocenić swoją znajomość materiału
- System zapisuje postępy użytkownika
- Kolejne powtórki są planowane zgodnie z algorytmem
- Na początku wyswietlany jest przód fiszki, poprzez interfakcje uzytkownik wyświetla jej tył.

### US-017: Filtrowanie fiszek podczas powtórek
**Opis:** Jako zalogowany użytkownik, chcę filtrować fiszki podczas sesji powtórek, aby skupić się na konkretnych kategoriach.

**Kryteria akceptacji:**
- Użytkownik może wybrać kategorie przed rozpoczęciem sesji
- System uwzględnia tylko fiszki z wybranych kategorii
- Algorytm powtórek działa poprawnie na wyfiltrowanym zestawie
- Użytkownik może zmienić filtry między sesjami

### US-018: Przeglądanie statystyk nauki
**Opis:** Jako zalogowany użytkownik, chcę przeglądać statystyki mojej nauki, aby śledzić moje postępy.

**Kryteria akceptacji:**
- Użytkownik może przejść do sekcji statystyk
- System prezentuje podstawowe statystyki (liczba fiszek, liczba sesji, etc.)
- System wyświetla informacje o postępie nauki dla poszczególnych kategorii
- Statystyki są aktualizowane na bieżąco

### US-019: Zarządzanie profilem administratora
**Opis:** Jako administrator, chcę mieć dostęp do panelu administracyjnego, aby zarządzać systemem.

**Kryteria akceptacji:**
- Administrator może zalogować się do dedykowanego panelu
- Administrator widzi statystyki systemu (liczba użytkowników, fiszek, etc.)
- Administrator ma dostęp do wszystkich danych w systemie
- Administrator może zarządzać kontami użytkowników

### US-020: Przeglądanie logów błędów
**Opis:** Jako administrator, chcę przeglądać logi błędów, aby monitorować i naprawiać problemy systemu.

**Kryteria akceptacji:**
- Administrator ma dostęp do logów błędów
- Logi zawierają istotne informacje (znacznik czasu, typ błędu, lokalizacja)
- Administrator może filtrować logi według różnych kryteriów
- System umożliwia eksport logów do analizy

### US-021: Wykrywanie duplikatów fiszek
**Opis:** Jako użytkownik, chcę aby system wykrywał potencjalne duplikaty podczas tworzenia fiszek, aby uniknąć redundancji.

**Kryteria akceptacji:**
- System porównuje nowo tworzone fiszki z istniejącymi
- W przypadku wykrycia podobieństwa system wyświetla ostrzeżenie
- Użytkownik może podjąć decyzję o kontynuowaniu lub modyfikacji
- Proces wykrywania duplikatów nie wpływa znacząco na wydajność systemu

## 6. Metryki sukcesu

### 6.1 Metryki adopcji
- Liczba zarejestrowanych użytkowników
- Liczba aktywnych użytkowników (dziennie/tygodniowo/miesięcznie)
- Średni czas spędzony w aplikacji
- Częstotliwość powracania do aplikacji

### 6.2 Metryki efektywności generowania
- 75% fiszek wygenerowanych przez AI jest akceptowanych przez użytkowników
- 75% wszystkich fiszek w systemie jest tworzonych przy pomocy AI
- Średni czas potrzebny na wygenerowanie zestawu fiszek
- Stosunek zaakceptowanych do odrzuconych fiszek

### 6.3 Metryki funkcjonalne
- Liczba fiszek tworzonych przez użytkownika (dziennie/tygodniowo)
- Liczba i częstotliwość sesji powtórek
- Średnia liczba kategorii per użytkownik
- Średnia liczba fiszek per kategoria

### 6.4 Metryki techniczne
- Czas odpowiedzi systemu na żądania użytkownika
- Liczba błędów systemu
- Dostępność systemu (uptime)
- Czas generowania fiszek przez AI

### 6.5 Monitorowanie i raportowanie
- System logowania podstawowych błędów
- Śledzenie operacji akceptacji/odrzucenia fiszek
- Gromadzenie anonimowych statystyk użytkowania
- Cykliczne generowanie raportów dla zespołu produktowego 