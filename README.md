# Lab3
#include <iostream>
#include <cmath>
#include <string>

using namespace std;

// Клас Point для представлення точки
class Point {
public:
    double x;
    double y;
    string name;

    Point(double _x, double _y, const string& _name) : x(_x), y(_y), name(_name) {}

    double GetX() const {
        return x;
    }

    double GetY() const {
        return y;
    }

    string GetName() const {
        return name;
    }
};

// Клас Figure для представлення багатокутника
class Figure {
private:
    Point* points; // Масив точок
    int count;     // Кількість точок в багатокутнику

public:
    Figure(Point* _points, int _count) : points(_points), count(_count) {}

    // Розрахунок довжини відрізка між двома точками
    double GetSideLength(const Point& A, const Point& B) const {
        return sqrt(pow(A.GetX() - B.GetX(), 2) + pow(A.GetY() - B.GetY(), 2));
    }

    // Розрахунок периметра багатокутника
    double CalculatePerimeter() const {
        double perimeter = 0.0;
        for (int i = 0; i < count; i++) {
            int nextIndex = (i + 1) % count; // Індекс наступної точки (циклічно)
            perimeter += GetSideLength(points[i], points[nextIndex]);
        }
        return perimeter;
    }
};

int main() {
    // Визначення точок для багатокутника
    Point A(0, 0, "A");
    Point B(4, 0, "B");
    Point C(4, 3, "C");
    Point D(0, 3, "D");

    // Масив точок багатокутника
    Point points[] = {A, B, C, D};

    // Створення екземпляра класу Figure
    Figure figure(points, sizeof(points) / sizeof(points[0]));

    // Розрахунок та виведення периметра багатокутника
    double perimeter = figure.CalculatePerimeter();
    cout << "Периметр багатокутника: " << perimeter << endl;

    return 0;
}
