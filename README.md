# Проект по сбору всей иерархии вложенных директорий в единый df и проведению операций над ним
## 1) Задача
Собрать все данные из папки **data** в один датафрэйм и выполнить необходимые операции c данными

Данные имеют следующую структуру:
- записываются для каждого пользователя, совершившего покупки, каждый день
- для каждой даты есть своя папка, внутри неё – папки для каждого пользователя
- внутри каждой папки есть файл data.csv, где и хранятся данные
Схематично выглядит так:
<p align="left" width="100%">
    <img width="33%" src="Scheme.png">
</p>

## 2) Стек
   - Python
       - pandas
       - seaborn
       - matplotlib.pyplot
       - OS Module

Specific functions:
- os.walk() store directories and filenames as df
- os.getcwd() to get the current working directory in Python
- drop_duplicates( ) and duplicated()
- merging data from 2 files merge()
- sns.barplot()

## 3) Этапы
- Просмотр папок и пр. операции, связанные с файлами и папками, выполняются с помощью библиотеки os. При вложенности папок и необходимости добраться до дна можно использовать os.walk
- Создаём список путей до нижнего уровня, отбирая соответствующие директории по длине пути
- Из директорий, найденныех ранее при помощи os.walk извлекаем содержимое csv файла
- Добавляем в df х столбец, где название директории бьём на названия папок отделенных '/' и добавляем поле с именем
- Складываем в один df все выгружаемые циклом данные
- Отбираем топ-10 товаров по числу проданных единиц за всё время и построить барплот (столбчатую диаграмму, sns.barplot)
- Через drop_duplicates находим дубликаты по трём полям 'product_id', 'name', 'date' и удаляем их

## 4) Результат

*Из файлового дерева сложили всю иерархию в один df и назвали столбцы по назывнию файлов:*
<p align="left" width="100%">
    <img width="33%" src="df.png">
</p>

*Сгруппировали и изуализировали топ-10 товаров по числу проданных единиц за всё время:*
<p align="left" width="100%">
    <img width="33%" src="Barplot.png">
</p>


