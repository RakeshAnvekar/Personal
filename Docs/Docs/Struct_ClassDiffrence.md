## Classes vs Structs in C#

## Classes vs Structs in C#

| Feature              | Struct                                                        | Class                                                                                  |
| -------------------- | ------------------------------------------------------------- | -----------------------------------------------------------------                      |
| **Type**             | Value type                                                    | Reference      type                                                                                   |
| **Memory Storage**   | Data stored directly on the **stack**                         | Reference stored on stack, object stored on the **heap**                                                                 |
| **Usage**            | Used for **simple data types**                                | Used for **complex objects** with multiple properties and methods                                                        |
| **Performance**      | **Lightweight**, good for performance-critical applications   | **Heavier** than structs                                                                                |
| **Access Speed**     | Faster because stored on **stack**                            | Slower compared to structs because stored on **heap**                                                                     |
| **Copy Behavior**    | Copied **by value**                                           | Copied **by reference**                                                                            |
| **Inheritance**      | **Cannot inherit** from other structs                         | **Supports inheritance**                                                                          |
| **Polymorphism**     | **Not supported**                                             | **Supported**                                                                          |
| **Modifiers**        | `abstract` and `sealed` **not allowed**                       | `abstract` and `sealed` **allowed**                                                                            |
| **Access Modifiers** | Members cannot be **protected** or **protected internal**     | Members **can be protected** or **protected internal**                                                                 |
| **Methods**          | Methods cannot be **abstract** or **virtual**                 | Methods **can be abstract or virtual**                                                                              |
| **Override**         | Limited override (from `System.ValueType`)                    | Full **override support**                                                                              |
| **Size Limit**       | Recommended around **16 bytes**                               | **No size limit**                                                                                |
| **Large Objects**    | Large structs may move to **heap** causing performance issues | Designed for **large complex objects**                                                                                                             |

---
## When to Use Structs in C#

- Structs are best used when you need to represent **simple data types**, such as integers, strings, or other basic data types.

- They are useful when working with **large datasets**, such as **arrays or lists**, where performance is critical.

- Use a struct when you need to pass a **small amount of data to a method** and want to avoid the overhead of passing a reference to a class.

- Structs are useful when you need a **lightweight object that does not require inheritance or polymorphism**.

- Since structs are **value types**, they can be easily copied and passed around without complex memory management.

---

## When to Use Classes in C#

- Classes are best used when you need to represent **complex objects**, such as **real-world entities** like cars, people, or animals.

- They are useful when creating **object hierarchies**, where one class **inherits from another**.

- Use classes when working with **large amounts of data**, such as when interacting with a **database or other external data sources**.

- Classes are useful when you need to **encapsulate data and functionality together**.

- By using classes, you can group **related methods and properties into a single unit**, making code more organized and easier to maintain.