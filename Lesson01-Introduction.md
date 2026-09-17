# Lesson01-Introduction

### **Table of Contents**

- [Lesson01-Introduction](#lesson01-introduction)
    - [**Table of Contents**](#table-of-contents)
  - [1. Basic Knowledge of Computer](#1-basic-knowledge-of-computer)
    - [1.1 Source Code, Binary Code, and Byte Code](#11-source-code-binary-code-and-byte-code)
    - [1.2 Compilation vs. Interpretation](#12-compilation-vs-interpretation)
    - [1.3 JRE, JVM and JDK](#13-jre-jvm-and-jdk)
  - [2. Software and Tools](#2-software-and-tools)
    - [2.1 Integrated Development Environments (IDE)](#21-integrated-development-environments-ide)
    - [2.2 Version Control Systems (VCS)](#22-version-control-systems-vcs)


## 1. Basic Knowledge of Computer

### 1.1 Source Code, Binary Code, and Byte Code

At the lowest level, a computer works with only two symbols: `0` and `1`. This representation is called *binary code* or *machine code*. Text, images, audio, and video are all ultimately stored as patterns made from these two symbols.

Each `0` or `1` is a *bit* (`b`). Eight bits form a *byte* (`B`), for example: `10010011`. Data is measured in increasing units:

- `1024 bytes = 1 KB`
- `1024 KB = 1 MB`
- `1024 MB = 1 GB`
- `1024 GB = 1 TB`

High-level programming languages like **Java** allow developers to write instructions in a human-readable way. For example:

```java
double salary = hourlyPay * workingHour;
```

Even without much background, you can guess what this line means. However, computers cannot directly understand this code. The source code must be *translated* into binary code. This translation is called *compilation*.

### 1.2 Compilation vs. Interpretation

Source code is commonly translated in one of two ways:

- **Compiled languages**: The source code is translated entirely into machine code before execution. (e.g., C, C++)
- **Interpreted languages**: The source code is translated line by line as the program runs. (e.g., Python, JavaScript)

Java takes a hybrid approach. Java source code is first compiled into an intermediate form called *bytecode*. Bytecode is not tied to a specific machine but runs on the **Java Virtual Machine (JVM)**, making Java programs portable across platforms.

### 1.3 JRE, JVM and JDK

To allow Java to run on a computer, we need to pre-install something to allow our computer to understand Java.

* Java Runtime Environment (**JRE**):
* Java Virtual Machine (**JVM**): JVM contains JRE plus some supported tools for Java to run on a computer. JRE is required for Java to be executed.
* Java Development Kit (**JDK**): JDK contains JVM plus more libraries and a compiler. JDK is required for Java development. The current Long-Term Support (**LTS**) version for JDK is *JDK 25*, and the previous one is *JDK 21*. Either of these two versions is fine.

## 2. Software and Tools

### 2.1 Integrated Development Environments (IDE)

An **IDE** is software that helps developers write, test, and debug code efficiently. Popular Java IDEs include:

- **IntelliJ IDEA**
- **Eclipse**
- **NetBeans**

Each provides tools such as syntax highlighting, code completion, and debugging features to make coding easier and more efficient.

### 2.2 Version Control Systems (VCS)

As projects grow, managing versions of code becomes essential. A **Version Control System** tracks changes, enables collaboration, and allows you to roll back to earlier versions if needed.

The most widely used VCS today is **Git**, and platforms like **GitHub** and **GitLab** make collaboration easier by hosting repositories online.
