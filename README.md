# bank-app

Remigiusz Kamiński grupa 2

| Termin oddania | Punkty |
| ------- | ------ |
| 26.10.2022 23:00 | 10 |

Przekroczenie terminu o n zajęć wiąże się z karą:

- punkty uzyskania za realizację zadania są dzielone przez 2^n.

Zadanie:
Jesteś osobą odpowiedzialną za stworzenie corowej funkcjonalności aplikacji bankowej.
Pierwszym zadaniem jest stworzenie funkcjonalności zakładania konta bankowego. W celu zoptymalizowania procesu developmentu wybierasz metodologie TDD.

Zaimplementuj poniże funkcjonalności używając TDD. 

Feature 1:
System powinien umożliwiać stworzenie osobistego konta bankowego.
Konto powinno posiadać następujące parametry:
- imię i nazwisko właściciela (podawane w trakcie tworzenia konta)
- saldo (początkowe saldo dla wszystkich kont wynosi 0)

*Podpowiedź*:
Proszę sklonować swoje repozytorium:
```
git clone nazwa_repo
```
Proszę stworzyć swojego feature brancha
```
git checkout -b feature_1
```
Aby wykonać testy:
```
python3 -m unittest
```
Testy będą "czerwone" z errorem:
*__init__() takes 1 positional argument but 3 were given'*

Proszę dopisać kod w pliku Konto.py tak aby testy przechodziły.
**Proszę zrobić push swojej zmiany oraz stworzyć PR do brancha main oraz przypisać mnie (konrad-sol) do review.**

Proszę zastanowić się co można poprawić w naszym teście.
Proszę zastanowić się nad testem do kolejnego feature.
Gdy PR będzie zmergowany proszę stworzyć nowego brancha:
```
git checkout -b lab2
```
Po zakończeniu wszystkich features proszę ponownie wystawić PR.

Feature 2:
Okazało się że imię i nazwisko nie są unikatowymi wartościami pozwalającymi zidentyfikować właściciela konta.
Musimy dodać zmienną wejściową niezbędną do tworzenia konta - numer PESEL. Konto powinno przechowywać podany PESEL.

Feature 3:
Problem: Nasi użytkownicy podają zbyt krótkie lub zbyt długie numery PESEL. 
Musimy dodać funkcjonalność która sprawdzi czy podany PESEL ma dokładnie 11 znaków. Jeżeli nie ma, w zmiennej *pesel* powinniśmy przechowywać informację "Niepoprawny pesel!"

Feature 4:
By zwiększyć sprzedaż zakładanych kont zespół sprzedaży rozpoczął akcje promocyjną.
Jeżeli przy zakładaniu konta użytkownik poda kod rabatowy w postaci PROM_XYZ (gdzie XYZ to dowolne znaki) do nowo utworzonego konta dodajemy 50zł. Kod rabatowy nie jest obowiązkowy do założenia konta.

*Podpowiedź*:
Jeżeli zmienna nie jest obowiązkowa – w definicji konstruktora możemy ustawić default na None.

Proszę skupić się możliwych scenariuszach, napisać testy i na końcu dokonać zmian w programie.

Feature 5:
W rezultacie akcji promocyjnej konto było bardzo popularne wśród seniorów. Bank jest teraz na skraju bankructwa. Musimy ograniczyć promocję – od teraz tylko osoby urodzone po roku 1960 roku życia otrzymają 50zł przy zakładaniu konta z uzyciem kodu.

Podpowiedź:
Rok urodzenia ukryty jest w numerze PESEL.

Znów, proszę najpierw skupić się na testach.

Podpowiedź 2: Może warto dodatkową logikę przenieść do oddzielnej metody?

Po zakończeniu proszę wystawić PR i przypisać mnie do review.
By uzyskać pełną ilość punktów (10) PR powinien być wsyatwiony do 26.10.2022 do godziny 23:00.

 
Kontynuujemy nasze zadanie z aplikacja bankową.
Proszę pamiętać o tym że aplikacje implementujemy w metodologii TDD (zawsze zaczynamy od
pisania testów).
Proszę stworzyć nowy branch (odbić się od main) i po zrobieniu wszystkich zadań wystawić PR,
dodać mnie (konrad-sol) do review. Termin wystawienia PR to 02.11.2022 23:00.
Feature 6 Przelewy:
Podstawowym zadaniem konta bankowego jest dokonywanie i otrzymywanie przelewów.
Musimy zaimplementować mechanizm odpowiedzialny za księgowanie przelewów
wychodzących i przychodzących.
Na chwile obecną interesuje nas tylko kwota przelewu.
Podpowiedź 1: co powinno zmienić się na naszym koncie po wykonaniu przelewu?
Podpowiedź 2: żeby zachować porządek proszę utworzyć nową klasę z testami
Podpowiedź 3: jaki musi być spełniony warunek, aby użytkownik mógł dokonać przelewu
wychodzącego?
Feature 7 Konta firmowe:
Nasz bank chce wprowadzić ofertę kont firmowych. Konto firmowe na chwile obecną będzie
różnić się tym że zamiast:
- imienia, nazwiska, peselu
konto powinno przechowywać:
- nazwę firmy i NIP.
Konta firmowe nie są objęte promocją.
W przypadku gdy NIP ma długość inną niż 10 cyfr – w polu NIP zapiszemy wiadomość
„Niepoprawny NIP!”.
Podpowiedź: proszę pamiętać, że programujemy obiektowo.
Feature 8 Przelew ekspresowy:
Nasz bank wprowadza „przelew ekspresowy”, opłat za zaksięgowanie takiego przelewu
wychodzącego to dla kont zwykłych 1zł, a dla kont biznesowych 5zł. Opłata pomniejsza saldo na
koncie. Opłata pobierana jest w tym samym momencie co kwota przelewu. W tym wypadku
saldo może zejść poniżej 0 (maksymalnie o kwotę opłaty).