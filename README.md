
Projekt czerpie z tabeli googleplaystore.csv gdzie można pobrać ze strony: https://www.kaggle.com/datasets/lava18/google-play-store-apps?resource=download


1. Cel i Zakres Projektu

Głównym technicznym było zbudowanie modelu Machine Learning (ML), który potrafi przewidzieć popularność aplikacji na podstawie jej cech (Cena, Rozmiar, Kategoria, Liczba Recenzji, Ocena).

2. Przygotowanie i Czyszczenie Danych (Data Preprocessing)

Zbiór danych (googleplaystore.csv) wymagał czyszczenia przed przystąpieniem do analizy. Wykonano następujące operacje:

-Konwersja Installs: Usunięto znaki + oraz , i przekonwertowano dane na liczby całkowite. Jest to nasza zmienna celu (target), którą przewidujemy.

-Obsługa Size: Skonwertowano wartości tekstowe (np. "19M", "500k") na liczby (bajty).

-Obsługa Price: Usunięto znak $ i zamieniono na typ float.

-Braki danych (NaN)

3. Metodologia i Modele

Zastosowano podejście nadzorowanego uczenia maszynowego (Supervised Learning).
Dane podzielono w stosunku 80% (treningowe) do 20% (testowe).
Wykorzystano przetwarzający dane:

-Cechy liczbowe (Rating, Reviews, Price) poddano standaryzacji (StandardScaler), aby różnice w rzędach wielkości nie zaburzyły modelu.

-Cechy kategoryczne (Category, Type) zakodowano metodą OneHotEncoder.

Porównano dwa algorytmy:

-Regresja Liniowa (Linear Regression)

-Drzewo Decyzyjne (Decision Tree Regressor)

4. Analiza Wyników

Po wytrenowaniu modeli uzyskano następujące wyniki dopasowania (R² Score):

Regresja Liniowa: 0.3045

Drzewo Decyzyjne: 0.8790

Zwycięskim modelem okazało się Drzewo Decyzyjne. Oznacza to, że relacja między cechami aplikacji a liczbą pobrań nie jest w pełni liniowa i wymaga bardziej złożonych reguł decyzyjnych.


Wniosek: Aplikacja z oceną 4.0, ale posiadająca 100 000 recenzji (co świadczy o jej "wirusowości"), osiąga zazwyczaj więcej pobrań niż niszowa aplikacja z idealną oceną 5.0, ale tylko 10 recenzjami. Ocena jest ważna dla jakości, ale to "szum medialny" (ilość recenzji) napędza instalacje.

5. Podsumowanie

Stworzony system pozwala z wysoką skutecznością przewidywać popularność aplikacji.
Hipoteza o kluczowym wpływie oceny została zweryfikowana częściowo negatywnie – ocena ma znaczenie, ale drugorzędne w porównaniu do zasięgu (liczby recenzji) oraz kategorii aplikacji.
