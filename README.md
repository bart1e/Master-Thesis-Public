# Master Thesis written back in 2021

## Important information
Project source code (written in c++) is password protected since it could potentially be used against its purpose (which is to protect intellectual property by obsuscating programs) - for instance to obfuscate malware.

You can use the provided password to unzip the [source_code.zip](source_code.zip) file (if you didn't receive the password, you won't be able to see the source code). You can use the following command:
- 7za x source_code.zip -p<PASSWORD>

## Scope
Implementation of the tool named <b>VMObf</b> that performs software obfuscation using virtualization technique.

## Algorithm used
All the details regarding algorithm, implementation and evaluation can be found in [VMObf.pdf](VMObf.pdf).

In short, obfuscation algorithm runs for each function in a program separately, in five main steps:
- Split basic blocks of a given function so that it contains < <i>c</i> (some constant) instructions.
- Divide graph of the function into connected components chosen randomly each time.
- Each connected component becomes a single instruction of the Virtual Machine (VM).
- Each instruction is provided with local variables it needs and returns the modified ones along with the next VM instruction address.
- Since each selected connected component of original graph of the function (VM instruction) may have possibly many entry points and end points, instruction input / output depends on additional argument (passed to this instruction) telling which code it should execute.

## Requirements
In order to run <b>VMObf</b>, the following tools should be installed:
- llvm-11
- clang++-11

## Installation and use
- Clone the repository.
- VMObf can be started in two different ways (on Linux):
  - using <i>runVMObf.sh</i>
  - using <i>runVMObf_optimized.sh</i>
  
Each script expects a single argument: name of a file with .cpp extension. Scripts will automatically build the project.

The first script runs <b>VMObf</b> on an unoptimized code produced by clang.
The second one runs <b>VMObf</b> on an optimized code.

Note that, for more complicated programs, obfuscation may take some time (even up to several minutes).
