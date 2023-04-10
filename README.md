# olavm-workshop

This tutorial explains the steps necessary to run the program on OlaVM, generate ZK(zero-knowledge) proof and verify.

# Prerequisites
There are some resources about OlaVM. The developers should learn the concepts and demonstrates to grasp the designs of OlaVM.
* [Hello, OlaVM!](https://hackmd.io/@sin7y/H1yPj_J8i)
* [Ola - A ZKVM-based, High-performance, and Privacy-focused Layer2 platform](https://github.com/Sin7Y/olavm-whitepaper-v2/blob/master/Ola%20-%20A%20ZKVM-based%2C%20High-performance%2C%20and%20Privacy-focused%20Layer2%20platform.pdf)
* [Unveiling OlaVM Proof of Concept: The Next-Generation Full-Featured zkVM](https://medium.com/@sin7y/unveiling-olavm-proof-of-concept-the-next-generation-full-featured-zkvm-5840b27f8e4c)

# Table of Contents

* Edit the program: Ola supports writing on vscode, we have developed an extension to vscode to support ola syntax highlighting, and we will continue to improve the plugin in the future.
The extension can be found on the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=Sin7y.ola).
* Compile the program: The compilation process can refer to the official documentation of the Ola language [Usage](https://github.com/Sin7Y/ola-lang#usage).
* Run the program: refer to [olavm-execute.md](docs/olavm-execute.md).
* Generate ZK proof: 
* Verify ZK proof:

Beginner Workshop: implement the fibonacci algorithm with loop and recursive two versions.

Advanced Workshop:  implement the sqrt algorithm with Newton's method and prophet two versions.

Helpful Resources: 
* [source code](docs/ola-lang.md) of the above two workshops.
* [ola-lang github project](https://github.com/Sin7Y/ola-lang.git) 
* [ola-vm github project](https://github.com/Sin7Y/olavm) - PoC(Proof of concept) version

# Multi-core prover performance

| Algorithm                        |                Machine core                 | Machine Memory | OS type | Execution time | Proving time | Trace size |
|----------------------------------|:-------------------------------------------:|----------------|--------:|----------------|--------------|------------|
| 1000 times sqrt with prophet     |          Apple M1 Pro (10 threads)          | 32 GB          |  macosx | 58 ms          | 11.8 ses     | 18 MB      |
| 1000 times sqrt(Newton's method) |          Apple M1 Pro (10 threads)          | 32 GB          |  macosx | 4441 ms        | 163 ses      | 681 MB     |


# Contact
Twitter: https://twitter.com/Sin7y_Labs

Discord: http://discord.gg/vDFy7YEG6j

Email: contact@sin7y.org