---
Title: TypeScript 类型体操通关秘籍
tag:
- projects
- TypeScript
created: 2023-01-11 17:01
modification date: 星期三 11日 一月 2023 17:01:04
category: 学习,阅读
starts: 5星级
status: 写作中
---

# TypeScript 类型体操通关秘籍

## 科普

### 什么是类型检查?
> **如果能保证对某种类型只做该类型允许的操作，这就叫做`类型安全`**。**类型检查是为了保证类型安全的**。
> 类型检查可以在运行时做。
> 可以运行之前的编译期做。

### 动态类型检查与静态类型检查？
> `动态类型检查` 在源码中不保留类型信息，对某个变量赋什么值、做什么操作都是允许的，写代码很灵活。但这也埋下了类型不安全的隐患，比如对 string 做了乘除，对 Date 对象调用了 exec 方法，这些都是运行时才能检查出来的错误。
> `静态类型检查`则是在源码中保留类型信息，声明变量要指定类型，对变量做的操作要和类型匹配，会有专门的编译器在编译期间做检查。

**动态类型只适合简单的场景，对于大项目却不太合适，因为代码中可能藏着的隐患太多了，万一线上报一个类型不匹配的错误，那可能就是大问题。**

**而静态类型虽然会增加写代码的成本，但是却能更好的保证代码的健壮性，减少 Bug 率。**

所以，**大型项目注定会用静态类型语言开发。**

### TypeScript 给 JavaScript进行类型检查？
通过 TS Compiler 编译为 JS，编译的过程做类型检查。
它并没有改变 JavaScript 的语法，只是在 JS 的基础上添加了类型语法，所以被叫做 JavaScript 的超集。
TypeScript 类型系统又分为 `简单类型系统` 与 `支持泛型的类型系统`与`支持类型编程的类型系统`

简单类型系统是基础的类型系统，能保证类型安全，但有些死板。所有就有了支持泛型的类型系统，泛型的英文是 Generic Type，也叫做**类型参数**。（其实就是一个类型变量）

支持类型编程的类型系统
**对传入的类型参数（泛型）做各种逻辑运算，产生新的类型，这就是类型编程。**
所以把TS 的类型编程戏称为`类型体操`了。

### TypeScript 类型系统中的类型
TS 类型系统中肯定要把 JS 的运行时类型拿过来
基本类型：number、boolean、string、object、bigint、symbol、undefined、null
包装类型：Number、Boolean、String、Object、Symbol
复合类型：class、Array，**元组（Tuple）、接口（Interface）、枚举（Enum）**

`元组（Tuple）`就是元素个数和类型固定的数组类型：
```typescript
type Tuple = [number, string];
```

`接口（Interface）`可以描述函数、对象、构造器的结构：

`枚举（Enum）`是一系列值的复合：

#### 索引签名
对象可以**动态添加属性**，如果不知道会有什么属性，可以用可索引签名：
```typescript
interface IPerson {
    [prop: string]: string | number;
}
const obj:IPerson = {};
obj.name = 'guang';
obj.age = 18;
```

#### 类型装饰
是否可选，是否只读等：
```typescript
interface IPerson {
    readonly name: string;
    age?: number;
}

type tuple = [string, number?];
```

### TypeScript 类型系统中的类型运算
