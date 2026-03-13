# C# Memory Concepts for Value Types (Structs)

This document explains **how memory works in C# for value types**,
including stack allocation, struct size, and how memory is calculated
based on the variables inside the struct.

------------------------------------------------------------------------

# Value Types and Memory Allocation

In C#, **structs are value types**.\
Value types store their **actual data directly in memory**.

When a struct variable is created, the runtime allocates memory for
**all its fields together**.

Example:

``` csharp
struct Employee
{
    public int Salary;
    public int Age;
}
```

------------------------------------------------------------------------

# Size of Primitive Types

The memory size of a struct depends on the **size of its fields**.

  Type      Size
  --------- ----------
  byte      1 byte
  bool      1 byte
  short     2 bytes
  int       4 bytes
  float     4 bytes
  long      8 bytes
  double    8 bytes
  decimal   16 bytes
  char      2 bytes

------------------------------------------------------------------------

# Struct Memory Calculation

Example:

``` csharp
struct Employee
{
    public int Salary;
    public int Age;
}
```

Memory calculation:

    Salary (int) = 4 bytes
    Age (int)    = 4 bytes
    ----------------------
    Total        = 8 bytes

So **each Employee variable uses 8 bytes of memory**.

------------------------------------------------------------------------

# Stack Memory Example

Code:

``` csharp
Employee e = new Employee();
Employee e1 = e;
Employee e2 = e;
```

Stack memory layout:

    STACK
    -----------------
    e2
    Salary : 5000 (4 bytes)
    Age    : 23   (4 bytes)

    e1
    Salary : 5000 (4 bytes)
    Age    : 23   (4 bytes)

    e
    Salary : 5000 (4 bytes)
    Age    : 25   (4 bytes)

Each variable has its **own copy of the struct**.

Memory usage:

    e  = 8 bytes
    e1 = 8 bytes
    e2 = 8 bytes
    ----------------
    Total = 24 bytes

------------------------------------------------------------------------

# Memory Alignment and Padding

Sometimes the CLR adds **padding bytes** to align memory.

Example:

``` csharp
struct Example
{
    public byte A;   // 1 byte
    public int B;    // 4 bytes
}
```

Actual layout:

    A = 1 byte
    Padding = 3 bytes
    B = 4 bytes
    ----------------
    Total = 8 bytes

Padding improves **CPU memory alignment and performance**.

------------------------------------------------------------------------

# How to Check Struct Size in C

You can check the size using:

``` csharp
Console.WriteLine(sizeof(Employee));
```

or

``` csharp
Console.WriteLine(System.Runtime.InteropServices.Marshal.SizeOf<Employee>());
```

Output:

    8

------------------------------------------------------------------------

# Important Interview Points

1.  Struct size depends on **the size of its fields**.
2.  Each struct variable contains **a full copy of the data**.
3.  Value types usually live in **stack memory**.
4.  Struct size may increase due to **memory padding**.
5.  Copying structs increases **memory usage because full data is
    copied**.

------------------------------------------------------------------------

# Summary

  