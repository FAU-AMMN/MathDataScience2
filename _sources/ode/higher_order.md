
(s:dgl_hoehere_ordnung)=
# Differentialgleichungen höherer Ordnung

Obwohl wir gewöhnliche Differentialgleichungen höherer Ordnung bereits im vorigen Abschnitt erwähnt haben, haben wir diese noch nicht näher diskutiert. Wir wollen im Folgenden ein zusätzliches Kriterium zur Klassifikation von gewöhnlichen Differentialgleichungen einführen und beschreiben, wie sich eine gewöhnliche Differentialgleichung höherer Ordnung in ein System von gewöhnlichen Differentialgleichungen erster Ordnung umformulieren lässt.

Beginnen wir zunächst mit der Definition einer gewöhnlichen Differentialgleichung $n$-ter Ordnung.
Eine Differentialgleichung $n$-ter Ordnung schreibt eine Bedingung für die $n$-te Ableitung der gesuchten Lösung $\varphi$ vor.
Diese $n$-te Ableitung hängt sowohl von $x$ als auch von der Lösung $\varphi$ und ihren Ableitungen bis zur $(n-1)$-ten Ordnung im Punkt $x$ ab.

````{prf:definition} Differentialgleichung $n$-ter Ordnung
Sei $G\subset\R\times\R^n$ eine offene Teilmenge und
\begin{align*}
f\colon G&\to\R
\end{align*}
eine stetige Funktion.


Wir nennen eine Gleichung der Form
\begin{equation*}
y^{(n)}(x) \, = \, f(x,y(x),y^\prime(x), \ldots, y^{(n-1)}(x))
\end{equation*}
eine _explizite_ gewöhnliche Differentialgleichung $n$-ter Ordnung. Ist die gewöhnliche Differentialgleichung nicht nach der höchsten vorkommenden Ableitung aufgelöst, d.h. wenn sie von der folgenden Form ist
\begin{equation*}
f(x,y(x),y^\prime(x), \ldots, y^{(n-1)}(x), y^{(n)}(x)) \, = \, 0,
\end{equation*}
so nennen wir sie eine _implizite_ gewöhnliche Differentialgleichung $n$-ter Ordnung.

Wir nennen eine $n$-mal differenzierbare Funktion $\varphi\colon I\to\R$ auf dem offenen Intervall $I \subset \R$ eine _Lösung der Differentialgleichung_, wenn sie die folgenden Eigenschaften besitzt:

$i)$ Der von der unbekannten Lösung $\varphi$  abhängende Menge
\begin{equation*}
\Gamma_\varphi \ \coloneqq \ \left\{(x,y_1, y_2, \ldots, y_{n})\in I\times \R^n~\Big\vert~y_k = \varphi^{(k-1)}(x), \ 1\leq k\leq n\right\}
\end{equation*}
ist eine Teilmenge von $G$,

$ii)$ Für alle Punkte $x\in I$ gilt
\begin{equation*}
\varphi^{(n)}(x) \ = \ f(x,\varphi (x), \varphi^\prime(x), \ldots, \varphi^{(n-1)}(x))\,.
\end{equation*}
````

Das folgende Beispiel illustriert den Begriff einer gewöhnlichen Differentialgleichung in expliziter und impliziter Form.

````{prf:example}
Sei $I \subset \R$ ein offenes Intervall.
Die Gleichung
\begin{equation*}
y'(x)\cdot y(x) + x \, = \, 0
\end{equation*}
ist eine nichtlineare, implizite gewöhnliche Differentialgleichung erster Ordnung.
Diese Differentialgleichung lässt sich in die folgende explizite Form umschreiben
\begin{equation*}
y'(x) \, = \, -\frac{x}{y(x)}
\end{equation*}
wenn wir annehmen, dass $y(x) \neq 0$ für alle Punkte $x \in I$ gilt.
Aus der Kreisgleichung $x^2 + y^2 = c > 0$ lässt sich eine explizite Lösung dieser gewöhnlichen Differentialgleichung angeben mit
\begin{equation*}
\varphi(x) \ = \ \pm \sqrt{c - x^2}, \qquad \text{für} \ |x| < \sqrt{c}.
\end{equation*}
````

Man kann eine gewöhnliche Differentialgleichung $n$-ter Ordnung in ein System von gewöhnlichen Differentialgleichungen erster Ordnung überführen wie folgende Bemerkung zeigt.
Diese Beobachtung hat den großen Vorteil, dass man sich bei Lösungsmethoden von gewöhnlichen Differentialgleichungen, egal ob analytisch oder numerisch, nur auf das Lösen von Differentialgleichungssystemen erster Ordnung konzentrieren muss.

````{prf:remark}
Sei $G \subset \R \times \R^n$ eine offene Teilmenge und $f\colon G\to\R$  eine stetige Funktion.
Wir betrachten im Folgenden die explizite gewöhnliche Differentialgleichung $n$-ter Ordnung

```{math}
:label: eq:ode:redODEOri
y^{(n)}(x) \, = \, f(x,y(x),y^\prime(x), \ldots,y^{(n-1)}(x)).
```

Wir können die Gleichung {eq}`eq:ode:redODEOri` zu einem Differentialgleichungssystem erster Ordnung umformulieren bestehend aus $n+1$ Gleichungen mit
\begin{equation*}
\left\{\begin{array}{rl}
y &=~y_1,\\
y_1^\prime&=~y_2,\\
&\vdots\\
y_{n-1}^\prime&=~y_{n},\\
y_{n}^\prime&=~f(x,y_1, \ldots,y_{n}).
\end{array}\right.
:label: eq:ode:redODE
\end{equation*}

Definieren wir nun zwei $n$-dimensionale Vektoren $Y,F \in \R^n$ mit
\begin{equation*}
Y(x) \, \coloneqq \, \left(\begin{array}{c}y_1(x)\\\vdots\\y_{n-1}(x)\\y_{n}(x)\end{array}\right)
\qquad \text{und} \qquad 
F(x,Y) \, \coloneqq \, \left(\begin{array}{c}y_2(x)\\\vdots\\y_{n}(x)\\f(x,Y(x))\end{array}\right)
\end{equation*}
dann können wir  das Differentialgleichungssystem {eq}`eq:ode:redODE` umschreiben zu
\begin{equation*}
Y^\prime(x) \, = \, F(x,Y(x)).
\end{equation*}
Die Ableitung $Y'$ ist hierbei komponentenweise zu interpretieren.

Sei nun $\varphi\colon I\to\R$ eine Lösung der expliziten gewöhnlichen Differentialgleichung $n$-ter Ordnung in {eq}`eq:ode:redODEOri`, d.h.,
\begin{equation*}
\varphi^{(n)}(x) \ = \ f(x,\varphi(x), \varphi^\prime(x), \ldots, \varphi^{(n-1)}(x)).
\end{equation*}
Basierend auf $\varphi$ können wir uns nun eine vektorwertige Funktion $\Phi \colon I \rightarrow \R^n$ definieren mit
\begin{equation*}
\Phi(x) \ \coloneqq \ \left(\begin{array}{c}\varphi_1(x)\\\varphi_2(x)\\\vdots\\\varphi_{n}(x)\end{array}\right) \ = \ \left(\begin{array}{c} \varphi(x) \\ \varphi'(x) \\ \vdots \\ \varphi^{(n-1)}(x) \end{array}\right) .
\end{equation*}
Dann wird aus der obigen Definition klar, dass $\Phi$ eine Lösung des Differentialgleichungssystems {eq}`eq:ode:redODE` ist.

Ist nun umgekehrt vorausgesetzt, dass $\Phi \colon I \to \R^n$ eine Lösung des Differentialgleichungssystems erster Ordnung in {eq}`eq:ode:redODE` ist, dann ist
\begin{equation*}
\varphi \, \coloneqq\, \varphi_1 \colon I\to\R
\end{equation*}
eine Lösung der Differentialgleichung $n$-ter Ordnung {eq}`eq:ode:redODEOri`.
Dieser Zusammenhang gilt, da aus den ersten $n$ Gleichungen des Systems {eq}`eq:ode:redODE` folgt
\begin{align*}
\varphi_1(x) \, &= \, \varphi(x)\\
\varphi_2(x) \, &= \, \varphi_1^\prime(x) \, = \, \varphi^{\prime}(x),\\
\varphi_3(x) \, &= \, \varphi_2^\prime(x) \, = \, \varphi_1^{\prime\prime}(x) \, = \, \varphi^{\prime\prime}(x),\\
&\vdots\\
\varphi_{n}(x) \, &= \, \varphi_{n-1}^\prime(x) \, = \, \ldots \, = \, \varphi^{(n-1)}(x).
\end{align*}
Da $\varphi_{n}$ einmal differenzierbar ist, folgt daraus, dass $\varphi$ $n$-mal differenzierbar sein muss.
Die $(n+1)$-te Gleichung von {eq}`eq:ode:redODE` liefert dann
\begin{equation*}
\varphi_n^\prime(x) \ = \ \varphi^{(n)}(x) \ = \ f(x,\varphi(x),\varphi^\prime(x), \ldots, \varphi^{(n-1)}(x)).
\end{equation*}
Wir sehen also, dass die Lösungen von {eq}`eq:ode:redODEOri` und {eq}`eq:ode:redODE` in einer eindeutigen Beziehung zueinander stehen.
````

````{prf:example}
Die Gleichung

```{math}
:label: eq:ode:2ordnSinCos
y^{\prime\prime}(x) + y(x) \, = \, 0
```

für $x\in \R$ ist eine implizite gewöhnliche  Differentialgleichung zweiter Ordnung.
Um diese Differentialgleichung in ein Differentialgleichungssystem erster Ordnung zu transformieren führen wir zwei neue Variablen wie folgt ein:
\begin{equation*}
y_1 \, \coloneqq \, y, \qquad y_2 \, \coloneqq \, y_1'.
\end{equation*}
Mit diesen Variablen können wir die Differentialgleichung {eq}`eq:ode:2ordnSinCos` umschreiben in die Gleichung
\begin{equation*}
y_2' + y_1 \, = \, 0.
\end{equation*}
Zusammen mit der Bedingung $y_1' = y_2$ ergibt sich damit das folgende lineare, homogene Differentialgleichungssystem erster Ordnung:
\begin{equation*}
Y' \ \coloneqq \
\begin{pmatrix}
y_1'\\ 
y_2'
\end{pmatrix} \ = \ 
\begin{pmatrix}
0 & 1\\
-1 & 0
\end{pmatrix}
\cdot
\begin{pmatrix}
y_1\\
y_2
\end{pmatrix}.
\end{equation*}

Die gewöhnliche Differentialgleichung {eq}`eq:ode:2ordnSinCos` besitzt offensichtlich die auf ganz $\R$ definierten Lösungen
\begin{equation*}
\varphi(x) \ \coloneqq \ \cos x, \qquad\text{und}\qquad \varphi(x) \ \coloneqq \ \sin x.
\end{equation*}
Aufgrund der Linearität der Ableitung sind in diesem Fall auch sämtliche Linearkombinationen von Lösungen wiederum Lösungen.
Das heißt wir können eine allgemeine Lösung der gewöhnlichen Differentialgleichung angeben für beliebige Konstanten $c_0,c_1\in\R$:
\begin{equation*}
\varphi_{c_0,c_1}(x) \ \coloneqq \ c_0\cdot \cos x + c_1\cdot \sin x.
\end{equation*}
Betrachten wir die beiden Anfangswertgleichungen
\begin{equation*}
\begin{split}
\varphi_{c_0,c_1}(0) \ &= \ c_0 \cdot \cos(0) + c_1 \cdot \sin (0) \ = \ c_0\\
\varphi^\prime_{c_0,c_1}(0) \ &= \ - c_0 \cdot \sin (0) + c_1 \cdot \cos (0) \ = \ c_1\,,
\end{split}
\end{equation*}
so stellen wir fest, dass $\varphi_{c_0,c_1} \colon \R \rightarrow \R$ die eindeutig bestimmte Lösung $\varphi$ der Differentialgleichung {eq}`eq:ode:2ordnSinCos` mit den Anfangswertbedingungen $\varphi_{c_0,c_1}(0)=c_0$ und $\varphi_{c_0,c_1}^\prime(0)=c_1$ ist.
````
