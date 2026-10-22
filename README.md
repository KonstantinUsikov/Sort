# Sort

Сравнение скорости работы алгоритмов сортировки: пузырьком, вставками, слиянием и быстрой сортировки.

## Возможности

- Четыре алгоритма сортировки (`ClassLibrarySort/Sort.cs`): пузырьком, вставками, слиянием и быстрая сортировка.
  Все методы обобщённые (`T : IComparable<T>`), поддерживают сортировку по возрастанию и по убыванию и прерывание через `CancellationToken`.
- Генерация массивов случайных значений: `int`, `long`, `double` и строк из заглавных латинских букв.
- Графический интерфейс на WinForms:
  - выбор типа данных, минимального и максимального значения (для строк — длины);
  - количество элементов — до 1 000 000;
  - количество тестовых прогонов — до 1000;
  - вывод отсортированного массива и среднего времени работы каждого алгоритма в мс.

  Каждый алгоритм выполняется в отдельном потоке.

## Структура решения

| Проект             | Описание                                                    |
|--------------------|-------------------------------------------------------------|
| `ClassLibrarySort` | Библиотека с алгоритмами сортировки и генераторами массивов |
| `WinFormsSort`     | Основное приложение с графическим интерфейсом               |
| `ConsoleSort`      | Временное консольное приложение для ручной проверки         |
| `TestProjectSort`  | Модульные тесты (MSTest)                                    |

## API

```csharp
using ClassLibrarySort;

var arr = Sort.GenerateArrayInt(-100, 100, 10);
Sort.QuickSort(arr, true, CancellationToken.None);
```

Генерация массивов:

```csharp
int[]    GenerateArrayInt(int min, int max, long n)
long[]   GenerateArrayLong(long min, long max, long n)
double[] GenerateArrayDouble(double min, double max, long n)
string[] GenerateArrayString(int minLen, int maxLen, long n)
```

Сортировки (`ascending`: `true` — по возрастанию, `false` — по убыванию):

```csharp
void BubbleSort<T>(T[] arr, bool ascending, CancellationToken ct)
void InsertSort<T>(T[] arr, bool ascending, CancellationToken ct)
void MergeSort<T>(T[] arr, bool ascending, CancellationToken ct)
void QuickSort<T>(T[] arr, bool ascending, CancellationToken ct)
```

## Требования

- [.NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
- Windows (для WinForms-приложения)

## Сборка и запуск

```
dotnet build Sort.sln
dotnet run --project WinFormsSort
dotnet test TestProjectSort
```
