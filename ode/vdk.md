# Variation der Konstanten

Bisher haben wir uns auf den Fall von linearen, homogenen Differentialgleichungen beschränkt.
Das heißt wir haben nur den Spezialfall ohne Störfunktion, d.h., $b(x) \equiv 0$ diskutiert.
Im Folgenden wollen wir nun inhomogene lineare Differentialgleichungen der Forn
\begin{equation*}
y^\prime(x) = a(x)\cdot y(x) + b(x),
\end{equation*}
betrachten, wobei $a,b\colon I\to\R$ stetige Funktionen auf dem offenen Intervall $I\subset\R$ sind.
Für einen beliebigen Punkt $x_0\in I$ und einen Anfangswert $c\in\R$ suchen wir eine Lösung $\varphi\colon I\to\R$ der Differentialgleichung die der Anfangsbedingung $\varphi(x_0) = c$ genügt.

Da eine Trennung der Variablen aus Kapitel \ref{s:trennung_variablen} in diesem Fall nicht zum Ziel führt, wollen wir eine andere wichtige Technik zur analytischen Lösung von gewöhnlichen Differentialgleichungen untersuchen.
Die sogenannte \emph{Variation der Konstanten} ist ein Verfahren zur Bestimmung einer speziellen Lösung einer inhomogenen linearen Differentialgleichung erster Ordnung. 
Die einzige Zutat, die diese Technik voraussetzt, ist das Vorliegen einer Lösung der zugehörigen homogenen Differentialgleichung
\begin{equation*}
y^\prime(x) = a(x)\cdot y(x).
\end{equation*}
Aus Satz \ref{satz:ode_lin_hom} wissen wir bereits, dass diese von der folgenden Form sind
\begin{equation*}
\varphi_0(x) \ \coloneqq \ c\cdot \exp\left(\int\limits_{x_0}^xa(t)\, \mathrm{d}t\right)\,.
\end{equation*}

Der folgende Satz beschreibt analytische Lösungen der inhomogenen Differentialgleichung basierend auf der Lösung $\varphi_0$ der zugehörigen homogenen Differentialgleichung.
\begin{satz}[Variation der Konstanten]\label{satz:ode:varDerKonstanten}
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
\end{satz}
\begin{proof}
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
\end{proof}

Im folgenden Beispiel wollen wir das Verfahren der Variation der Konstanten nutzen, um die analytische Lösung einer inhomogenen Differentialgleichung herzuleiten.
\begin{bsp}[Variation der Konstanten]
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
\end{bsp}

\section{Differentialgleichungen höherer Ordnung}\label{s:dgl_hoehere_ordnung}
Obwohl wir gewöhnliche Differentialgleichungen höherer Ordnung bereits im vorigen Abschnitt erwähnt haben, haben wir diese noch nicht näher diskutiert.
Wir wollen im Folgenden ein zusätzliches Kriterium zur Klassifikation von gewöhnlichen Differentialgleichungen einführen und beschreiben, wie sich eine gewöhnliche Differentialgleichung höherer Ordnung in ein System von gewöhnlichen Differentialgleichungen erster Ordnung umformulieren lässt.

Beginnen wir zunächst mit der Definition einer gewöhnlichen Differentialgleichung $n$-ter Ordnung.
Eine Differentialgleichung $n$-ter Ordnung schreibt eine Bedingung für die $n$-te Ableitung der gesuchten Lösung $\varphi$ vor.
Diese $n$-te Ableitung hängt sowohl von $x$ als auch von der Lösung $\varphi$ und ihren Ableitungen bis zur $(n-1)$-ten Ordnung im Punkt $x$ ab.
\begin{definition}[Differentialgleichung $n$-ter Ordnung]
Sei $G\subset\R\times\R^n$ eine offene Teilmenge und
\begin{align*}
f\colon G&\to\R
\end{align*}
eine stetige Funktion.

\begin{enumerate}
\item
Wir nennen eine Gleichung der Form
\begin{equation*}
y^{(n)}(x) \, = \, f(x,y(x),y^\prime(x), \ldots, y^{(n-1)}(x))
\end{equation*}
eine \emph{explizite} gewöhnliche Differentialgleichung $n$-ter Ordnung.
Ist die gewöhnliche Differentialgleichung nicht nach der höchsten vorkommenden Ableitung aufgelöst, d.h. wenn sie von der folgenden Form ist
\begin{equation*}
f(x,y(x),y^\prime(x), \ldots, y^{(n-1)}(x), y^{(n)}(x)) \, = \, 0,
\end{equation*}
so nennen wir sie eine \emph{implizite} gewöhnliche Differentialgleichung $n$-ter Ordnung.

\item
Wir nennen eine $n$-mal differenzierbare Funktion $\varphi\colon I\to\R$ auf dem offenen Intervall $I \subset \R$ eine \emph{Lösung der Differentialgleichung}, wenn sie die folgenden Eigenschaften besitzt:
\begin{enumerate}[i)]
\item Der von der unbekannten Lösung $\varphi$  abhängende Menge
\begin{equation*}
\Gamma_\varphi \ \coloneqq \ \left\{(x,y_1, y_2, \ldots, y_{n})\in I\times \R^n~\Big\vert~y_k = \varphi^{(k-1)}(x), \ 1\leq k\leq n\right\}
\end{equation*}
ist eine Teilmenge von $G$,
\item Für alle Punkte $x\in I$ gilt
\begin{equation*}
\varphi^{(n)}(x) \ = \ f(x,\varphi (x), \varphi^\prime(x), \ldots, \varphi^{(n-1)}(x))\,.
\end{equation*}
\end{enumerate}
\end{enumerate}
\end{definition}

Das folgende Beispiel illustriert den Begriff einer gewöhnlichen Differentialgleichung in expliziter und impliziter Form.
\begin{example}
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
\end{example}

Man kann eine gewöhnliche Differentialgleichung $n$-ter Ordnung in ein System von gewöhnlichen Differentialgleichungen erster Ordnung überführen wie folgende Bemerkung zeigt.
Diese Beobachtung hat den großen Vorteil, dass man sich bei Lösungsmethoden von gewöhnlichen Differentialgleichungen, egal ob analytisch oder numerisch, nur auf das Lösen von Differentialgleichungssystemen erster Ordnung konzentrieren muss.
\begin{remark}
Sei $G \subset \R \times \R^n$ eine offene Teilmenge und $f\colon G\to\R$  eine stetige Funktion.
Wir betrachten im Folgenden die explizite gewöhnliche Differentialgleichung $n$-ter Ordnung
\begin{equation}\label{eq:ode:redODEOri}
y^{(n)}(x) \, = \, f(x,y(x),y^\prime(x), \ldots,y^{(n-1)}(x)).
\end{equation}
\begin{enumerate}
\item
Wir können die Gleichung \eqref{eq:ode:redODEOri} zu einem Differentialgleichungssystem erster Ordnung umformulieren bestehend aus $n+1$ Gleichungen mit
\begin{equation}
\left\{\begin{array}{rl}
y &=~y_1,\\
y_1^\prime&=~y_2,\\
&\vdots\\
y_{n-1}^\prime&=~y_{n},\\
y_{n}^\prime&=~f(x,y_1, \ldots,y_{n}).
\end{array}\right.\label{eq:ode:redODE}
\end{equation}

Definieren wir nun zwei $n$-dimensionale Vektoren $Y,F \in \R^n$ mit
\begin{equation*}
Y(x) \, \coloneqq \, \left(\begin{array}{c}y_1(x)\\\vdots\\y_{n-1}(x)\\y_{n}(x)\end{array}\right)
\qquad \text{und} \qquad 
F(x,Y) \, \coloneqq \, \left(\begin{array}{c}y_2(x)\\\vdots\\y_{n}(x)\\f(x,Y(x))\end{array}\right)
\end{equation*}
dann können wir  das Differentialgleichungssystem \eqref{eq:ode:redODE} umschreiben zu
\begin{equation*}
Y^\prime(x) \, = \, F(x,Y(x)).
\end{equation*}
Die Ableitung $Y'$ ist hierbei komponentenweise zu interpretieren.

\item
Sei nun $\varphi\colon I\to\R$ eine Lösung der expliziten gewöhnlichen Differentialgleichung $n$-ter Ordnung in \eqref{eq:ode:redODEOri}, d.h.,
\begin{equation*}
\varphi^{(n)}(x) \ = \ f(x,\varphi(x), \varphi^\prime(x), \ldots, \varphi^{(n-1)}(x)).
\end{equation*}
Basierend auf $\varphi$ können wir uns nun eine vektorwertige Funktion $\Phi \colon I \rightarrow \R^n$ definieren mit
\begin{equation*}
\Phi(x) \ \coloneqq \ \left(\begin{array}{c}\varphi_1(x)\\\varphi_2(x)\\\vdots\\\varphi_{n}(x)\end{array}\right) \ = \ \left(\begin{array}{c} \varphi(x) \\ \varphi'(x) \\ \vdots \\ \varphi^{(n-1)}(x) \end{array}\right) .
\end{equation*}
Dann wird aus der obigen Definition klar, dass $\Phi$ eine Lösung des Differentialgleichungssystems \eqref{eq:ode:redODE} ist.

Ist nun umgekehrt vorausgesetzt, dass $\Phi \colon I \to \R^n$ eine Lösung des Differentialgleichungssystems erster Ordnung in \eqref{eq:ode:redODE} ist, dann ist
\begin{equation*}
\varphi \, \coloneqq\, \varphi_1 \colon I\to\R
\end{equation*}
eine Lösung der Differentialgleichung $n$-ter Ordnung \eqref{eq:ode:redODEOri}.
Dieser Zusammenhang gilt, da aus den ersten $n$ Gleichungen des Systems \eqref{eq:ode:redODE} folgt
\begin{align*}
\varphi_1(x) \, &= \, \varphi(x)\\
\varphi_2(x) \, &= \, \varphi_1^\prime(x) \, = \, \varphi^{\prime}(x),\\
\varphi_3(x) \, &= \, \varphi_2^\prime(x) \, = \, \varphi_1^{\prime\prime}(x) \, = \, \varphi^{\prime\prime}(x),\\
&\vdots\\
\varphi_{n}(x) \, &= \, \varphi_{n-1}^\prime(x) \, = \, \ldots \, = \, \varphi^{(n-1)}(x).
\end{align*}
Da $\varphi_{n}$ einmal differenzierbar ist, folgt daraus, dass $\varphi$ $n$-mal differenzierbar sein muss.
Die $(n+1)$-te Gleichung von \eqref{eq:ode:redODE} liefert dann
\begin{equation*}
\varphi_n^\prime(x) \ = \ \varphi^{(n)}(x) \ = \ f(x,\varphi(x),\varphi^\prime(x), \ldots, \varphi^{(n-1)}(x)).
\end{equation*}
Wir sehen also, dass die Lösungen von \eqref{eq:ode:redODEOri} und \eqref{eq:ode:redODE} in einer eindeutigen Beziehung zueinander stehen.
\end{enumerate}
\end{remark}

\begin{bsp}
Die Gleichung
\begin{equation}
y^{\prime\prime}(x) + y(x) \, = \, 0\label{eq:ode:2ordnSinCos}
\end{equation}
für $x\in \R$ ist eine implizite gewöhnliche  Differentialgleichung zweiter Ordnung.
Um diese Differentialgleichung in ein Differentialgleichungssystem erster Ordnung zu transformieren führen wir zwei neue Variablen wie folgt ein:
\begin{equation*}
y_1 \, \coloneqq \, y, \qquad y_2 \, \coloneqq \, y_1'.
\end{equation*}
Mit diesen Variablen können wir die Differentialgleichung \eqref{eq:ode:2ordnSinCos} umschreiben in die Gleichung
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

Die gewöhnliche Differentialgleichung \eqref{eq:ode:2ordnSinCos} besitzt offensichtlich die auf ganz $\R$ definierten Lösungen
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
so stellen wir fest, dass $\varphi_{c_0,c_1} \colon \R \rightarrow \R$ die eindeutig bestimmte Lösung $\varphi$ der Differentialgleichung \eqref{eq:ode:2ordnSinCos} mit den Anfangswertbedingungen $\varphi_{c_0,c_1}(0)=c_0$ und $\varphi_{c_0,c_1}^\prime(0)=c_1$ ist.
\end{bsp}

\section{Existenz und Eindeutigkeit von Lösungen}
Bisher haben wir uns vornehmlich um analytische Lösungsverfahren für lineare gewöhnliche Differentialgleichungen erster Ordnung beschäftigt.
Dabei haben wir theoretische Überle\-gun\-gen zur Existenz und Eindeutigkeit von Lösungen allgemeiner gewöhnlicher Differentialgleichungen vernachlässigt.
Daher wollen wir uns in diesem Abschnitt den notwendigen und hinreichenden Bedingungen widmen, die uns sagen wann eine Differentialgleichung lösbar ist und wann ihre Lösung sogar eindeutig ist.

Da wir in Kapitel \ref{s:dgl_hoehere_ordnung} gesehen haben, dass sich beliebige gewöhnliche Differentialgleichungen höherer Ordnung in ein Differentialgleichungssystem erster Ordnung transformieren lassen, beschränken wir uns auf diese Differentialgleichungssysteme.
Dies motiviert die folgende Definition.
\begin{definition}[Differentialgleichungssystem erster Ordnung]\label{def:dglsystem_erster_ordnung}
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
ein \emph{System von $n$ Differentialgleichungen erster Ordnung}.
Eine Lösung dieser Gleichung ist eine auf dem offenen Intervall $I\subset \R$ total differenzierbare Funktion $\varphi\colon I\to\R^n$, für die die folgenden Eigenschaften gelten:
\begin{enumerate}
\item Der Graph $\Gamma_\varphi$ von $\varphi$ liegt in der Teilmenge $G$, d.h,
\begin{equation*}
\Gamma_\varphi \ \coloneqq  \ \lbrace (x,y)\in I\times \R^n~\vert~ y=\varphi(x)\rbrace \, \subset \, G.
\end{equation*}
\item Die Funktion $\varphi$ erfüllt die Gleichung
\begin{equation*}
\varphi^\prime(x) \: = \: f(x, \varphi(x))\qquad \text{für alle} \ x\in I.
\end{equation*}
\end{enumerate}
\end{definition}

\begin{remark}
Im Gegensatz zu vorigen Abschnitten handelt es sich in Definition \ref{def:dglsystem_erster_ordnung} nicht um eine Differentialgleichung einer skalarwertigen Funktion sondern um ein Differentialgleichungssystem einer vektorwertigen Funktion.
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
\end{remark}

Der folgende Satz charakterisiert die Lösung eines Differentialgleichungssystems mit Anfangswertbedingungen als Lösung einer zugehörigen Integralgleichung.
\begin{satz}[Integralgleichung]\label{satz:ode_integralgleichung}
Sei $G\subset \R\times \R^n$ eine offene Teilmenge, $I \subset R$ ein offenes Intervall und sei $f\colon G\to\R^n$ eine stetige Abbildung.
Weiter seien die Anfangwerte $(x_0,c)\in G$ mit $x_0 \in I$ gegeben.
Sei nun $\varphi\colon I\to \R^n$ eine total differenzierbare Funktion, deren Graph in $G$ enthalten ist

Die Funktion $\varphi$ ist genau dann eine Lösung der Differentialgleichung
\begin{equation*}
y^\prime(x) \ = \ f(x,y(x))
\end{equation*}
unter der Anfangswertbedingung $\varphi(x_0) = c$, wenn sie die folgende Integralgleichung erfüllt:
\begin{equation}\label{eq:ode_integralgleichung}
\varphi(x) \ = \ c + \int\limits_{x_0}^x f(t,\varphi(t))\,\mathrm{d}t \qquad \text{für alle } \ x\in I.
\end{equation}
\end{satz}
\begin{proof}
Wir zeigen zunächst die Rückrichtung des Satzes. 
Sei also die Integralgleichung \eqref{eq:ode_integralgleichung} erfüllt.
Für die Anfangswertbedingung setzen wir $x = x_0$ und sehen somit, dass $\varphi(x_0) = c$ gilt.
Da die Funktion $f$ nach Voraussetzung stetig ist, folgt aus dem Hauptsatz der Integral- und Differentialrechnung \cite[Kapitel 7.2]{burger_2020}, dass
\begin{equation*}
\frac{\mathrm{d}}{\mathrm{d}x} \int_{x_0}^x f(t, \varphi(t)) \, \mathrm{d}t \ = \ f(x, \varphi(x)).
\end{equation*}
Damit folgt aus der Definition der Funktion $\varphi$ in \eqref{eq:ode_integralgleichung}, dass $\varphi$ total differenzierbar ist und die gewöhnliche Differentialgleichung $\varphi'(x) = f(x, \varphi(x))$ erfüllt.

Für die Hinrichtung des Beweises nehmen wir an, dass die Funktion $\varphi$ eine Lösung der gewöhnlichen Differentialgleichung $\varphi'(x) = f(x, \varphi(x))$ ist, total differenzierbar sei und die Anfangswertbedingung $\varphi(x_0) = c$ erfülle.
Dann können wir das folgende Integral betrachten und erhalten aus dem Hauptsatz der Integral- und Differentialrechnung:
\begin{equation*}
\int_{x_0}^x f(t, \varphi(t)) \, \mathrm{d}t \ = \ \int_{x_0}^x \varphi'(t) \, \mathrm{d}t \ = \ \varphi(x) - \varphi(x_0) \ = \ \varphi(x) - c.
\end{equation*}
Durch Umstellen von $c$ auf die linke Seite erhält man die Identität der Integralgleichung in \eqref{eq:ode_integralgleichung}.
\end{proof}

%\begin{definition}[Lipschitz-Bedingung]
%Sei $G\subset R\times \R^n$ und
%\begin{equation*}
%f\colon G\to\R^n\,,\quad(x,y)\mapsto f(x,y)
%\end{equation*}
%eine Funktion.
%Man sagt, dass $f$ in $G$ einer \emph{Lipschitz-Bedingung} genügt (bezüglich $y$) mit der Lipschitz-Konstanten $L\geq0$, wenn
%\begin{equation*}
%\Vert f(x,y) - f(x,\widetilde{y}) \Vert \leq L \Vert y-\widetilde{y}\Vert\quad\text{für alle }(x,y), (x,\widetilde{y})\in G\,.
%\end{equation*}
%Man sagt, $f$ genüge in $G$ lokaal einer Lipschitz-Bedingung, falls jeder Punkt $(a,b)\in G$ eine Umgebung $U$ besitzt, sodass $f$ in $G\cap U$ einer Lipschitzbedingung mit einer gewisen (von $U$ abhängigen) Konstanten $L\in\R_+$ genügt.
%\end{definition}

Das folgende Lemma liefert uns ein hinreichendes Kriterium für die Lipschitz-Stetigkeit einer Funktion.
Diese Eigenschaft wird für die Existenz und Eindeutigkeit von Lösungen gewöhnlicher Differentialgleichungen entscheidend sein.
\begin{lemma}\label{lem:ode_lokalLipschitz}
Sei $G\subset \R\times\R^n$ eine offene Teilmenge und $f\colon G\to\R^n$ eine bezüglich der Variablen $y=(y_1,\ldots,y_n)$ stetig partiell differenzierbare Funktion.

Dann ist die Funktion $f$ lokal Lipschitz-stetig in $G$ bezüglich des $y$-Variable.
\end{lemma}
\begin{proof}
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

Aus einer Folgerung des Mittelwertsatzes in \ref{thm:meanest} folgt für alle $(x,y), (x,\tilde{y}) \in B_r(a,b)$, dass gilt
\begin{equation*}
||f(x,y) - f(x,\tilde{y})|| \ \leq \ L \cdot ||y - \tilde{y}||.
\end{equation*}
\end{proof}

Nun sind wir in der Lage die hinreichenden Bedingungen für die Eindeutigkeit von Lösungen gewöhnlicher Differentialgleichungen zu formulieren.
\begin{satz}[Eindeutigkeitssatz]\label{satz:ode_eindeutigkeitssatz}
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
\end{satz}
\begin{proof}
Wir beginnen zunächst damit die Eindeutigkeit von Lösungen in einer lokalen $\epsilon$-Umgebung zu zeigen.
Sei $x_0 \in I$ ein Punkt, so dass für die beiden Lösungen $\varphi, \vartheta \colon I \rightarrow \R^n$ der gewöhnlichen Differentialgleichung gilt $\varphi(x_0) = \vartheta(x_0)$.
Auf Grund der Integraldarstellung in Satz \ref{satz:ode_integralgleichung} folgt nun
\begin{equation}\label{eq:ode_eindeutigkeit_integralgleichung}
\varphi(x) - \vartheta(x) \ = \ \int_{x_0}^x f(t, \varphi(t)) - f(t, \vartheta(t)) \, \mathrm{d}t.
\end{equation}
Da $f$ nach Voraussetzung lokal Lipschitz-stetig bezüglich der $y$-Variablen ist, existieren Konstanten $L \geq 0$ und $\delta > 0$, so dass für alle $t \in I \cap B_\delta(x_0) \coloneqq \lbrace t \in I \colon |t - x_0| < \delta \rbrace$ gilt:
\begin{equation*}\label{eq:ode_eindeutigkeit_lipschitz}
||f(t, \varphi(t)) - f(t, \vartheta(t))|| \ \leq \ L \cdot ||\varphi(t) - \vartheta(t)||.
\end{equation*}

Wir definieren nun die zwei Variablen
\begin{equation*}
\epsilon \, \coloneqq \, \min( \delta, \frac{1}{2L} ) \quad \text{ und } \quad M \, \coloneqq \, \sup\{ ||\varphi(x) - \vartheta(x)|| \, \colon \, x \in I \cap B_\epsilon(x_0) \}.
\end{equation*}
Aus Gleichung \eqref{eq:ode_eindeutigkeit_integralgleichung} und \eqref{eq:ode_eindeutigkeit_lipschitz} können wir nun für alle $x \in I \cap B_\epsilon(x_0)$ folgern
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
\end{proof}

Um zu verstehen, wann die Lösung einer gewöhnlichen Differentialgleichung nicht eindeutig ist, diskutieren wir im Folgenden ein Gegenbeispiel.
\begin{bsp}
Wir betrachten die folgende nichtlineare gewöhnliche Differentialgleichung
\begin{equation}\label{eq:bsp_dgl_nichteindeutig}
y^\prime(x) \ = \ (y(x))^{\frac23}.
\end{equation}
Wie man sofort einsieht ist eine spezielle Lösung der Differentialgleichung gegeben durch
\begin{equation*}
\varphi_0(x) \ \equiv \ 0, \qquad \text{ für alle } x\in\R.
\end{equation*}
Da die Differentialgleichung separierbar ist, lassen sich die Lösungen unter der Annahme $y\neq 0$ mit Hilfe von Satz \ref{satz:ode_getrennteVariablen} bestimmen.

Man sieht aber auch leicht, dass für beliebiges $a\in\R$ die Funktion $\vartheta_a\colon\R\to\R$ mit
\begin{equation*}
\vartheta_a(x) \ \coloneqq \ \frac1{27}(x-a)^3
\end{equation*}
die gewöhnliche Differentialgleichung \eqref{eq:bsp_dgl_nichteindeutig} erfüllt, denn es gilt
\begin{equation*}
\vartheta'_a(x) \ = \ \frac19(x-a)^2 \ = \ \left(\frac1{27}(x-a)^3\right)^{\frac{2}{3}} \ = \ \vartheta_a(x)^{\frac23}.
\end{equation*}

Obwohl die Lösung $\varphi$ und $\vartheta_0$ im Punkt $x_0 = a$ übereinstimmen mit
\begin{equation*}
\varphi_0(a) \, = \, \vartheta_a(a) \, = \, 0,
\end{equation*}
sieht man ein, dass der der Eindeutigkeitssatz \ref{satz:ode_eindeutigkeitssatz} nicht gilt.
Der Grund hierfür ist eine Verletzung der Voraussetzungen des Satzes, denn die Funktion $f(x,y) \coloneqq y^{\frac23}$ ist nicht für alle Punkte $y\in \R$ bezüglich der $y$-Variable Lipschitz-stetig.
Zwar ist $f$ für $y\neq 0$ stetig partiell differenzierbar bezüglich der Variablen $y$ mit
\begin{equation*}
\frac{\partial f}{\partial y}(x,y) \ = \ \frac23 y^{-\frac13}.
\end{equation*}
Nach Lemma \ref{lem:ode_lokalLipschitz} ist $f$ somit lokal Lipschitz-stetig in ganz $\R\times \R\setminus \{0\}$ in Bezug auf die $y$-Variable.
Jedoch ist $f$ in keiner Umgebung eines Punktes $(a,0)$ Lipschitz-stetig bezüglich de $y$-Variablen, da dieser Punkt eine Singularität mit unendlicher Steigung darstellt.
\end{bsp}

Der folgende wichtige Satz formuliert die hinreichenden Bedingungen für die Existenz von Lösungen einer gewöhnlichen Differentialgleichung.
\begin{satz}[Existenzsatz von Picard-Lindelöf]\label{satz:ode:picardlindeloef}
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
\end{satz}
\begin{proof}
Siehe \cite[§12, Satz 4]{forster}.
\end{proof}


Selbst wenn die Funktion $f$ der Differentialgleichung $y^\prime(x) = f(x,y(x))$ auf ganz $\R\times\R^n$ definiert ist und überall lokal Lipschitz-stetig bezüglich der $y$-Variablen ist, so kann eine Lösung, die die Anfangsbedingung $\varphi(x_0)=c$ erfüllt unter Umständen nur in einer sehr kleinen Umgebung von $x_0 \in \R$ definiert sein.
Dies wird durch das folgende Beispiel klar.
\begin{bsp}
Wir betrachten die folgende nichtlineare gewöhnliche Differentialgleichung erster Ordnung
\begin{equation*}
y^\prime(x) = 2x\cdot (y(x))^2\,.
\end{equation*}
Die Funktion $f(x,y) = 2xy^2$ ist offensichtlich auf ganz $\R\times\R$ definiert und stetig partiell differenzierbar bezüglich der Variable $y$ und somit nach Lemma  \ref{lem:ode_lokalLipschitz} lokal Lipschitz-stetig bezüglich der $y$-Variablen.

Wir suchen eine Lösung $\phi \colon \R \rightarrow \R$ der Differentialgleichung, die die Anfangswertbedingung $\varphi(0) = c$ erfüllt.
Für den Fall $c=0$ ist dies offensichtlich die konstante Funktion $\varphi(x) \equiv 0$ für alle $x\in\R$.
Für $c\neq0$ können wir die Lösung durch Trennung der Variablen (siehe Kapitel \ref{s:trennung_variablen}) wie folgt unter der Annahme $y(x) \neq 0$ berechnen:
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
\end{bsp}
