# 基础信息

|      |      |
|------|------|
| 编码语言 | .java |
| 代码路径 | RuoYi-framework/ruoyi-framework/src/main/java/com/ruoyi/framework/shiro/rememberMe/CustomCookieRememberMeManager.java |
| 包名 | com.ruoyi.framework.shiro.rememberMe |
| 依赖项 | ['java.util.HashMap', 'java.util.List', 'java.util.Map', 'java.util.Set', 'org.apache.shiro.subject.PrincipalCollection', 'org.apache.shiro.subject.Subject', 'org.apache.shiro.subject.SubjectContext', 'org.apache.shiro.web.mgt.CookieRememberMeManager', 'com.ruoyi.common.core.domain.entity.SysRole', 'com.ruoyi.common.core.domain.entity.SysUser', 'com.ruoyi.common.utils.spring.SpringUtils', 'com.ruoyi.framework.shiro.service.SysLoginService'] |
| 概述说明 | 自定义Cookie管理器，优化权限控制，防止请求头过大。 |

# 说明

自定义Cookie记住我管理器用于管理用户登录状态的持久化，通过清除和恢复角色权限来确保用户权限的正确性和安全性。该管理器还通过优化Cookie数据，防止HTTP请求头过大，从而提升网络传输效率和系统性能。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| CustomCookieRememberMeManager | class | 自定义Cookie记住我管理器，清除和恢复角色权限，防止HTTP请求头过大。 |



## 类 CustomCookieRememberMeManager

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | CustomCookieRememberMeManager |
| 说明 | 自定义Cookie记住我管理器，清除和恢复角色权限，防止HTTP请求头过大。 |


### UML类图

```mermaid
classDiagram
    class CookieRememberMeManager {
        <<Interface>>
        +rememberIdentity(Subject subject, PrincipalCollection principalCollection)
        +getRememberedPrincipals(SubjectContext subjectContext) PrincipalCollection
    }

    class CustomCookieRememberMeManager {
        +rememberIdentity(Subject subject, PrincipalCollection principalCollection)
        +getRememberedPrincipals(SubjectContext subjectContext) PrincipalCollection
    }

    class SysUser {
        +List~SysRole~ getRoles()
    }

    class SysRole {
        +Set~String~ getPermissions()
        +void setPermissions(Set~String~ permissions)
    }

    class SysLoginService {
        +void setRolePermission(SysUser user)
    }

    class SpringUtils {
        +~T~ getBean(Class~T~ clazz) ~T~
    }

    CustomCookieRememberMeManager --> CookieRememberMeManager : 继承
    CustomCookieRememberMeManager --> SysUser : 依赖
    CustomCookieRememberMeManager --> SysRole : 依赖
    CustomCookieRememberMeManager --> SysLoginService : 依赖
    CustomCookieRememberMeManager --> SpringUtils : 依赖
    SysUser --> SysRole : 依赖
```

这段代码定义了一个 `CustomCookieRememberMeManager` 类，继承自 `CookieRememberMeManager`，用于管理“记住我”功能的身份验证。该类重写了 `rememberIdentity` 方法，在记住用户身份时临时清除角色的权限字符串，以防止HTTP请求头过大，并在处理完成后恢复这些权限。此外，`getRememberedPrincipals` 方法在获取记住的用户身份时，通过 `SysLoginService` 恢复角色的权限字符串。代码涉及 `SysUser`、`SysRole`、`SysLoginService` 和 `SpringUtils` 等类的交互。


### 内部方法调用关系图

```mermaid
graph TD
    A["类CustomCookieRememberMeManager"]
    B["方法: rememberIdentity(Subject subject, PrincipalCollection principalCollection)"]
    C["方法: getRememberedPrincipals(SubjectContext subjectContext)"]
    D["创建Map<SysRole, Set<String>> rolePermissions"]
    E["遍历principalCollection"]
    F["判断principal是否为SysUser实例"]
    G["获取SysUser的角色列表"]
    H["遍历角色列表"]
    I["将角色及其权限存入rolePermissions"]
    J["清空角色的permissions"]
    K["将principalCollection转换为bytes"]
    L["恢复角色的permissions"]
    M["调用rememberSerializedIdentity(subject, bytes)"]
    N["调用super.getRememberedPrincipals(subjectContext)"]
    O["判断principals是否为空"]
    P["遍历principals"]
    Q["判断principal是否为SysUser实例"]
    R["调用SysLoginService.setRolePermission(SysUser principal)"]
    S["返回principals"]

    A --> B
    A --> C
    B --> D
    B --> E
    E --> F
    F -->|是| G
    G --> H
    H --> I
    H --> J
    B --> K
    B --> E
    E --> F
    F -->|是| G
    G --> H
    H --> L
    B --> M
    C --> N
    C --> O
    O -->|是| S
    O -->|否| P
    P --> Q
    Q -->|是| R
    R --> S
```

这段代码描述了一个自定义的CookieRememberMeManager类，主要用于在记住用户身份时临时清除和恢复角色的权限字符串，以防止HTTP请求头过大。在`rememberIdentity`方法中，首先清除角色的权限字符串并将其存储在Map中，然后将用户身份信息序列化为字节数组，最后恢复角色的权限字符串并调用父类的方法保存序列化后的身份信息。在`getRememberedPrincipals`方法中，首先获取记住的用户身份信息，如果存在且不为空，则遍历用户信息并调用服务类恢复角色的权限字符串。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| rememberIdentity | void | 清除并恢复用户角色权限，保存序列化身份信息。 |
| getRememberedPrincipals | PrincipalCollection | 重写方法，获取记住的Principal，若为空返回，否则设置角色权限。 |




