
# Sterowanie quadrocopterem z wykorzystaniem regulatora LQR

Projekt zrealizowany w ramach pracy inżynierskiej na kierunku **Robotyka i Automatyka** na Politechnice Warszawskiej. Obejmuje modelowanie dynamiki quadrocoptera, implementację regulatora liniowo-kwadratowego (LQR) oraz symulacyjną ocenę śledzenia zadanych trajektorii w **GNU Octave**.

**Autor:** Paweł Marton  
**Promotor:** dr inż. Franciszek Dul  
**Rok:** 2024

## Cel projektu

Celem było sprawdzenie możliwości wykorzystania regulatora LQR do sterowania quadrocopterem poruszającym się w ograniczonej przestrzeni, w pobliżu zadanej trasy. Badania obejmowały dobór nastaw regulatora, wpływ prędkości referencyjnej na dokładność ruchu oraz reakcję układu na turbulencje.

## Zakres realizacji

- Wyprowadzenie modelu matematycznego ruchu quadrocoptera na podstawie równań dynamiki i kinematyki bryły sztywnej.
- Uwzględnienie sił zewnętrznych oraz modelu napędu.
- Linearyzacja modelu na potrzeby projektowania regulatora LQR.
- Implementacja modelu i układu regulacji w GNU Octave.
- Iteracyjny dobór macierzy wag **Q** i **R**.
- Symulacja lotu po dwóch zdefiniowanych trasach.
- Analiza wpływu prędkości zadanej i turbulencji na jakość regulacji.

## Sterowanie

Regulator wyznacza sterowanie na podstawie wektora uchybów stanu:

$$
u = -K e
$$

gdzie **K** oznacza macierz wzmocnień regulatora, a **e** uwzględnia różnice między zadanymi i aktualnymi położeniami oraz prędkościami liniowymi, a także kąty orientacji i prędkości kątowe.

Macierze **Q** i **R** określają wagi uchybów stanu i sygnałów sterujących. Ich dobór przeprowadzono iteracyjnie, analizując przebiegi lotu i wskaźniki jakości regulacji.

## Badania symulacyjne

| Obszar badań | Zakres |
| --- | --- |
| Dobór nastaw | Analiza wpływu zmian macierzy Q i R na ruch drona |
| Śledzenie trasy | Dwie zadane trajektorie lotu |
| Prędkość referencyjna | Testy w zakresie 0,1–0,3 m/s |
| Zakłócenia | Turbulencje włączane na wybranym odcinku lotu |

Jakość regulacji oceniano na podstawie średniego i maksymalnego odchylenia od położenia referencyjnego w płaszczyźnie YZ oraz średniego uchybu prędkości. Analizowano również wykresy uzyskanych trajektorii.

## Najważniejsze wnioski

- Dobrane nastawy LQR umożliwiły odwzorowanie obu zadanych tras w badanych warunkach bez turbulencji.
- Zwiększanie prędkości referencyjnej pogarszało dokładność regulacji; dalsze zwiększanie prędkości wymagałoby ponownego doboru nastaw.
- Testy turbulencji wykazały ograniczoną odporność dobranego układu: występowały duże odchylenia od trajektorii, a w jednym z opisanych przebiegów utrata sterowności.
- Wyniki potwierdzają znaczenie doboru wag Q i R oraz testowania regulatora poza nominalnymi warunkami pracy.

## Narzędzia i zagadnienia

**GNU Octave · LQR · modelowanie dynamiki · linearyzacja · sprzężenie zwrotne · symulacja numeryczna · analiza jakości regulacji**

## Ograniczenia

Projekt ma charakter symulacyjny. Wyniki odnoszą się do przyjętego modelu, dwóch tras i wybranych nastaw regulatora. Nie stanowią potwierdzenia działania na rzeczywistym dronie ani odporności na dowolne zakłócenia. Iteracyjne strojenie wag nie gwarantuje najlepszego możliwego zestawu nastaw dla rozpatrywanego zadania.

## Praca inżynierska

**„Sterowanie dronem wielowirnikowym z wykorzystaniem regulatora liniowo-kwadratowego”**, Paweł Marton, Politechnika Warszawska, Wydział Mechaniczny Energetyki i Lotnictwa, 2024.
