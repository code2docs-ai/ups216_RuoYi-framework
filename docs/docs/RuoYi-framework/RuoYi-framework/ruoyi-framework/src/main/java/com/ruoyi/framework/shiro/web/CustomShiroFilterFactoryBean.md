# 基础信息

|      |      |
|------|------|
| 编码语言 | .java |
| 代码路径 | RuoYi-framework/ruoyi-framework/src/main/java/com/ruoyi/framework/shiro/web/CustomShiroFilterFactoryBean.java |
| 包名 | com.ruoyi.framework.shiro.web |
| 依赖项 | ['org.apache.shiro.spring.web.ShiroFilterFactoryBean', 'org.apache.shiro.web.filter.InvalidRequestFilter', 'org.apache.shiro.web.filter.mgt.DefaultFilter', 'org.apache.shiro.web.filter.mgt.FilterChainManager', 'org.apache.shiro.web.filter.mgt.FilterChainResolver', 'org.apache.shiro.web.filter.mgt.PathMatchingFilterChainResolver', 'org.apache.shiro.web.mgt.WebSecurityManager', 'org.apache.shiro.web.servlet.AbstractShiroFilter', 'org.apache.shiro.mgt.SecurityManager', 'org.springframework.beans.factory.BeanInitializationException', 'javax.servlet.Filter', 'java.util.Map'] |
| 概述说明 | 扩展ShiroFilterFactoryBean，重写方法，确保SecurityManager正确设置并修复URL中文校验问题。 |

# 说明

CustomShiroFilterFactoryBean扩展了ShiroFilterFactoryBean，通过重写getObjectType和createInstance方法，确保SecurityManager能够正确设置，并解决了URL中文校验的bug。这一改进使得过滤器在处理包含中文字符的URL时能够正常工作，提升了系统的稳定性和兼容性。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| CustomShiroFilterFactoryBean | class | CustomShiroFilterFactoryBean扩展ShiroFilterFactoryBean，重写getObjectType和createInstance方法，确保SecurityManager正确设置并跳过URL中文校验bug。 |



## 类 CustomShiroFilterFactoryBean

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | CustomShiroFilterFactoryBean |
| 说明 | CustomShiroFilterFactoryBean扩展ShiroFilterFactoryBean，重写getObjectType和createInstance方法，确保SecurityManager正确设置并跳过URL中文校验bug。 |


### UML类图

```mermaid
classDiagram
    class CustomShiroFilterFactoryBean {
        +Class~MySpringShiroFilter~ getObjectType()
        +AbstractShiroFilter createInstance() throws Exception
        -FilterChainManager createFilterChainManager()
    }

    class AbstractShiroFilter {
        <<Abstract>>
        +void setSecurityManager(WebSecurityManager securityManager)
        +void setFilterChainResolver(FilterChainResolver resolver)
    }

    class MySpringShiroFilter {
        +MySpringShiroFilter(WebSecurityManager webSecurityManager, FilterChainResolver resolver)
    }

    class WebSecurityManager {
        <<Interface>>
    }

    class FilterChainManager {
        <<Interface>>
        +Map~String, Filter~ getFilters()
    }

    class PathMatchingFilterChainResolver {
        +void setFilterChainManager(FilterChainManager manager)
    }

    class InvalidRequestFilter {
        +void setBlockNonAscii(boolean blockNonAscii)
    }

    CustomShiroFilterFactoryBean --> AbstractShiroFilter : 创建实例
    CustomShiroFilterFactoryBean --> FilterChainManager : 创建FilterChainManager
    CustomShiroFilterFactoryBean --> PathMatchingFilterChainResolver : 设置FilterChainManager
    CustomShiroFilterFactoryBean --> InvalidRequestFilter : 配置InvalidRequestFilter
    MySpringShiroFilter --> AbstractShiroFilter : 继承
    MySpringShiroFilter --> WebSecurityManager : 依赖
    MySpringShiroFilter --> FilterChainResolver : 依赖
    PathMatchingFilterChainResolver --> FilterChainManager : 依赖
    InvalidRequestFilter --> Filter : 继承
```

这段代码展示了`CustomShiroFilterFactoryBean`类的实现，它继承自`ShiroFilterFactoryBean`，并重写了`getObjectType`和`createInstance`方法。`createInstance`方法负责创建并配置`MySpringShiroFilter`实例，确保`SecurityManager`和`FilterChainResolver`正确设置。`MySpringShiroFilter`是`AbstractShiroFilter`的子类，用于处理Shiro过滤器链的解析。代码中还涉及`FilterChainManager`、`PathMatchingFilterChainResolver`和`InvalidRequestFilter`等类，用于管理和配置过滤器链。


### 内部方法调用关系图

```mermaid
graph TD
    A["类CustomShiroFilterFactoryBean"]
    B["重写方法: Class<MySpringShiroFilter> getObjectType()"]
    C["重写方法: AbstractShiroFilter createInstance() throws Exception"]
    D["获取SecurityManager: getSecurityManager()"]
    E["检查SecurityManager是否为null"]
    F["抛出异常: BeanInitializationException('SecurityManager property must be set.')"]
    G["检查SecurityManager是否实现WebSecurityManager接口"]
    H["抛出异常: BeanInitializationException('The security manager does not implement the WebSecurityManager interface.')"]
    I["创建FilterChainManager: createFilterChainManager()"]
    J["创建PathMatchingFilterChainResolver: new PathMatchingFilterChainResolver()"]
    K["设置FilterChainManager: chainResolver.setFilterChainManager(manager)"]
    L["获取FilterMap: manager.getFilters()"]
    M["获取InvalidRequestFilter: filterMap.get(DefaultFilter.invalidRequest.name())"]
    N["检查InvalidRequestFilter是否为InvalidRequestFilter实例"]
    O["设置blockNonAscii为false: ((InvalidRequestFilter) invalidRequestFilter).setBlockNonAscii(false)"]
    P["创建MySpringShiroFilter实例: new MySpringShiroFilter((WebSecurityManager) securityManager, chainResolver)"]
    Q["类MySpringShiroFilter"]
    R["构造方法: MySpringShiroFilter(WebSecurityManager webSecurityManager, FilterChainResolver resolver)"]
    S["检查webSecurityManager是否为null"]
    T["抛出异常: IllegalArgumentException('WebSecurityManager property cannot be null.')"]
    U["设置SecurityManager: this.setSecurityManager(webSecurityManager)"]
    V["检查resolver是否为null"]
    W["设置FilterChainResolver: this.setFilterChainResolver(resolver)"]

    A --> B
    A --> C
    C --> D
    D --> E
    E -->|是| F
    E -->|否| G
    G -->|否| H
    G -->|是| I
    I --> J
    J --> K
    K --> L
    L --> M
    M --> N
    N -->|是| O
    O --> P
    A -.-> Q
    Q --> R
    R --> S
    S -->|是| T
    S -->|否| U
    U --> V
    V -->|否| W
```

这段代码展示了`CustomShiroFilterFactoryBean`类如何重写`getObjectType`和`createInstance`方法，以及内部类`MySpringShiroFilter`的构造过程。`createInstance`方法负责创建`MySpringShiroFilter`实例，期间会检查`SecurityManager`的有效性，并设置`FilterChainResolver`。流程图清晰地描绘了从获取`SecurityManager`到最终创建`MySpringShiroFilter`实例的整个过程，包括异常处理和关键步骤的调用关系。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| getObjectType | Class<MySpringShiroFilter> | 重写getObjectType方法，返回MySpringShiroFilter类类型。 |
| createInstance | AbstractShiroFilter | 创建ShiroFilter实例，检查SecurityManager，处理FilterChain，解决中文URL校验问题。 |




