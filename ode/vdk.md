# Variation der Konstanten

Bisher haben wir uns auf den Fall von linearen, homogenen Differentialgleichungen beschränkt.
Das heißt wir haben nur den Spezialfall ohne Störfunktion, d.h., $b(x) \equiv 0$ diskutiert.
Im Folgenden wollen wir nun inhomogene lineare Differentialgleichungen der Forn
\begin{equation*}
y^\prime(x) = a(x)\cdot y(x) + b(x),
\end{equation*}
betrachten, wobei $a,b\colon I\to\R$ stetige Funktionen auf dem offenen Intervall $I\subset\R$ sind.
Für einen beliebigen Punkt $x_0\in I$ und einen Anfangswert $c\in\R$ suchen wir eine Lösung $\varphi\colon I\to\R$ der Differentialgleichung die der Anfangsbedingung $\varphi(x_0) = c$ genügt.

Da eine Trennung der Variablen aus Kapitel {ref}`s:trennung_variablen` in diesem Fall nicht zum Ziel führt, wollen wir eine andere wichtige Technik zur analytischen Lösung von gewöhnlichen Differentialgleichungen untersuchen.
Die sogenannte _Variation der Konstanten_ ist ein Verfahren zur Bestimmung einer speziellen Lösung einer inhomogenen linearen Differentialgleichung erster Ordnung. Die einzige Zutat, die diese Technik voraussetzt, ist das Vorliegen einer Lösung der zugehörigen homogenen Differentialgleichung
\begin{equation*}
y^\prime(x) = a(x)\cdot y(x).
\end{equation*}
Aus Satz \ref{satz:ode_lin_hom} wissen wir bereits, dass diese von der folgenden Form sind
\begin{equation*}
\varphi_0(x) \ \coloneqq \ c\cdot \exp\left(\int\limits_{x_0}^xa(t)\, \mathrm{d}t\right)\,.
\end{equation*}

Der folgende Satz beschreibt analytische Lösungen der inhomogenen Differentialgleichung basierend auf der Lösung $\varphi_0$ der zugehörigen homogenen Differentialgleichung.

````{prf:theorem} Variation der Konstanten
:label: satz:ode:varDerKonstanten

Sei $I\subset\R$ ein offenes Intervall und seien $a,b\colon I\to\R$ zwei stetige Funktionen.
Dann gibt es zu einem beliebigen Punkt $x_0\in\ I$ und einem Anfangswert $c\in\R$ eine eindeutige Lösung $\varphi\colon I\to\R$ der linearen, inhomogenen Differentialgleichung erster Ordnung
\begin{equation*}
y^\prime(x) \ = \ a(x)\cdot y(x) + b(x) \quad \text{ für alle } \ x \in I
\end{equation*}
unter der Anfangsbedingung $\varphi(x_0) = c$.
Die Lösung hat die Form
\begin{equation*}
\varphi(x) \ = \ \varphi_0(x) \cdot \left(c+\int\limits_{x_0}^x\varphi^{-1}_0(t)\cdot b(t)\,\mathrm{d}t\right),
\end{equation*}
wobei
\begin{equation*}
\varphi_0(x) \ \coloneqq \ \exp\left(\,\int\limits_{x_0}^xa(t)\,\mathrm{d}t\right).
\end{equation*}
````

````{prf:proof}
Sei $\varphi_0$ eine Lösung der zugehörigen homogenen Differentialgleichung und $\varphi$ die zu bestimmende Lösung der inhomogenen Differentialgleichung.
Wir betrachten nun eine sogenannte Ansatzfunktion $u$ mit
\begin{equation*}
u(x) \ \coloneqq \ \varphi(x) \cdot \varphi_0^{-1}(x) \ = \ \varphi(x) \cdot \exp\left(\,-\int\limits_{x_0}^x a(t)\,\mathrm{d}t\right).
\end{equation*}
Durch Multiplikation mit $\varphi_0$ lässt sich der Ausdruck dieser Funktion nun umstellen zur unbekannten Lösung $\varphi$ mit
\begin{equation}\label{eq:dgl_inhomogen_varphi}
\varphi(x) \ = \ \varphi_0(x) \cdot  u(x) \ = \ \exp\left(\,\int\limits_{x_0}^xa(t)\,\mathrm{d}t\right) \cdot u(x).
\end{equation}
Setzen wir diesen Ausdruck nun in die inhomogene Differentialgleichung ein, so erhalten wir für alle $x \in I$
\begin{equation}\label{eq:dgl_inhomogen_u}
(u\cdot \varphi_0)'(x) \ = \ a(x) \cdot u(x) \cdot \varphi_0(x) + b(x).
\end{equation}
Durch Anwendung der Produkt- und Kettenregel der Differentiation und des Hauptsatzes der Differential- und Integralrechnung lässt sich die linke Seite der Gleichung noch vereinfachen zu
\begin{equation*}
\begin{split}
(u\cdot \varphi_0)'(x) \ &= \ u'(x) \cdot  \varphi_0(x) + u(x) \cdot \varphi_0'(x) \\ 
&= \ u'(x) \cdot  \varphi_0(x) + u(x) \cdot \varphi_0(x) \cdot \left(\,\int\limits_{x_0}^xa(t)\,\mathrm{d}t\right)'\\ 
&= \ u'(x) \cdot  \varphi_0(x) + u(x) \cdot \varphi_0(x) \cdot a(x).
\end{split}
\end{equation*}
Wir erkennen, dass sich die Terme auf der linken und rechten Seite von \eqref{eq:dgl_inhomogen_u} teilweise annullieren wodurch wir die folgende einfache Darstellung der Funktion $b$ erhalten:
\begin{equation*}
\begin{split}
 &u'(x) \cdot  \varphi_0(x) + u(x) \cdot \varphi_0(x) \cdot a(x) \ = \ a(x) \cdot u(x) \cdot \varphi_0(x) + b(x)\\
\Leftrightarrow \quad &u'(x) \cdot  \varphi_0(x) \ = \ b(x).
\end{split}
\end{equation*}
Multiplizieren wir diese Gleichung wiederum mit $\varphi_0^{-1}$, so erhalten wir die folgende Darstellung der Ableitung von $u$ mit
\begin{equation*}
u'(x) \ = \ \varphi_0^{-1}(x) \cdot b(x) \quad \text{ für alle } x \in I.
\end{equation*}
Somit können wir die unbekannte Funktion $u$ charakterisieren als Stammfunktion durch
\begin{equation*}
u(x) \ = \ \int_{x_0}^x \varphi_0^{-1}(t) \cdot b(t) \, \mathrm{d}t + C,
\end{equation*}
wobei $C \in \R$ eine Integrationskonstante ist.
Setzen wir dies nun in die Gleichung \eqref{eq:dgl_inhomogen_varphi} für die Lösung $\varphi$ der inhomogenen Differentialgleichung ein, so erhalten wir für alle $x \in I$:
\begin{equation*}
\varphi(x) \ = \  \varphi_0(x)  \cdot u(x) \ = \ \varphi_0(x)  \cdot \left( \int_{x_0}^x \varphi_0^{-1}(t) \cdot b(t) \, \mathrm{d}t + C \right).
\end{equation*}
Zur Bestimmung der Integrationskonstante $C$ setzen wir $x = x_0$ und sehen durch Anwendung der Anfangswertbedingung
\begin{equation*}
\varphi(x_0) \ = \ \underbrace{\varphi_0(x_0)}_{=1} \cdot \Bigl( \underbrace{\int_{x_0}^{x_0} \varphi_0^{-1}(t) \cdot b(t) \, \mathrm{d}t}_{=0} +\: C \Bigr) \ = \ C \ \overset{!}{=} \ c.
\end{equation*}
Damit ist nun die Aussage des Satzes vollständig bewiesen.
````

Im folgenden Beispiel wollen wir das Verfahren der Variation der Konstanten nutzen, um die analytische Lösung einer inhomogenen Differentialgleichung herzuleiten.

````{prf:example} Variation der Konstanten
Wir betrachten die folgende lineare, inhomogene Differentialgleichung erster Ordnung
\begin{equation}\label{eq:dgl_inhomogen}
y^\prime(x) \ = \ 2x\cdot y(x) + x^3,
\end{equation}
für die die Anfangsbedingung $y(0) = c$ mit $c \in \R$ erfüllt sein soll.
Die zugehörige homogene Differentialgleichung $y^\prime(x) = 2x\cdot y(x)$ besitzt nach Satz \ref{satz:ode_lin_hom} Lösungen der Form
\begin{equation*}
\varphi_0(x) \ = \ \exp\left(\int\limits_0^x2t\,\mathrm{d}t\right) \ = \ e^{x^2}.
\end{equation*}

Wir erhalten eine Lösung $\varphi\colon\R\to\R$ der inhomogenen Gleichung \eqref{eq:dgl_inhomogen} unter der Anfangsbedingung $\varphi(0) = c$ durch
\begin{equation*}
\varphi(x) \ = \ e^{x^2} \cdot \left(c+\int\limits_0^xt^3e^{-t^2}\,\mathrm{d}t\right).
\end{equation*}
Wir können glücklicherweise dieses Integral weiter berechnen indem wir die Substitution $s\coloneqq t^2$ anwenden und darüber hinaus partielle Integration durchführen.
Damit erhält man
\begin{equation*}
\int\limits_0^xt^3e^{-t^2}\,\mathrm{d}t \ = \ \frac12-\frac12\left(x^2+1\right)e^{-x^2},
\end{equation*}
und somit insgesamt die Lösung der inhomogenen Differentialgleichung \eqref{eq:dgl_inhomogen} mit 
\begin{equation*}
\begin{split}
\varphi(x) \ &= \ e^{x^2} \cdot \left(c+\int\limits_0^xt^3e^{-t^2}\,\mathrm{d}t\right) \ = \ e^{x^2} \cdot \left( c + \frac12-\frac12\left(x^2+1\right)e^{-x^2}\right) \\
 &= \ \left(c+\frac12\right)e^{x^2} - \frac12\left(x^2+1\right).
 \end{split}
\end{equation*}
````
