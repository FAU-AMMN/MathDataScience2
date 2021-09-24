(s:partielle_ableitungen)=
# Partielle Integration

Aus der Produktregel in Satz {prf:ref}`satz:produktregel` können wir eine Regel für die _Partielle Integration_ ableiten:

````{prf:theorem} Partielle Integration
:label: satz:partielle_integration

Seien $f,g\colon[a,b]\to\R$ stetig differenzierbare Funktionen.
Dann gilt die folgende Rechenregel der partiellen Integration:
```{math}
:label: eq:partielle_integration
  \int_a^b f(x)g'(x)\,\mathrm{d}x \ = \ (f\cdot g)\Big\vert_a^b \, - \, \int_a^b f'(x) g(x)\,\mathrm{d}x\,.
```
````

````{prf:proof}
Siehe Satz 7.13 {cite:p}`burger_2020`
````

````{prf:remark}
Um die Stammfunktion $F$ einer Funktion $f$ mit $F'(x) = f(x)$ zu bestimmen, betrachten wir ein unbestimmtes Integral ohne Grenzen
\begin{equation*}
F(x) \ = \ \int f(x)\, \mathrm{d}x.
\end{equation*}
Wir können dann mittels der Produktregel der Differentiation in Satz \ref{satz:produktregel} eine Stammfunktion der Form $F(x) = (f \cdot g)(x)$ bestimmen als
```{math}
:label: eq:partInt_unbestimmt
\begin{split}
F(x) \ &= \ (f \cdot g)(x)  \ = \ \int (f \cdot g' + f' \cdot g)(x)\,\mathrm{d}x\\
 \ &= \ \int f(x) \cdot g'(x)\,\mathrm{d}x + \int f'(x) \cdot g(x)\,\mathrm{d}x.
 \end{split}
```

````

Das folgende Beispiel wendet die Regel der partiellen Integration an.

````{prf:example}
:label: bsp:partielle_integration

Wir wenden die partielle Integration im Folgenden für zwei verschiedene Fälle an.
Zuerst wollen wir eine Stammfunktion herleiten und danach ein Integral berechnen.

* Wir wollen eine Stammfunktion des natürlichen Logarithmus $\ln \colon \R^+ \rightarrow \R$ herleiten.
Wir können in diesem Fall zwei Funktionen $f$ und $g$ so definieren, dass wir die Rechenregel für partielle Integration in Satz {prf:ref}`satz:partielle_integration` anwenden können.
Sei also $f(x) \coloneqq \ln(x)$ und $g(x) \coloneqq x$ gewählt, dann gilt offensichtlich, dass $g'(x) \equiv 1$ konstant ist.
Stellen wir die Formel {eq}`eq:partInt_unbestimmt` geeignet um und setzen diese Funktionen ein, so erhalten wir
\begin{align*}
  \int\ln(x)\cdot 1\,\mathrm{d}x \ &= \ \int f(x)g'(x)\, \mathrm{d}x \ = \ (f\cdot g)(x) - \int f^\prime(x)g(x)\,\mathrm{d}x \\
  \ &= \ \ln(x) \cdot x - \int \frac{1}{x} \cdot x\, \mathrm{d}x \ = \ \ln(x) \cdot x - x + C.
\end{align*}

* Wir wollen das Integral der Arkussinus Funktion 
\begin{equation*}
\arcsin \colon [-1, 1] \rightarrow [-\frac{\pi}{2}, \frac{\pi}{2}]
\end{equation*}
in einem Intervall $[0, y]$ mit $0 < y \leq 1$ berechnen.

Wir können in diesem Fall zwei Funktionen $f$ und $g$ so definieren, dass wir die Rechenregel für partielle Integration in Satz {prf:ref}`satz:partielle_integration` anwenden können.
Sei also $f(x) \coloneqq \arcsin(x)$ und $g(x) \coloneqq x$ gewählt, dann gilt offensichtlich, dass $g'(x) \equiv 1$ konstant ist.
Setzen wir dies in {eq}`eq:partielle_integration` ein, erhalten wir
\begin{align*}
  \int_0^y\arcsin(x)\cdot 1\,\mathrm{d}x \ &= \ \int_0^y f(x)g'(x)\, \mathrm{d}x \ = \ (f\cdot g)\Big\vert_0^y-\int_0^yf^\prime(x)g(x)\,\mathrm{d}x \\
  \ &= \ y \cdot \arcsin(y) - \int_0^y \frac{x}{\sqrt{1-x^2}}\, \mathrm{d}x.
\end{align*}
Das zweite Integral in dieser Gleichung, wollen wir zunächst so hinnehmen.
Im folgenden Abschnitt werden wir eine praktische Integrationsregel, genannt _Substitutionsregel_, einführen mit der sich dieses Integral einfach berechnen lässt.
````
