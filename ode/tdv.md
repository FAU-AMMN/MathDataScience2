# Trennung der Variablen

Nachdem wir im letzten Abschnitt einige motivierende Beispiele für gewöhnliche Differentialgleichungen aus der Physik diskutiert haben, wollen wir im Folgenden eine erste Technik zur Bestimmung von Lösungen für bestimmte Spezialfälle herleiten.
Die Methode der Trennung der Variablen, auch Separationsmethode genannt, erlaubt es separierbare Differentialgleichungen erster Ordnung zu lösen.

Hierzu führen wir zunächst den Begriff von separierbaren Differentialgleichungen ein.

````{prf:definition} Separierbare Differentialgleichung
:label: def:ode:getrenntVar

Seien $I,J\subset \R$ zwei offene Intervalle und es seien $f\colon I\to\R$ und $g\colon J\to\R$ zwei stetige Funktionen.
Wir setzen voraus, dass $g(y)\neq 0$ für alle $y\in J$.
Eine gewöhnliche Differentialgleichung erster Ordnung der Form
\begin{equation*}
y^\prime(x) \ = \ f(x) \cdot g(y(x)) \ = \ f(x) \cdot g(y)
\end{equation*}
heißt _separierbare Differentialgleichung_ und wird häufig auch _Differentialgleichung mit getrennten Variablen_ genannt.
````

Der folgende Satz sagt aus unter welchen Voraussetzungen eindeutige Lösungen für separierbare Differentialgleichungen existieren und welche Gestalt diese besitzen.

````{prf:theorem} Trennung der Variablen
:label: satz:ode_getrennteVariablen

Seien $I,J\subset \R$ zwei offene Intervalle und $(x_0, y_0) \in I \times J$ ein beliebiger Punkt. Es seien nun $f\colon I\to\R$ und $g\colon J\to\R$ zwei stetige Funktionen, wobei $g(y)\neq 0$ für alle $y\in J$ gelte.
Wir betrachten die separierbare Differentialgleichung
\begin{equation*}
y^\prime(x) \ = \  f(x) \cdot g(y).
\end{equation*}

Wir definieren außerdem Funktionen $F\colon I\to \R$ und $G\colon J\to\R$ durch
\begin{equation*}
F(x) \ \coloneqq \ \int\limits_{x_0}^x f(t)\,\mathrm{d}t,\qquad G(y) \ \coloneqq \ \int\limits_{y_0}^y \frac{1}{g(s)}\,\mathrm{d}s.
\end{equation*}
Sei nun $I^\prime\subset I$ ein Intervall mit $x_0\in I^\prime$ und $F(I^\prime)\subset G(J)$.
Dann existiert eine eindeutige Lösung $\varphi\colon I^\prime \to\R$ der separierbaren Differentialgleichung mit der Anfangsbedingung $\varphi(x_0) = y_0$.
Die Lösung genügt außerdem der folgenden Beziehung
\begin{equation*}
G(\varphi(x)) \ = \ F(x) \qquad \text{ für alle } \ x\in I^\prime.
\end{equation*}
````

````{prf:proof}
Wir bemerken zunächst, dass wir für $g(y) \neq 0$ für alle $y \in J$ die separierbare Differentialgleichung umschreiben können in
\begin{equation*}
\frac{y'(x)}{g(y)} \ = \ f(x).
\end{equation*}
Außerdem wissen wir, dass die stetige Funktion $g \colon J \rightarrow \R$ entweder positiv mit $g(y) > 0$ oder negativ mit $g(y) < 0$ für alle $y \in J$ sein muss.
Denn ansonsten würde es nach dem Zwischenwertsatz \cite[Satz 5.13]{burger_2020} eine Stelle $y_0 \in J$ geben mit $g(y_0) = 0$, was nach Voraussetzung ausgeschlossen ist.
Damit folgt aber schon, dass die Funktion $G \colon J \rightarrow \R$ mit
\begin{equation*}
G(y) \ = \ \int\limits_{y_0}^y \frac{1}{g(s)}\,\mathrm{d}s
\end{equation*}
streng monoton und somit insbesondere injektiv ist.
Damit existiert also eine Umkehrabbildung $G^{-1} \colon G(J) \rightarrow J$.
Diese Beobachtung können wir im Folgenden ausnutzen.

Zuerst wollen wir die Eindeutigkeit der Lösung zeigen.
Sei also $\varphi \colon I' \rightarrow \R$ eine Lösung der separierbaren Differentialgleichung, dann erfüllt die Lösung offensichtlich
\begin{equation*}
\frac{\varphi'(x)}{g(\varphi)} \ = \ f(x) \qquad \text{ für alle } \ x \in I'.
\end{equation*}
Betrachten wir nun die Funktion $F \colon I \rightarrow \R$ so sehen wir unter Ausnutzung der Substitutionsregel der Integralrechnung aus Satz \ref{satz:substitutionsregel} ein, dass für alle $x \in I'$ gilt
\begin{equation*}
F(x) \ = \ \int_{x_0}^x f(t)\, \mathrm{d}t \ = \ \int_{x_0}^x \frac{\varphi'(t)}{g(\varphi(t))}\, \mathrm{d}t \ = \ \int_{\varphi(x_0)}^{\varphi(x)} \frac{1}{g(s)}\, \mathrm{d}s \ = \ \int_{y_0}^{\varphi(x)} \frac{1}{g(s)}\, \mathrm{d}s \ = \ G(\varphi(x)).
\end{equation*}
Da $G$ eine Umkehrfunktion $G^{-1}$ besitzt können wir die Lösung der separierbaren Differentialgleichung also eindeutig charakterisieren durch
\begin{equation*}
G^{-1}(F(x)) \ = \ \varphi(x) \qquad \text{ für alle } x \in I'.
\end{equation*}

Nun müssen wir nur noch zeigen, dass die Funktion $\varphi \coloneqq G^{-1} \circ F \colon I' \rightarrow \R$ eine Lösung der separierbaren Differentialgleichung darstellt.
Durch Anwendung der Ketten- und Umkehrregel der Differentialrechnung und dem Hauptsatz der Differential- und Integralrechnung gilt für alle $x \in I'$:
\begin{equation*}
\begin{split}
\varphi'(x) \ &= \ (G^{-1} \circ F)'(x) \ = \ (G^{-1})'(F(x)) \cdot F'(x) \ = \ \frac{1}{G'(G^{-1}(F(x)))} \cdot F'(x) \\
\ &= \ \frac{1}{G'(\varphi(x))} \cdot F'(x) \ = \ g(\varphi(x)) \cdot f(x).
\end{split}
\end{equation*}
Außerdem gilt $\varphi(x_0) = y_0$, wie man nachrechnen kann:
\begin{equation*}
\varphi(x_0) \ = \ G^{-1}(F(x_0)) \ = \ G^{-1}\left( \int_{x_0}^{x_0} f(t)\, \mathrm{d}t \right) \ = \ G^{-1}(0) \ = \ y_0.
\end{equation*}
````

Das folgende Beispiel illustriert wie das Verfahren der Trennung der Variablen eingesetzt werden kann, um analytische Lösungen für separierbare Differentialgleichungen zu erhalten.

````{prf:example} Trennung der Variablen
:label: bsp:ode_getrennteVariablen

Betrachten wie die folgende gewöhnliche Differentialgleichung erster Ordnung
\begin{equation*}
y^\prime(x) \ = \ -\frac{y(x)}{x},
\end{equation*}
welche definiert ist für alle $x \in \R \setminus \lbrace 0 \rbrace$ und außerdem linear und homogen ist.
Wir nehmen an, dass die  Anfangsbedingung $y(1)=c$ für eine Konstante $c > 0$ gelte.

Es handelt sich hierbei um eine separierbare Differentialgleichung da wir sie mit getrennten Variablen wie folgt darstellen können:
\begin{equation*}
y^\prime(x) \ = \  f(x) \cdot g(y)\qquad\text{mit}\quad f(x) \, \coloneqq \, -\frac1x\quad\text{und}\quad g(y) \, \coloneqq \, y\,.
\end{equation*}
Nach Satz \ref{satz:ode_getrennteVariablen} berechnen wir nun die Funktionen $F$ und $G$ als
\begin{align*}
F(x) \ &= \ \int\limits_1^xf(t)\,\mathrm{d}t \ = \ -\int\limits_1^x\frac1t\,\mathrm{d}t \ = \ - \log\Big\vert_1^x \ = \ -\log x + \underbrace{\log 1}_{=0} \ = \ -\log x,\\
G(y)\ &= \ \int\limits_c^y\frac1{g(s)}\,\mathrm{d}s \ = \ \int\limits_c^y\frac1s\,\mathrm{d}s \ = \ \log\Big\vert_c^y \ = \ \log(y) - \log(c) \ = \  \log\left(\frac{y}{c}\right).
\end{align*}
Setzen wir den Definitionsbereich $J$ der Funktionen $g$ und $G$ auf $J = \R^+$, wissen wir, dass der Logarithmus $\R_+$ auf ganz $\R$ abbildet und daher können wir den Definitionsbereich $I$ der Funktionen $f$ und $F$ auf $I^\prime = I = \R_+$ setzen.
Offensichtlich gilt $\R^+ = F(I') \subset G(J) = \R$ und somit sind die Voraussetzungen von Satz \ref{satz:ode_getrennteVariablen} erfüllt.

Es existiert also eine auf $\R^+$ definierte eindeutige Lösung $\varphi\colon\R_+\to\R$ mit
\begin{equation*}
\log\frac{\varphi(x)}{c} \ = \ G(\varphi(x)) \ = \ F(x) \ = \ -\log x \qquad \text{ für alle } \ x\in\R_+.
\end{equation*}

Durch Anwendung der Exponentialfunktion auf beiden Seiten der Gleichung erhält man dann die explizite Lösung
\begin{equation*}
\varphi(x) \ = \ \frac{c}{x}\qquad\text{ für alle } \ x\in\R^+.
\end{equation*}
Die Korrektheit der Lösung lässt sich leicht überprüfen, denn es gilt
\begin{equation*}
\varphi'(x) \ = \ \left( \frac{c}{x} \right)' \ = \ - \frac{c}{x^2} \ = \ - \frac{c}{x} \cdot \frac{1}{x} \ = \ - \frac{\varphi(x)}{x}.
\end{equation*}
````

Die Trennung der Variablen lässt sich von Beispiel \ref{bsp:ode_getrennteVariablen} auf allgemeine lineare, homogene Differentialgleichungen erster Ordnung mit beliebiger Koeffizientenfunktion verallgemeinern, wie der folgende Satz zeigt.

````{prf:theorem} Lineare und homogene gewöhnliche Differentialgleichung erster Ordnung
:label: satz:ode_lin_hom

Sei $I \subset \R$ ein offenes Intervall. 
Betrachten wir eine lineare und homogene Differentialgleichung erster Ordnung, die im Allgemeinen von folgender Form ist:
\begin{equation*}
y^\prime(x) \ = \ a(x)\cdot y(x), \quad \text{ für alle } x \in I.
\end{equation*}
Für einen beliebigen Punkt $x_0\in I$ und einen konstanten Anfangswert $c\in\R$ gibt es dann genau eine Lösung $\varphi\colon I\to\R$ der Differentialgleichung, die der Anfangsbedingung $\varphi(x_0) = c$ genügt.
Diese ist für alle $x \in I$ von der Form
\begin{equation*}
\varphi(x) \ \coloneqq \ c \cdot \exp\left(\, \int\limits_{x_0}^xa(t)\,\mathrm{d}t\right).
\end{equation*}
````

````{prf:proof}
Jede homogene lineare Differentialgleichung erster Ordnung ist ein Spezialfall einer separierbaren Differentialgleichung in Satz {prf:ref}`satz:ode_getrennteVariablen` für $f(x) \coloneqq a(x)$ und $g(y) \coloneqq y$.

Zuerst zeigen wir, dass $\varphi$ eine Lösung der Differentialgleichung ist.
Man rechnet leicht nach, dass die Anfangsbedingung erfüllt ist, da
\begin{equation*}
\varphi(x_0) \ = \  c \cdot \exp\left(\, \int\limits_{x_0}^{x_0} a(t)\,\mathrm{d}t\right) \ = \ c \cdot \exp(0) \ = \ c.
\end{equation*}
Außerdem gilt für alle Punkte $x \in I$ 
\begin{equation*}
\varphi^\prime (x) \ = \ c \cdot \left( \exp\left(\, \int\limits_{x_0}^{x} a(t)\,\mathrm{d}t\right) \right)' \ = \ a(x) \cdot c \cdot \exp\left(\, \int\limits_{x_0}^xa(t)\,\mathrm{d}t\right) \ = \ a(x) \cdot  \varphi(x).
\end{equation*}

Um die Eindeutigkeit der Lösung zu beweisen bemerken wir zunächst, dass 
\begin{equation*}
\varphi_0(x) \ \coloneqq \ \exp\left(-\int\limits_{x_0}^x a(t)\,\mathrm{d}t\right)
\end{equation*}
die Differentialgleichung $\varphi_0^\prime (x) = -a(x)\cdot \varphi_0(x)$ löst mit einem analogen Argument wie oben.
Sei nun $\vartheta\colon I\to\R$ eine beliebige Lösung der Differentialgleichung $y^\prime(x) = a(x) \cdot y(x)$ mit den Anfangsbedingungen $\vartheta(x_0)=c$.
Wir bilden nun das Produkt $\vartheta_0(x) \coloneqq\vartheta(x)\cdot \varphi_0(x)$ und differenzieren die Funktion $\vartheta_0$ mit der Produktregel:
\begin{align*}
\vartheta_0^\prime(x) \ &= \ \vartheta^\prime(x) \cdot \varphi_0(x) + \vartheta(x)\cdot \varphi_0^\prime(x)\\
\ &= \ a(x)\cdot \vartheta(x)\cdot \varphi_0(x) - \vartheta(x)\cdot a(x)\cdot \varphi_0(x) \ = \ 0.
\end{align*}
Da dies für alle $x \in I$ gilt muss $\vartheta_0$ somit eine Konstante sein und es gilt
\begin{equation*}
\vartheta_0(x) \ = \ \vartheta_0(x_0) \ = \ \vartheta(x_0)\cdot \varphi_0(x_0) \ = \ c\cdot \exp(0) \ = \ c.
\end{equation*}
Damit folgt nun schließlich aus $\vartheta_0(x) = \vartheta(x)\cdot \varphi_0(x)$ für alle $x\in I$:
\begin{equation*}
\vartheta(x) \ = \ c \cdot \varphi_0(x)^{-1} \ = \ c\cdot \exp\left(\,\int\limits_{x_0}^xa(t)\, \mathrm{d}t\right).
\end{equation*}
Hierbei können wir die Umkehrfunktion $\varphi_0^{-1}$ betrachten, da die Exponentialfunktion streng monoton und somit insbesondere injektiv ist.
````
