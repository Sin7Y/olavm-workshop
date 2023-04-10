# Client
ola is standalone client of Olavm.
It contains three version:


ola-mac-m1-pro: arch: aarch64(m1 pro), system: macos
ola-x86-64-linux: arch: x86_64, system: linux
ola-x86-64-win.exe: arch: x86_64, system: windows

* asm
This command relocates the label and encodes the assembly code.
parameters:

-i: input the file contain Ola-lang assemble code.
-o: output the file contain OlaVM executable instruction code.

```
./ola asm -i assembler/test_data/asm/prophet_sqrt.json -o prophet_sqrt.json
```

* run
This command makes OlaVM run the program and generate the trace of the program.
parameters:

-i: input raw-code file for executing
-o: output trace json file

```
./ola run  -i prophet_sqrt.json -o prophet_sqrt_trace.json
```

* prove
This command generates proof from the trace.
parameters:

-i: input trace_table json file for generating proof
-o: output the proof binary file of program 

```
./ola prove  -i prophet_sqrt_trace.json -o prophet_sqrt_prove.bin
```

* verify

This command verifies the proof of program.If true, it prints "Verify succeed!", else prints the error when verifying.
parameters:

-i: input the proof binary file of program

```
./ola prove  -i prophet_sqrt_trace.json -o prophet_sqrt_prove.bin
```