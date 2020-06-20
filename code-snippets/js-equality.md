## Equality


JavaScript provides three different value-comparison operations:
* **==** Abstract Equality Comparison ("loose equality", "double equals")
* **===** Strict Equality Comparison ("strict equality", "identity", "triple equals")
* **Object.is** provides SameValue (new in ES2015).

---

### Data types

|         |          |
| ------------- |-------------|
| Primitive     | number, string, boolean, undefined, null, bigInt, symbol |
| Non-primitive | object, arrray, function |

---

### Coercion
Process of converting value from one type to another

#### String

> Explicit string conversion

|         |          |
| ------------- |-------------|
| String("hello")  | "hello"   |
| String(null)  | "null"      |
| String(undefined)  | "undefined"   |
| String(true)  | "true"     |
| String(false)  | "false"   |
| String(12.345)  | "12.345"  |
| String(0)  | "0"      |
| String(-0)  | "0"         |
| String(Infinity)  | "Infinity" |
| String(-Infinity)  | "-Infinity"  |


> Implicit string conversion

|         |          |
| ------------- |-------------|
| "" + "hello"  | "hello"   |
| "" + null  | "null"      |
| "" + undefined  | "undefined"   |
| "" + true  | "true"     |
| "" + false  | "false"   |
| "" + 12.345  | "12.345"  |
| "" + 0  | "0"      |
| "" + -0  | "0"         |
| "" + Infinity  | "Infinity" |
| "" + -Infinity  | "-Infinity"  |


