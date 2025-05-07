# 🌳 Przykład działania B-Drzewa jako indeksu w bazie danych

## 📄 Założenie

Załóżmy, że mamy następujące wartości kluczy, które chcemy wstawić do indeksu opartego na B-drzewie:

**Klucze:** 10, 20, 5, 6, 12, 30, 7, 17

Użyjemy uproszczonego B-drzewa o **stopniu t = 2**, co oznacza:

* Każdy węzeł może mieć **maksymalnie 3 klucze** (2t - 1)
* Każdy węzeł może mieć **od 2 do 4 dzieci**

---

## 🔧 Krok po kroku – wstawianie kluczy

### 🔢 1. Wstaw 10

* Drzewo jest puste. Tworzymy korzeń z jednym kluczem: `[10]`

### 🔢 2. Wstaw 20

* `[10, 20]` — węzeł ma teraz dwa klucze

### 🔢 3. Wstaw 5

* `[5, 10, 20]` — nadal mieści się w jednym węźle

### 🔢 4. Wstaw 6

* Węzeł przekracza limit (3 klucze), trzeba go rozdzielić
* Środkowy klucz (10) idzie do góry
* Powstają dwa węzły: `[5, 6]` i `[20]`
* Nowy korzeń: `[10]`

```
        [10]
       /    \
 [5, 6]      [20]
```

### 🔢 5. Wstaw 12

* Trafia do prawego dziecka `[20]` → `[12, 20]`

### 🔢 6. Wstaw 30

* `[12, 20, 30]` — ok

### 🔢 7. Wstaw 7

* `[5, 6]` → `[5, 6, 7]`

### 🔢 8. Wstaw 17

* Prawy węzeł `[12, 20, 30]` musi się rozdzielić
* Środkowy klucz 20 idzie do góry
* Nowy korzeń: `[10, 20]`
* Dzieci: `[5, 6, 7]`, `[12, 17]`, `[30]`

```
           [10, 20]
         /    |     \
  [5,6,7] [12,17] [30]
```

---

## 🧠 Podsumowanie

* B-drzewa utrzymują klucze w uporządkowanej strukturze i balansują się automatycznie.
* Gwarantują, że operacje wstawiania, wyszukiwania i usuwania mają złożoność $O(\log n)$.
* Są idealne dla dużych zbiorów danych przechowywanych na dysku — minimalizują liczbę odczytów I/O.

> 💡 **Wskazówka**: W praktyce B-drzewa są podstawą dla indeksów w systemach takich jak MySQL, PostgreSQL oraz silnikach NoSQL typu RocksDB.

---

## 🔗 Symulator B-Drzewa

🎯 Wypróbuj interaktywny symulator B-drzewa online: [https://www.cs.usfca.edu/\~galles/visualization/BST.html](https://www.cs.usfca.edu/~galles/visualization/BST.html)
