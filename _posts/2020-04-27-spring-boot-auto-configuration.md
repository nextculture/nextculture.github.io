---
layout: single
title: 나만의 자동 configuration 만들기
excerpt: github pages 를 활용해서 기술 blog 를 시작해보자.
categories: blog
tags: github github-pages
---


스프링 프로젝트에 여러 starter 들이 있는데 내가 직접 starter를 만들기 위해 어떻게 해야 하는지 알아보자.

springboot version : `2.2.6.RELEASE`

## 기본 auto configuration 프로젝트 구성
테스트를 위해 두 개의 프로젝트가 필요하다. 하나는 starter 프로젝트, 다른 하나는 starter 프로젝트를 참조하여 사용 할 프로젝트.

최종 결과물은 github에서 받을 수 있다.

[starter 프로젝트](https://github.com/puredouble/custom-spring-boot-starter)

[사용 프로젝트](https://github.com/puredouble/spring-boot-custom-started)

### starter 프로젝트 생성
우선 starter 프로젝트를 생성 해 보자. maven 프로젝트로 생성 후 groupId 는 "me.puredouble" artifactId 는 "custom-spring-boot-starter"로 생성한다.
starter는 기본적으로 autoconfigure 모듈, starter 모듈로 나뉘어지는데 그냥 starter 프로젝트 하나만 만들어 사용해도 된다.
naming rule로 starter 프로젝트는 {name}-spring-boot-starter 형태로 지정해야 한다.

생성한 프로젝트에 Animal 클래스를 하나 선언 한다. 
```java
public class Animal {

    private String name;

    private Integer age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Integer getAge() {
        return age;
    }

    public void setAge(Integer age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Animal{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

}
```
이제 AnimalConfiguration class를 생성하여 Animal을 bean으로 등록한다.
```java
@Configuration
public class AnimalConfiguration {

    @Bean
    public Animal animal() {
        Animal animal = new Animal();
        animal.setName("dog");
        animal.setAge(1);
        return animal;
    }

}
```
이름이 dog 이고 나이는 1살인 animal이 빈으로 등록되었다.
starter 프로젝트로 등록하려면 pom.xml 에 관련 의존성을 추가 해야 한다.
```xml
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <maven.compiler.source>1.6</maven.compiler.source>
        <maven.compiler.target>1.6</maven.compiler.target>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-autoconfigure</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-autoconfigure-processor</artifactId>
            <optional>true</optional>
        </dependency>
    </dependencies>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>2.0.3.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
```
properties 영역은 maven install 시 오류가 발생하여 추가했는데 항상 발생하는 것 같지는 않다.
spring boot 프로젝트로 생성하면 괜찮은데 maven 프로젝트로 생성 했을 때 발생하는듯 하다.

Spring Boot는 게시 된 jar 내에 META-INF/spring.factories 파일이 있는지 확인하여 auto-configuration을 등록한다.
프로젝트의 resources 폴더 내에 META-INF/spring.factories 파일을 생성하여 아래 내용을 저장한다.
```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
  me.puredouble.AnimalConfiguration
```

이제 프로젝트를 install 한다.
```sh
mvn clean install
```
프로젝트를 install 하여 maven local repository에 프로젝트가 저장되었으면 starter는 끝!

### starter 사용 할 프로젝트 생성
이제 starter를 사용 할 프로젝트를 생성한다.
이번에는 start.spring.io 에서 프로젝트를 생성해서 사용했다. 설정은 아래와 같이...
- 2.2.6.RELEASE, 
- maven, 
- groupId : me.puredouble, 
- artifactId : spring-boot-custom-started

생성한 프로젝트의 pom.xml 에 만들어 놓은 starter project를 추가한다.
```xml
		<dependency>
			<groupId>me.puredouble</groupId>
			<artifactId>custom-spring-boot-starter</artifactId>
			<version>1.0-SNAPSHOT</version>
		</dependency>
```
이제 Runner Class인 AnimalRunner를 만들고 Animal class를 주입 받아 사용 가능 한지 확인 해보자
```java
@Component
public class AnimalRunner implements ApplicationRunner {

    @Autowired
    private Animal animal;

    @Override
    public void run(ApplicationArguments args) throws Exception {
        System.out.println(animal);
    }

}
system out 으로 animal 객체를 출력 한다.
```
실행결과
```sh
Animal{name='dog', age=1}
```
자동 설정이 잘 동작 하는 것을 확인 할 수 있다.

### 사용 프로젝트에서 bean 등록하여 사용하기
사용 프로젝트에서 Animal type의 bean을 재정의 하여 사용하기 위해 main 메서드가 있는 Application 클래스에 Animal type의 bean을 등록 해보자
```java
@SpringBootApplication
public class Application {

	public static void main(String[] args) {
		SpringApplication.run(Application.class, args);
	}

	@Bean
	public Animal animal() {
		Animal animal = new Animal();
		animal.setName("cat");
		animal.setAge(2);
		return animal;
	}

}
```
이제 프로젝트를 실행 해보면 오류가 발생한다. (springboot 버전에 따라 다를 수 있는 것 같다. 하지만 실행 되더라도 원하는 값인 cat, 2 가 나오지 않고 dog, 1 이 나오게 된다.)
```sh
***************************
APPLICATION FAILED TO START
***************************

Description:
The bean 'animal', defined in class path resource [me/puredouble/AnimalConfiguration.class], could not be registered. A bean with that name has already been defined in me.puredouble.Application and overriding is disabled.
```
해당 bean이 이미 정의되어 있어서 중복 오류가 발생하는데 이를 해결 하기 위해선 @Conditional annotaion을 사용해야 한다.

starter 프로젝트로 돌아가서 Animal Bean 구현에 @ConditionalOnMissingBean annotation을 추가한다.
```java
@Configuration
public class AnimalConfiguration {

    @Bean
    @ConditionalOnMissingBean
    public Animal animal() {
        Animal animal = new Animal();
        animal.setName("dog");
        animal.setAge(1);
        return animal;
    }

}
```
starter 프로젝트를 다시 인스톨 한 뒤 
```sh
mvn clean install
```
사용 프로젝트를 실행 해보면 의도한 대로 출력하는 것을 볼 수 있다.
```sh
Animal{name='cat', age=2}
```
springboot의 auto-configuration 은 두 번의 페이즈로 나뉘는데, 우선 실행 프로젝트의 bean을 먼저 등록 한 뒤 auto-configuration 프로젝트의 bean을 등록하게 되어있다. 
따라서 실행 프로젝트에 이미 등록된 Animal type의 bean 이 있으면 두 번째 페이즈인 auto-configuration 페이즈에서 중복된 bean 등록에 의해 오류가 발생 한 것이었다.
이때, @ConditionalOnMissingBean annotation을 추가하면 두 번째 페이즈 동작 시 해당 type의 bean이 없을 경우에만 생성해 주도록 하여 오류가 발생 하지 않게 된다.

### 사용 프로젝트에서 application.properties 설정으로 bean 생성하기.
springboot web 프로젝트의 server port를 변경 하는 것처럼 추가한 stater module의 자동 생성 bean이 실행 프로젝트의 설정 파일 값을 참조하여 생성 되도록 할 수 있다.

우선 사용 프로젝트에 설정 값을 넣어보자.
```
animal.name = cow
animal.age = 5
```
이제 starter 프로젝트의 pom.xml 에 "spring-boot-configuration-processor" 의존성을 추가한다.
```xml
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-configuration-processor</artifactId>
            <optional>true</optional>
        </dependency>
```

그리고 프로젝트에서 해당 설정 값을 참조 할 수 있도록 properties class를 생성한다.
```java
@ConfigurationProperties("animal")
public class AnimalProperties {

    private String name;

    private Integer age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Integer getAge() {
        return age;
    }

    public void setAge(Integer age) {
        this.age = age;
    }
}
```
생성된 AnimalProperties 타입의 properties 를 전달받아서 bean을 생성하도록 bean 설정을 수정한다.
```java
@Configuration
@EnableConfigurationProperties(AnimalProperties.class)
public class AnimalConfiguration {

    @Bean
    @ConditionalOnMissingBean
    public Animal animal(AnimalProperties animalProperties) {
        Animal animal = new Animal();
        animal.setName(animalProperties.getName());
        animal.setAge(animalProperties.getAge());
        return animal;
    }

}
```
@EnableConfigurationProperties annotation을 추가 했고, AnimalProperties type의 객체를 인자로 받아 bean을 생성하도록 수정했다.

이제 사용 프로젝트의 bean 등록 코드를 주석 처리 후
```java
@SpringBootApplication
public class Application {

	public static void main(String[] args) {
		SpringApplication.run(Application.class, args);
	}

//	@Bean
//	public Animal animal() {
//		Animal animal = new Animal();
//		animal.setName("cat");
//		animal.setAge(2);
//		return animal;
//	}

}
```
다시 stater 프로젝트를 인스톨 후 사용 프로젝트를 실행 해보자
```sh
Animal{name='cow', age=5}
```
application.properties 파일에 설정한 값으로 Animal 객체가 생성되어 주입되었다.
이 이상 자세한 설정은 아래 내용을 참조하자.

****

## 4.28 나만의 자동configuration 만들기
https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-developing-auto-configuration
여기부터는 상기 스프링 부트 공식문서를 기반으로 번역 된 내용이 작성 되었습니다.
영어를 잘 못해서 번역기의 힘을 빌린 뒤 어색한 부분만 수정 했습니다. (springboot 2.2.6.RELEASE 기반)

공유 라이브러리를 개발하는 회사에서 작업하거나 오픈 소스 또는 상용 라이브러리에서 작업하는 경우 고유한 auto-configuration을 개발할 수 있습니다.auto-configuration 클래스는 외부 jar에 번들로 묶을 수 있으며 스프링 부트에서 여전히 픽업할 수 있습니다.

auto-configuration은 auto-configuration 코드와 함께 사용할 일반적인 라이브러리를 제공하는 "starter"에 연결할 수 있습니다. 먼저 사용자 고유의 auto-configuration을 빌드하기 위해 알아야 할 사항을 다루고 사용자 지정 스타터를 만드는 데 필요한 일반적인 단계로이동합니다.

스타터를 단계별로 작성하는 방법을 보여주는 [데모 프로젝트](https://github.com/snicoll/spring-boot-master-auto-configuration)가 제공됩니다.

### 4.28.1 Auto-configured Beans 이해
기본적으로 auto-configuration은 표준 `@Configuration` 클래스로 구현됩니다. 추가 `@Conditional` annotation은 auto-configuration이 적용되는시기를 제한하는 데 사용됩니다.일반적으로 auto-configuration 클래스는 `@ConditionalOnClass` 및 `@ConditionalOnMissingBean` annotation을 사용합니다. 이렇게하면 auto-configuration이 관련 클래스를 찾은 경우 자신의 `@Configuration`을 선언하지 않은 경우에만 적용됩니다.

`spring-boot-autoconfigure`의 소스 코드를 탐색하여 Spring이 제공하는 `@Configuration` 클래스를 볼 수 있습니다 (`META-INF / spring.factories` 파일 참조).

### 4.28.2. Auto-configuration 후보 찾기
Spring Boot는 게시 된 jar 내에 `META-INF/spring.factories` 파일이 있는지 확인합니다. 파일은 다음 예제와 같이 `EnableAutoConfiguration` 키 아래에 configuration 클래스를 나열해야합니다.
```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
com.mycorp.libx.autoconfigure.LibXAutoConfiguration,\
com.mycorp.libx.autoconfigure.LibXWebAutoConfiguration
```
```
auto-configuration은 그런 식으로만 로드해야합니다. 특정 패키지 공간에 정의되어 있고 구성 요소 스캔의 대상이 되지 않는지 확인하십시오. 또한 auto-configuration 클래스는 구성 요소 검색을 통해 추가 구성 요소를 찾을 수 없습니다. 대신 특정 @Imports를 사용해야합니다.
```
Configuration을 특정 순서로 적용해야하는 경우 `@AutoConfigureAfter` 또는 `@AutoConfigureBefore` annotation을 사용할 수 있습니다. 예를 들어, web-specific configuration을 제공하는 경우 `WebMvcAutoConfiguration` 후에 클래스를 적용해야 할 수 있습니다.

서로 직접적인 지식이 없어야하는 특정 auto-configuration을 주문하려면 `@AutoConfigureOrder`를 사용할 수도 있습니다. 이 annotation은 일반 `@Order` annotation과 동일한 의미를 갖지만 auto-configuration 클래스를위한 전용 순서를 제공합니다.

### 4.28.3. Condition Annotations
거의 항상 auto-configuration 클래스에 하나 이상의 `@Conditional` annotation을 포함하려고합니다. `@ConditionalOnMissingBean` annotation은 개발자가 기본값에 만족하지 않는 경우 auto-configuration을 재정의하는 데 사용되는 일반적인 예입니다.

Spring Boot에는 `@Configuration` 클래스 또는 개별 `@Bean` 메소드에 annotation을 달아 자신의 코드에서 재사용 할 수있는 여러 `@Conditional` 어노테이션이 포함되어 있습니다. 이러한 annotation에는 다음이 포함됩니다.
- Class Conditions
- Bean Conditions
- Property Conditions
- Resource Conditions
- Web Application Conditions
- SpEL Expression Conditions

#### Class Conditions

`@ConditionalOnClass` 및 `@ConditionalOnMissingClass` annotation을 사용하면 특정 클래스의 존재 여부에 따라 `@Configuration` 클래스를 포함시킬 수 있습니다. annotation 메타 데이터가 ASM을 사용하여 구문 분석되므로 실제로 해당 클래스가 실행중인 애플리케이션 클래스 경로에 표시되지 않을 수도 있지만 value attribute을 사용하여 실제 클래스를 참조 할 수 있습니다. `String` value를 사용하여 클래스 이름을 지정하려는 경우 `name` attribute을 사용할 수도 있습니다.

이 메커니즘은 일반적으로 리턴 type이 조건의 대상인 `@Bean` 메소드에 동일한 방식으로 적용되지 않습니다. 메소드의 조건이 적용되기 전에 JVM이 클래스를로드하고 클래스가 실패 할 경우 잠재적으로 처리 된 메소드 참조를 로드합니다. 만일 클래스가 존재하지 않는다면.

이 시나리오를 처리하기 위해 다음 예제와 같이 별도의 `@Configuration` 클래스를 사용하여 조건을 분리 할 수 있습니다.

```java
@Configuration(proxyBeanMethods = false)
// Some conditions
public class MyAutoConfiguration {

    // Auto-configured beans

    @Configuration(proxyBeanMethods = false)
    @ConditionalOnClass(EmbeddedAcmeService.class)
    static class EmbeddedConfiguration {

        @Bean
        @ConditionalOnMissingBean
        public EmbeddedAcmeService embeddedAcmeService() { ... }

    }

}
```
```
메타 annotation의 일부로 @ConditionalOnClass 또는 @ConditionalOnMissingClass를 사용하여 고유 한 annotation을 작성하는 경우 처리되지 않는 클래스를 참조하는 이름을 사용해야합니다.
```

#### Bean Conditions

`@ConditionalOnBean` 및 `@ConditionalOnMissingBean` 어노테이션은 특정 Bean의 존재 여부에 따라 Bean을 포함 할 수 있습니다. `value` attribute를 사용하여 type별로 Bean을 지정하거나 `name`별로 Bean을 지정할 수 있습니다. `search` attribute를 사용하면 Bean을 검색 할 때 고려해야 할 `ApplicationContext` 계층 구조를 제한 할 수 있습니다.

`@Bean` 메소드에 배치 될 때 대상 type의 기본값은 다음 예제와 같이 메소드의 리턴 type입니다.

```java
@Configuration(proxyBeanMethods = false)
public class MyAutoConfiguration {

    @Bean
    @ConditionalOnMissingBean
    public MyService myService() { ... }

}
```

이전 예제에서 MyService type의 Bean이 ApplicationContext에 이미 포함되어 있지 않은 경우 myService Bean이 작성됩니다.
```
Bean 정의가 추가되는 순서에 대해 매우주의해야합니다. 이러한 조건은 지금까지 처리 된 내용을 기반으로 평가되기 때문입니다. 이러한 이유로 auto-configuration 클래스에 @ConditionalOnBean 및 @ConditionalOnMissingBean annotation 만 사용하는 것이 좋습니다 (사용자 정의 Bean 정의가 추가 된 후에는 로드가 보장되므로.)
```
```
@ConditionalOnBean 및 @ConditionalOnMissingBean은 @Configuration 클래스가 작성되는 것을 막지 않습니다. 클래스 레벨에서 이러한 조건을 사용하는 것과 annotation이 포함 된 각 @Bean 메소드를 표시하는 것의 유일한 차이점은 조건이 일치하지 않으면 전자가 @Configuration 클래스를 Bean으로 등록하는 것을 방지한다는 것입니다.
```

#### Property Conditions
`@ConditionalOnProperty` 어노테이션은 Spring 환경 특성을 기반으로 configuration을 포함 할 수 있습니다. `prefix` 및 `name` attribute을 사용하여 점검해야하는 특성을 지정하십시오. 기본적으로 존재하고 `false`가 아닌 모든 attribute이 일치합니다. `havingValue` 및 `matchIfMissing` attribute을 사용하여 고급 검사를 만들 수도 있습니다.

#### Resource Conditions
`@ConditionalOnResource` 주석을 사용하면 특정 리소스가있는 경우에만 configuration을 포함 할 수 있습니다. file : /home/user/test.dat와 같이 일반적인 Spring 규칙을 사용하여 자원을 지정할 수 있습니다.

#### Web Application Conditions
`@ConditionalOnWebApplication` 및 `@ConditionalOnNotWebApplication` 주석을 사용하면 응용 프로그램이 "웹 응용 프로그램"인지 여부에 따라 configuration을 포함 할 수 있습니다. 서블릿 기반 웹 애플리케이션은 Spring `WebApplicationContext`를 사용하거나 `session` 범위를 정의하거나 `ConfigurableWebEnvironment`를 갖는 애플리케이션이다. 반응 형 웹 응용 프로그램은 `ReactiveWebApplicationContext`를 사용하거나 `ConfigurableReactiveWebEnvironment`가있는 모든 응용 프로그램입니다.

#### SpEL Expression Conditions
`@ConditionalOnExpression` 주석을 사용하면 SpEL 식의 결과를 기반으로 configuration을 포함 할 수 있습니다.


### 4.28.4. Testing your Auto-configuration
auto-configuration은 사용자 configuration (`@Bean` 정의 및 `Environment` 사용자 정의), 조건 평가 (특정 라이브러리의 존재) 및 기타 여러 요인의 영향을받을 수 있습니다. 구체적으로, 각 테스트는 이러한 사용자 정의 조합을 나타내는 잘 정의 된 `ApplicationContext`를 작성해야합니다. `ApplicationContextRunner`는이를 달성하기위한 좋은 방법을 제공합니다.

`ApplicationContextRunner`는 일반적으로 기본 공통 configuration을 수집하기 위해 테스트 클래스의 필드로 정의됩니다. 다음 예제는 `UserServiceAutoConfiguration`이 항상 호출되는지 확인합니다.

```java
private final ApplicationContextRunner contextRunner = new ApplicationContextRunner()
        .withConfiguration(AutoConfigurations.of(UserServiceAutoConfiguration.class));
```
```
여러 개의 auto-configuration을 정의해야하는 경우 응용 프로그램을 실행할 때와 동일한 순서로 선언이 수행되므로 order를 선언 할 필요가 없습니다.
```
각 테스트는 러너를 사용하여 특정 사용 사례를 나타낼 수 있습니다. 예를 들어 아래 샘플은 사용자 configuration (`UserConfiguration`)을 호출하고 auto-configuration이 제대로 종료되는지 확인합니다. 실행 호출은 `Assert4J`와 함께 사용할 수있는 콜백 컨텍스트를 제공합니다.

```java
@Test
void defaultServiceBacksOff() {
    this.contextRunner.withUserConfiguration(UserConfiguration.class).run((context) -> {
        assertThat(context).hasSingleBean(UserService.class);
        assertThat(context).getBean("myUserService").isSameAs(context.getBean(UserService.class));
    });
}

@Configuration(proxyBeanMethods = false)
static class UserConfiguration {

    @Bean
    UserService myUserService() {
        return new UserService("mine");
    }

}
```

다음 예제와 같이 `Environment`을 쉽게 사용자 정의 할 수도 있습니다.

```java
@Test
void serviceNameCanBeConfigured() {
    this.contextRunner.withPropertyValues("user.name=test123").run((context) -> {
        assertThat(context).hasSingleBean(UserService.class);
        assertThat(context.getBean(UserService.class).getName()).isEqualTo("test123");
    });
}
```

러너를 사용하여 `ConditionEvaluationReport`를 표시 할 수도 있습니다. 보고서는 `INFO` 또는 `DEBUG` 수준에서 print 할 수 있습니다. 다음 예는 `ConditionEvaluationReportLoggingListener`를 사용하여 자동 구성 테스트에서 보고서를 인쇄하는 방법을 보여줍니다.

```java
@Test
public void autoConfigTest {
    ConditionEvaluationReportLoggingListener initializer = new ConditionEvaluationReportLoggingListener(
            LogLevel.INFO);
    ApplicationContextRunner contextRunner = new ApplicationContextRunner()
            .withInitializer(initializer).run((context) -> {
                    // Do something...
            });
}
```

#### 웹 컨텍스트 시뮬레이션
서블릿 또는 반응성 웹 애플리케이션 컨텍스트에서만 작동하는 자동 구성을 테스트해야하는 경우 각각 `WebApplicationContextRunner` 또는 `ReactiveWebApplicationContextRunner`를 사용하십시오.

#### 클래스 패스 재정의
런타임에 특정 클래스 and/or 패키지가 없을 때 발생하는 상황을 테스트 할 수도 있습니다. Spring Boot는 러너가 쉽게 사용할 수있는 `FilteredClassLoader`와 함께 제공됩니다. 다음 예에서는 `UserService`가 없으면 자동 구성이 올바르게 비활성화되어 있다고 가정합니다.

```java
@Test
void serviceIsIgnoredIfLibraryIsNotPresent() {
    this.contextRunner.withClassLoader(new FilteredClassLoader(UserService.class))
            .run((context) -> assertThat(context).doesNotHaveBean("userService"));
}
```

### 4.28.5. Creating Your Own Starter
라이브러리의 전체 스프링 부트 스타터에는 다음 구성 요소가 포함될 수 있습니다.
- auto-configuration code가 포함 된 `autoconfigure` module.
- `autoconfigure` module뿐만 아니라 라이브러리 및 일반적으로 유용한 추가 dependency에 대한 dependency을 제공하는 `starter` module입니다. 간단히 말해서, 스타터를 추가하면 해당 라이브러리 사용을 시작하는 데 필요한 모든 것이 제공됩니다.
```
이러한 두 가지 문제를 분리 할 필요가없는 경우 자동 구성 코드와 dependency 관리를 단일 모듈로 결합 할 수 있습니다.
```
#### Naming
starter를위한 적절한 네임 스페이스를 제공해야합니다. 다른 Maven `groupId`를 사용하더라도 `spring-boot`로 모듈 이름을 시작하지 마십시오. 향후 자동 구성에 대한 공식 지원을 제공 할 수 있습니다.

일반적으로 시작 후 결합 모듈의 이름을 지정해야합니다. 예를 들어, "acme"에 대한 스타터를 작성하고 autoconfigure module의 이름을 `acme-spring-boot-autoconfigure` 및 스타터 `acme-spring-boot-starter`로 지정한다고 가정하십시오. 두 모듈을 결합한 모듈이 하나 뿐인 경우 이름을 `acme-spring-boot-starter`로 지정하십시오.

#### Configuration keys
스타터가 구성 키를 제공하는 경우 고유 한 네임 스페이스를 사용하십시오. 특히 스프링 부트가 사용하는 네임 스페이스 (예 : `server`, `management`, `spring` 등)에 키를 포함시키지 마십시오. 동일한 네임 스페이스를 사용하는 경우 나중에 모듈을 손상시키는 방식으로 이러한 네임 스페이스를 수정할 수 있습니다. 일반적으로 모든 키 앞에 소유 한 네임 스페이스 (예 : `acme`)를 접두어로 사용하십시오.

다음 예제와 같이 각 특성에 대해 javadoc 필드를 추가하여 구성 키가 문서화되어 있는지 확인하십시오.

```java
@ConfigurationProperties("acme")
public class AcmeProperties {

    /**
     * Whether to check the location of acme resources.
     */
    private boolean checkLocation = true;

    /**
     * Timeout for establishing a connection to the acme server.
     */
    private Duration loginTimeout = Duration.ofSeconds(3);

    // getters & setters

}
```
```
JSON에 추가되기 전에 처리되지 않으므로 @ConfigurationProperties 필드 Javadoc과 함께 간단한 텍스트 만 사용해야합니다.
```
다음은 설명의 일관성을 유지하기 위해 내부적으로 따르는 몇 가지 규칙입니다.
  - "The"또는 "A"로 설명을 시작하지 마십시오.
  - `boolean` type의 경우 "Whether"또는 "Enable"로 설명을 시작하십시오.
  - 콜렉션 기반 type의 경우 "쉼표로 구분 된 목록"으로 설명을 시작하십시오.
  - `long` 대신 `java.time.Duration`을 사용하고 밀리 초와 다른 경우 기본 단위를 설명하십시오 (예 : "지속 기간 접미사가 지정되지 않으면 초가 사용됩니다."
  - 런타임시 판별해야하는 경우가 아니면 설명에 기본값을 제공하지 마십시오.
  
키에 IDE 지원을 제공 할 수 있도록 메타 데이터 생성을 트리거해야합니다. 생성 된 메타 데이터 (META-INF/spring-configuration-metadata.json)를 검토하여 키가 올바르게 문서화되었는지 확인할 수 있습니다. 호환 가능한 IDE에서 자체 스타터를 사용하는 것도 메타 데이터의 품질을 검증하는 것이 좋습니다.


#### `autoconfigure` Module

`autoconfigure` module에는 라이브러리를 시작하는 데 필요한 모든 것이 포함되어 있습니다. 또한 구성 키 정의 (예 : `@ConfigurationProperties`) 및 구성 요소 초기화 방법을 추가로 사용자 정의하는 데 사용할 수있는 모든 콜백 인터페이스가 포함될 수 있습니다.
```
프로젝트에 autoconfigure module을 더 쉽게 포함 할 수 있도록 라이브러리에 대한 dependency를 선택적으로 표시해야합니다. 그렇게하면 라이브러리가 제공되지 않으며 기본적으로 Spring Boot가 종료됩니다.
```
Spring Boot는 주석 프로세서를 사용하여 메타 데이터 파일 (`META-INF/spring-autoconfigure-metadata.properties`)에서 자동 구성 조건을 수집합니다. 해당 파일이 있으면 일치하지 않는 자동 구성을 열심히 필터링하는 데 사용되어 시작 시간이 향상됩니다. 자동 구성이 포함 된 모듈에 다음 dependency를 추가하는 것이 좋습니다.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-autoconfigure-processor</artifactId>
    <optional>true</optional>
</dependency>
```

Gradle 4.5 이하 버전에서는 다음 예제와 같이 compileOnly 구성에서 dependency를 선언해야합니다.

```grrovy
dependencies {
    compileOnly "org.springframework.boot:spring-boot-autoconfigure-processor"
}
```

Gradle 4.6 이상에서는 다음 예제와 같이 annotationProcessor 구성에서 dependency를 선언해야합니다.

```grrovy
dependencies {
    annotationProcessor "org.springframework.boot:spring-boot-autoconfigure-processor"
}
```

#### Starter Module
starter는 실제로 빈 jar입니다. 이 라이브러리의 유일한 목적은 라이브러리 작업에 필요한 dependency를 제공하는 것입니다. 시작하기 위해 필요한 것에 대한 의견이있는 견해로 생각할 수 있습니다.

스타터가 추가 된 프로젝트에 대해 가정하지 마십시오. auto-configuring 라이브러리에 일반적으로 다른 스타터가 필요한 경우 해당 라이브러리도 언급하십시오. 라이브러리의 일반적인 사용에 필요하지 않은 dependency를 포함하지 않아야하므로 선택적 dependency 수가 많으면 적절한 기본 dependency 세트를 제공하기가 어려울 수 있습니다. 즉, 선택적 dependency를 포함하지 않아야합니다.
```
어느 쪽이든, 스타터는 코어 스프링 부트 스타터 (spring-boot-starter)를 직접 또는 간접적으로 참조해야합니다 (즉, 스타터가 다른 스타터에 의존하는 경우 추가 할 필요가 없습니다). 커스텀 스타터만으로 프로젝트를 생성 한 경우 스프링 스타트의 핵심 기능은 코어 스타터의 존재로 인해 인정됩니다.
```




