# 引言

> `Monorepo` 是一种管理团队代码的方式，它摒弃了一个模块一个仓库的方式，而是尽可能地将所有的模块放在一个仓库进行管理

`Monorepo` 的出现改变了传统一个包一个仓库的局面,而是尽可能使所有包依赖模块都在一个仓库下

## 使用前了解相关缺点😱
-   随着项目的迭代，在 `Monorepo` 中每个 `package` 都会十分庞大，**对构建工具是个不小的挑战**。（目前已有的方案：例如 Google 的 [Bazel](https://link.juejin.cn?target=https%3A%2F%2Fbazel.build%2F "https://bazel.build/"), Facebook 的 [Buck](https://link.juejin.cn?target=https%3A%2F%2Fbuckbuild.com%2F "https://buckbuild.com/") 和 Twitter 的 [Pants](https://link.juejin.cn?target=https%3A%2F%2Fwww.pantsbuild.org%2F "https://www.pantsbuild.org/")，但**它们都没有很好的支持`JS`打包**）
-   由于项目之间相互依赖，你必须**时刻保证良好的代码结构，编译规范以及测试用例**。
-   除了对构建工具的挑战外，当**项目达到一定规模时，IDE可能会面临崩溃**。

  