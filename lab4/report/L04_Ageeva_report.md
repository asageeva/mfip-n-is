---
# Титульный лист
title: |
    Отчёт по лабораторной работе №4  
    Вычисление наибольшего общего делителя
author:
- "Студент: Агеева Анастасия Сергеевна, 1032212304"
- "Группа: НФИмд-02-21"
- "Преподаватель: Кулябов Дмитрий Сергеевич,"
- "д-р.ф.-м.н., проф."
date: "Москва 2021"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

# Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Pdf output format
toc: true # Содержание
toc_depth: 2
lof: true # Список изображений
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric

## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text

  - \usepackage{titling}
  - \setlength{\droptitle}{-9em}
  - \pretitle{\begin{center}
      \textbf{РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ}\\
      \textbf{Факультет физико-математических и естественных наук}\\
      \textbf{Кафедра прикладной информатики и теории вероятностей}
      \vspace{9cm}
      \LARGE\\}
  - \posttitle{\vskip 1em \Large \emph{\textit{Дисциплина$:$ Математические основы защиты информации и информационной безопасности}} \end{center}}
  - \preauthor{\vskip 3em \begin{flushright} \large \begin{tabular}[t]{c}}
  - \postauthor{\end{tabular}\par\end{flushright} \vfill \vskip 5em}
---

# Цель работы

Цель данной лабораторной работы изучение нахождения наибольшего общего делителя при помощи алгоритма Евклида и его адаптаций.

# Задание

1.  Реализовать алгоритм Евклида;
1.  Реализовать бинарный алгоритм Евклида;
1.  Реализовать расширенный алгоритм Евклида;
1.  Реализовать расширенный бинарный алгоритм Евклида.

# Теоретическое введение

## Алгоритм Евклида

**Алгори́тм Евкли́да** — эффективный алгоритм для нахождения наибольшего общего делителя двух целых чисел (или общей меры двух отрезков) [@euclid].

В самом простом случае алгоритм Евклида применяется к паре положительных целых чисел и формирует новую пару, которая состоит из меньшего числа и разницы между большим и меньшим числом. Процесс повторяется, пока числа не станут равными. Найденное число и есть наибольший общий делитель исходной пары. 

Для данного алгоритма существует множество теоретических и практических применений. В частности, он является основой для криптографического алгоритма с открытым ключом RSA, широко распространённого в электронной коммерции. Также алгоритм используется при решении линейных диофантовых уравнений, при построении непрерывных дробей, в методе Штурма. Алгоритм Евклида является основным инструментом для доказательства теорем в современной теории чисел, например таких как теорема Лагранжа о сумме четырёх квадратов и основная теорема арифметики.

## Бинарный алгоритм Евклида

**Бинарный алгоритм Евклида** — метод нахождения наибольшего общего делителя двух целых чисел [@bi_euclid]. Данный алгоритм "быстрее" обычного алгоритма Евклида, т.к. вместо медленных операций деления и умножения используются сдвиги.

**Он основан на использовании следующих свойств НОД**:

- НОД(2m, 2n) = 2 НОД(m, n),
- НОД(2m, 2n+1) = НОД(m, 2n+1),
- НОД(-m, n) = НОД(m, n).

## Расширенный алгоритм Евклида

**Расширенный алгоритм Евклида** — это алгоритм определения коэффициентов, позволяющих выразить наибольший общий делитель числовой пары через эти два числа, т.е. вычислить *d = НОД (a, b)* и в то же самое время вычислить значения *x* и *y*, такие что *ax + by = d* [@ex_euclid].

## Расширенный бинарный алгоритм Евклида

Расширенный бинарный алгоритм Евклида является, как очевидно из названия, квинтэссенцией расширенного и бинарного алгоритмов. Таким образом, при вычислении НОД используются сдвиги, как в бинарном алгоритме, и при этом на выходе можно получить значения коэффициентов *x* и *y*, как в расширенном алгоритме.

# Выполнение лабораторной работы

1. **Реализация алгоритма Евклида**

   1. Задам функцию *euclid()*, в которую буду передавать два числа. По алгоритму Евклида найду НОД и передам его как результат выполнения функции. 

   2. Вызову функцию для чисел 12345 и 24690. Алгоритм верно находит НОД = 12345.

      ![Алгоритм Евклида](image/euclid.jpg){#fig:001 width="70%"}

2. **Реализация бинарного алгоритма Евклида**

   1. Задам функцию *binary_euclid()*, в которую буду передавать два числа. По бинарному алгоритму Евклида найду НОД и передам его как результат выполнения функции.

   2. Вызову функцию для чисел 12345 и 24690. Алгоритм верно находит НОД = 12345.

      ![Бинарный алгоритм Евклида](image/bi_euclid.jpg){#fig:002 width="70%"}

3. **Реализация расширенного алгоритма Евклида**

   1. Задам функцию *extended_euclid()*, в которую буду передавать два числа. По расширенному алгоритму Евклида найду НОД, коэффициенты *x* и *y*, затем передам их как результат выполнения функции.

   2. Вызову функцию для чисел 12345 и 24690. Алгоритм верно находит НОД = 12345, *x = 1* и *y = 0*: 12345х1 + 24690х0 = 12345.

      ![Расширенный алгоритм Евклида](image/ex_euclid.jpg){#fig:003 width="70%"}

4. **Реализация расширенного  бинарного алгоритма Евклида**

   1. Задам функцию *ext_bi_euclid()*, в которую буду передавать два числа. По расширенному бинарному алгоритму Евклида найду НОД, коэффициенты *x* и *y*, затем передам их как результат выполнения функции.
   
   2.  Вызову функцию для чисел 12345 и 24690. Алгоритм верно находит НОД = 12345, *x = 1* и *y = 0*: 12345х1 + 24690х0 = 12345.
      ![Расширенный бинарный алгоритм Евклида (1)](image/ex_bi_euclid1.jpg){#fig:004 width="70%"}
      
      ![Расширенный бинарный алгоритм Евклида (2)](image/ex_bi_euclid2.jpg){#fig:005 width="70%"}

# Выводы

В ходе данной лабораторной работы я реализовала четыре алгоритма нахождения НОД.

# Список литературы {#список-литературы .unnumbered}
