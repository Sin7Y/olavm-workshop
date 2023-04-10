# olavm-workshop

This tutorial explains the steps necessary to run the program on OlaVM, generate ZK(zero-knowledge) proof and verify.

## Prerequisites
There are some resources about OlaVM. The developers should learn the concepts and demonstrates to grasp the designs of OlaVM.
* [Hello, OlaVM!](https://hackmd.io/@sin7y/H1yPj_J8i)
* [Ola - A ZKVM-based, High-performance, and Privacy-focused Layer2 platform](https://github.com/Sin7Y/olavm-whitepaper-v2/blob/master/Ola%20-%20A%20ZKVM-based%2C%20High-performance%2C%20and%20Privacy-focused%20Layer2%20platform.pdf)
* [Unveiling OlaVM Proof of Concept: The Next-Generation Full-Featured zkVM](https://medium.com/@sin7y/unveiling-olavm-proof-of-concept-the-next-generation-full-featured-zkvm-5840b27f8e4c)

## Table of Contents

* [Edit the program](#Edit the program): Ola supports writing on vscode, we have developed an extension to vscode to support ola syntax highlighting, and we will continue to improve the plugin in the future.
The extension can be found on the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=Sin7y.ola).
* [Compile the program](#Compile the program): The compilation process can refer to the official documentation of the Ola language [Usage](https://github.com/Sin7Y/ola-lang#usage).
* [Run the program](#Execute the program): refer to [olavm-execute.md](docs/olavm-execute.md).
* Generate ZK proof: OlaVM execution results and all intermediate processes are recorded during execution and saved as json, including CPU execution trace table, Memory trace table, Range Check trace table, Bitwise trace table and comparison trace table. You can open these json files directly for a simple view, or you can convert it to an excel file for further analysis with the [tools](docs/olavm-trace-analysis.md) we provide. Generating proof can take some time, depending on the size of the trace you are generating.
```
ola prove  -i my_exec_trace.json -o my_generated_proof
```
* Verify ZK proof: Congratulations you have successfully generated the proof, now you only need to execute one command to verify it.
```
ola verify -i my_generated_proof
```

Beginner Workshop: implement the Fibonacci algorithm with loop and recursive two versions.

Advanced Workshop: implement the sqrt algorithm with Newton's method and prophet two versions.

Helpful Resources: 
* [source code](docs/ola-lang.md) of the above two workshops.
* [ola-lang github project](https://github.com/Sin7Y/ola-lang.git) 
* [ola-vm github project](https://github.com/Sin7Y/olavm) - PoC(Proof of concept) version

## User run steps guide
In the paragraph, we guide the developer through the implementation of the loop Fibonacci algorithm.

### Edit the program
At first, the developer should use an editor(recommend [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=Sin7y.ola)) to develop the Fibonacci algorithm code(refer to below) and save to file fibo_loop.ola.

``
contract Fibonacci {

    fn main() {
       fib_loop(10);
    }

    fn fib_loop(u32 n) -> (u32) {
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
``

### Compile the program
In this step, the developer should compile the code to the JSON format executable file. Using below tool:

compile code to assembly file fibo_loop_asm.json:
``

``

compile code to executable file fibo_loop_exe.json:

``
``

### Execute the program and generate trace file fibo_loop_trace.json.

``
./ola run  -i fibo_loop_exe.json -o fibo_loop_trace.json
``

## Multi-core prover performance

| Algorithm                        |                Machine core                 | Machine Memory | OS type | Execution time | Proving time | Trace size |
|:---------------------------------|:-------------------------------------------:|:--------------:|:-------:|:--------------:|:------------:|:----------:|
| 1000 times sqrt(prophet)         |          Apple M1 Pro (10 threads)          |     32 GB      | macosx  |     58 ms      |   11.8 ses   |   18 MB    |
| 1000 times sqrt(Newton's method) |          Apple M1 Pro (10 threads)          |     32 GB      | macosx  |    4441 ms     |   163 ses    |   681 MB   |


# Contact
Twitter: https://twitter.com/Sin7y_Labs

Discord: http://discord.gg/vDFy7YEG6j

Email: contact@sin7y.org