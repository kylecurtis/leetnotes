
---

<br>

## Negation (Opposite Number)

<br>

To obtain the opposite (negation) of any integer, multiply it by `-1`. This is valid for all integers, including `0`, which remains `0`.

```cpp
int x = 10; // 10
int y = -5; // -5

int new_x = (x * -1); // -10
int new_y = (y * -1); // 5
```

<br>

Alternatively, you can use the negation operator `-` to achieve the same result in a more concise way:

```cpp
int a = -32; // -32 -> 32
int b = -(-32); // -(-32) -> 32
```

<br>

---

<br>

## Integer Extraction

<br>

To extract the last digit of an integer, use the modulo operator `% 10`. This gives the remainder when the number is divided by 10, which corresponds to the last digit.

```cpp
int x = 123;
int last_digit = x % 10; // 3
```

<br>

To remove the last digit from an integer, perform integer division by `10`, which effectively shifts the digits to the right (removes the last digit).

```cpp
int x = 123;
int truncated_num = x / 10; // 12
```

<br>

### Extracting Other Digits

You can extract digits from any position in an integer by repeatedly using both division and modulo operations.

<br>

To get the second-to-last digit, first divide by `10` and then apply `% 10`:

```cpp
int x = 12345;
int second_last_digit = (x / 10) % 10; // 4
```

<br>

To get the third-to-last digit, divide by `100` and apply `% 10`:

```cpp
int third_last_digit = (x / 100) % 10; // 3
```

<br>

### General Formula

For extracting any digit at position `n` (counting from the right, starting at `1`):
- First, divide the number by `10^(n-1)` to shift the desired digit to the units place.
- Then apply `% 10` to isolate it.

For example, to get the `n`th digit:
```cpp
int nth_digit = (x / pow(10, n - 1)) % 10;
```

<br>

---

<br>

