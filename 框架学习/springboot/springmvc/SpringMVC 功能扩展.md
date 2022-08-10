[toc]

# SpringMVC 功能扩展

## 接口 WebMvcConfigurer

### 是什么

我们可以通过实现接口 WebMvcConfigurer，重写方法的方式来扩展 SpringMVC

### SpringMVC 的官方扩展

1. 在类 SpringMvcAutoConfiguration 中，实现了接口 WebMvcConfigurer 的类 WebMvcAutoConfigurationAdapter 扩展了 SpringMVC 的部分功能。在这里我称这个类为 SpringMVC 官方扩展类。

   ```java
   public static class WebMvcAutoConfigurationAdapter implements WebMvcConfigurer {
       public void configureMessageConverters(){}
       public void configureAsyncSupport(){}
       public void configurePathMatch(){}
       public void configureContentNegotiation(){}
   }
   ```


### SpringMVC 的自定义扩展

1. 由于类 WebMvcAutoConfigurationAdapter 扩展了 SpringMVC 的部分功能，因此我们只需要扩展 SpringMVC 的拦截器、视图控制器、CORS 等在开发中需要额外扩展的功能

2. 创建一个实现了接口 WebMvcConfigurer 的类 MyWebAutoConfigurationAdapter，重写需要扩展的功能的方法。在这里我称这个类为 SpringMVC 自定义扩展类。下面以扩展拦截器功能为例子：

   ```java
   import org.springframework.context.annotation.Configuration;
   import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
   import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;
   import top.hansarchive.interceptors.MyInterceptor;
   
   /* 实现 WebMvcConfigurer 接口 */
   @Configuration
   public class MyWebMvcAutoConfigurationAdapter implements WebMvcConfigurer {
   
       /* 重写方法，配置拦截器 */
       @Override
       public void addInterceptors(InterceptorRegistry registry) {
           /* 添加拦截器 */
           registry.addInterceptor(new MyInterceptor())
                   /* 添加拦截的请求接口 */
                   .addPathPatterns("/**")
                   /* 添加不拦截的请求接口 */
                   .excludePathPatterns();
       }
       
   }
   ```

那么是如何能自定义扩展 SpirngMvc 的功能，又能保留 SpirngBoot 的官方扩展的呢？

## SpringMVC 多扩展类共同扩展原理

1. 在 SpringMVC 官方扩展类上使用注解让类 EnableWebMvcConfiguration 导入了容器中

   ```java
   @Import({WebMvcAutoConfiguration.EnableWebMvcConfiguration.class})
   ```

2. 这个类的父类 DelegatingWebMvcConfiguration 有一个使用属性注入的 set 方法：setConfigurers. 它可以将所有实现了接口 WebConfigurer 并注册进容器成为 Bean 的 SpringMVC 扩展类全部找到并组合成列表，然后依赖注入到类 DelegatingWebMvcConfiguration 里，然后调用类 WebMvcConfigurerComposite 的 addWebMvcConfigurers 方法

   ```java
   private final WebMvcConfigurerComposite configurers = new WebMvcConfigurerComposite();
   
   @Autowired(
       required = false
   )
   public void setConfigurers(List<WebMvcConfigurer> configurers) {
       if (!CollectionUtils.isEmpty(configurers)) {
           this.configurers.addWebMvcConfigurers(configurers);
       }
   
   }
   ```

3. 在类 WebMvcConfigurerComposite 的 addWebMvcConfigurers 方法中将扩展类列表添加到 delegates 委派器

   ```java
   private final List<WebMvcConfigurer> delegates = new ArrayList();
   
   public void addWebMvcConfigurers(List<WebMvcConfigurer> configurers) {
       if (!CollectionUtils.isEmpty(configurers)) {
           this.delegates.addAll(configurers);
       }
   
   }
   ```

4. 底层调用 WebMvcConfigurer 对应方法时是循环调用委派器的

   ```java
   public void addInterceptors(InterceptorRegistry registry) {
       Iterator var2 = this.delegates.iterator();
   
       while(var2.hasNext()) {
           WebMvcConfigurer delegate = (WebMvcConfigurer)var2.next();
           delegate.addInterceptors(registry);
       }
   
   }
   ```

一句话：SpringBoot底层将所有实现了接口 WebMvcConfigurer 且注册进容器中的扩展类全部放入委派器 delegates（列表）里，通过遍历委派器，调用扩展类对象的方法来对 SpringMVC 进行扩展