
## Spring Framework Email Server Application using HTML Template

This is the sample Spring Framework project demostrating via a unit test the capability of sending a electronic mail message containing HTML markup that gets created from a Thymeleaf template. 
The following information explains the design and coding found in this Git code repostary.

### Spring Mail Message Handling Process

The spring-bean-implementation diagram depicts the flow of a Spring mail message process of sending mail using a Spring mailing template. A message is created and sent to the transport protocol, which interacts with internet protocols. Then, the message is received by the recipients. The Spring mail framework requires a mail configuration, or SMTP configuration, as the input and message that needs to be sent. The mail API interacts with internet protocols to send messages.

### Installing and Running

Just run the Spring  application.
Type http://localhost:8080 in your browser to open the application.


### Sending test emails

Follow UI links to send simple email, email using template or email with attachment.


### Java Mail Class Diagram Details

The interfaces and classes for Java mail support in the Spring framework are organized as follows:

1. MailSender interface: the top-level interface that provides basic functionality for sending simple email messages.

2. JavaMailSender interface: the subinterface of the above MailSender. It supports MIME messages and is mostly used in conjunction with the MimeMessageHelper class for the creation of a MimeMessage. It’s recommended to use the MimeMessagePreparator mechanism with this interface

3. MineMessagePreparator interface: the callback interface for the preparation of JavaMail MIME messages. The corresponding send methods of JavaMailSender will take care of the actual creation of a MimeMessage instance, and of proper exception conversion.

4. JavaMailSenderImpl class: provides an implementation of the JavaMailSender interface. It supports the MimeMessage and SimpleMailMessage class.

5. SimpleMailMessage class: used to create a simple mail message including the from, to, cc, subject and text fields

6. MimeMessagePreparator interface: provides a callback interface for the preparation of MIME messages and references MimeMessageHelper class.

7. MailMessage interface: a common interface for mail messages, allowing the user to set key values required in assembling a mail message. Implements both SimpleMailMessage and MineMessageHelper to populate a simple message or a MIME message through a common interface.

8. MineMailMessage class: implements the MailMessage interface for a JavaMail MINE messag.

9. MimeMessageHelper class: helper class for the creation of MIME messages. It offers support for images, typical mail attachments and text content in an HTML layout. Supports the population of the passed-in MimeMessage, in particular when working with attachments or special character encodings.

### Spring Mail Server Properties

Mail properties that are needed to specify e.g. the SMTP server may be defined using the JavaMailSenderImpl. Once the dependency is in place, the next step is to specify the mail server properties in the application dot properties file using the spring.mail.* namespace. 

spring.mail.default-encoding is Default MimeMessage encoding. (Default value: UTF-8).
spring.mail.host is SMTP server host.
spring.mail.jndi-name is Session JNDI name. When set, takes precedence over any other mail settings.

spring.mail.username is the login user of the SMTP server.
spring.mail.password is login password of the SMTP server.
spring.mail.port is SMTP server port.
spring.mail.properties is used for additional JavaMail session properties.
spring.mail.protocol is the protocol used by the SMTP server. (Default value: smtp)
spring.mail.test-connection defines a test to determine the mail server is available on startup. (Default value: false)

Note: Some SMTP servers require a TLS connection, so the property spring.mail.properties.mail.smtp.starttls.enable is used to enable a TLS-protected connection.

### Gmail SMTP Bean Properties

Some SMTP servers require a TLS connection, so the property spring.mail.properties.mail.smtp.starttls.enable is used to enable a TLS-protected connection.

We can send an email via Gmail SMTP server. Have a look at the documentation to see the Gmail outgoing mail SMTP server properties.

spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=<login user to smtp server>
spring.mail.password=<login password to smtp server>
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true

Our application.the properties file is already configured to use Gmail SMTP (see the previous section).

Note that the password for your account should not be an ordinary password, but an application password generated for your google account. Follow this link to see the details and to generate your Google App Password.

### Amazon SES SMTP Bean Properties

To send emails using Amazon SES Service, set your application.properties as we do below:

spring.mail.host=email-smtp.us-west-2.amazonaws.com
spring.mail.username=username
spring.mail.password=password
spring.mail.properties.mail.transport.protocol=smtp
spring.mail.properties.mail.smtp.port=25
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
spring.mail.properties.mail.smtp.starttls.required=true

Amazon requires you to verify your credentials before using your username and password.

### Sending Email

Once dependency management and configuration are in place, we can use the JavaMailSender to send an email.

#### Sending Simple Emails

NOTE: Add simplified JavaMail message code to repo.

### Thymeleaf Bean Properties

spring.thymeleaf.cache does enable template caching. (Default value: true)
spring.thymeleaf.check-template-location does check that the templates location exists. (Default value: true)
spring.thymeleaf.content-type is the content-Type value. (Default value: text/html)
spring.thymeleaf.enabled does enable MVC Thymeleaf view resolution. (Default value: true)
spring.thymeleaf.encoding Template encoding. (Default value: UTF-8)
spring.thymeleaf.excluded-view-names is the comma-separated list of view names that should be excluded from resolution.
spring.thymeleaf.mode is the template mode to be applied to templates. See also StandardTemplateModeHandlers.
(Default value: HTML5)
spring.thymeleaf.prefix is the prefix that gets prepended to view names when building a URL. (Default value:
classpath:/templates/)
spring.thymeleaf.suffix is the suffix that gets appended to view names when building a URL. (Default value:
.html)
spring.thymeleaf.template-resolver-order is the order of the template resolver in the chain. By default, the template resolver is first in the chain. Ordering starts at 1 and should only be set if you have defined additional TemplateResolver beans.
spring.thymeleaf.view-names is the comma-separated list of view names that can be resolved.

## Summary

The Spring Framework presents as an easy to use and highly productive framework. The configuration step is almost completely hidden from developers so they can focus on implementing actual use cases rather than common, repeatable setup steps.

