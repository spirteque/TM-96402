# 📱 Mobile Automation & Cloud-Ready Testing Suite

**Prowadzący:** mgr Mariusz Dworniczak 
**Student:** Sylwia Banach
**Numer Albumu:** 96402

---

## 🏗️ Architektura Projektu (Marketing & Tech Stack)
Ten projekt to kompletny ekosystem testowy oparty na podejsciu **Cloud-Ready / Headless**. Zamiast polegać na ciężkich emulatorach, skupiamy się na narzędziach CLI, analizie statycznej, konteneryzacji (Docker) oraz automatyzacji procesów (Pipeline). 

**Główne technologie:**
* **Język:** Python 3.10+
* **Automatyzacja UI:** Appium 2.x (Mobile Engine)
* **Infrastruktura:** Docker & Docker Compose
* **Raportowanie:** Allure Framework
* **Analiza:** MobSF (Static Analysis) & ADB CLI

---

## 📅 PRZEBIEG LABORATORIUM (Kamienie Milowe)

### 🔹 BLOK 1: Tooling & Environment (Infrastruktura)
Przygotowanie bazy narzędziowej w modelu kontenerowym.
* **Co zrobiono:** Pobranie i konfiguracja obrazów `appium`, `android-sdk` oraz `mobsf`.
* **Wniosek:** Wykorzystanie Dockera pozwala na stworzenie powtarzalnego i niezależnego od systemu środowiska testowego. Dzięki temu eliminuje się problemy związane z konfiguracją lokalną, konfliktami wersji oraz różnicami między komputerami. Obrazy kontenerów zapewniają, że każdy tester pracuje na identycznym środowisku, co zwiększa stabilność testów i ułatwia ich automatyzację.

### 🔹 BLOK 2: Debugowanie i Analiza Statyczna (MobSF)
Zrozumienie "wnętrza" aplikacji mobilnej przed przystąpieniem do testów.
* **Co zrobiono:** Wykorzystanie MobSF do skanowania plików APK pod kątem podatności i uprawnień.
* **Wniosek:** Analiza statyczna APK pozwala testerowi zrozumieć strukturę i działanie aplikacji bez jej uruchamiania. Dzięki temu można wcześniej wykryć potencjalne problemy, takie jak nadmiarowe uprawnienia, niebezpieczne ustawienia czy podatności wynikające z niskiego poziomu API. Daje to możliwość szybszego identyfikowania ryzyk oraz lepszego przygotowania do dalszych testów dynamicznych.

### 🔹 BLOK 3-4: Fundamenty Skryptowania (Python for QA)
Budowa logiki testowej w języku Python.
* **Co zrobiono:** Poznano podstawowe elementy języka Python wykorzystywane w testowaniu, takie jak operacje na listach i słownikach, pętle, funkcje oraz przetwarzanie plików. Wykorzystano je do tworzenia skryptów analizujących dane (np. parsowanie plików XML aplikacji, generowanie raportów JSON). Dodatkowo nauczono się definiowania selektorów UI na podstawie struktury aplikacji (ID, contentDescription, XPath) oraz oceny ich stabilności i poprawności w kontekście automatyzacji testów.

### 🔹 BLOK 5-7: Hybrydowe Testowanie API (Requests & Pytest) Weryfikacja warstwy backendowej aplikacji mobilnej. 
* **Co zrobiono:** Testowanie endpointów REST (JSONPlaceholder), obsługa kodów HTTP i asercja danych JSON. 
* **Wniosek:** Testowanie API pozwala wyłapać błędy zanim uruchomimy ciężkie testy UI.

### 🔹 BLOK 8: Appium UI Automation (Deep Dive)
Automatyzacja interakcji z interfejsem użytkownika.
* **Co zrobiono:** Wykorzystano Appium do automatyzacji interakcji z interfejsem użytkownika aplikacji mobilnej. Do lokalizowania elementów używano selektorów takich jak ID, XPath oraz contentDescription, zwracając uwagę na ich stabilność. W testach symulowano podstawowe akcje użytkownika, takie jak kliknięcia, wprowadzanie tekstu, przewijanie ekranu oraz nawigację między widokami. Dodatkowo zastosowano mechanizmy oczekiwania na elementy (wait), aby zapewnić poprawne działanie testów w środowisku mobilnym.

### 🔹 BLOK 9: Konteneryzacja Serwera (Docker Compose)
Izolacja silnika Appium od systemu operacyjnego.
* **Co zrobiono:** Stworzenie pliku `docker-compose.yml` zarządzającego serwerem Appium i sterownikami.

### 🔹 BLOK 10: MASTER PIPELINE (Capstone Project) 🏆
Finałowa automatyzacja całego procesu testowego.
* **Co zrobiono:** Stworzenie skryptu `pipeline.py`, który w jednym cyklu:
1. Rezerwuje zasoby i stawia infrastrukturę Docker.
2. Wykonuje testy hybrydowe (API + UI).
3. Generuje profesjonalny raport Allure z metadanymi.
4. Czyści środowisko po zakończonej pracy.

---

## 📊 Raportowanie Wyników (Allure)
Projekt wykorzystuje zaawansowane raportowanie Allure, które pozwala na:
* Śledzenie kroków testowych (`@allure.step`).
* Analizę błędów wraz z załącznikami (zrzuty ekranu, logi JSON).
* Dokumentowanie środowiska wykonawczego w sekcji **Environment**.

![img.png](img.png)

---

## 🚀 Jak uruchomić cały proces?
```bash
# Wejdź do folderu finałowego
cd Artefakt10

# Uruchom wszystko jednym poleceniem
python3 pipeline.py

# Po zakończeniu zobacz raport
allure serve allure-results

 