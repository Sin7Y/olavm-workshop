# Client
Ola is standalone client of OlaVM.
It has four versions:

| Ola client        | CPU arch | OS type |
|-------------------|:--------:|--------:|
| ola-arm64-macosx  | aarch64  |  macosx |
| ola-amd64-linux   |  x86_64  |   linux |
| ola-amd64-win.exe |  x86_64  | windows |
| ola-amd64-arm64   |  x86_64  |  macosx |


Ola contains 4 command(asm, run, prove, verify). Their usage is as follows:

## asm
This command relocates the label and encodes the assembly code.

parameters:

-i: input the file contain Ola-lang assemble code.
-o: output the file contain OlaVM executable instruction code.

```
./ola asm -i assembler/test_data/asm/prophet_sqrt.json -o prophet_sqrt.json
```

## run
This command makes OlaVM run the program and generate the trace of the program.
parameters:

-i: input raw-code file for executing
-o: output trace json file

```
./ola run  -i prophet_sqrt.json -o prophet_sqrt_trace.json
```

## prove
This command generates proof from the trace.
parameters:

-i: input trace_table json file for generating proof
-o: output the proof binary file of program 

```
./ola prove  -i prophet_sqrt_trace.json -o prophet_sqrt_prove.bin
```

## verify

This command verifies the proof of program.If true, it prints "Verify succeed!", else prints the error when verifying.
parameters:

-i: input the proof binary file of program

```
./ola prove  -i prophet_sqrt_trace.json -o prophet_sqrt_prove.bin
```