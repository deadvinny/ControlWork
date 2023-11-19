# Итоговая контрольная работа по основному блоку

## Условия.

1. Создать репозиторий на GitHub.
2. Нарисовать блок-схему алгоритма (можно обойтись блок-схемой основной содержательной части, если вы выделяете её в отдельный метод).
3. Снабдить репозиторий оформленным текстовым описанием решения (файл README.md).
4. Написать программу, решающую поставленную задачу.
5. Использовать контроль версий в работе над этим небольшим проектом (не должно быть так, что всё залито одним коммитом, как минимум этапы 2, 3, и 4 должны быть расположены в разных коммитах).

*Задача:* Написать программу, которая из имеющегося массива строк формирует новый массив из строк, длина которых меньше, либо равна 3 символам. 
Первоначальный массив можно ввести с клавиатуры, либо задать на старте выполнения алгоритма.

Примеры:
* [“Hello”, “2”, “world”, “:-)”] → [“2”, “:-)”]
* [“1234”, “1567”, “-2”, “computer science”] → [“-2”]
* [“Russia”, “Denmark”, “Kazan”] → []

&#9757;**Важно!**
  
**При решении не рекомендуется пользоваться коллекциями, лучше обойтись исключительно массивами.**

## Блок-схема.

![Блок-схема](scheme.png)

## Текстовое описание решения.

    ﻿Console.WriteLine("Введите элементы массива через пробел:");
    string input = Console.ReadLine();
    string[] inputArray = input.Split(new[] { ' ' },StringSplitOptions.RemoveEmptyEntries);

    int count = 0; 
    for (int i = 0; i < inputArray.Length; i++)
    {
        if (inputArray[i].Length <= 3)
        {
            count++;
        }
    }

    string[] resultArray = new string[count];
    int index = 0; 
    for (int i = 0; i < inputArray.Length; i++)
    {
        if (inputArray[i].Length <= 3)
        {
            resultArray[index] = inputArray[i];
            index++;
        }
    }

    string inputOutput = string.Join("\", \"", inputArray);
    string resultOutput = string.Join("\", \"", resultArray);
    Console.WriteLine($"[\"{inputOutput}\"] -> [\"{resultOutput}\"]");

### Текстовое описание решения с комментариями.
Считаю необходимым снабдить готовое решение комментариями.

    ﻿Console.WriteLine("Введите элементы массива через пробел:");
    string input = Console.ReadLine();
    string[] inputArray = input.Split(new[] { ' ' },StringSplitOptions.RemoveEmptyEntries);
    //Split - разделение. В качестве разделителя используется пробел.
    //StringSplitOptions.RemoveEmptyEntries - удаление пустот.
    //Если, например, пробел случайно был нажат более одного раза, или пробел был нажат после введения последнего элемента.

    //1.1 Подсчет количества элементов, длина которых менее либо равна трем символам.

    int count = 0; // Переменная для подсчета кол-ва выполненных условий (количество строк, длина которых меньше, либо равна 3 символам)
    for (int i = 0; i < inputArray.Length; i++)
    {
        if (inputArray[i].Length <= 3) // проверяем длину каждой строки (элемента) в массиве, который мы ввели.
        {
            count++; 
        }
    }

    string[] resultArray = new string[count]; // в зависимости от count в новом массиве будет count строк (элементов).
    //Например, ввели 5 строк, из них 2  - подходят под условия, значит, у нас будет новый массив с двумя элементами.


    //2. ЗАПОЛЕНЕНИЕ НОВОГО МАССИВА ЭЛЕМЕНТАМИ С СИМВОЛАМИ, ПРОШЕДШИХ ПРОВЕРКУ.

    int index = 0; // (счетчик, индекс) нового массива. 
    for (int i = 0; i < inputArray.Length; i++)
    {
        if (inputArray[i].Length <= 3)
        {
            resultArray[index] = inputArray[i];
            index++;
        }
    }
    
    string inputOutput = string.Join("\", \"", inputArray);
    string resultOutput = string.Join("\", \"", resultArray); 
    //Переменные inputOutput и  resultOutput объявлены для удобства форматированного вывода массивов в виде, который приведен в примере.

    Console.WriteLine($"[\"{inputOutput}\"] -> [\"{resultOutput}\"]");
