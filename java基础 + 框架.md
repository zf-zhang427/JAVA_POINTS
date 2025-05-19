- 类加载

![](../../../LEETCODE/pic/类加载.png)



- spring事务实现

  ![](../../../LEETCODE/pic/spring事务实现.png)

  - **使用AOP的切面来实现的事务**

    实现：目标方法有注解@transactional， 

    原理：通过aop对方法前后进行拦截，aop方法使用@component、@aspect、@around(“。。。。”)；然后在此类中实现具体的方法try-catch进行回滚

  - 应用场景

    用户信息判断与优惠卷秒杀

  - aop实现

    动态代理，利用反射机制在运行时为接口生成代理对象