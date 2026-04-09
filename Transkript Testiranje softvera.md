# Transkript: Testiranje softvera (Black Box metoda)

**Tema:** Analiza klasa ekvivalencije i graničnih vrednosti na primeru IT prodavnice
**Model:** Gemini 3 Flash (Expert Guide Mode)

---

## 1. Postavka zadatka
IT firma prodaje opremu pod sledećim uslovima isporuke:
1. Kupovina **do 1500** -> dostava iznosi **195**
2. Kupovina **od 1500 do 5000** -> dostava iznosi **295**
3. Kupovina **preko 5000** -> dostava je **besplatna (0)**

---

## 2. Analiza klasa ekvivalencije

### A. Validne klase (Ispravni podaci)
| Klasa ekvivalencije | Opseg vrednosti | Predstavnik | Očekivani izlaz |
| :--- | :--- | :--- | :--- |
| **Mala kupovina** | 0.01 – 1500.00 | 500 | 195 |
| **Srednja kupovina** | 1500.01 – 5000.00 | 3000 | 295 |
| **Velika kupovina** | Preko 5000.01 | 7500 | 0 |

### B. Nevalidne klase (Greške u unosu)
| Klasa ekvivalencije | Opseg / Tip | Predstavnik | Očekivani izlaz |
| :--- | :--- | :--- | :--- |
| **Nula ili minus** | <= 0 | -50 | Poruka o grešci |
| **Pogrešan tip** | Tekst / Simboli | "ABC" | Poruka o grešci |

---

## 3. Dokumentacija test slučajeva (QA izveštaj)

### Test Case #1: Provera niske tarife
* **Šta se testira?** Isplativost dostave za male iznose.
* **Šta želimo da dokažemo?** Da sistem ispravno primenjuje tarifu od 195 za iznose do 1500.
* **Vrednost:** 500

### Test Case #2: Provera srednje tarife
* **Šta se testira?** Prelazak u srednji rang potrošnje.
* **Šta želimo da dokažemo?** Da sistem prepoznaje promenu tarife na 295 kada kupac pređe prag od 1500.
* **Vrednost:** 3000

### Test Case #3: Provera besplatne isporuke
* **Šta se testira?** Maksimalni prag kupovine.
* **Šta želimo da dokažemo?** Da softver ne naplaćuje dostavu kupcima koji troše više od 5000.
* **Vrednost:** 6000

---

## 4. Profesionalni savet (Granične vrednosti - BVA)

Kao profesionalni tester, fokusiramo se na **"ivice"** jer tu programi najčešće pucaju. 

> **Problem:** Zadatak kaže "do 1500" i "od 1500". Šta se dešava sa tačno 1500?
> **Rešenje:** Uvek testiramo tri tačke oko granice:
> * **1499.99** (Mala kupovina)
> * **1500.00** (Granica - proveravamo specifikaciju)
> * **1500.01** (Srednja kupovina)

---

## 5. Zaključak
Ovaj pristup osigurava da je softver pokriven i sa logičke strane (klase ekvivalencije) i sa tehničke strane (granične vrednosti), dok istovremeno sprečava pad sistema usled unosa nevalidnih podataka.