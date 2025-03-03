# Sterowanie przebiegiem programu

Instrukcja warunkowa `if`:
```python
wiek = 21
if wiek < 0:
    print("Wiek nie moze byc ujemny!")
elif x < 18:
    print("Jestes niepelnoletni.")
else:
    print("Jestes pelnoletni.")
```
  
Pętla `for`:
```python
for i in range(10):
    if i == 4:
        break
    print(i)

for i in range(5):
    if i % 2 == 0:
        continue
    print(i)

lista = [1, 2, 3]
for element in lista:
    print(lista)
else:
    print("Koniec!")
```
  
Pętla `while`:
```python
x = 0
while x < 5:
    print(x)
    x += 1
```
  
Instrukcja `match`  
Pozornie podobna do instrukcji `switch` z języka C, ale z większymi możliwościami dopasowania:
```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case _:
            return "Something's wrong with the internet"
```
  
Więcej przykładów i szczegółów w [dokumentacji](https://docs.python.org/3/tutorial/controlflow.html#more-control-flow-tools).
  
**Zadania**
1. Wypisz wszystkie liczby od 1 do 50, jednak jeżeli liczba jest podzielna przez:
trzy – zamiast liczby wypisz „Fizz”,
pięć – wypisz „Buzz”,
jeśli jest podzielna zarówno przez trzy i pięć - wypisz „FizzBuzz”.

2. Stwórz prostą grę polegającą na zgadywaniu losowej liczby z zakresu 1-100 wygenerowanej przez komputer. Uzyj modułu `random`.
Użytkownik wprowadza liczbę, a program nakierowuje gracza przez podpowiedzi, np. "Podałeś za małą/za dużą liczbę" lub w przypadku trafienia informuje o wygranej. Możesz opcjonalnie dodać warunek maksymalnie `n` prób. 
Pytanie "przy okazji": jaka jest najlepsza strategia na wygraną?
  
3. Napisz program, który pyta użytkownika o dzień tygodnia i zwraca odpowiednio napis `dzień roboczy`, `weekend` lub `nieprawidlowa wartosc`. 

# Obsługa i manipulacja napisami (typ str)

Python udostępnia bardzo bogatą bibliotekę funkcji wbudowanych, za pomocą których można manipulować łańcuchami znaków w wygodny i zwięzły sposób.

1. Tworzenie napisów
```python
s1 = "Witaj, swiecie!"
s2 = 'Mozna stosowac zamiennie pojedynczy \' lub podwójny \" cudzyslow'
s3 = """albo przechowywac 
wieloliniowy  
napis w potrojnym cudzyslowie"""
```

2. Indeksowanie napisów
```python
# indeksowanie
s1 = 'Python'
print(s[0])
print(s[-1])

# tzw. slicing - dziala rowniez na listach
s2 = 'Hello, World!'
print(s2[0:5])   # 'Hello'
print(s2[:5])    # 'Hello'
print(s2[7:])    # 'World!'
print(s2[-6:-1]) # 'World'
print(s2[0::2])  # 'Hlo ol!
```
Zwróć szczególną uwagę na znaczenie wartości podawanych w zakresach, np. ile i które indeksy zawiera zakres [0:5].

3. Modyfikowanie napisów
```python
s = 'python '
print(s.upper())  # 'PYTHON '
print(s.lower())  # 'python '
print(s.capitalize())  # 'Python '
```
```python
s = "  hello!  "
print(s.strip())   # 'hello!'
print(s.lstrip())  # 'hello!  '
print(s.rstrip())  # '  hello!'
```
```python
s1 = "Hello, world!"
print(s.replace("world", "Python"))  # 'Hello, Python!'
s2 = "apple,banana,orange"
print(text.split(","))  # ['apple', 'banana', 'orange']
```
```python
words = ["Python", "is", "fun"]
print(" ".join(words))  # 'Python is fun'
```
4. Szukanie w napisach:
```python
s = "Python is awesome"
print("Python" in s)   # True
print("Java" not in s) # True
```
```python
s = "Hello, Python!"
print(s.find("Python"))  # zwraca indeks pierwszego wystapienia lub -1 w razie braku
print(s.startswith("Hello"))
print(s.endswith("!"))
```

Więcej w [dokumentacji](https://docs.python.org/3/library/stdtypes.html#string-methods).

**Zadania**
1. Napisz funkcję, która zwraca inicjały (wielkimi literami) dla podanego imienia i nazwiska.  
Przykład: `print(get_initials("katarzyna marczak"))  # "KM"`

2. Napisz funkcję, która w podanym tekście cenzuruje (wygwiazdkuje) dane słowo.  
Przykład: `print(censor("tekst do cenzury", "tekst"))  # "***** do cenzury"`

3. Napisz funkcję, która zliczy unikalne słowa w danym napisie. Np. dla napisu "test auto test abc" zliczy : 2 wystąpienia słowa test, 1 auto i 1 abc. Zastanów się, jakiej struktury danych najlepiej użyć do tego zadania.

4. Napisz funkcję, która poprawi zdanie tak, by zaczynało się od wielkiej litery i kończyło kropką.
Przykład: `print(correct("popraw mnie"))  # "Popraw mnie."`  
