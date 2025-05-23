# Wprowadzenie

Python to język wysokiego poziomu, dynamicznie typowany i interpretowany (a nie kompilowany). W przeciwieństwie do C, Python nie wymaga deklarowania typów zmiennych i zarządzania pamięcią. Jego składnia jest bardziej czytelna i zwięzła.

# Uruchamianie Pythona

Kod w Pythonie można uruchamiać w interpreterze interaktywnym lub zapisywać w plikach .py i uruchamiać za pomocą python nazwa_pliku.py w konsoli.
  
Język C:  
```c
#include <stdio.h>

int main() {
  int array[3] = { 1, 2, 3 };
  for(int i = 0; i < 3; i++) {
    printf("%d\n", array[i]);
  }
  return 0;
}
```

Python:

```python
# komentarz: przykladowy program w jezyku Python
numbers = [1, 2, 3]
for i in numbers:
    print(i)
```

**Zadanie**  
Porównaj powyzsze programy i wymień wszystkie różnice między językiem C i Python, które są widoczne w tym przykładzie. Uruchom przykładowy program zarówno w IDLE, jak i w terminalu.

# Definiowanie funkcji

W Pythonie funkcje definiuje się za pomocą słowa kluczowego `def`.
```python
def multiply(a, b):
    return a * b

result = multiply(3, 4)
print(f'{a} * {b} = {result}')
```  
Powyższy przykład używa tak zwanych `f-strings` do formatowania napisu. Więcej na ten temat: https://docs.python.org/3/tutorial/inputoutput.html

**Zadanie**  
Napisz funkcję, która zapyta uzytkownika o jego imię i wypisze komunikat z uzyciem tego imienia (np. "Witaj, Jan Kowalski!"). Potrzebną funkcję biblioteczną znajdziesz w [dokumentacji.](https://docs.python.org/3/library/functions.html#built-in-functions)

# Zarządzanie modułami
  
Python posiada bogaty ekosystem modułów, które można importować i używać w swoich programach. Moduły pozwalają na organizację kodu oraz ponowne wykorzystanie gotowych funkcji i klas.
  
Mozna importować cały moduł, a pochodzące z niego elementy nalezy poprzedzać nazwą modułu:
```python
import math
print(math.sqrt(16))
```
lub tylko wybrane elementy (stałe, funkcje itd.).
```python
from math import sqrt
print(sqrt(16))
```
Można również nadawać importowanym modułom w swoim programie dowolny alias (uważając na kwestie przesłonięcia innej nazwy):
```python
import pandas as pd
import math as moj_ulubiony_przedmiot
```

**Zadanie**  
Sprawdź działanie instrukcji `import this`.
  
Standardowa biblioteka Pythona posiada bardzo wiele przydatnych modułów. Jeśli potrzebujemy modułu spoza tej biblioteki, zainstalujemy go za pomocą narzędzia `pip` (https://pypi.org/).  
  
Najwazniejsze komendy `pip`:  
  
Wypisanie dostępnych modułów  
`pip list`  
  
Zapisanie modułów do pliku  
`pip freeze > requirements.txt`  
Uwaga: requirements.txt to powszechnie przyjęta konwencja przechowywania listy modułów wymaganych do uruchomienia danego programu w Pythonie.  
  
Instalacja i usuwanie modułów  
```
pip install [--user] nazwa_pakietu[==konkretna wersja]
pip install -r requirements.txt
pip uninstall nazwa_pakietu
```

# Typy zmiennych

Python jest językiem dynamicznie typowanym. To znaczy, ze typ zmiennej jest określany w trakcie przypisania wartości i może się zmienić w czasie działania programu.

```python
var = 'Ala ma kota'  # napis, czyli typ str (string)
print(f'Wartość zmiennej={var}, typ={type(var)}')
var = 12345  # typ int (liczba całkowita)
print(f'Wartość zmiennej={var}, typ={type(var)}')
var = 0.4533113  # typ float (liczba zmiennoprzecinkowa)
print(f'Wartość zmiennej={var}, typ={type(var)}')
```

Proste typy:
```python
str      # string - łańcuch znakowy
bool     # boolean - wartość logiczna prawda/fałsz
int      # integer - liczba całkowita
float    # floating point number - liczba zmiennoprzecinkowa
complex  # complex - liczb zespolona
```

Złożone typy (struktury danych):
```python
list      # lista - odpowiednik tablicy, kluczem jest indeks 
dict      # słownik, kluczem może być (prawie) dowolna wartość
set       # zbiór unikalnych wartości, kluczem jest indeks
tuple     # krotka - niemodyfikowalny odpowiednik listy
```

Przykłady użycia struktur danych:
  
```python
# lista
lista = [1, 2, 3, 'abc', True]  # uwaga - nie nazywac zmiennej "list" (dlaczego?)
print(lista[3])
lista[2] = 4
lista.append(6)
print(lista)
print(f'Dlugosc listy: {len(lista)}')

# słownik
slownik = {
  'k1': 'ala ma kota',
  'k2': 1337,
  'moja_lista': lista,
  1: 'one'
}

print(slownik[1])
slownik[1] = 'jeden'  # modyfikacja wartosci pod kluczem 1
slownik[2] = 'dwa'  # dodanie nowej pary klucz-wartosc
print(slownik)

# zbior
zbior = set([1, 2, 3, 1, 2, 3, 4])  # jeden argument: lista wartosci
print(zbior)
zbior.add(9)
print(zbior)
zbior = {1, 2, 3, 1, 2, 3, 4}  # alternatywna składnia tworzenia zbioru

krotka = (1, 4, 5, 3, 2, 1)
print(krotka)
print(krotka[1])
# krotka[1] = 0  wywoła błąd!
```

Iterowanie po strukturach danych  
  
W Pythonie nie musimy znać rozmiaru kolekcji (listy, zbioru itd.) aby móc ją przeiterować.  
Pętla `for` przechodzi po kazdym elemencie, az do końca kolekcji:  
```python
lista = ['q', 'w', 'e']
for element in lista:
    print(element, end=" ")
```
  
**Zadania**  
  
1. Stwórz listę zawierającą liczby całkowite od 1 do 10 000, używajac `range` [(dokumentacja)](https://docs.python.org/3/library/stdtypes.html#range). Następnie użyj pętli, aby każdą liczbę w liście zwiększyć o 1. Użyj modułu `timeit` by sprawdzić, ile czasu zajmie wykonanie tej pętli.
2. Napisz funkcję, ktora zwróci listę krotek. Każda krotka to para liczb naturalnych dająca sumę `2*n`. Wartosc `n` jest parametrem funkcji. Np. lista dla n=50: `[(0, 100), (1, 99), (2, 98), ..., (99, 1), (100, 0)]`
3. Stwórz słownik przechowujący w kluczu imię i nazwisko osoby, a w wartości datę jej urodzin. Do słownika zapisz 3 różne osoby. Do przechowania daty użyj typu `date` z modułu `datetime` ([dokumentacja](https://docs.python.org/3/library/datetime.html#examples-of-usage-date)). Następnie wypisz za pomoca pętli `for` wszystkie rekordy w słowniku w formacie 'Imie Nazwisko ur. dd-mm-rr'.
4. Przetestuj, które z omówionych powyżej typow danych można użyc w roli klucza w słowniku. Następnie porównaj swoje obserwacje z informacjami w [tym artykule](https://wiki.python.org/moin/DictionaryKeys).
5. Poczytaj o [listach składanych](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions). Przepisz poniższe pętle tak, by używały składania list (tworzyły tę samą listę w jednej linii).
```python
values = []
for i in range(10):
    numbers.append(i**2)

values = []
for i in range(1, 6):
    for j in range(1, 4):
        values.append((i, j))
```
