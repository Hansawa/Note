# @EnableWebMvc

## 是什么

当使用了 @EnableWebMvc 注解时，SpringBoot 就不会使用 SpringMVC 的默认自动配置类。这个时候我们就可以完全自定义 SpringMVC 了

## 怎么做到的

1. 在 SpringMVC 的自动配置类 WebMvcAutoConfiguration 中，有一个条件注解 @ConditionalOnMissingBean({WebMvcConfigurationSupport.class})，意味着容器中存在类 WebMvcConfigurationSupport 时，自动配置类不再执行，SpringBoot 就不会使用这个自动配置类的配置

   ```java
   @ConditionalOnMissingBean({WebMvcConfigurationSupport.class})
   ```

2. 而在注解 @EnableWebMvc 中，通过注解让容器导入了类 DelegatingWebMvcConfiguration

   ```java
   @Import({DelegatingWebMvcConfiguration.class})
   ```

3. 并且该类又继承自 WebMvcConfigurationSupport

   ```java
   public class DelegatingWebMvcConfiguration extends WebMvcConfigurationSupport {...}
   ```

因此，使用了 @EnableWebMvc 注解时，SpringBoot 就不会使用 SpringMVC 自动配置类的默认配置

