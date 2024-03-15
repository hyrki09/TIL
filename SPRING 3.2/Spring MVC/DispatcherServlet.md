DispatcherServlet
-----

---

Spring의 웹 MVC 프레임워크는 요청 중심으로 설계되어 컨트롤러에 요청을 보내고 웹 애플리케이션 개발을 용이하게 하는 기타 기능을 제공합니다.   
그러나 Spring의 DispatcherServlet은 그 이상의 기능을 수행합니다.     
Spring IoC 컨테이너와 완전히 통합되어 있으므로 Spring이 가지고 있는 다른 모든 기능을 사용할 수 있습니다.

----

DispatcherServlet은 실제 Servlet(HttpServlet 기본 클래스에서 상속됨)이므로 웹 응용 프로그램의 web.xml에 선언됩니다.     
동일한 web.xml 파일의 URL 매핑을 사용하여 DispatcherServlet이 처리할 요청을 매핑해야 합니다.     
이것은 표준 Java EE Servlet 구성입니다. 

 [DispatcherServlet 선언 및 매핑]
``` xml
<web-app>

    <servlet>
        <servlet-name>example</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>example</servlet-name>
        <url-pattern>/example/*</url-pattern>
    </servlet-mapping>

</web-app>
```

이전 예제에서 /example로 시작하는 모든 요청은 예제라는 이름의 DispatcherServlet 인스턴스에서 처리됩니다.   
Servlet 3.0+ 환경에서는 Servlet 컨테이너를 프로그래밍 방식으로 구성할 수도 있습니다.    

[위의 web.xml 예제와 동등한 코드 기반]
``` java
public class MyWebApplicationInitializer implements WebApplicationInitializer {

    @Override
    public void onStartup(ServletContext container) {
        ServletRegistration.Dynamic registration = container.addServlet("dispatcher", new DispatcherServlet());
        registration.setLoadOnStartup(1);
        registration.addMapping("/example/*");
    }

}
```
----
WebApplicationInitializer는 Spring MVC에서 제공하는 인터페이스로 코드 기반 구성이 탐지되어 자동으로 모든 서블릿 3 컨테이너를 초기화하는 데 사용되도록 보장합니다. 
AbstractDispatcherServletInitializer라는 이름의 이 인터페이스의 추상적인 기본 클래스 구현은 서블릿 매핑을 지정하는 것만으로도 DispatcherServlet을 등록하는 것을 더욱 쉽게 해줍니다.     
자세한 내용은 코드 기반 서블릿 컨테이너 초기화를 참조(Code-based Servlet container initialization)


---     


위의 내용은 스프링 웹 MVC를 설정하는 첫 번째 단계일 뿐입니다.    
이제 스프링 웹 MVC 프레임워크에서 사용하는 다양한 빈(Dispatcher Servlet 자체 위 및 위)을 구성해야 합니다.


> 섹션 5.14의 “Additional Capabilities of the ApplicationContext”(ApplicationContext의 추가 기능)에서 자세히 설명한 대로 Spring의 ApplicationContext 인스턴스의 범위를 지정할 수 있습니다.   
Web MVC 프레임워크에서 각 DispatcherServlet에는 고유한 WebApplicationContext가 있으며, 이는 루트 WebApplicationContext에 이미 정의된 모든 빈을 상속합니다.    
이러한 상속된 빈은 Servlet별 범위에서 재정의할 수 있으며, 주어진 Servlet 인스턴스에 로컬인 새로운 범위별 빈을 정의할 수 있습니다.    

---

DispatcherServlet을 초기화하면 Spring MVC는 웹 애플리케이션의 WEB-INF 디렉터리에서 [servlet-name]-servlet.xml이라는 파일을 찾고 거기에 정의된 Bean을 생성하고 동일한 이름으로 정의된 모든 Bean의 정의를 재정의합니다. 글로벌 범위에서.

다음 DispatcherServlet Servlet 구성(web.xml 파일)을 고려하십시오.

``` xml
<web-app>

    <servlet>
        <servlet-name>golfing</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>

    <servlet-mapping>
        <servlet-name>golfing</servlet-name>
        <url-pattern>/golfing/*</url-pattern>
    </servlet-mapping>

</web-app>
```
 위의 서블릿 구성을 사용하면 애플리케이션에 /WEB-INF/golfing-servlet.xml이라는 파일이 있어야 합니다. 이 파일에는 모든 Spring Web MVC 관련 구성 요소(빈)가 포함됩니다. 서블릿 초기화 매개변수를 통해 이 구성 파일의 정확한 위치를 변경할 수 있습니다(자세한 내용은 아래 참조).

WebApplicationContext는 웹 애플리케이션에 필요한 몇 가지 추가 기능을 포함하는 일반 ApplicationContext의 확장입니다.    
 WebApplicationContext는 ServletContext에 바인딩되어 있으며 RequestContextUtils 클래스의 정적 메서드를 사용하면 WebApplicationContext에 액세스해야 하는 경우 언제든지 WebApplicationContext를 조회할 수 있습니다.

 




    
       

참고한 자료 : https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/mvc.html#mvc-servlet