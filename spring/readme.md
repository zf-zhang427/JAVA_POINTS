#### **1. Java反射（Reflection）**

**目标**：理解Spring如何动态操作类。

- 核心内容：`Class`对象、`Method.invoke()`、字段访问。
- **小实践**：写一个工具类，通过反射调用`UserService`的私有方法。

#### **2. 动态代理（Dynamic Proxy）**

**目标**：掌握Spring AOP的底层机制。

- 核心内容：
  - JDK动态代理（基于接口）
  - CGLIB（基于子类继承）
- **小实践**：
  - 手动为`PointService`创建一个代理类，在方法调用前后打印日志。
  - 对比`Proxy.newProxyInstance()`和CGLIB的区别。

#### **3. Bean与IoC容器**

**目标**：理解Spring如何管理对象生命周期。

- 核心内容：
  - Bean的定义（XML/注解）
  - 容器的作用：`ApplicationContext` vs `BeanFactory`
- **小实践**：
  - 通过`applicationContext.xml`配置`UserService`和`PointService`，手动启动容器。

#### **4. 依赖注入（DI）与注解**

**目标**：掌握现代Spring开发模式。

- 核心内容：
  - `@Autowired`的三种注入方式（构造器/Setter/字段）
  - `@Component` vs `@Service` vs `@Repository`
- **小实践**：
  - 改造项目，用`@ComponentScan`替换XML配置。
  - 故意制造循环依赖，观察错误并解决（`@Lazy`）。

#### **5. AOP与动态代理的实战**

**目标**：理解代理如何增强Bean。

- 核心内容：
  - `@Transactional`的实现原理
  - 自定义切面（`@Aspect` + `@Around`）
- **小实践**：
  - 为`PointService`添加日志切面，统计方法耗时。
  - 通过`getClass()`观察代理后的Bean类型。

#### **6. 高级整合：事务传播与代理机制**

**目标**：解决复杂场景问题。

- 核心内容：
  - 事务传播行为（`Propagation.REQUIRED`）
  - 同一类内方法调用导致代理失效问题（`@Autowired self`）
- **小实践**：
  - 在`UserService`中调用自己的另一个`@Transactional`方法，分析代理失效原因。