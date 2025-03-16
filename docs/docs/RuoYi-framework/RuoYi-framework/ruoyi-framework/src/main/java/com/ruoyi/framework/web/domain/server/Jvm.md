# 基础信息

|      |      |
|------|------|
| 编码语言 | .java |
| 代码路径 | RuoYi-framework/ruoyi-framework/src/main/java/com/ruoyi/framework/web/domain/server/Jvm.java |
| 包名 | com.ruoyi.framework.web.domain.server |
| 依赖项 | ['java.lang.management.ManagementFactory', 'com.ruoyi.common.utils.Arith', 'com.ruoyi.common.utils.DateUtils'] |
| 概述说明 | JVM类管理内存、JDK版本、路径、启动时间及运行参数。 |

# 说明

JVM类是一个用于管理Java虚拟机内存、JDK版本、路径、启动时间及运行参数的工具。它提供了对内存分配和回收的监控与调整功能，支持不同JDK版本的识别与切换，能够获取和设置系统路径，记录并分析JVM启动时间，同时允许用户配置和优化运行参数，以确保应用程序的高效稳定运行。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| Jvm | class | JVM类用于管理内存、JDK版本、路径、启动时间及运行参数。 |



## 类 Jvm

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | Jvm |
| 说明 | JVM类用于管理内存、JDK版本、路径、启动时间及运行参数。 |


### UML类图

```mermaid
classDiagram
    class Jvm {
        -double total
        -double max
        -double free
        -String version
        -String home
        +double getTotal()
        +void setTotal(double total)
        +double getMax()
        +void setMax(double max)
        +double getFree()
        +void setFree(double free)
        +double getUsed()
        +double getUsage()
        +String getName()
        +String getVersion()
        +void setVersion(String version)
        +String getHome()
        +void setHome(String home)
        +String getStartTime()
        +String getRunTime()
        +String getInputArgs()
    }

    class Arith {
        <<Interface>>
        +double div(double a, double b, int scale)
        +double mul(double a, double b, int scale)
    }

    class ManagementFactory {
        <<Interface>>
        +RuntimeMXBean getRuntimeMXBean()
    }

    class DateUtils {
        <<Interface>>
        +String parseDateToStr(String format, Date date)
        +Date getServerStartDate()
        +Date getNowDate()
        +String timeDistance(Date start, Date end)
    }

    class RuntimeMXBean {
        <<Interface>>
        +String getVmName()
        +List<String> getInputArguments()
    }

    Jvm --> Arith : 依赖
    Jvm --> ManagementFactory : 依赖
    Jvm --> DateUtils : 依赖
    ManagementFactory --> RuntimeMXBean : 依赖
```

这段代码定义了一个 `Jvm` 类，用于管理和获取JVM的相关信息，如内存使用情况、JDK版本、启动时间等。`Jvm` 类依赖于 `Arith`、`ManagementFactory` 和 `DateUtils` 等接口来实现具体的计算和日期处理功能。通过这些接口，`Jvm` 类能够获取JVM的运行时信息，并进行相应的格式化输出。


### 内部方法调用关系图

```mermaid
graph TD
    A["类Jvm"]
    B["属性: double total"]
    C["属性: double max"]
    D["属性: double free"]
    E["属性: String version"]
    F["属性: String home"]
    G["方法: double getTotal()"]
    H["方法: void setTotal(double total)"]
    I["方法: double getMax()"]
    J["方法: void setMax(double max)"]
    K["方法: double getFree()"]
    L["方法: void setFree(double free)"]
    M["方法: double getUsed()"]
    N["方法: double getUsage()"]
    O["方法: String getName()"]
    P["方法: String getVersion()"]
    Q["方法: void setVersion(String version)"]
    R["方法: String getHome()"]
    S["方法: void setHome(String home)"]
    T["方法: String getStartTime()"]
    U["方法: String getRunTime()"]
    V["方法: String getInputArgs()"]

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
    A --> Q
    A --> R
    A --> S
    A --> T
    A --> U
    A --> V
```

这段代码定义了一个名为 `Jvm` 的类，用于管理和获取JVM（Java虚拟机）的相关信息。类中包含多个属性，如 `total`、`max`、`free` 等，分别表示JVM占用的内存总数、最大可用内存和空闲内存。类中还定义了一系列方法，用于获取和设置这些属性，并计算JVM的内存使用情况、JDK版本、路径、启动时间、运行时间以及运行参数等信息。通过这些方法，用户可以方便地监控和管理JVM的状态。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| home | String | 定义私有字符串变量home。 |
| version | String | 定义私有字符串变量version。 |
| free | double | 私有双精度浮点数变量free。 |
| total | double | 声明一个私有的双精度浮点型变量total。 |
| max | double | 定义了一个私有的双精度浮点数变量max。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| getName | String | 获取Java虚拟机名称的方法。 |
| getVersion | String | 获取版本号的公共方法。 |
| setVersion | void | 设置对象版本属性的方法。 |
| setHome | void | 定义设置home属性的方法。 |
| getStartTime | String | 获取服务器启动时间并格式化为指定字符串。 |
| getHome | String | 获取并返回home变量的值。 |
| setFree | void | 该方法用于设置free变量的值。 |
| setMax | void | 设置最大值为指定参数。 |
| getUsed | double | 计算已用内存，返回保留两位小数的MB值。 |
| getRunTime | String | 获取当前时间与服务器启动时间的时间差。 |
| getInputArgs | String | 该方法返回JVM启动时的输入参数。 |
| setTotal | void | 设置总数值的方法，将传入的total赋值给类的total属性。 |
| getTotal | double | 该方法将total除以1024*1024，保留两位小数后返回结果。 |
| getUsage | double | 计算资源使用率，公式为((总资源-空闲资源)/总资源)*100。 |
| getMax | double | 该方法返回最大值的MB单位，保留两位小数。 |
| getFree | double | 该方法计算并返回以MB为单位的可用空间，保留两位小数。 |




