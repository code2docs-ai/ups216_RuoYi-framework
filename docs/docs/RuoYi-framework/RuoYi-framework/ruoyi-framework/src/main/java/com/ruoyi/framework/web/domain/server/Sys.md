# 基础信息

|      |      |
|------|------|
| 编码语言 | .java |
| 代码路径 | RuoYi-framework/ruoyi-framework/src/main/java/com/ruoyi/framework/web/domain/server/Sys.java |
| 包名 | com.ruoyi.framework.web.domain.server |
| 依赖项 | [] |
| 概述说明 | Sys类包含服务器信息属性及访问方法。 |

# 说明

Sys类是一个用于管理服务器相关信息的类，包含五个主要属性：服务器名称、IP地址、项目路径、操作系统和系统架构。每个属性都配有对应的getter和setter方法，用于获取和设置这些属性的值。通过这个类，用户可以方便地管理和操作服务器的基本信息，确保数据的封装性和可访问性。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| Sys | class | Sys类包含服务器名称、IP、项目路径、操作系统和系统架构属性及其getter和setter方法。 |



## 类 Sys

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | Sys |
| 说明 | Sys类包含服务器名称、IP、项目路径、操作系统和系统架构属性及其getter和setter方法。 |


### UML类图

```mermaid
classDiagram
    class Sys {
        -String computerName
        -String computerIp
        -String userDir
        -String osName
        -String osArch
        +String getComputerName()
        +void setComputerName(String computerName)
        +String getComputerIp()
        +void setComputerIp(String computerIp)
        +String getUserDir()
        +void setUserDir(String userDir)
        +String getOsName()
        +void setOsName(String osName)
        +String getOsArch()
        +void setOsArch(String osArch)
    }
```

这段代码定义了一个名为 `Sys` 的类，用于表示系统信息。类中包含五个私有属性：`computerName`（服务器名称）、`computerIp`（服务器IP）、`userDir`（项目路径）、`osName`（操作系统）和 `osArch`（系统架构）。每个属性都有对应的 `getter` 和 `setter` 方法，用于获取和设置这些属性的值。该类主要用于封装和操作与系统相关的信息，适合在需要获取或修改系统配置的场景中使用。


### 内部方法调用关系图

```mermaid
graph TD
    A["类Sys"]
    B["属性: String computerName"]
    C["属性: String computerIp"]
    D["属性: String userDir"]
    E["属性: String osName"]
    F["属性: String osArch"]
    G["方法: String getComputerName()"]
    H["方法: void setComputerName(String computerName)"]
    I["方法: String getComputerIp()"]
    J["方法: void setComputerIp(String computerIp)"]
    K["方法: String getUserDir()"]
    L["方法: void setUserDir(String userDir)"]
    M["方法: String getOsName()"]
    N["方法: void setOsName(String osName)"]
    O["方法: String getOsArch()"]
    P["方法: void setOsArch(String osArch)"]

    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
    A --> G
    A --> H
    A --> I
    A --> J
    A --> K
    A --> L
    A --> M
    A --> N
    A --> O
    A --> P
```

这段代码定义了一个名为 `Sys` 的类，用于管理系统相关的信息，如服务器名称、IP地址、项目路径、操作系统名称和系统架构。类中包含多个私有属性和对应的 `getter` 和 `setter` 方法，用于获取和设置这些属性的值。流程图展示了类 `Sys` 的属性及其方法之间的调用关系，清晰地反映了类的结构及其功能。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| computerName | String | 声明一个私有的字符串变量computerName。 |
| osArch | String | 私有字符串变量存储操作系统架构信息。 |
| osName | String | 定义私有字符串变量osName。 |
| userDir | String | 定义私有字符串变量userDir。 |
| computerIp | String | 定义私有字符串变量computerIp。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| setComputerIp | void | 设置计算机IP地址的方法。 |
| getUserDir | String | 获取用户目录的字符串方法。 |
| getComputerIp | String | 获取计算机IP地址的方法。 |
| getOsName | String | 获取操作系统名称的方法。 |
| getComputerName | String | 获取计算机名称的方法，返回变量computerName的值。 |
| setOsName | void | 设置操作系统名称的方法。 |
| setComputerName | void | 设置计算机名称的方法。 |
| getOsArch | String | 获取操作系统架构的方法。 |
| setOsArch | void | 设置操作系统架构的方法。 |
| setUserDir | void | 设置用户目录路径的方法。 |




