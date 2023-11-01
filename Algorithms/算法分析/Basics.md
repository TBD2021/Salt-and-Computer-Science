# Lecture 1: Basics

**Topics:**

- [Problems，Algorithms，Programs](#PAP20231101)
- 数据的组织与存储

## Problems，Algorithms，and Programs <a name = "PAP20231101">

Programmers commonly deal with problems, algorithms, and computer programs. These are three distinct concepts.

### Problems

A problem is a task to be performed. A problem definition should not include any constraints on how the problem is to be solved. However, a problem definition should include constraints on the resources that may be consumed by any acceptable solution. For any problem to be solved by a computer, there are always such constraints, whether stated or implied.

### Algorithms

算法，就是指一组定义清晰的计算步骤，它利用有限的时间和空间资源，将输入数据转换成输出数据。算法不拘形式，它可以用自然语言、计算机程序乃至计算机硬件结构等形式来表达。

A problem can be solved by many different algorithms. A given algorithm solves only one problem.

算法应当具有以下特性：

- 正确（Correct）: 算法应当把每一个输入都转化为正确的输出。
- 由具体的（concrete）、无歧义的（no ambiguity）、有限（finite）的步骤组成，并具有终止(terminate)步骤。
  
```html
- Concrete means that the action described by that step is completely understood — and doable — by the person or machine that must perform the algorithm. Each step must also be doable in a finite amount of time. 

- There can be no ambiguity as to which step will be performed next. 

- It must be composed of a finite number of steps.

- It must terminate. In other words, it may not go into an infinite loop.
```

### Programs

We often think of a computer program as an instance, or concrete representation, of an algorithm in some programming language. Algorithms are usually presented in terms of programs, or parts of programs. Naturally, there are many programs that are instances of the same algorithm, because any modern computer programming language can be used to implement the same collection of algorithms

对一个计算机程序的评估是多方面的，除了正确性，还有性能（performance）、对计算机资源的利用效率（resource usage）、代码可读性、可扩展性、用户交互等多个方面。而好的算法设计能够使计算机程序在其中的多个方面获益。

## 数据的组织与存储

