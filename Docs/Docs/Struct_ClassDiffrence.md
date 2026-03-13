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

### Quick Summary

| Struct          | Class                |
| --------------- | -------------------- |
| Value type      | Reference type       |
| Stored on stack | Stored on heap       |
| Copied by value | Copied by reference  |
| No inheritance  | Supports inheritance |
| Lightweight     | Heavier              |


---

### Quick Summary

| Struct | Class |
|------|------|
| Value type | Reference type |
| Stored on stack | Stored on heap |
| Copied by value | Copied by reference |
| No inheritance | Supports inheritance |
| Lightweight | Heavier |