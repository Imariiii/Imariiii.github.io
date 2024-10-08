# Функциональный язык программирования
[Онлайн-редактор](http://51.250.105.118:8080/)
1. [Авторы](#авторы)
2. [Реализованный функционал](#реализованный-функционал)
3. [Основные типы данных](#основные-типы-данных)
4. [Синтаксис](#синтаксис)
5. [Описание интерпретатора](#описание-интерпретатора)
6. [Примеры](#примеры)
    - [Объявление переменных](#объявление-переменных)
    - [Объявление функций](#объявление-функций)
    - [Пример факториала](#пример-факториала)
    - [Пример счетчика с использованием замыкания](#пример-счетчика-с-использованием-замыкания) 
7. [Библиотеки и платформы](#библиотеки-и-платформы)
8. [Использование ИИ](#использование-ии)

## Авторы

|       Имя       |                  Роль в проекте                  |
|:---------------:|:------------------------------------------------:|
|  Ибрагимов Далгат  |                        |
| Останина Анна | технический писатель |
| Юнусов Рустам  |  |

## Реализованный функционал
В языке реализованы:
* [x] Именованные привязки (`let`)
* [x] Рекурсия
* [ ] Ленивое вычисление
* [x] Функции
* [x] Замыкания
* [ ] Библиотечные функции: ввод-вывод файлов
* [ ] Списки / Последовательности
* [ ] Библиотечные функции: списки/последовательности

А также: 
 - ```sigillum <expr>;```
   (выводит объект на экран)
## Основные типы данных

 - IntVal (целые числа)

Представление целых чисел, например, IntVal n.
 - BoolVal (булевы значения)

 - Логические значения (BoolVal true/false).
 - FunVal (функции)

Функции представлены как замыкания, хранящие имя параметра, тело функции и окружение.
 - Env (окружение), список пар вида (переменная, значение), который используется для хранения переменных и их значений.

## Синтаксис


### Арифметические операции

Пример: 

```
1 additamentum 2
``` 
(сложение)

```
3 multiplicatio 4
```
(умножение)
### Условные выражения

Примеры: 

```
si 1  pares 1
deinde  sigillum 3
aliter sigillum 4
;
```

```
si x plus_quam 2 deinde y aliter z
```


### Функции

Пример: 

```
munus x -> x additamentum 1
```
### Объявление переменных

Пример: 

```
sit x assign 3 in x additamentum 1
```
### Функциональное применение

Пример: 

```
f(1, 2)
```


## Описание интерпретатора
### Парсер

Используется библиотека FParsec для разбора входного синтаксиса. Парсер разбирает выражения в виде деревьев синтаксиса (Expr).
### Интерпретатор

Интерпретатор рекурсивно обрабатывает выражения, поддерживает операции с целыми числами и логические сравнения. Он также выполняет функции и позволяет создавать замыкания.
Пример использования: функция eval обрабатывает выражения в зависимости от их типа: если это число — возвращает его значение, если функция — создает замыкание, и так далее.
### Окружение

Окружение хранит переменные и их значения. При каждом вызове функции создается новое окружение, что позволяет поддерживать локальную область видимости.
Ошибка времени выполнения

В коде предусмотрена обработка ошибок через исключения (RuntimeError), например, при попытке доступа к несуществующей переменной или делении на ноль.

## Примеры

### Объявление переменных
```
sit x assign 10 in x additamentum 5;
```
Этот пример создает переменную x, присваивает ей значение 10, а затем использует ее для вычисления выражения x + 5, результатом которого будет 15.

### Объявление функций
```
munus x -> x multiplicatio x;
```
Этот пример определяет функцию, которая принимает один аргумент x и возвращает его квадрат (результат операции умножения).

Пример вызова функции:
```
munus x -> x multiplicatio x (4);
```
### Пример факториала
```
sit factorial assign munus n -> 
    si n pares 0 
    deinde 1 
    aliter n multiplicatio (factorial (n detractio 1));

factorial(5);
```
Этот пример вычисляет факториал числа 5. Функция рекурсивно вызывает сама себя, пока аргумент n не станет равным 0, возвращая произведение всех чисел от 1 до n.
### Пример счетчика с использованием замыкания
```
sit createCounter assign 
    munus initial -> 
        sit count assign initial in 
        munus () -> 
            sit newCount assign count additamentum 1 in 
            count assign newCount in 
            newCount;

sit counter assign createCounter(0) in 
counter();
counter();
counter();
```
Этот пример демонстрирует использование замыкания для создания счетчика. Внутренняя функция хранит состояние переменной count, которая увеличивается на единицу при каждом вызове функции counter.

## Библиотеки и платформы

Реализация языка программирования происходила при помощи библиотеки __fparsec__ и платформы __.NET__ версии _net8.0_

## Использование ИИ

Языковые модели оказались полезными для решения различных задач, включая:

 - Форматирование markdown файлов: улучшение их визуального представления и удобства чтения.
 - Организация текста отчёта.
 - Поиск информации для запуска и настройки проектов на .NET, что помогает избежать ошибок и задержек в процессе разработки.
 - Ответы на вопросы по F# и fparsec, что устраняет недоразумения в работе с языком и ускоряет процесс обучения.

Таким образом, использование ИИ в проекте значительно улучшило процесс разработки, сократило время на рутинные задачи и повысило эффективность работы команды.
