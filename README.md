# 这是什么仓库
利用Github Action来构建内核，目前支持4.19和4.14。

# 如何使用
### 1.将此仓库Fork到你自己的账号下      
### 2.修改config.env，这里对config作以下解释：
| config.env | 解释 |
| ---------- | ----------------- | 
| USE_CONFIG | 改为 true 时代表使用配置文件构建内核，不要动 |
| KERNEL_SOURCE | 内核源码，一般用 github 链接 |
| KERNEL_SOURCE_BRANCH | 你想使用的内核源码分支，因为一份源码下可能有多个分支 |
| KERNEL_DEFCONFIG | 内核的 defconfig 位置 |
| KERNEL_FILE | 内核文件输出形式，可改为 Image 或者 Image.gz 或者 Image.gz-dtb |
| CLANG_VERSION | 你想使用的 Clang 编译器版本 |
| EXTRA_BUILD_COMMAND | 额外编译参数，某些内核需要这些参数才能编译，自行修改或添加。请注意，此处的每条参数后必须加空格，再续写新的参数。如 a=a b=b  |
### 3.参数修改完成后，点击Star即可触发构建。时间约为25分钟。产物在Action内，自行下载。
### 请注意，内核默认加入了KernelSU。为保证稳定性，我没有打开KPROBES，这意味着如果要使用KernelSU，你必须自己打补丁。如何为内核源码打补丁请参考 ：   [如何为非GKI设备集成KernelSU](https://kernelsu.org/zh_CN/guide/how-to-integrate-for-non-gki.html)。
### 内核已经关闭了设备检查，请不要跨设备刷内核。

# 已支持使用的 Clang 版本
| Clang 版本 | 对应 Android 版本 | AOSP-Clang 版本 |
| ---------- | ----------------- | --------------- |
| 12.0.5 | Android S | r416183b |
| 14.0.6 | Android T | r450784d |
| 14.0.7 | | r450784e |

推荐使用Clang14.0.7，当然，你也可以选择你喜欢的版本

# EXTRA_BUILD_COMMAND 额外编译参数参考
| 额外编译参数参考 | 
| ---------- | 
| LD=ld.lld |
| LLVM=1 |
| LLVM_IAS=1 |

# 致谢
- [XiaoleGun Github-Action](https://github.com/xiaoleGun/KernelSU_Action)
- [tiann KernelSU](https://github.com/tiann/KernelSU)
