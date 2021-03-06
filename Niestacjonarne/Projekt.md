# Projekt

## Etap 1

#### Stwórz Podstawową implementację wektora

Celem tego etapu projektu jest stworzenie własnej implementacji kontenera `vector`, na podstawie podanej poniżej deklaracji.

Deklaracja zawiera metody, które są wymagane do zaimplementowania i takie, które można wykonać dodatkowo. Zostały one dodatkowo oznaczone.

```c++
template<typename type>
class Vector {
private:
    type data*;
    size_t allocatedDataSize;
    size_t usingDataSize;

public:
    /**
     * Create empty vector
     * Tworzenie pustego wektora
     */
    Vector();

    /**
     * Create vector with passed size
     * Tworzenie wektor o podanym rozmiarze
     * @param usingDataSize size of creating vector
     */
    Vector(size_t usingDataSize);

    /**
     * Deallocating, do cleanings
     * Zwalnianie pamięci, robienie porządków
     */
    ~Vector();

    /**
     * Get element from specified index
     * Pobieranie elementów spod przekazanego indeksu
     * @param index index of element
     * @return reference to element
     */
    type *at(size_t index);

    /**
     * Get address of first element
     * Pobieranie adresu pierwszego elementu
     * @return address of first element
     */
    type *front();

    /**
     * Get address of last element
     * Pobieranie adresu ostatniego używanego elementu
     * @return address of last element
     */
    type *back();

    /**
     * Get size of using data
     * Pobieranie rozmiaru tablicy (używanej części)
     * @return size of using vector
     */
    size_t size();

    /**
     * Add new element on the end of vector
     * Dodaj nowy element na koniec wektora
     * @param newRecord new value
     */
    void pushBack(type newRecord);

    /**
     * Delete last element
     * Usuwanie ostatniego elementu
     */
    void popBack();

    /**
     * Check vector is empty
     * Sprawdzanie, czy wektor jest pusty
     * @return true if vector is empty, false if not empty
     */
    bool isEmpty();

    /** Dodatkowe
     * Delete all elements
     * Usuwanie wszystkich elementów z wektora
     */
    void clear();
    
    /** Dodatkowe
     * Reallocate data to fit allocated data to using data
     * Realokowanie pamięci, aby dopasować rozmiar zaalokowanej tablicy do używanej
     */
    void shrinkToFit();
    
    /**
     * Delete element on passed index
     * Usuwanie elementu pod wskazanym indeksem
     * @param size_t index of element to erase
     */
    void erase(size_t index);
};
```

#### Pola

Klasa zawiera następujące pola:
- data - wskaźnik służący do przechowywania danych
- allocatedDataSize - rozmiar (ilość elementów) zaalokowanej pamięci
- usingDataSize - rozmiar (ilość) używanych elementów

#### Konstruktory

Podczas tworzenia obiektu powinna być alokowana pamięć do przechowywania elementów. Można zaalokować więcej pamięci, niż jest używane. Przykładowo przy wywołaniu pustego konstruktora można zaalokować pamięć dla 10 elementów i ustawić używaną wielkość (usingDataSize) na 0.

## Dodatkowe informacje

Można tworzyć dodatkowe metody bądź pola, jeżeli będzie to potrzebne.

&nbsp;

&nbsp;

&nbsp;

## Etap 2

#### Stwórz obsługę plików

Celem tego etapu jest stworzenie obsługi plików dla klasy `Vector`, która będzie umożliwiała zapisywanie i odczytywanie zawartości z dysku.

### Korekta w klasie `Vector`

W klasie `Vector` pola prywatne przenieś do sekcji chronionych (zamień `private`, na `protected`).

### Klasa do obsługi plików

Stwórz nową klasę, która będzie dodawała do klasy `Vector` nowe funkcjonalności, zapisywani i odczytywnaie jej zawartości z pliku. Ma to być dokonywane za pomocą operatorów `<<` i `>>`.

1. Klasa ma się nazywać `VectorFile` i ma dziedziczyć `Vector`.
2. Ma posiadać w sobie publiczne implementacje dla następujących operatorów:
   1. `<<` - zapisywanie danych do pliku binarnego
   2. `>>` - odczytywanie danych z pliku binarnego
   3. Sam wymyśl, co ma zwracać i przyjmować jako argument ten operator.
3. Może posiadać inne prywatne pola i metody.

&nbsp;

### Przykładowe użycie

1. Stworzenie `VectorFile`.
2. Dodanie różnych danych za pomocą metody `push_back`.
3. Użycie operatora `<<` do zapisania wprowadzonych danych do pliku binarnego.
4. Zakończenie aplikacji
5. Uruchomienie aplikacji
6. wczytanie danych za pomocą operatora `>>` z pliku.
7. Usunięcie ostatniego rekordu (`popBack`) i dodanie dwóch nowych (`pushback`).
8. Zapisanie danych do pliku za pomocą operatora `<<`.
9. Zakończenie aplikacji.
10. Uruchomienie aplikacji.
11. Wyświetlenie wszystkich zapisanych danych.

&nbsp;

&nbsp;

&nbsp;

# Etap 3

#### Stwórz klasy przechowujące dane

Stwórz klasę:

```c++
class MCoord
{
protected:
	double *pcoord;
public:
	mcoord(double xx, double yy);
	mcoord() { pcoord = NULL; }
	~mcoord() { ……………… }
};
```

Utwórz klasę node, która publicznie dziedziczy po klasie mcoord:

```c++
class Node
{
int numb;       //numer wierzchołka
char str[512];  //nazwa wierzchołka
public:
node(int nb, char *st, double xx, double yy);
node();
…………………
};
```

Klasa node ma dodatkowo zawierać:

- przeciążenia operatorów
  - `=` - przypisywanie
  - `==` - porównywanie
  - `<<` i `>>` - obsługa dowolnych strumieni
- konstruktor kopiujący


### Klasa obsługi błędów

Stwórz obsługę błędów, ostrzeżeń i komunikatów. Wszystkie mają być zapisane w jednym pliku.


&nbsp;

&nbsp;

&nbsp;

# Etap 4

#### Funkcja find

Stwórz szablonową funkcję find służącą do wyszukiwania elementu w tablicy.

```c++
template <class T, class Key>
T * find(const T *p_begin, const T *p_end, const Key &k);
```

Gdzie:

- `T *p_begin` - wskaźnik na pierwszy element tablicy
- `T *p_end` - pierwszy element po ostatnim elemencie tablicy (pierwszy wolny element tablicy)
- `Key &k` - klucz przeszukiwania (np. numer wierzchołka).

Zwracane:

- wskaźnik do odnalezionego elementu
- `NULL` lub `nullptr` (wybierz i konsekwentnie się tego trzymaj) w razie nieznalezienia obiektu



&nbsp;

&nbsp;

&nbsp;

# Etap 5

#### Stwórz interfejs użytkownika (w konsoli za pomocą `cin` i `cout`)

Stwórz aplikację zarządzającą danymi. Będzie ona przechowywać obiekty typu `MCoord` w kontenerze stworzonym w etapie 1.
Utwórz tekstowy interfejs użytkownika, który będzie działał w pętli i będzie posiadał opcje:

- dodawania obiektu
- usuwania obiektu
- wyczyszczenie tablicy obiektów
- modyfikację obiektu
- wstawiania obiektu w określone miejsce
- znalezienia wszystkich obiektów zgodnych z kluczem (numerem wierzchołka)
- zapisanie danych na dysk
- odczytanie danych z dysku
- wyświetlenie danych na ekranie
- zakończenie działania programu

&nbsp;

&nbsp;

&nbsp;

# Uwagi ogólne

Wszystkie dynamiczne alokacje i dealokacje mają być dokonywane za pomocą operatorów `new` i `delete`. Pamiętaj o podziale projektu na pliki `*.cpp` i `*.h`.

Pamiętaj o tworzeniu komentarzy dokumentacyjnych przed funkcjami i metodami.

&nbsp;

**Wyszukiwanie**

Wyszukiwania dokonuj za pomocą stworzonej funkcji find. Szukaj tylko po numerach wierzchołków w tym celu stwórz w klasie 
`Node` odpowiednie przeciążenie operatora `==`.

&nbsp;

&nbsp;

Projekt stworzony na podstawie materiałów: dr hab. inż. Sergiy Fialko (http://torus.uck.pk.edu.pl/~fialko/)


