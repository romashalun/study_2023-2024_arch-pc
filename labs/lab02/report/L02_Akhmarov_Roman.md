---
## Front matter
title: "Отчёт по лабораторной работе №2"
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

Целью данной работы является изучить идеологию и применение средств
контроля версий, а также приобрести практические навыки по работе с системой
git.

# Теоретическое введение

Системы контроля версий (Version Control System, VCS) применяются при работе
нескольких человек над одним проектом. Обычно основное дерево проекта хранится в
локальном или удалённом репозитории, к которому настроен доступ для участников проекта. При внесении изменений в содержание проекта система контроля версий позволяет
их фиксировать, совмещать изменения, произведённые разными участниками проекта,
производить откат к любой более ранней версии проекта, если это требуется.

Система контроля версий Git представляет собой набор программ командной строки.
Доступ к ним можно получить из терминала посредством ввода команды git с различными
опциями.
Благодаря тому, что Git является распределённой системой контроля версий, резервную
копию локального хранилища можно сделать простым копированием или архивацией.


# Выполнение лабораторной работы
## Базовая настройка

Создаем учетную запись на сайте GitHub. Заполняем данные и регестрируем
аккаунт. В моем случае мое имя пользователя: «romashalun» (рис. @fig:fig1).

![Учетная запись GitHub](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/1.png){ #fig:fig1 }

Запускаю виртуальную машину, затем в терминале задаю
предварительную конфигурацию git. Ввожу команду git config –global
user.name “”, указывая свое имя и команду git config –global user.email
“work@mail”, указывая в ней электронную почту владельца, то есть
мою. (рис. @fig:fig2)

![](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/2.png){ #fig:fig2 }
![Конфигурация git](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/3.png)

Настраиваю utf-8 в выводе сообщений git для корректного отображения
символов(рис. @fig:fig3)

![Настройка](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/4.png){ #fig:fig3 }

Задаю имя «master» для начальной ветки (рис. @fig:fig4)

![Создание имени для ветки](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/5.png){ #fig:fig4 }

Задаю параметр autocrlf со значением input (рис. @fig:fig5)

![Параметр autocrlf](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/6.png){ #fig:fig5 }

Задаю параметр safecrlf со значением warn (рис. @fig:fig6).

![Параметр safecrlf](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/7.png){ #fig:fig6 }

## Создание SSH-ключа

ОВвожу комнаду ssh-keygen -C “имя фамилия, почта” , указываю свои данные.
Ключ сохранятся в каталоге ~/.ssh/. (рис. @fig:fig7)

![Генерация ssh-ключа](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/8.png){ #fig:fig7 }

Копирую открытый ключ из директории, в которой он был сохранен, с
помощью утилиты xclip. (рис. @fig:fig8)

![Копирование ключа](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/9.png){ #fig:fig8 }

Открываю свой профиль и выбираю страницу SSH and GPG key. Нажимаю
кнопку New SSH key и вставляю скопированный ключ в специальное поле и
называю своим именем.(рис. @fig:fig9)

![Добавление ключа](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/10.png){ #fig:fig9 }

## Создание рабочего пространства и репозитория курса на основе шаблона

Открываю терминал. Создаю директорию, рабочее пространство, с
помощью утилиты mkdir, благодаря ключу -p создаю все директории
после домашней ~/work/study/2023-2024/“Computer architecture”
рекурсивно. Далее проверяю с помощью ls, действительно ли были
созданы необходимые мне каталоги (рис. @fig:fig10)

![Создание рабочего пространства](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/11.png){ #fig:fig10 }

##  Создание репозитория курса на основе шаблона

В браузере перехожу на страницу репозитории с шаблонами курса.
Далее выбираю «Use this template», чтобы использовать этот шаблон для
своего репозитория.(рис. @fig:fig11)

![Использование шаблона](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/12.png){ #fig:fig11 }
![Созданны репозиторий](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/13.png){ #fig:fig11 }

Через терминал перехожу в созданный каталог курса с помощью утилиты cd(рис. @fig:fig12)

![Перемещение с помощью cd](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/14.png){ #fig:fig12 }

Копирую ссылку для клонирования на странице созданного репозитория,
сначала перейдя в окно
«code», далее выбрав в
окне вкладку «SSH» (рис. @fig:fig13)

![Окно с ссылкой для копирования репозитория](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/15.png){ #fig:fig13 }

Клонирую созданный репозиторий с помощью команды git clone – recursive git@github.com:/study_2023–2024_arh-pc.git arch-pc (рис. @fig:fig14)

![Клонирование репозитория](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/16.png){ #fig:fig14 }

## Настройка каталога курса

Перехожу в каталог arch-pc с помощью утилиты cd (рис. @fig:fig15)

![Перемещение между директориями](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/17.png){ #fig:fig15 }

Удаляю лишние файлы с помощью утилиты rm (рис. @fig:fig16)

![Удаление файлов](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/18.png){ #fig:fig16 }

Создаю необходимые каталоги. (рис. @fig:fig17)

![Создание каталогов](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/19.png){ #fig:fig17 }

Отправляю созданные каталоги на сервер и сохраняю изменения. (рис. @fig:fig18)

![Добавление и сохранение изменений на сервере ](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/20.png){ #fig:fig18 }

Отправляю все на сервер с помощью команды git push (рис. @fig:fig19)

![Выгрузка изменений на сервер](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/21.png){ #fig:fig19 }

Проверяю правильность выполнения работы на самом сайте GitHub. Вижу что
каталоги созданы недавно, это те которые мы отправили на сервер. (рис. @fig:fig20)

![Страница репозитория](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/22.png){ #fig:fig20 }






## Выполнение заданий для самостоятельной работы.

Перехожу в директорию labs/lab02/report с помощью утилиты cd.
Создаю в каталоге файл для отчета по третьей лабораторной
работе с помощью утилиты touch. (рис. @fig:fig21)

![Создание файла](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/24.png){ #fig:fig21 }

После открытия текстового редактора открываю в нем созданный
файл и могу начать в нем работу над отчетом. (рис. @fig:fig22)

![Работа с отчетом в текстовом редакторе](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/25.png){ #fig:fig22 }

Перехожу из подкаталога lab02/report в подкаталог lab01/report с
помощью утилиты cd. (рис. @fig:fig23)

![Перемещение между директориями](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/26.png){ #fig:fig23 }

Проверяю местонахождение файлов с отчетами по первой
лабораторной работe. Она должна быть в подкаталоге домашней
директории «Документы», для проверки использую команду ls.(рис. @fig:fig24)

![Проверка местанахождения файлов](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/27.png){ #fig:fig24 }

Копирую первую лабораторную с помощью утилиты cp и
проверяю правильность выполнения команды cp с помощью ls.(рис. @fig:fig25)

![Копирование файла](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/28.png){ #fig:fig25 }

Добавляю файл L01_Akhmarov_Report.doc на сервер.(рис. @fig:fig26)

![Добавление файла на сервер](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/33.png){ #fig:fig26 }

Сохраняю изменения на сервере командой git commit -m “…”,
поясняя, что добавил файлы. То же самое делаю для отчета по
третьей лабораторной работе: перехожу в директорию
labs/lab02/report с помощью cd, добавляю с помощью git add
нужный файл, сохраняю изменения с помощью git commit. (рис. @fig:fig27)

![Подкаталоги и файлы в репозитории](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/29.png){ #fig:fig27 }

Отправляю в центральный репозиторий сохраненные изменения
командой git push -f origin master. (рис. @fig:fig28)

![Отправка в центральный репозиторий сохраненных изменений](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/34.png){ #fig:fig28 }

Проверяю на сайте GitHub правильность выполнения заданий.
 Вижу, что отчеты по лабораторным работам находятся в
соответствующих каталогах репозитория.(рис. @fig:fig29)

![Каталог lab01, lab02/report](/home/rrakhmarov/work/study/2023-2024/Computer architecture/arch-pc/labs/lab02/report/image/31.png){ #fig:fig29 }




# Вывод

При выполнении данной лабораторной работы я изучила идеологию и
применение средств контроля версий, а также приобрела практические
навыки по работе с системой git. 

# Список литературы
1. https://esystem.rudn.ru/pluginfile.php/2091228/mod_resource/content/0/Лабораторная%20работа%20№2.%20Система%20контроля%20версий%20Git.pdf