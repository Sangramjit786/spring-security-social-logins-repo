# Spring Security - Social Logins (GitHub & Facebook)

This repository demonstrates how to integrate **Spring Security** with **social logins** using **GitHub** and **Facebook**.  
It includes multiple approaches to achieve OAuth 2.0-based authentication, enabling users to log in to your application via their existing social accounts.

🔗 **GitHub Repository:** [spring-security-social-logins-repo](https://github.com/Sangramjit786/spring-security-social-logins-repo.git)

---

## 📌 Features Implemented

### 1. **Spring Security Social Logins**
- Configured **Spring Security OAuth 2.0 Login** to allow authentication via third-party providers.
- Provides seamless login without requiring a separate username/password for the application.

---

### 2. **Implementation - GitHub & Facebook Login**
- **First Approach**:
  - Configured **application.yml** with GitHub and Facebook OAuth 2.0 client details.
  - Used Spring Boot’s **`spring-boot-starter-oauth2-client`** dependency.
  - Users can:
    1. Click "Login with GitHub" or "Login with Facebook"
    2. Authenticate with the provider
    3. Get redirected back to the application with a valid OAuth 2.0 access token.
  - Mapped OAuth user details (name, email, profile picture) to the application’s user object.

---

### 3. **Alternative Implementation**
- Demonstrates **another way** to implement social login:
  - Uses a **custom `OAuth2UserService`** to fetch additional details from GitHub/Facebook APIs after login.
  - Allows storing authenticated users in a **database** for future sessions.
  - Provides flexibility to customize authentication flow and integrate with existing security mechanisms.

---

## 🚀 Getting Started

### **Prerequisites**
- Java 21
- Maven 3.5+
- GitHub and Facebook developer accounts with registered OAuth apps.

---

### **Clone the Repository**
```bash
git clone https://github.com/Sangramjit786/spring-security-social-logins-repo.git
cd spring-security-social-logins-repo


Configure OAuth Credentials

Update application.properties with your GitHub and Facebook client credentials:
spring.application.name=springsecOAUTH2
spring.security.user.name=${SECURITY_USERNAME:eazybytes}
spring.security.user.password=${SECURITY_PASSWORD:12345}
logging.level.org.springframework.security=${SPRING_SECURITY_LOG_LEVEL:TRACE}
logging.pattern.console = ${LOGPATTERN_CONSOLE:%green(%d{HH:mm:ss.SSS}) %blue(%-5level) %red([%thread]) %yellow(%logger{15}) - %msg%n}

spring.security.oauth2.client.registration.github.client-id=${GITHUB_CLIENT_ID:Ov23livqvBjkcWjrj057}
spring.security.oauth2.client.registration.github.client-secret=${GITHUB_CLIENT_SECRET:58aab52ac4295b7ae3aa90591f82676a4ba32f9d}

spring.security.oauth2.client.registration.facebook.client-id=${FACEBOOK_CLIENT_ID:1990171295059355}
spring.security.oauth2.client.registration.facebook.client-secret=${FACEBOOK_CLIENT_SECRET:61b3f88efe9f1a058ce75b1d9c0495f4}


Run the Application:
mvn spring-boot:run


Access the application at:
http://localhost:8080

📚 How It Works
User selects GitHub or Facebook login.
Spring Security redirects to the provider’s authorization endpoint.
Provider authenticates the user and redirects back with an authorization code.
Spring Security exchanges the code for an access token.

User details are fetched and stored in the application’s context.

🔑 Key Endpoints
Endpoint	Description
/login	Login page with social options
/logout	Logout the authenticated user
/	Home page after successful login
