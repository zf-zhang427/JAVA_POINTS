1. 解释一下IOC和AOP？IOC的好处？ 

   IOC（控制反转）是将对象的创建和依赖关系交由容器管理，通过依赖注入实现解耦。AOP（面向切面编程）是通过动态代理实现关注点（如日志、事务）与业务逻辑分离。

   IOC好处： 解耦、模块化开发与测试、提升代码可维护性。

   **关键词：依赖注入, 解耦, 动态代理。**

   

2. AOP的应用场景？实现原理？ 

   日志记录、权限校验、事务管理、性能监控。

   动态代理（JDK动态代理或CGLIB）。

   **关键词：动态代理, 横切关注点, 解耦, 性能监控。**

   

3. Spring事务的实现原理？ 

   基于AOP，使用TransactionInterceptor拦截方法调用，结合数据库连接的事务管理器控制事务提交或回滚。

   **关键词：AOP, TransactionInterceptor, 事务管理器, 提交回滚。**

   

4. SpringBoot自动装配原理？ 

   通过`@EnableAutoConfiguration`扫描`factories`文件加载自动配置类，根据条件注解决定是否生效。

   **关键词：@EnableAutoConfiguration, 自动配置, 条件注解, 扫描加载。**

   

5. Spring常见注解有哪些？

   `@Component`, `@Service`, `@Repository`, `@Controller`, `@Autowired`, `@Qualifier`, `@Scope`, `@Transactional`。

   

6. Spring Bean的作用域有哪些？ 

   ingleton（单例）、prototype（多例）、request（请求级）、session（会话级）、application（应用级）。

   

7. Spring MVC的执行流程？ 

   - 请求到达前端控制器`DispatcherServlet`。
   - 调用`HandlerMapping`找到对应前端控制器。
   - 处理器执行业务逻辑并返回`ModelAndView`。
   - 视图解析器解析视图并渲染。
   - 返回响应结果。

   **关键词：前端控制器、找处理器、执行业务、视图解析、响应结果。**

   

8. SpringBoot的启动流程？ 

   - 执行`main`方法，启动`SpringApplication.run`。
   - 初始化环境、加载配置、创建应用上下文。
   - 刷新上下文，触发自动装配。
   - 启动完成回调。

   **关键词：启动SpringApplication、初始化、自动装配、回调机制。**

   

9. Spring中用到了哪些设计模式？

   - 单例模式（Bean默认单例）。
   - 工厂模式（BeanFactory创建Bean）。
   - 代理模式（AOP动态代理）。
   - 观察者模式（事件监听机制）。

   **关键词：单例, 工厂, 代理, 模板方法, 观察者。**