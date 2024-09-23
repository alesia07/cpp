# C++ Struct

Cel mai simplu tip nou.

```c++
struct Rectangle
{
    // campuri
    double width;
    double height;
};
```

Campurile din Rectangle pot fi accesate cu '.' sau '->' in cazul pointer la Rectangle.

```c++
Rectangle r;
r.width = 2;
r.height = 6;

Rectangle *r2 = &r;
cout << r2->width;
cout << r2->height;
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

## Instantiere (creare obiecte)

Avem tipul nou si putem crea oricate obiecte de acest tip avem nevoie.
La exemplul de mai sus avem 3 constructori deci putem folosi oricare din ei pentru a crea obiecte de tip Rectangle.

```c++
void foo()
{
    Rectangle r1 = Rectangle();
    
    Rectangle r2 = Rectangle(10, 5.5);
    
    Rectangle r1 = Rectangle(10, 5, 2);
}
```

In exemplul de mai sus, obiectele r1, r2, r3 sunt create pe stiva si cand functia foo() se termina atunci memoria folosita de ele este eliberata si disponibila pentru urmatoarele apeluri de functii.
Daca vrem sa cream obiecte in zona de memorie dinamica folosim `new`. In acest caz obtinem un pointer la Rectangle deci si variabilele trebuie declarate de tip pointer.
Folosim `new` daca obiectul creat are 'viata' mai lunga decat functia in care a fost creat, adica vrem sa existe si dupa ce functia foo() face return. 

```c++
void foo()
{
    Rectangle *r1 = new Rectangle();
    
    Rectangle *r2 = new Rectangle(10, 5.5);
    
    Rectangle *r1 = new Rectangle(10, 5, 2);
}
```

## Metode ale Struct

Putem crea metode/functii care pot fi invocate doar pe obiecte ale acelui tip.

```c++
struct Rectangle
{
    // campuri
    double width;
    double height;
    int thickness;

    void display() {
        cout << "width:" << width << " height:" << height << " thickness:" << thickness << endl;
    }
}

void foo()
{
    Rectangle r2 = Rectangle(10, 5.5);
    r2.display();

    Rectangle *r1 = new Rectangle();
    r1->display();
}
```

