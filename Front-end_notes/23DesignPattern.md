## 前言
> 在软件工程中，设计模式（Design Pattern）是对软件设计中普遍存在（反复出现）的各种问题，所提出的解决方案。 ——维基百科

**前端驾驭技术的能力**
-   能用健壮的代码去解决具体的问题；
-   能用抽象的思维去应对复杂的系统；
-   能用工程化的思想去规划更大规模的业务。

设计模式具有**抽象性**，所以学习设计模式最好方法就是**把自己放到一个正确的场景里，去体会这个模式的好**，理解其设计原理才能记得更加牢固，但它**毕竟是人们在实践过程中总结、提炼出来的**，掌握它的意义，正是为了把它**还原到我们日常的实践中去**。

### SOLID设计原则🐼
> "SOLID" 是由罗伯特·C·马丁在 21 世纪早期引入的记忆术首字母缩略字，指代了面向对象编程和面向对象设计的五个基本原则。

SOLID 指代的五个基本原则分别是：
-   单一功能原则（Single Responsibility Principle）
-   开放封闭原则（Opened Closed Principle）
-   里式替换原则（Liskov Substitution Principle）
-   接口隔离原则（Interface Segregation Principle）
-   依赖反转原则（Dependency Inversion Principle）

### 设计模式的核心思想——封装变化
软件设计越来越复杂的“罪魁祸首”，就是**变化**。实际开发中，不发生变化的代码可以说是不存在的。我们能做的只有将这个变化造成的影响**最小化** —— **将变与不变分离，确保变化的部分灵活、不变的部分稳定**。
> 23种设计模式。二十年前，四位程序员前辈（Erich Gamma, Richard Helm, Ralph Johnson & John Vlissides）通过编写《设计模式：可复用面向对象软件的基础》这本书，阐述了设计模式领域的开创性成果。在这本书中，将23种设计模式按照“创建型”、“行为型”和“结构型”进行划分

无论是创建型、结构型还是行为型，这些具体的设计模式都是在用自己的方式去封装不同类型的变化
- **创建型**模式封装了**创建对象过程中的变化**
- **结构型**模式封装的是**对象之间组合方式的变化**，目的在于灵活地表达对象间的配合与依赖关系
- **行为型**模式则将是**对象千变万化的行为进行抽离**，确保我们能够更安全、更方便地对行为进行更改

# 创建型模式
## 前置知识
### 构造器（构造方法，构造函数）
> 初始化该对象的特殊函数，就叫做构造器。在 JavaScript 中，我们使用构造函数去初始化对象，就是应用了**构造器模式**

<sub>构造器不就是一个类么</sub>
在 Javascript 中使用构造函数来初始化对象
```javascript
function User(name , age, career) {
    this.name = name
    this.age = age
    this.career = career 
}
```
> User 就是一个**构造器**。此处我们采用了 ES5 构造函数的写法，因为 **ES6 中的 class 其实本质上还是函数，class 语法只是语法糖，构造函数，才是它的真面目**。

## 简单工厂模式
当程序存在大量的构造器（类），是否可以根据变与不变，抽离相同的共性，返回初始化对象
### 举个栗子🌰
有如下的代码：
```javascript
function Coder(name , age) {
    this.name = name
    this.age = age
    this.career = 'coder' 
    this.work = ['写代码','写系分', '修Bug']
}
function ProductManager(name, age) {
    this.name = name 
    this.age = age
    this.career = 'product manager'
    this.work = ['订会议室', '写PRD', '催更']
}
```
这些构造器里共有的属性都可以进行相关的抽离，并返回一个构造好的初始化对象
```javascript
function User(name , age, career, work) {
    this.name = name
    this.age = age
    this.career = career 
    this.work = work
}

function Factory(name, age, career) {
    let work
    switch(career) {
        case 'coder':
            work =  ['写代码','写系分', '修Bug'] 
            break
        case 'product manager':
            work = ['订会议室', '写PRD', '催更']
            break
        case 'boss':
            work = ['喝茶', '看报', '见客户']
        case 'xxx':
            // 其它工种的职责分配
            ...
            
    return new User(name, age, career, work)
}
```
### 总结
**将创建对象的过程单独封装，这样的操作就是工厂模式。** 
应用场景是在用到了大量的构造函数与大量的new方法的时候，就饿可以使用工程模式重构代码