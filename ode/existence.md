# Existenz und Eindeutigkeit von Lösungen

Bisher haben wir uns vornehmlich um analytische Lösungsverfahren für lineare gewöhnliche Differentialgleichungen erster Ordnung beschäftigt.
Dabei haben wir theoretische Überlegungen zur Existenz und Eindeutigkeit von Lösungen allgemeiner gewöhnlicher Differentialgleichungen vernachlässigt.
Daher wollen wir uns in diesem Abschnitt den notwendigen und hinreichenden Bedingungen widmen, die uns sagen wann eine Differentialgleichung lösbar ist und wann ihre Lösung sogar eindeutig ist.

Da wir in Kapitel {ref}`s:dgl_hoehere_ordnung` gesehen haben, dass sich beliebige gewöhnliche Differentialgleichungen höherer Ordnung in ein Differentialgleichungssystem erster Ordnung transformieren lassen, beschränken wir uns auf diese Differentialgleichungssysteme.
Dies motiviert die folgende Definition.

````{prf:definition} Differentialgleichungssystem erster Ordnung
:label: def:dglsystem_erster_ordnung

Sei $G\subset\R\times\R^n$ eine offene Teilmenge und

\begin{align*}
f\colon G \ &\to \ \R^n, \\
(x,y) \ &\mapsto \ f(x,y)
\end{align*}

eine vektorwertige stetige Funktion.

Dann nennt man die folgende Gleichung

\begin{equation*}
y^\prime(x)  \ = \ f(x,y(x))
\end{equation*}

ein _System von $n$ Differentialgleichungen erster Ordnung_.
Eine Lösung dieser Gleichung ist eine auf dem offenen Intervall $I\subset \R$ total differenzierbare Funktion $\varphi\colon I\to\R^n$, für die die folgenden Eigenschaften gelten:

* Der Graph $\Gamma_\varphi$ von $\varphi$ liegt in der Teilmenge $G$, d.h,
\begin{equation*}
\Gamma_\varphi \ \coloneqq  \ \lbrace (x,y)\in I\times \R^n~\vert~ y=\varphi(x)\rbrace \, \subset \, G.
\end{equation*}

* Die Funktion $\varphi$ erfüllt die Gleichung

\begin{equation*}
\varphi^\prime(x) \: = \: f(x, \varphi(x))\qquad \text{für alle} \ x\in I.
\end{equation*}

````

````{prf:remark}
Im Gegensatz zu vorigen Abschnitten handelt es sich in Definition {prf:ref}`def:dglsystem_erster_ordnung` nicht um eine Differentialgleichung einer skalarwertigen Funktion sondern um ein Differentialgleichungssystem einer vektorwertigen Funktion.
Wir können die vektorwertigen Funktionen $y$ und $f$ also komponentenweise notieren als
\begin{equation*}
y (x) \ = \ \left(\begin{array}{c}y_1(x)\\\vdots\\y_n(x)\end{array}\right) \qquad\text{und}\qquad f(x,y) \ = \ \left(\begin{array}{c}
f_1(x,y) \\\vdots\\f_n(x,y) \end{array}\right),
\end{equation*}
was zu folgendem Differentialgleichungssystem erster Ordnung führt:
\begin{equation*}
\left\{\begin{array}{c}
y_1^\prime(x) \, = \, f_1 (x, y_1(x), \ldots, y_n(x)),\\
y_2^\prime(x) \, = \, f_2 (x, y_1(x), \ldots, y_n(x)),\\
\ldots\\
y_n^\prime(x) \, = \, f_n (x, y_1(x), \ldots, y_n(x)).
\end{array}\right.
\end{equation*}
````

Der folgende Satz charakterisiert die Lösung eines Differentialgleichungssystems mit Anfangswertbedingungen als Lösung einer zugehörigen Integralgleichung.

````{prf:theorem} Integralgleichung
:label: satz:ode_integralgleichung

Sei $G\subset \R\times \R^n$ eine offene Teilmenge, $I \subset R$ ein offenes Intervall und sei $f\colon G\to\R^n$ eine stetige Abbildung.
Weiter seien die Anfangwerte $(x_0,c)\in G$ mit $x_0 \in I$ gegeben.
Sei nun $\varphi\colon I\to \R^n$ eine total differenzierbare Funktion, deren Graph in $G$ enthalten ist

Die Funktion $\varphi$ ist genau dann eine Lösung der Differentialgleichung
\begin{equation*}
y^\prime(x) \ = \ f(x,y(x))
\end{equation*}
unter der Anfangswertbedingung $\varphi(x_0) = c$, wenn sie die folgende Integralgleichung erfüllt:

```{math}
:label: eq:ode_integralgleichung
\varphi(x) \ = \ c + \int\limits_{x_0}^x f(t,\varphi(t))\,\mathrm{d}t \qquad \text{für alle } \ x\in I.
```

````

````{prf:proof}
Wir zeigen zunächst die Rückrichtung des Satzes. 
Sei also die Integralgleichung {eq}`eq:ode_integralgleichung` erfüllt.
Für die Anfangswertbedingung setzen wir $x = x_0$ und sehen somit, dass $\varphi(x_0) = c$ gilt.
Da die Funktion $f$ nach Voraussetzung stetig ist, folgt aus dem Hauptsatz der Integral- und Differentialrechnung Kapitel 7.2 {cite:p}`burger_2020`, dass
\begin{equation*}
\frac{\mathrm{d}}{\mathrm{d}x} \int_{x_0}^x f(t, \varphi(t)) \, \mathrm{d}t \ = \ f(x, \varphi(x)).
\end{equation*}
Damit folgt aus der Definition der Funktion $\varphi$ in {eq}`eq:ode_integralgleichung`, dass $\varphi$ total differenzierbar ist und die gewöhnliche Differentialgleichung $\varphi'(x) = f(x, \varphi(x))$ erfüllt.

Für die Hinrichtung des Beweises nehmen wir an, dass die Funktion $\varphi$ eine Lösung der gewöhnlichen Differentialgleichung $\varphi'(x) = f(x, \varphi(x))$ ist, total differenzierbar sei und die Anfangswertbedingung $\varphi(x_0) = c$ erfülle.
Dann können wir das folgende Integral betrachten und erhalten aus dem Hauptsatz der Integral- und Differentialrechnung:
\begin{equation*}
\int_{x_0}^x f(t, \varphi(t)) \, \mathrm{d}t \ = \ \int_{x_0}^x \varphi'(t) \, \mathrm{d}t \ = \ \varphi(x) - \varphi(x_0) \ = \ \varphi(x) - c.
\end{equation*}
Durch Umstellen von $c$ auf die linke Seite erhält man die Identität der Integralgleichung in {eq}`eq:ode_integralgleichung`.
````

Das folgende Lemma liefert uns ein hinreichendes Kriterium für die Lipschitz-Stetigkeit einer Funktion.
Diese Eigenschaft wird für die Existenz und Eindeutigkeit von Lösungen gewöhnlicher Differentialgleichungen entscheidend sein.

````{prf:lemma}
:label: lem:ode_lokalLipschitz

Sei $G\subset \R\times\R^n$ eine offene Teilmenge und $f\colon G\to\R^n$ eine bezüglich der Variablen $y=(y_1,\ldots,y_n)$ stetig partiell differenzierbare Funktion.

Dann ist die Funktion $f$ lokal Lipschitz-stetig in $G$ bezüglich des $y$-Variable.
````

````{prf:proof}
Sei $(a,b) \in G$ ein beliebiger Punkt.
Dann existiert ein $r > 0$, so dass die kompakte Menge
\begin{equation*}
B_r(a,b) \ \coloneqq \ \lbrace (x,y) \in \R \times \R^n \: \colon \: |x - a| \leq r, \ ||y - b|| \leq r \rbrace
\end{equation*}
ganz in $G$ liegt.
Da nach Voraussetzung alle Komponenten der Jacobi-Matrix $J \coloneqq (\frac{\partial f_i}{\partial y_j})_{1 \leq i,j \leq n}$ stetige Funktionen sind, können wir eine Konstante $L \in R_0^+$ finden mit
\begin{equation*}
L \ \coloneqq \ \sup_{(x,y) \in B_r(a,b)} \left\Vert J(x,y) \right\Vert \ < \ +\infty.
\end{equation*}

Aus einer Folgerung des Mittelwertsatzes in {prf:ref}`thm:meanest` folgt für alle $(x,y), (x,\tilde{y}) \in B_r(a,b)$, dass gilt
\begin{equation*}
||f(x,y) - f(x,\tilde{y})|| \ \leq \ L \cdot ||y - \tilde{y}||.
\end{equation*}
````

Nun sind wir in der Lage die hinreichenden Bedingungen für die Eindeutigkeit von Lösungen gewöhnlicher Differentialgleichungen zu formulieren.

````{prf:theorem} Eindeutigkeitssatz
:label: satz:ode_eindeutigkeitssatz

Sei $G\subset \R\times\R^n$ eine offene Teilmenge und sei $f\colon G\to\R^n$ eine stetige Funktion, die lokal Lipschitz-stetig in $G$ bezüglich der $y$-Variablen ist.
Seien nun $\varphi,\vartheta\colon I\to \R^n$ zwei Lösungen der Differentialgleichung
\begin{equation*}
y^\prime(x) \, = \, f(x,y(x)) \qquad \text{ für alle } x\in I.
\end{equation*}

Stimmen die beiden Lösungen der Differentialgleichung in einem Punkt $x_0 \in I$ überein, d.h., es gilt $\varphi(x_0) \, = \, \vartheta(x_0)$,
so folgt schon
\begin{equation*}
\varphi(x) \, = \, \vartheta(x)\qquad \text{ für alle } x\in I.
\end{equation*}
````

````{prf:proof}
Wir beginnen zunächst damit die Eindeutigkeit von Lösungen in einer lokalen $\epsilon$-Umgebung zu zeigen.
Sei $x_0 \in I$ ein Punkt, so dass für die beiden Lösungen $\varphi, \vartheta \colon I \rightarrow \R^n$ der gewöhnlichen Differentialgleichung gilt $\varphi(x_0) = \vartheta(x_0)$.
Auf Grund der Integraldarstellung in Satz {prf:ref}`satz:ode_integralgleichung` folgt nun

```{math}
:label: eq:ode_eindeutigkeit_integralgleichung
\varphi(x) - \vartheta(x) \ = \ \int_{x_0}^x f(t, \varphi(t)) - f(t, \vartheta(t)) \, \mathrm{d}t.
```
Da $f$ nach Voraussetzung lokal Lipschitz-stetig bezüglich der $y$-Variablen ist, existieren Konstanten $L \geq 0$ und $\delta > 0$, so dass für alle $t \in I \cap B_\delta(x_0) \coloneqq \lbrace t \in I \colon |t - x_0| < \delta \rbrace$ gilt:

```{math}
:label: eq:ode_eindeutigkeit_lipschitz
||f(t, \varphi(t)) - f(t, \vartheta(t))|| \ \leq \ L \cdot ||\varphi(t) - \vartheta(t)||.
```

Wir definieren nun die zwei Variablen
\begin{equation*}
\epsilon \, \coloneqq \, \min( \delta, \frac{1}{2L} ) \quad \text{ und } \quad M \, \coloneqq \, \sup\{ ||\varphi(x) - \vartheta(x)|| \, \colon \, x \in I \cap B_\epsilon(x_0) \}.
\end{equation*}
Aus Gleichung {eq}`eq:ode_eindeutigkeit_integralgleichung` und {eq}`eq:ode_eindeutigkeit_lipschitz` können wir nun für alle $x \in I \cap B_\epsilon(x_0)$ folgern
\begin{equation*}
||\varphi(x) - \vartheta(x)|| \ \leq \ L \cdot \left| \int_{x_0}^x ||\varphi(t) - \vartheta(t)||\, \mathrm{d}t \, \right| \ \leq \ L \cdot |x - x_0| \cdot M \ \leq \ \frac{M}{2}.
\end{equation*}
Da diese Abschätzung auch für den Punkt $x \in I \cap B_\epsilon(x_0)$ gilt, für den das Supremum $M$ angenommen wird, folgt also $M \leq \frac{M}{2}$.
Dies ist jedoch nur möglich, wenn $M=0$ gilt, d.h., wenn die Funktionen $\varphi$ und $\vartheta$ in $I \cap B_\epsilon(x_0)$ übereinstimmen.

Basierend auf obigem Resultat zeigen wir nun, dass $\varphi(x) = \vartheta(x)$ für alle $x \in I$ mit $x \geq x_0$ gilt.
Der Beweis für den Fall $x \leq x_0$ funktioniert analog und wird daher nicht näher diskutiert.
Wir definieren zunächst den am weitest rechts liegenden Punkt $\xi \in I$, so dass die Funktionen $\varphi$ und $\vartheta$ noch übereinstimmen durch
\begin{equation*}
x_1 \ \coloneqq \ \sup\, \{ \xi \in I \: \colon \: \varphi|_{[x_0, \xi]} \equiv \vartheta|_{[x_0, \xi]} \}.
\end{equation*}

Falls $x_1 = \infty$ oder gleich dem rechten Rand des Intervalls $I$ gilt, so ist die Aussage bereits bewiesen.
Nehmen wir also an, dass ein Punkt $x_1 \in I$ existiert bis zu dem die Funktionen $\varphi$ und $\vartheta$ übereinstimmen und darüber hinaus ein $\delta > 0$ existiert, so dass $[x_1, x_1 + \delta] \subset I$ gilt.
Nach Voraussetzung wissen wir nun, dass $\varphi(x_1) = \vartheta(x_1)$ gilt und die Funktionen stetig sind.
Nun wissen wir aus dem ersten Teil des Beweises, dass ein $\epsilon > 0$ existiert, so dass gilt
\begin{equation*}
\varphi(x) \ = \ \vartheta(x) \qquad \text{ für alle } x \in I \cap B_\epsilon(x_1).
\end{equation*}
Das widerspricht jedoch offensichtlich der Definition von $x_1 \in I$.
Daher gilt also $\varphi(x) = \vartheta(x)$ für alle $x\in I$ mit $x \geq x_0$.
````

Um zu verstehen, wann die Lösung einer gewöhnlichen Differentialgleichung nicht eindeutig ist, diskutieren wir im Folgenden ein Gegenbeispiel.

````{prf:example}
Wir betrachten die folgende nichtlineare gewöhnliche Differentialgleichung

```{math}
:label: eq:bsp_dgl_nichteindeutig
y^\prime(x) \ = \ (y(x))^{\frac23}.
```
Wie man sofort einsieht ist eine spezielle Lösung der Differentialgleichung gegeben durch
\begin{equation*}
\varphi_0(x) \ \equiv \ 0, \qquad \text{ für alle } x\in\R.
\end{equation*}
Da die Differentialgleichung separierbar ist, lassen sich die Lösungen unter der Annahme $y\neq 0$ mit Hilfe von Satz {prf:ref}`satz:ode_getrennteVariablen` bestimmen.

Man sieht aber auch leicht, dass für beliebiges $a\in\R$ die Funktion $\vartheta_a\colon\R\to\R$ mit
\begin{equation*}
\vartheta_a(x) \ \coloneqq \ \frac1{27}(x-a)^3
\end{equation*}
die gewöhnliche Differentialgleichung {eq}`eq:bsp_dgl_nichteindeutig` erfüllt, denn es gilt
\begin{equation*}
\vartheta'_a(x) \ = \ \frac19(x-a)^2 \ = \ \left(\frac1{27}(x-a)^3\right)^{\frac{2}{3}} \ = \ \vartheta_a(x)^{\frac23}.
\end{equation*}

Obwohl die Lösung $\varphi$ und $\vartheta_0$ im Punkt $x_0 = a$ übereinstimmen mit
\begin{equation*}
\varphi_0(a) \, = \, \vartheta_a(a) \, = \, 0,
\end{equation*}
sieht man ein, dass der der Eindeutigkeitssatz {prf:ref}`satz:ode_eindeutigkeitssatz` nicht gilt.
Der Grund hierfür ist eine Verletzung der Voraussetzungen des Satzes, denn die Funktion $f(x,y) \coloneqq y^{\frac23}$ ist nicht für alle Punkte $y\in \R$ bezüglich der $y$-Variable Lipschitz-stetig.
Zwar ist $f$ für $y\neq 0$ stetig partiell differenzierbar bezüglich der Variablen $y$ mit
\begin{equation*}
\frac{\partial f}{\partial y}(x,y) \ = \ \frac23 y^{-\frac13}.
\end{equation*}
Nach Lemma {prf:ref}`lem:ode_lokalLipschitz` ist $f$ somit lokal Lipschitz-stetig in ganz $\R\times \R\setminus \{0\}$ in Bezug auf die $y$-Variable.
Jedoch ist $f$ in keiner Umgebung eines Punktes $(a,0)$ Lipschitz-stetig bezüglich de $y$-Variablen, da dieser Punkt eine Singularität mit unendlicher Steigung darstellt.
````

Der folgende wichtige Satz formuliert die hinreichenden Bedingungen für die Existenz von Lösungen einer gewöhnlichen Differentialgleichung.

````{prf:theorem} Existenzsatz von Picard-Lindelöf
:label: satz:ode:picardlindeloef

Sei $G\subset \R\times\R^n$  eine offene Teilmenge und sei $f\colon G\to\R^n$ eine stetige Funktion, die lokal Lipschitz-stetig auf $G$ bezüglich der $y$-Variablen ist.
Dann existiert zu jedem Anfangswert $(x_0,c) \in G$ ein $\varepsilon>0$, sowie eine Lösung
\begin{equation*}
\varphi \colon \left[x_0-\varepsilon, x_0+\varepsilon\right] \to \R^n
\end{equation*}
der gewöhnlichen Differentialgleichung 
\begin{equation*}
y^\prime(x) \ = \ f(x,y(x))
\end{equation*}
unter der Anfangsbedingung $\varphi(x_0)=c$.
````

````{prf:proof}
Siehe §12, Satz 4 {cite:p}`forster`.
````

Selbst wenn die Funktion $f$ der Differentialgleichung $y^\prime(x) = f(x,y(x))$ auf ganz $\R\times\R^n$ definiert ist und überall lokal Lipschitz-stetig bezüglich der $y$-Variablen ist, so kann eine Lösung, die die Anfangsbedingung $\varphi(x_0)=c$ erfüllt unter Umständen nur in einer sehr kleinen Umgebung von $x_0 \in \R$ definiert sein.
Dies wird durch das folgende Beispiel klar.

````{prf:example}
Wir betrachten die folgende nichtlineare gewöhnliche Differentialgleichung erster Ordnung
\begin{equation*}
y^\prime(x) = 2x\cdot (y(x))^2\,.
\end{equation*}
Die Funktion $f(x,y) = 2xy^2$ ist offensichtlich auf ganz $\R\times\R$ definiert und stetig partiell differenzierbar bezüglich der Variable $y$ und somit nach Lemma  {prf:ref}`lem:ode_lokalLipschitz` lokal Lipschitz-stetig bezüglich der $y$-Variablen.

Wir suchen eine Lösung $\phi \colon \R \rightarrow \R$ der Differentialgleichung, die die Anfangswertbedingung $\varphi(0) = c$ erfüllt.
Für den Fall $c=0$ ist dies offensichtlich die konstante Funktion $\varphi(x) \equiv 0$ für alle $x\in\R$.
Für $c\neq0$ können wir die Lösung durch Trennung der Variablen (siehe Kapitel {ref}`s:trennung_variablen`) wie folgt unter der Annahme $y(x) \neq 0$ berechnen:
\begin{align*}
y' \ = \ \frac{\mathrm{d}y}{\mathrm{d}x} \ &= \ 2xy^2 \\
\Rightarrow \quad \frac{1}{y^2}\, \mathrm{d}y \ &= \ 2x\, \mathrm{d}x\,,\\
\Rightarrow \quad \int\limits_c^y\frac{1}{\eta^2}\, \mathrm{d}\eta \ &= \ \int\limits_0^x 2\xi\,\mathrm{d}\xi,\\
\Rightarrow \quad -\frac1y+\frac1c \ &= \ x^2\,,\\
\Rightarrow \quad \varphi(x) \ \coloneqq \ y \ &= \ \frac1{\gamma - x^2},\qquad \text{ mit } \ \gamma \, \coloneqq \, \frac{1}{c}.
\end{align*}
Dies ist die Lösung der gewöhnlichen Differentialgleichung unter der Anfangswertbedingung $\varphi(0)=c$, was man direkt durch Einsetzen verifizieren kann.

Falls $c>0$ gilt, so ist der maximale Definitionsbereich dieser Lösung gegeben durch
\begin{equation*}
I_c \ \coloneqq \ \left\{x\in\R~\colon~\vert x\vert < \sqrt{\gamma}=c^{-\frac12}\right\}\,.
\end{equation*}
Nähert sich $x$ von innen dem Rand des Intervalls $I_c$, so strebt der Funktionswert der Lösung gegen $+\infty$.
Für $c<0$ ist die Lösung hingegen auf ganz $\R$ definiert.
````
