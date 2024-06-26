# Лабораторная работа № 5 - Списки

**Время выполнения - 6 часов**

## Содержание

___

1. [Общие теоретические сведения](#общие-теоретические-сведения)
2. [Практические задания](#практические-задания)
3. [Задания для самостоятельного выполнения (по вариантам)](#задания-для-самостоятельного-выполнения-по-вариантам)
    * [Задание 1](#задание-1-написать-программу)
    * [Задание 2](#задание-2-написать-программу)
4. [Контрольные вопросы](#контрольные-вопросы)
5. [Содержание отчета](#содержание-отчета)

## Цель работы:

___

Ознакомиться с понятием "список" в языке программирования Python.

## Задачи работы:

___

1. Изучить понятие "список" в языке программирования Python;
2. Изучить способы задания списка;
3. Изучить основные методы по работе со списками в языке программирования Python;
4. Научиться выводить элементы списка на экран.

## Общие теоретические сведения

___
Список в языке Python представляет собой структуру для хранения объектов
различных типов. Элементы одного списка могут иметь одинаковый тип, но
допускаются и смешанные типы. Элементы списка заключаются в квадратные скобки.
Все элементы проиндексированы (пронумерованы), начиная с 0.

```python
L = []  # Пустой список  
L = [5, 10, 15, 20]  # Четыре элемента с индексами 0..3
L = ['pqr', ['abc', 'xyz']]  # Вложенные списки
```

Списки в Python, с одной стороны, похожи на массивы в других языках
программирования, например Pascal, но, с другой стороны, имеется ряд отличий.
Например, Python размещает элементы списка в памяти, затем размещает указатели на
эти элементы. Таким образом, список в Python – это массив указателей.

Опишем ряд существенных свойств списков в языке Python. Можно обращаться к
элементу списка по его индексу, начиная с 0. В языке Python также используют
отрицательную индексацию, которая начинается с индекса –1, при этом индекс –1
относится к последнему элементу списка. В таблице представлены различные виды
индексации элементов списка.

|                      |    |    |    |    |    |    |
|:--------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
|       Список L       | 8  | -2 | 6  | 1  | 0  | 2  |
|        Индекс        | 0  | 1  | 2  | 3  | 4  | 5  |
| Отрицательный индекс | -6 | -5 | -4 | -3 | -2 | -1 |

Например, элемент `L[3]` равен 1, а элемент `L[–4]` равен 6.
Список в языке Python может иметь переменную длину. Например, можно удалять
элементы списка. Оператор `del list[i]` удаляет из списка list элемент с индексом i, `del L[2]`
удаляет элемент с индексом 2.

Далее рассмотрим способы задания списка в языке Python.
Можно непосредственно задать список, перечислив его элементы в квадратных
скобках через запятую:

```python
l = [4, 8, 10]
```

Также можно использовать функцию range, описанную ранее:

```python
a = list(range(20))
```

В результате сформируется список значений от 0 до 19. Для задания элементов
списка случайным образом можно использовать функцию randint из модуля random.
Например:

```python
from random import randint

a = [randint(-10, 10) for i in range(20)]
print(a)
```

В данном примере формируется список из 20 элементов, заданных случайным
образом.

Ещё один вариант – задать список с клавиатуры:

```python
a = [input() for i in range(10)]
```

Для формирования списка с клавиатуры можно использовать следующий вариант:

```python
a = []
n = int(input())
for i in range(n):
    k = int(input())
    a.append(k)
print(a)
```

Для получения доступа к элементам списка можно использовать следующие
конструкции:

```python
for x in ['abc', 'cde', 'efg']:
    print(x)

# ИЛИ

l = ['abc', 'cde', 'efg']
for x in l:
    print(x)
```

При работе со списками в языке Python часто используют срезы. Эти конструкции
нужны, чтобы обрезать список, взяв лишь те элементы, которые нам требуются. Срезы
работают по следующей схеме:

`list[начало: конец: шаг]`

Здесь:

* начало указывает, с какого элемента нужно начать (по умолчанию равно 0);
* конец указывает, по какой элемент берутся элементы (по умолчанию равен длине списка);
* шаг определяет, с каким шагом берутся элементы, например каждый второй или третий (по умолчанию каждый первый).

Приведём примеры работы со срезами.

```python
l = [2, 4, 6, 8, 10, 12, 14, 16]
print(l[2::2])  # Пример выборки из списка каждого второго элемента, начиная со второго
print(l[::3])  # Пример выборки из списка каждого третьего элемента
l = l[1:6:1]  # Пример изменения существующего списка. В списке остаются только элементы со второго по шестой
print(l)
```

В языке Python доступно достаточно много встроенных методов для обработки
списков. Некоторые из них описаны в таблице

|        **Метод**         |                                                                            **Описание**                                                                             |
|:------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|       `append(x)`        |                                                                Добавляет элемент `x` в конец списка                                                                 |
|        `clear()`         |                                                                           Очищает список                                                                            |
|         `copy()`         |                                                                       Возвращает копию списка                                                                       |
|        `count(x)`        |                                                       Возвращает количество элементов списка со значением `x`                                                       |
|       `extend(L)`        |                                                 Расширяет список путем добавления в него всех элементов списка `L`                                                  |
| `index(x[,start[,end]])` | Возвращает индекс первого элемента со значением `x` (при этом поиск ведётся от `start` до `end`; если `start` и `end` не указываются, то начиная с нулевой позиции) |
|      `insert(i, x)`      |                                                           Вставляет в список на i-ю позиция значение `x`                                                            |
|         `pop(i)`         |                                 Удаляет из списка i-й элемент и возвращает его. Если индекс не указан, удаляется последний элемент                                  |
|       `remove(x)`        |                         Удаляет первый элемент в списке, имеющий значение `x`. Возвращает `ValueError`, если такого элемента не существует                          |
|       `reverse()`        |                                                                        Переворачивает список                                                                        |
|         `sort()`         |                                                                          Сортирует список                                                                           |

Поскольку данные методы являются методами класса «список», то обращение к
ним имеет вид: `<имя списка>.<имя метода>`

Рассмотрим несколько примеров по работе с описанными функциями.

```python
l = [2, 4, 6, 8, 10, 12, 14, 16]
print(l.index(4))  # Вывод на экран индекса элемента, равного 4
print(l.count(12))  # Вывод количества элементов в списке, равных 12
l.append(0)  # В конец списка добавляется новый элемент – 0
print(l)
z = [3, 7, 10]
l.extend(z)  # Расширение списка l за счет добавления элементов списка z
print(l)
```

## Практические задания

___ 

1. Задать числовой список случайным образом. Заменить значения элементов в списке на их квадраты;
2. Задан числовой список, вывести на экран те значения списка, которые встречаются в нём более одного раза.
3. Найти в списке наибольший и наименьший элементы. Вывести их индексы на экран.
4. Дан список некоторых целых чисел, поискать в нём значение 20 и, если оно присутствует, заменить его на 200.

## Задания для самостоятельного выполнения (по вариантам)

___

### Задание 1. Написать программу

| **Вариант** | **Алгоритм сортировки 1** | **Алгоритм сортировки 2** | **Алгоритм сортировки 3** |
|:-----------:|:--------------------------|:--------------------------|:--------------------------|
|      1      | Сортировка выбором        | Сортировка слиянием       | Сортировка Шелла          | 
|      2      | Сортировка обменом        | Сортировка Шелла          | Гномья сортировка         |  
|      3      | Шейкерная сортировка      | Быстрая сортировка        | Сортировка расческой      |   
|      4      | Сортировка слиянием       | Сортировка вставками      | Гномья сортировка         |   
|      5      | Сортировка Шелла          | Гномья сортировка         | Сортировка слиянием       |   
|      6      | Быстрая сортировка        | Сортировка расческой      | Сортировка вставками      |    
|      7      | Сортировка вставками      | Сортировка выбором        | Шейкерная сортировка      |     
|      8      | Гномья сортировка         | Сортировка обменом        | Сортировка выбором        |      
|      9      | Сортировка расческой      | Шейкерная сортировка      | Сортировка Шелла          |      
|     10      | Сортировка выбором        | Сортировка слиянием       | Сортировка Шелла          |      
|     11      | Сортировка обменом        | Сортировка Шелла          | Гномья сортировка         |      
|     12      | Шейкерная сортировка      | Быстрая сортировка        | Сортировка расческой      |      
|     13      | Сортировка слиянием       | Сортировка вставками      | Гномья сортировка         |      
|     14      | Сортировка Шелла          | Гномья сортировка         | Сортировка слиянием       |      
|     15      | Быстрая сортировка        | Сортировка расческой      | Сортировка вставками      | 

### Задание 2. Написать программу

На соревнованиях восемь арбитров каждому участнику выставляют баллы от 1 до 10.
Создайте список (список списков) выставленных баллов шести участникам каждым из
арбитров. Перед подсчетом среднего балла из оценок выбрасывают наименьшее и
наибольшее значения (экстремальные значения), а затем считают средний балл (среднее
арифметическое). Создайте список средних баллов участников соревнований.

Например, исходные данные (список баллов):

`[[2,5,7,3,6,4,6,5],[3,5,4,6,7,5,4,6],[5,6,6,5,7,4,5,8],[7,8,9,7,5,6,7,8],[4,7,3,8,6,5,5,7], [8,7,9,5,7,7,6,8]]`

Список после удаления экстремальных значений:

`[[5, 3, 6, 4, 6, 5], [5, 4, 6, 5, 4, 6], [5, 6, 6, 5, 7, 5], [7, 8, 7, 6, 7, 8], [4, 7, 6, 5, 5, 7], [8, 7, 7, 7, 6, 8]]`

Список средних баллов участников соревнований:

`[4.833333333333333, 5.0, 5.666666666666667, 7.166666666666667, 5.666666666666667, 7.166666666666667]`

## Контрольные вопросы

___

1. Какова основная задача сортировки?
2. Какие виды сортировки вы знаете?
3. Дайте определение списка в языке программирования Python. Приведите
примеры списков?
4. Как можно обратиться к элементу списка в языке программирования Python?
5. Для чего используется срез при работе со списками в языке Python?
6. Какие основные встроенные методы для работы со списками в языке Python вы
можете назвать?
7. Какой функцией надо воспользоваться для подсчёта количества элементов с
данным значением в списке?

## Содержание отчета

___

1. Титульный лист
2. Цель и задачи работы
3. Задание
4. Описание выполнения алгоритма
5. Исходный код программы
6. Результаты работы программы
7. Ответы на контрольные вопросы.
8. Общий вывод о проделанной работе.