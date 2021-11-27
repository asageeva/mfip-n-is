---
# Титульный лист
title: |
    Отчёт по лабораторной работе №3  
    Шифрование гаммированием
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

Цель данной лабораторной работы изучение реализация алгоритма шифрования гаммированием.

# Задание

1.  Реализовать программно шифрование гаммированием.

# Теоретическое введение

## Гаммирование

**Гамми́рование**, или **Шифр XOR**, — метод симметричного шифрования, заключающийся в «наложении» последовательности, состоящей из случайных чисел, на открытый текст. Последовательность случайных чисел называется гамма-последовательностью и используется для зашифровывания и расшифровывания данных [@cypher].

В этом способе шифрование выполняется путем сложения символов исходного текста и ключа по модулю, равному числу букв в алфавите. Если в исходном алфавите, например, 33 символа, то сложение производится по модулю 33. Такой процесс сложения исходного текста и ключа называется в криптографии **наложением гаммы** [@intuit].

## Пример

Пусть символам исходного алфавита соответствуют числа от 0 (А) до 32 (Я). Если обозначить число, соответствующее исходному символу, x, а символу ключа – k, то можно записать правило гаммирования следующим образом:

*z = x + k (mod N)*,

где *z* – закодированный символ, *N* - количество символов в алфавите, а сложение по модулю *N* - операция, аналогичная обычному сложению, с тем отличием, что если обычное суммирование дает результат, больший или равный *N*, то значением суммы считается остаток от деления его на *N*. Например, пусть сложим по модулю 33 символы Г (3) и Ю (31):

*3 + 31 (mod 33) = 1*,

то есть в результате получаем символ Б, соответствующий числу 1.

# Выполнение лабораторной работы

1.  Подключение библиотек.

    ![Подключение библиотеки](image/numpy.jpg){#fig:001 width="70%"}

2. **Реализация шифрования гаммированием**

   1.  В качестве начальных значений берется гамма "гамма". Алфавитом
       может быть любая строка неповторяющихся символов. Я использую
       кириллицу. Также задаю строку сообщение, которое будет
       шифроваться. 

   ![Начальные значения для шифрования гаммированием](image/insert.jpg){#fig:002 width="70%"}

   2.  Задам функцию *gamming()*, в качестве параметров передаются
       заданные начальные данные. Внутри функции ключ-гамма, алфавит и
       сообщение преобразую в массив. Затем увеличу длину ключа-гаммы, чтобы число символов совпадало с сообщением, делаю это дописывая ключ пока длина не будет равной или больше сообщению, лишние символы отсекаю. Затем нахожу индексы символов сообщения и ключа в алфавите и сохраняю их в массиве. В новый массив сохраняю символы, рассчитав индексы по формуле *z = x + k (mod N)*. Полученный массив преобразую в строку и возвращаю.

   ![Функция шифрования gamming()](image/function.jpg){#fig:003 width="70%"}

   3.  Выведу результат работы программы для заданных начальных
       значений. 

   ![Результат выполнения программы](image/result.jpg){#fig:004 width="70%"}

# Выводы

В ходе данной лабораторной работы я реализовала алгоритм шифрования гаммированием.

# Список литературы {#список-литературы .unnumbered}
