1、You do that by configuring Spring Security in the application. If Spring Security is on the classpath, then Spring Boot automatically secures all HTTP endpoints with "basic" authentication. But you can further customize the security settings. The first thing you need to do is add Spring Security to the classpath.

    compile("org.springframework.boot:spring-boot-starter-security")

2、As for the configureGlobal(AuthenticationManagerBuilder) method, it sets up an in-memory user store with a single user. That user is given a username of "user", a password of "password", and a role of "USER".

3、As you can see, this Thymeleaf template simply presents a form that captures a username and password and posts them to "/login". As configured, Spring Security provides a filter that intercepts that request and authenticates the user. If the user fails to authenticate, the page is redirected to "/login?error" and our page displays the appropriate error message. Upon successfully signing out, our application is sent to "/login?logout" and our page displays the appropriate success message.

4、Last we need to provide the user a way to display the current username and Sign Out. Update the hello.html to say hello to the current user and contain a "Sign Out" form as shown below

5、We display the username by using Spring Security’s integration with HttpServletRequest#getRemoteUser(). The "Sign Out" form submits a POST to "/logout". Upon successfully logging out it will redirect the user to "/login?logout".







