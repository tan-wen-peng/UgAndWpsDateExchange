现在的UG存在的问题是，不能和WPS的表格进行互通。
原因在于：
1，两者使用的接口不兼容。
2，默认wps的接口优先级高于UG的COM模式接口，导致被覆盖。
因此我在想可否在他们两个之间做一个中间层。比如在UG的环境里将WPS伪装成COM模式。
这样带来的效果是：因为WPS在我国普通人电脑里的占比比较多并且符合国人的操作习惯。将他们兼容在一起有助于在设计过程中繁琐的装卸软件工作简化为运行脚本。

---

## 实现（V0.1 已完成）

上述构想的完整实现位于子仓库 `UgAndWpsDateExchange\`：

- NX Open C++ 插件（中间层）：把 WPS 表格伪装成 `Excel.Application` COM 服务端，
  并支持电子表格导入/导出、环境诊断、COM 兼容设置与自检；
- 兼容 NX 12 及以上（x64），以 NX 12.0 SDK 编译（VS2017 v141 / C++17）；
- 已通过 32 项单元测试（构建环境实测通过）。

详见 [UgAndWpsDateExchange/README.md](UgAndWpsDateExchange/README.md) 与其中的 docs 目录。
