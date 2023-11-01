# Lab3
using System;

class Point
{
    public double X { get; }
    public double Y { get; }
    public string Name { get; }

    public Point(double x, double y, string name)
    {
        X = x;
        Y = y;
        Name = name;
    }
}

class Figure
{
    private Point[] points;

    public Figure(Point A, Point B, Point C)
    {
        points = new Point[] { A, B, C };
    }

    public Figure(Point A, Point B, Point C, Point D)
    {
        points = new Point[] { A, B, C, D };
    }

    public Figure(Point A, Point B, Point C, Point D, Point E)
    {
        points = new Point[] { A, B, C, D, E };
    }

    public double GetSideLength(Point A, Point B)
    {
        double dx = A.X - B.X;
        double dy = A.Y - B.Y;
        return Math.Sqrt(dx * dx + dy * dy);
    }

    public void CalculatePerimeter()
    {
        double perimeter = 0;
        int n = points.Length;

        for (int i = 0; i < n; i++)
        {
            int j = (i + 1) % n;
            perimeter += GetSideLength(points[i], points[j]);
        }

        Console.WriteLine("Периметр багатокутника: " + perimeter);
    }
}

class Program
{
    static void Main()
    {
        Console.WriteLine("Введіть координати точки A (x y name):");
        string[] inputA = Console.ReadLine().Split(' ');
        Point A = new Point(double.Parse(inputA[0]), double.Parse(inputA[1]), inputA[2]);

        Console.WriteLine("Введіть координати точки B (x y name):");
        string[] inputB = Console.ReadLine().Split(' ');
        Point B = new Point(double.Parse(inputB[0]), double.Parse(inputB[1]), inputB[2]);

        Console.WriteLine("Введіть координати точки C (x y name):");
        string[] inputC = Console.ReadLine().Split(' ');
        Point C = new Point(double.Parse(inputC[0]), double.Parse(inputC[1]), inputC[2]);

        Figure triangle = new Figure(A, B, C);
        triangle.CalculatePerimeter();
    }
}
