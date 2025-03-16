# 基础信息

|      |      |
|------|------|
| 编码语言 | .java |
| 代码路径 | RuoYi-framework/ruoyi-framework/src/main/java/com/ruoyi/framework/shiro/session/OnlineSession.java |
| 包名 | com.ruoyi.framework.shiro.session |
| 依赖项 | ['org.apache.commons.lang3.builder.ToStringBuilder', 'org.apache.commons.lang3.builder.ToStringStyle', 'org.apache.shiro.session.mgt.SimpleSession', 'com.ruoyi.common.enums.OnlineStatus'] |
| 概述说明 | OnlineSession继承SimpleSession，包含用户信息及在线状态。 |

# 说明

OnlineSession类继承自SimpleSession类，包含用户ID、名称、部门、头像、IP地址、浏览器类型、操作系统信息、在线状态以及属性变更标志等关键属性。该类用于管理用户的在线会话信息，涵盖用户的基本信息、设备信息及会话状态，确保对用户在线状态的全面跟踪和管理。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| OnlineSession | class | OnlineSession类继承SimpleSession，包含用户ID、名称、部门、头像、IP、浏览器、操作系统、在线状态及属性变更标志。 |



## 类 OnlineSession

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | OnlineSession |
| 说明 | OnlineSession类继承SimpleSession，包含用户ID、名称、部门、头像、IP、浏览器、操作系统、在线状态及属性变更标志。 |


### UML类图

```mermaid
classDiagram
    class SimpleSession {
        <<Interface>>
        +String getHost()
        +void setHost(String host)
        +void setAttribute(Object key, Object value)
        +Object removeAttribute(Object key)
    }

    class OnlineSession {
        -Long userId
        -String loginName
        -String deptName
        -String avatar
        -String host
        -String browser
        -String os
        -OnlineStatus status
        -boolean attributeChanged
        +String getHost()
        +void setHost(String host)
        +String getBrowser()
        +void setBrowser(String browser)
        +String getOs()
        +void setOs(String os)
        +Long getUserId()
        +void setUserId(Long userId)
        +String getLoginName()
        +void setLoginName(String loginName)
        +String getDeptName()
        +void setDeptName(String deptName)
        +OnlineStatus getStatus()
        +void setStatus(OnlineStatus status)
        +void markAttributeChanged()
        +void resetAttributeChanged()
        +boolean isAttributeChanged()
        +String getAvatar()
        +void setAvatar(String avatar)
        +void setAttribute(Object key, Object value)
        +Object removeAttribute(Object key)
        +String toString()
    }

    SimpleSession <|-- OnlineSession : 实现
```

类图描述：`OnlineSession` 类继承自 `SimpleSession` 接口，表示在线会话的信息。该类包含了用户ID、登录名、部门名称、头像、主机IP、浏览器类型、操作系统、在线状态等属性，并提供了相应的getter和setter方法。此外，`OnlineSession` 还实现了 `SimpleSession` 接口中的方法，并提供了标记属性是否改变的功能。


### 内部方法调用关系图

```mermaid
graph TD
    A["类OnlineSession"]
    B["属性: Long userId"]
    C["属性: String loginName"]
    D["属性: String deptName"]
    E["属性: String avatar"]
    F["属性: String host"]
    G["属性: String browser"]
    H["属性: String os"]
    I["属性: OnlineStatus status"]
    J["属性: boolean attributeChanged"]
    K["方法: String getHost()"]
    L["方法: void setHost(String host)"]
    M["方法: String getBrowser()"]
    N["方法: void setBrowser(String browser)"]
    O["方法: String getOs()"]
    P["方法: void setOs(String os)"]
    Q["方法: Long getUserId()"]
    R["方法: void setUserId(Long userId)"]
    S["方法: String getLoginName()"]
    T["方法: void setLoginName(String loginName)"]
    U["方法: String getDeptName()"]
    V["方法: void setDeptName(String deptName)"]
    W["方法: OnlineStatus getStatus()"]
    X["方法: void setStatus(OnlineStatus status)"]
    Y["方法: void markAttributeChanged()"]
    Z["方法: void resetAttributeChanged()"]
    AA["方法: boolean isAttributeChanged()"]
    AB["方法: String getAvatar()"]
    AC["方法: void setAvatar(String avatar)"]
    AD["方法: void setAttribute(Object key, Object value)"]
    AE["方法: Object removeAttribute(Object key)"]
    AF["方法: String toString()"]

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
    A --> W
    A --> X
    A --> Y
    A --> Z
    A --> AA
    A --> AB
    A --> AC
    A --> AD
    A --> AE
    A --> AF
```

这段代码定义了一个`OnlineSession`类，继承自`SimpleSession`类，用于管理在线会话的相关信息。类中包含多个属性，如用户ID、登录名、部门名称、头像、IP地址、浏览器类型、操作系统、在线状态等，并提供了相应的getter和setter方法。此外，还包含标记属性是否改变的方法，以及重写的`toString`方法，用于格式化输出对象的信息。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| loginName | String | 定义一个私有字符串变量loginName。 |
| userId | Long | 定义长整型变量userId用于存储用户ID。 |
| serialVersionUID = 1L | long | 定义了一个静态长整型常量serialVersionUID，值为1L。 |
| avatar | String | 定义了一个私有的字符串变量avatar。 |
| deptName | String | 定义私有字符串变量deptName。 |
| browser | String | 定义了一个私有字符串变量browser。 |
| host | String | 定义了一个私有字符串变量host。 |
| attributeChanged = false | boolean | 私有瞬态布尔变量attributeChanged初始值为false。 |
| status = OnlineStatus.on_line | OnlineStatus | 私有变量status设置为在线状态。 |
| os | String | 定义了一个私有的字符串类型变量os。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| setBrowser | void | 该方法用于设置浏览器属性。 |
| getDeptName | String | 该方法返回部门名称字符串。 |
| setLoginName | void | 设置用户登录名的方法。 |
| getOs | String | 获取操作系统信息的方法。 |
| getLoginName | String | 获取登录名的方法。 |
| setStatus | void | 该方法用于设置在线状态。 |
| getBrowser | String | 该方法返回浏览器名称的字符串。 |
| getUserId | Long | 该方法返回用户ID。 |
| isAttributeChanged | boolean | 方法返回属性是否已更改的布尔值。 |
| resetAttributeChanged | void | 该方法用于重置属性变更标志为false。 |
| setAvatar | void | 设置用户头像的方法，参数为字符串类型。 |
| getHost | String | 重写getHost方法，返回host变量值。 |
| toString | String | 重写toString方法，返回多行格式的用户信息。 |
| setAttribute | void | 重写setAttribute方法，调用父类方法设置键值对。 |
| setOs | void | 定义方法setOs，用于设置os变量。 |
| getAvatar | String | 获取头像的字符串方法。 |
| setUserId | void | 设置用户ID的方法，接受长整型参数。 |
| setHost | void | 重写setHost方法，将传入的host参数赋值给类的host属性。 |
| setDeptName | void | 设置部门名称的方法，将输入值赋给类属性deptName。 |
| removeAttribute | Object | 重写removeAttribute方法，调用父类实现删除指定属性。 |
| markAttributeChanged | void | 方法`markAttributeChanged`将`attributeChanged`属性设置为`true`。 |
| getStatus | OnlineStatus | 获取在线状态的公共方法，返回当前状态值。 |




