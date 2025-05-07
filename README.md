# 📊 Indeksy w Bazach Danych

## 🧭 Wprowadzenie

Indeksy w bazach danych pełnią rolę podobną do indeksu w książce — pozwalają szybko zlokalizować interesujące nas dane bez konieczności przeszukiwania całej zawartości. Są to specjalne struktury danych przyspieszające operacje wyszukiwania, filtrowania oraz sortowania rekordów w tabelach.

---

## 🧱 Czym Jest Indeks?

**Indeks** to dodatkowa struktura danych tworzona na jednej lub więcej kolumnach tabeli. Przechowuje on uporządkowaną kopię danych i wskaźniki prowadzące do właściwych rekordów.

### 🔑 Kluczowe Cechy Indeksów:

* 📐 **Struktura danych**: Najczęściej używa się B-drzew i B+-drzew.
* ⚡ **Skrócony czas dostępu**: Wyszukiwanie jest znacznie szybsze.
* 🔗 **Wskaźniki**: Pozwalają szybko zlokalizować rekordy w tabeli.
* 🧩 **Unikalność**: Tworzone automatycznie dla kluczy głównych i unikalnych.

### 💻 Przykłady SQL

```sql
-- Indeks nieklastrowany na kolumnie EmployeeID
CREATE INDEX idx_employee_id ON Employees (EmployeeID);

-- Indeks złożony na kolumnach LastName i FirstName
CREATE INDEX idx_name ON Employees (LastName, FirstName);
```

---

## ⚖️ Zalety i Wady Indeksów

### ✅ Zalety:

* 🔍 **Szybsze wyszukiwanie i filtrowanie**
* 📊 **Lepsze sortowanie**
* 🔐 **Wymuszanie unikalności danych**

### ❌ Wady:

* 💾 **Dodatkowe zużycie pamięci**
* 🐢 **Wolniejsze operacje DML (INSERT/UPDATE/DELETE)**
* 🧠 **Złożoność zarządzania indeksami**

---

## 🌳 B-Drzewa i B+-Drzewa jako Struktury Indeksów

### 🌲 B-Drzewa – Dlaczego są używane?

* ⚖️ **Zrównoważenie**: Wszystkie liście są na tym samym poziomie, operacje mają złożoność $O(\log n)$
* 📦 **Wielkość węzłów**: Pasują do bloków dyskowych, minimalizując operacje I/O
* 📥 **Wsadowość**: Obsługa wielu kluczy naraz zwiększa wydajność
* 🔁 **Sekwencyjny dostęp**: Ułatwia skanowanie zakresowe

### ➕ B+-Drzewa – Ulepszony wariant

* 🧾 **Klucze tylko w liściach**: Ułatwia sekwencyjne skanowanie
* 🔗 **Połączone liście**: Szybki dostęp do kolejnych rekordów
* 🧱 **Stała struktura węzłów wewnętrznych**: Prostsze algorytmy i większa wydajność

### 💡 Przykład SQL i Implementacja

```sql
CREATE INDEX idx_employee_id ON Employees (EmployeeID);
```

W bazie danych używającej B-drzew, powyższy indeks będzie reprezentowany jako struktura drzewa, której węzły zawierają klucze `EmployeeID` oraz wskaźniki do rekordów.

---

## 🔍 Indeksy Full-Text

### 📚 Czym jest indeks pełnotekstowy?

Indeks **full-text** to specjalna struktura danych umożliwiająca szybkie wyszukiwanie słów i fraz w dużych zbiorach tekstu, np. dokumentach lub kolumnach tekstowych w bazie danych.

### ⚙️ Algorytm tworzenia indeksu:

1. 🧩 **Tokenizacja** – podział tekstu na tokeny (słowa/frazy).
2. 🧼 **Normalizacja** – usunięcie interpunkcji, zamiana na małe litery, usunięcie tzw. *stop words*, stemming.
3. 🗺️ **Indeksowanie** – tworzenie odwróconego indeksu (inverted index), który przypisuje tokeny do list dokumentów.

#### 🗂️ Odwrócony indeks – przykład:

```
"Ala"   -> [Dokument1, Dokument3]
"ma"    -> [Dokument1, Dokument2]
"kota"  -> [Dokument1]
```

### 🔎 Algorytm wyszukiwania:

1. Tokenizacja i normalizacja zapytania.
2. Przeszukiwanie odwróconego indeksu.
3. Zwrócenie listy dokumentów zawierających wszystkie tokeny.

### 🧠 Porównania:

* 📖 **Indeks w książce** – spis słów i strony, na których występują.
* 📃 **Spis treści** – odniesienie do sekcji.
* 🗃️ **Hashmapa** – klucz-token, wartość-lista wystąpień.

### 🚀 Zastosowania:

* 🌐 Wyszukiwarki internetowe (Google, Bing).
* 🧮 Systemy bazodanowe (PostgreSQL, MySQL).
* 📂 Systemy zarządzania dokumentami (Elasticsearch, Apache Solr).

---

## 🧾 Podsumowanie

Indeksy — szczególnie te oparte na B-drzewach i ich wariantach — są fundamentem wydajnych systemów baz danych. Z kolei indeksy **full-text** umożliwiają szybkie przeszukiwanie danych tekstowych, co czyni je niezastąpionymi w aplikacjach internetowych i analitycznych. Wybór odpowiedniego typu indeksu zależy od rodzaju operacji, jakie mają być wykonywane na danych.

---

> 📘 **Wskazówka dla studentów**: Jeśli pracujesz z tekstem – nie zapomnij o pełnotekstowym indeksowaniu!
