# Ola language usage demo

The following example demonstrates the recursive and non-recursive implementation of the Fibonacci function in Ola.

## Fibonacci Contract

```js
contract Fibonacci {

    fn main() {
       fib_non_recursive(10);
    }

    fn fib_recursive(u32 n) -> (u32) {
        if (n == 0) {
            return 0;
        }
        if (n == 1) {
            return 1;
        }
        return fib_recursive(n -1) + fib_recursive(n -2);
    }

    fn fib_non_recursive(u32 n) -> (u32) {
        if (n == 0) {
            return 0;
        }
        u32 first = 0;
        u32 second = 1;
        u32 third = 1;
        for (u32 i = 2; i <= n; i++) {
             third = first + second;
             first = second;
             second = third;
        }
        return third;
    }

}
```

## Non-deterministic computation
Ola supports non-deterministic computation through the lib function. 
This improves the efficiency of code proofs that are difficult to compute but easy to verify in circuits. 
Below is an example demonstrating non-deterministic computation for u32_sqrt.

```js
contract SqrtContract {

    fn main() {
       sqrt_test(10000);
    }

    fn sqrt_test(u32 n) -> (u32) {
        u32 b = u32_sqrt(n);
        return b;
    }

}
```

## Performance comparison
The improvement in efficiency through non-deterministic computation is significant. 
Next, we will compare the differences between the implementation of non-deterministic computation and deterministic computation. 
The following example shows a u32_sqrt function implemented natively through Ola.

```js
contract SqrtContract {

    fn main() {
        sqrt_test(10000);
    }

    fn sqrt_test(u32 a) -> (u32) {
        u32 result = 0;
        if (a > 3) {
            result = a;
            u32 x = a / 2 + 1;
            // assume the maximum iteration is 100
            for (u32 i = 0; i < 100; i++) {
                if (x >= result) break;
                result = x;
                x = (a / x + x) / 2;
            }
        } else if (a != 0) {
            result = 1;
        }
        return result;
    }

}
```


## ola language compiler Usage

The olac compiler is run on the command line. The ola source file names are provided as command line arguments; the output is an Ola asm.

### Command line interface

```
olac --help
Ola Language Compiler

Usage: olac <COMMAND>

Commands:
  compile  Compile ola source files
  help     Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help
  -V, --version  Print version
```

### Compile Ola Language to LLVM IR

Olac's compile command supports subcommands, using the  `--gen  llvm-ir` option to generate llvm-ir

```
olac compile prophet_sqrt.ola --gen llvm-ir
```

### Compile Ola to Ola's Assembly code

using the `--gen  asm` option to generate Ola assembly code

```
olac compile prophet_sqrt.ola --gen asm
```