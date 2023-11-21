---
## Front matter
title: "Отчёт по лабораторной работе №3"
subtitle: "Дисциплина: архитектура компьютера"
author: "Ахмаров Роман"
## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
    - spelling=modern
    - babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
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
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы
Целью данной лабораторной работы является освоение процедуры оформления отчетов с помощью легковесного языка разметки Markdown.
# Задание
1. Заполнение отчета по выполнению лабораторной работы №3 с помощью языка разметки Markdown
2. Задание для самостоятельной работы


# Теоретическое введение
Markdown - легковесный язык разметки, созданный с целью обозначения форматирования в простом тексте, с максимальным сохранением его читаемости человеком, и пригодный для машинного преобразования в языки для продвинутых публикаций. Внутритекстовые формулы делаются аналогично формулам LaTeX. В Markdown вставить изображение в документ можно с помощью непосредственного указания адреса изображения. Синтаксис Markdown для встроенной ссылки состоит из части [link text], представляющей текст гиперссылки, и части (file-name.md) – URL-адреса или имени файла, на который дается ссылка. Markdown поддерживает как встраивание фрагментов кода в предложение, так и их размещение между предложениями в виде отдельных огражденных блоков. Огражденные блоки кода — это простой способ выделить синтаксис для фрагментов кода.


# Выполнение лабораторной работы
## Заполнение отчета по выполнению лабораторной работы №4 с помощью языка разметки Markdown

Открываю терминал. Перехожу в каталог курса, сформированный при выполненнии прошлой лаборатной работы (рис. @fig:fig1).

![Перемещение между директориями](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/1.png){ #fig:fig1 }

Обновляю локальный репозиторий, скачав изменения из удаленного репозитория с помощью команды git pull (рис. @fig:fig2)

![Обновление локального репозитория](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/2.png){ #fig:fig2 }

Перехожу в каталог с шаблоном отчета по лабораторной работе №3 с помощью cd.Компилирую шаблон с использованием Makefile, вводя команду make (рис. @fig:fig3)

![Компиляция шаблона](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/3.png){ #fig:fig3 }

Открываю сгенерированный файл report.docx в LibreOffice (рис. @fig:fig4)

![Открытие файла docx](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/4.png){ #fig:fig4 }

Далее открываю файл report.pdf и убеждаюсь, что все правильно работаает (рис. @fig:fig5)

![Открытие файла pdf](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/5.png){ #fig:fig5 }

Удаляю полученные файлы с использованием Makefile, вводя команду make clean (рис. @fig:fig6). С помощью команды ls проверяю, удалились ли созданные файлы.

![Удаление файлов](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/6.png){ #fig:fig6 }

Открываю файл report.md с помощью текстового редактора mousepad (рис. @fig:fig7)

![Открытие файла report.md](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/7.png){ #fig:fig7 }

Далее на всякий случай сохраню файл, создам и скопирую тот же файл, но с названием моего отчета (рис. @fig:fig8)

![Копирование файла с новым именем](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/8.png){ #fig:fig8 }

Начинаю заполнять отчет с помощью языка разметки Markdown в скопированном файле (рис. @fig:fig9)

![Заполнение отчета](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/9.png){ #fig:fig9 }

Компилирую файл с отчетом. Загружаю отчет на Github. (рис. @fig:fig10)

![Заполнение отчета](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/10.png){ #fig:fig10 }




## Выполнение заданий для самостоятельной работы.

Перехожу в директорию lab02/report с помощью cd, чтобы там заполнять отчет по второй лабораторной работе (рис. @fig:fig11).

![Перемещение между директориями](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/11.png){ #fig:fig11 }

Копирую файл L03_Akhmarov_Roman.md с новым именем для заполнения отчета (рис. @fig:fig12).

![Копирование файла](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/12.png){ #fig:fig12 }

Открываю файл с помощью текстового редактора mousepad и начинаю заполнять отчет (рис. @fig:fig13).

![Работа над отчётом](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab03/report/image/13.png){ #fig:fig13 }



# Выводы



# Список литературы

1. https://esystem.rudn.ru/pluginfile.php/1584628/mod_resource/content/1/%D0%9B%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%E2%84%965.pdf