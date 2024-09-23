# CPP Struct

Cel mai simplu tip nou.

```c++
struct Rectangle
{
    double width;
    double height;
};
```

## Constructor

Orice struct are un constructor. Daca nu il scriem noi este generat automat. 
Este apelat la creare de obiecte de acest tip.

```c++
struct Rectangle
{
    // campuri
    double width;
    double height;
    int thickness;

    // constructor fara parametri dar intializeaza campurile definite 
    Rectangle()
    {
        width = 1;
        height = 1;
        thickness = 1;
    }

    // constructor cu params care ascund campurile tipului - folosim `this`
    Rectangle(double width, double height)
    {
        // folosim this
        this->width = width;
        this->height = height;
        thickness = 1;
    }

    // alt constructor (parametri care nu ascund campurile)
    Rectangle(double w, double h, int t)
    {
        // folosim this
        width = w;
        height = h;
        thickness = t;
    }
};
```
