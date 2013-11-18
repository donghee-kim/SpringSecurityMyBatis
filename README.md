SpringSecurityMyBatis
=====================

Spring Security Provides both Authentication and Authority in JavaEE-Based Environment with POJO.



1. Configuration
	- web.xml Configuration / Filter Declaration

		 <filter>
		 	<filter-name>SpringSecurityFilterChain</filter-name>
		 	<filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
		 </filter>
		 <filter-mapping>
			<filter-name>SpringSecurityFilterChain</filter-name>
		  <url-pattern> /* </url-pattern>
		 </fitler-mapping>


	  * DelegatingFilterProxy is a Spring Framework class which delegates to a filter implementation (Spring bean)
    * filter name "SpringSecurityFilterChain" is Infrastructure bean(name) created by the namespace
    * Do not use this bean yourself
    * Adding this to web.xml as uppon, it's ready to start editing your application context file.
    
