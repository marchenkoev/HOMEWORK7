// Задача 47: Задайте двумерный массив размером m×n, заполненный случайными вещественными числами.

Console.Write("m: ");
int m = Convert.ToInt32(Console.ReadLine());
Console.Write("n: ");
int n = Convert.ToInt32(Console.ReadLine());

Console.Clear();
Console.WriteLine($"m = {m}, n = {n}.");

double[,] array = new double[m, n];

CreateArrayDouble(array);

WriteArray(array);

Console.WriteLine();

void CreateArrayDouble(double[,] array)
{
  for (int i = 0; i < m; i++)
  {
    for (int j = 0; j < n; j++)
    {
      array[i, j] = new Random().NextDouble() * 20 - 10;
    }
  }
}

void WriteArray (double[,] array){
for (int i = 0; i < m; i++)
  {
      for (int j = 0; j < n; j++)
      {
        double alignNumber = Math.Round(array[i, j], 1);
        Console.Write(alignNumber + " ");
      }
      Console.WriteLine();
  }
}


// Задача 50: Напишите программу, которая на вход принимает позиции элемента в двумерном массиве, и возвращает значение этого элемента или же указание, что такого элемента нет.

Console.Write("n: ");
int n = Convert.ToInt32(Console.ReadLine());
Console.Write("m: ");
int m = Convert.ToInt32(Console.ReadLine());
Console.Write("Введите координаты позиции элемента, разделенных запятой: ");

Console.Clear();
Console.WriteLine($"m = {m}, n = {n}.");

double[,] array = new double[m, n];


Console.WriteLine();


string? positionElement = Console.ReadLine();
positionElement = RemovingSpaces(positionElement);
int[] position = ParserString(positionElement);

if(position[0] <= m 
&& position[1] <= n 
&& position[0] >= 0 
&& position[1] >= 0) 
{
  double result = array[position[0]-1, position[1]-1];
  Console.Write($"Значение элемента: {result}");
}
else Console.Write($"такого элемента в массиве нет.");

int[] ParserString(string input)
{
  int countNumbers = 1;
  for (int i = 0; i < input.Length; i++)
  {
      if (input[i] == ',')
          countNumbers++;
  }

  int[] numbers = new int[countNumbers];

  int numberIndex = 0;
  for(int i = 0; i < input.Length; i++)
  {
    string subString = String.Empty;

    while (input[i] != ',')
    {
      subString += input[i].ToString();
      if (i >= input.Length - 1)
        break;
      i++;
    }
    numbers[numberIndex] = Convert.ToInt32(subString);
    numberIndex++;
  }

  return numbers;
}

string RemovingSpaces (string input)
{
  string output = String.Empty;
  for (int i = 0; i < input.Length; i++)
  {
    if (input[i] != ' ') 
    {
      output += input[i];
    }
  }
  return output;
}

// Задача 52: Задайте двумерный массив из целых чисел. Найдите среднее арифметическое элементов в каждом столбце.


Console.WriteLine ("m: ");
int m = Convert.ToInt32 (Console.ReadLine());
Console.WriteLine ("n: ");
int n = Convert.ToInt32 (Console.ReadLine());
int[,] massive = new int [m,n];
for (int i = 0; i < m; i++)
{
    for (int j = 0; j < n; j++)
    {
        massive[i,j] = new Random().Next (-10, 10);
        Console.Write (massive[i,j]+" ");
    }
    Console.WriteLine();
}

double result = 0;

for (int j = 0; j < n; j++)
{
    result = Average(j);
    Console.WriteLine(result);
}

double Average(int column)
{
    double average = 0;
    double x = 0;
    for (int i = 0; i < m; i++)
{
    average += massive[i, column];
}
x = average / m;
return x;
} 