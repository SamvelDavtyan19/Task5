# Task5
    using System;

    class Program
    {
    static void Main()
    {
        int[,] matrix = {
            {1, 2, 3, 4},
            {5, 6, 7, 8},
            {9, 10, 11, 12}
        };

        FindSaddlePoint(matrix);
    }

    static void FindSaddlePoint(int[,] matrix)
    {
        int rows = matrix.GetLength(0);
        int cols = matrix.GetLength(1);

        for (int i = 0; i < rows; i++)
        {
            int maxInRow = matrix[i, 0];
            int colIndexOfMax = 0;
            
            for (int j = 1; j < cols; j++)
            {
                if (matrix[i, j] > maxInRow)
                {
                    maxInRow = matrix[i, j];
                    colIndexOfMax = j;
                }
            }
            
            bool isSaddlePoint = true;
            for (int k = 0; k < rows; k++)
            {
                if (matrix[k, colIndexOfMax] < maxInRow)
                {
                    isSaddlePoint = false;
                    break;
                }
            }

            if (isSaddlePoint)
            {
                Console.WriteLine($"Saddle point found at position ({i + 1}, {colIndexOfMax + 1}): {maxInRow}");
                return;
            }
        }

        Console.WriteLine("No saddle point found.");
    }
    }
