SpringSecurityMyBatis
=====================

Spring Security Provides both Authentication and Authority in JavaEE-Based Environment with POJO.



1. Configuration
	- web.xml Configuration / Filter Declaration
	- It provides a hook into Spring Security Web InfraStructure

		 <filter>
		 	<filter-name>springSecurityFilterChain</filter-name>
		 	<filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
		 </filter>
		 <filter-mapping>
			<filter-name>springSecurityFilterChain</filter-name>
		  <url-pattern> /* </url-pattern>
		 </fitler-mapping>


	  * DelegatingFilterProxy is a Spring Framework class which delegates to a filter implementation (Spring bean)
    * filter name "SpringSecurityFilterChain" is Infrastructure bean(name) created by the namespace
    * Do not use this bean yourself
    * Adding this to web.xml as uppon, it's ready to start editing your application context file.
    * 
  
	- <http> configuration
		- Enable Web Security Sevices
	<http auto-config='true'>
		<intercept-url pattern="/**" method="" access="ROLE_USER"/>
	</http>
        *http elements create bean FilterChainProxy named "springSecurityFilterChain"
	
	<authentication-manager>
		<authentication-provider>
			<user-service>
				<user name ="jimi" password="jimipassword" authorities="ROLE_USER, ROLE_ADMIN"/>
			</user-serivce>
		</authentication-provider>
	</authentication-manager>

	* authentication-provider (child of authentication-manager which creates ProviderManager and registers the authentication providers with it) element creates DaoAuthenticationProvider bean
	* user-service element creates an InMemoryDaoImpl bean
	* 




	
