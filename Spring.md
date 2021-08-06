### Spring中bean的声明周期

- bean容器找到Spring bean的定义
- bean容器通过反射创建bean实例
- 如果涉及一些属性,就通过set()方法设置属性
- 如果该bean实现了BeanNameAware接口,则调用setNameAware()方法,给bean设置名字
- 如果该bean实现了BeanClassLoaderAware接口,则调用setClassLoader()方法,传入classLoder
- 相应了如果该bean实现了其他Aware接口,则调用对应的方法
- 如果有和加载这个bean的Spring容器相关的BeanPostProcessor对象,则调用postProcessorBeforeInitialization()方法,在初始化前进行处理
- 如果该bean实现了InitializingBean接口,则调用afterPropertiesSet()方法
- 如果配置文件中有关于这个bean的Init-method属性,则执行指定的方法
- 如果有和加载这个bean的Spring容器相关的beanPostProcessor对象,则调用postProcessorAfterInitialization()方法
- 当要销毁该bean时,如果该bean实现了DisposibleBean接口,执行destroy()方法
- 当要销毁该bean时,如果该bean在配置文件中的定义有destroy-method属性,则执行对应的方法

### 对Spring MVC的理解

- 在以前的web应用开发中,整个应用几乎都由jsp组成,只用少量的javaBean去处理数据库连接,访问等,这种模式下,jsp既是控制层又是表现层,这样前后端相互依赖,逻辑也比较混乱,不利于开发,测试,维护.
- 然后就是JavaBean+jsp+Servlet的模式,这种是最早的mvc模式,它的问题在于抽象和封装的程度不够,会重复造轮子,降低了可维护性和复用性.
- spring MVC天然与Spring集成,将后端项目分为Entity层,Dao层,Service层,Controller层,便于我们的开发,且运行速度很快.

### Spring MVC的原理

1.客户端发送请求

2.DispatcherServlet接收到请求,然后根据请求信息调用HandlerMapping,解析请求对应的Handler

3.HandlerAdapter会根据adapter来调用真正的处理器来处理请求,一般来说就是我们的controller

4.处理完请求后,会返回一个ModelAndView对象给DispatcherServlet,Model是返回的数据对象,View是个逻辑上的View

5.ViewResolve会根据逻辑View查找实际的View,然后返回给DispatcherServlet

6.DispatcherServlet把返回的Model传给View,也就是视图渲染.

7.最后将View返回给请求者

### Spring中用到了哪些设计模式

- 工厂模式:Spring使用工厂模式通过BeanFactory和ApplicationContext创建bean对象

### Spring管理事务的方式

### Spring中事务的隔离级别有哪几种

Spring中 事务的传播方式有哪几种

