# C++


## Structs and Classes

#### Structs, or Classes without Methods

```
struct MyStruct {
    char my_data[] = { 1, 2, 3 };
}
```

###### Instantiating Structs

```
MyStruct my_struct = { 3, 4, 5 };
```


#### Classes with Methods

```
class MyClass {
public:
    void Hello();
private:
    char my_data[] = { 1, 2, 3 };
}

void MyClass::Hello() {
    std::cout << "Hello, my data is " << my_data << std::endl;
}
```

###### Instantiating classes

To allocate the data on the stack:

```
MyClass my_class = MyClass;
MyClass.Hello();
```

Using heap allocation:

```
char* my_array = new char[3] {1, 2, 3};
delete(my_array);

MyClass* my_class = new MyClass();

// Access members of pointers to classes with the pointer notation
MyClass->Hello();
// ...
// Don't forget to clean up the heap when you're done:
delete(my_class);
```

Explicitly allocate at an arbitrary memory address:

```
char buffer[sizeof(MyClass)];
MyClass* my_class = new (buffer) MyClass();
```

Copy an existing instance to another location on the stack:

```
MyClass my_class;
MyClass copy_of_class = my_class;
```

## Syntax


#### Destructuring

```

```

