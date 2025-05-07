# 🔍 Przykład działania algorytmu Full-Text Search

## 📄 Założenie

Załóżmy, że mamy trzy dokumenty tekstowe:

* **Dokument1**: "Ala ma kota."
* **Dokument2**: "Ola ma psa."
* **Dokument3**: "Ala lubi czytać książki."

Chcemy stworzyć indeks full-text i umożliwić szybkie wyszukiwanie tekstu.

---

## ⚙️ Krok 1: Tokenizacja

Rozbijamy tekst na pojedyncze tokeny (słowa):

* Dokument1 → "ala", "ma", "kota"
* Dokument2 → "ola", "ma", "psa"
* Dokument3 → "ala", "lubi", "czytać", "książki"

---

## 🧼 Krok 2: Normalizacja

* Wszystkie słowa zamieniamy na małe litery.
* Usuwamy znaki interpunkcyjne.
* Opcjonalnie: usuwamy *stop words* (np. "ma") lub stosujemy stemming (np. "czytać" → "czyt").

---

## 🗺️ Krok 3: Tworzenie odwróconego indeksu (Inverted Index)

Tworzymy strukturę danych, w której:

```
"ala"     → [Dokument1, Dokument3]
"ma"      → [Dokument1, Dokument2]
"kota"    → [Dokument1]
"ola"     → [Dokument2]
"psa"     → [Dokument2]
"lubi"    → [Dokument3]
"czytać"  → [Dokument3]
"książki" → [Dokument3]
```

---

## 🔍 Przykład zapytania: "ala ma"

### Krok 1: Tokenizacja i normalizacja zapytania:

* Tokeny: "ala", "ma"

### Krok 2: Wyszukiwanie w indeksie:

* "ala" → \[Dokument1, Dokument3]
* "ma" → \[Dokument1, Dokument2]

### Krok 3: Przecięcie wyników:

* Wspólne dokumenty: **Dokument1**

📌 **Odpowiedź**: Dokument1 zawiera oba słowa — "ala" i "ma".

---

## 🧠 Podsumowanie

* Full-text indexing pozwala na szybkie przeszukiwanie dużych zbiorów tekstowych.
* Dzięki strukturze odwróconego indeksu możliwe jest efektywne odnajdywanie dokumentów na podstawie zawartości.
* To podejście jest używane m.in. w wyszukiwarkach, bazach danych oraz narzędziach typu Elasticsearch.

> 💡 **Wskazówka**: Full-text search może być dostosowywany np. przez lematyzację, ranking wyników, filtrację fraz i wiele innych technik.
