`println!` and `format!` placeholders 

### Basic Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{}` | Display the value as is |
| `{:<N}` | Display the value with a minimum width of `N`, left aligned |
| `{:>N}` | Display the value with a minimum width of `N`, right aligned |
| `{:^N}` | Display the value with a minimum width of `N`, centered |
| `{:.N}` | Display the value with `N` decimal places (applies to numbers only) |
| `{:+.N}` | Display the value with a sign and `N` decimal places (applies to numbers only) |
| `{:.Ne}` | Display the value in scientific notation with `N` decimal places (applies to numbers only) |

### Debug Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{:#?}` | Debug format the value with pretty-printing |
| `{:?}` | Debug format the value |

### Integer Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{}` or `{:d}` | Display the integer as is |
| `{:b}` | Display the integer in binary |
| `{:o}` | Display the integer in octal |
| `{:x}` or `{:X}` | Display the integer in hexadecimal |

### Floating-Point Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{}` or `{:f}` | Display the floating-point number as is |
| `{:e}` or `{:E}` | Display the floating-point number in scientific notation |
| `{:a}` or `{:A}` | Display the floating-point number in hexadecimal scientific notation |
| `{:g}` or `{:G}` | Display the floating-point number in either fixed or scientific notation, whichever is more compact |

### String Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{}` or `{:s}` | Display the string as is |
| `{:#?}` or `{:#?}` | Debug format the string with pretty-printing |

### Boolean Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{}` or `{}` | Display the boolean as "true" or "false" |
| `{:#?}` or `{:#?}` | Debug format the boolean with pretty-printing |

### Char Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{}` or `{}` | Display the char as is |
| `{:#?}` or `{:#?}` | Debug format the char with pretty-printing |

### Pointer Placeholders

| Placeholder | Description |
|-------------|-------------|
| `{}` or `{}` | Display the pointer as is |
| `{:#?}` or `{:#?}` | Debug format the pointer with pretty-printing |

These placeholders can be used with both the `println!` and `format!` macros in Rust.