SpringSecurityMyBatis
=====================

Spring Security Provides both Authentication and Authority in JavaEE-Based Environment with POJO.



1. Configuration
	- web.xml Configuration / Filter Declaration
	- It provides a hook into Spring Security Web InfraStructure

		 &lt;filter>
		 	&lt;filter-name>springSecurityFilterChain&lt;/filter-name>
		 	&lt;filter-class>org.springframework.web.filter.DelegatingFilterProxy&lt;/filter-class>
		 &lt;/filter>
		 &lt;filter-mapping>
			&lt;filter-name>springSecurityFilterChain&lt;/filter-name>
		  &lt;url-pattern> /* &lt;/url-pattern>
		 &lt;/fitler-mapping>


	  * DelegatingFilterProxy is a Spring Framework class which delegates to a filter implementation (Spring bean)
    * filter name "SpringSecurityFilterChain" is Infrastructure bean(name) created by the namespace
    * Do not use this bean yourself
    * Adding this to web.xml as uppon, it's ready to start editing your application context file.
    * 
  
	- &lt;http> configuration
		- Enable Web Security Sevices
	&lt;http auto-config='true'>
		&lt;intercept-url pattern="/**" method="" access="ROLE_USER"/>
	&lt;/http>
        *http element creates bean FilterChainProxy named "springSecurityFilterChain"
	(SecurityContextPersistenceFilter, ExceptionTranslationFilter,FilterSecurityInterceptor) - these are fixed
	(All filters are rquired a reference to the AuthenticaionManager
	
	&lt;authentication-manager>
		&lt;authentication-provider>
			&lt;user-service>
				&lt;user name ="jimi" password="jimipassword" authorities="ROLE_USER, ROLE_ADMIN"/>
			&lt;/user-serivce>
		&lt;/authentication-provider>
	&lt;/authentication-manager>

	* authentication-provider (child of authentication-manager which creates ProviderManager and registers the authentication providers with it) element creates DaoAuthenticationProvider bean
	* user-service element creates an InMemoryDaoImpl bean
	* 
    Advanced Web Features
      - Remember me
      - Adding HTTP/HTTPS Channel Security
      - Session Management
      	- Detecting Timeouts
      	- Concurrent Session Control

   Method Security
   	- From 2.0 JSR-250, @Secured annotation
   	- From 3.0 expression-based annotation
   	- apply security to a intercept-methods elements, entire service layer using AspectJ style pointcuts.
   	
   	@Secured Support
   	&lt;global-method-security secured-annotations="enable"/>
   	JSR-250 annotation
   	&lt;global-method-security jsr250-annotations="enable"/>
   	To use expression-based systax (recommaned if need to define role ... )
   	&lt;global-method-security pre-post-annotation="enable"/>


	
