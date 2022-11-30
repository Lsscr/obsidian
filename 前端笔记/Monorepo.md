# 引言

> `Monorepo` 是一种管理团队代码的方式，它摒弃了一个模块一个仓库的方式，而是尽可能地将所有的模块放在一个仓库进行管理

`Monorepo` 的出现改变了传统一个包一个仓库的局面,而是尽可能使所有包依赖模块都在一个仓库下

## 使用前了解相关缺点😱
-   随着项目的迭代，在 `Monorepo` 中每个 `package` 都会十分庞大，**对构建工具是个不小的挑战**。（目前已有的方案：例如 Google 的 [Bazel](https://link.juejin.cn?target=https%3A%2F%2Fbazel.build%2F "https://bazel.build/"), Facebook 的 [Buck](https://link.juejin.cn?target=https%3A%2F%2Fbuckbuild.com%2F "https://buckbuild.com/") 和 Twitter 的 [Pants](https://link.juejin.cn?target=https%3A%2F%2Fwww.pantsbuild.org%2F "https://www.pantsbuild.org/")，但**它们都没有很好的支持`JS`打包**）
-   由于项目之间相互依赖，你必须**时刻保证良好的代码结构，编译规范以及测试用例**。
-   除了对构建工具的挑战外，当**项目达到一定规模时，IDE可能会面临崩溃**。

| 工具                                                                                                | 简述                                                   |
| --------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| [Bit](https://link.juejin.cn/?target=https%3A%2F%2Fbit.dev%2F "https://bit.dev/")                   | 用于组件驱动开发的工具链                               |
| [Turborepo](https://link.juejin.cn/?target=https%3A%2F%2Fturborepo.org%2F "https://turborepo.org/") | 用于 JavaScript 和 TypeScript 代码库的高性能构建系统。 |
| [Rush](https://link.juejin.cn/?target=https%3A%2F%2Frushjs.io%2F "https://rushjs.io/")              | 一个可扩展的 web 单仓库管理器。                        |
| [Nx](https://link.juejin.cn/?target=https%3A%2F%2Fnx.dev%2F "https://nx.dev/")                      | 具有一流的 monorepo 支持和强大集成的下一代构建系统。   |
|[Lerna](https://link.juejin.cn/?target=https%3A%2F%2Fwww.lernajs.cn%2F "https://www.lernajs.cn/")|用于管理包含多个软件包的项目|
