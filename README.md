
## Spring Framework Email Server Application using HTML Template

This is the sample Spring Framework project demostrating via a unit test the capability of sending a electronic mail message containing HTML markup that gets created from a Thymeleaf template. 
The following information explains the design and coding found in this Git code repostary.

### Installing and Running

Just run the Spring  application.
Type http://localhost:8080 in your browser to open the application.


### Sending test emails

Follow UI links to send simple email, email using template or email with attachment.


### Java Mail Class Diagram Details

The interfaces and classes for Java mail support in the Spring framework are organized as follows:

1. MailSender interface: the top-level interface that provides basic functionality for sending simple emails

2. JavaMailSender interface: the subinterface of the above MailSender. It supports MIME messages and is mostly used in conjunction with the MimeMessageHelper class for the creation of a MimeMessage. It’s recommended to use the MimeMessagePreparator mechanism with this interface

3. MineMessagePreparator interface: the callback interface for the preparation of JavaMail MIME messages.
The corresponding send methods of JavaMailSender will take care of the actual creation of a MimeMessage instance, and of proper exception conversion.

4. JavaMailSenderImpl class: provides an implementation of the JavaMailSender interface. It supports the MimeMessage and SimpleMailMessage

5. SimpleMailMessage class: used to create a simple mail message including the from, to, cc, subject and text fields

6. MimeMessagePreparator interface: provides a callback interface for the preparation of MIME messages

7. MailMessage interface: a common interface for mail messages, allowing the user to set key values required in assembling a mail message. Implements both SimpleMailMessage and MineMessageHelper to populate a simple message or a MIME message through a common interface.

8. MineMailMessage class: implements the MailMessage interface for a JavaMail MINE messag.

9. MimeMessageHelper class: helper class for the creation of MIME messages. It offers support for images, typical mail attachments and text content in an HTML layout. Supports the population of the passed-in MimeMessage, in particular when working with attachments or special character encodings.

### Spring Mail Server Properties

Mail properties that are needed to specify e.g. the SMTP server may be defined using the JavaMailSenderImpl.

### Spring Boot Mail Server Properties

Once the dependency is in place, the next step is to specify the mail server properties in the application.properties file using the spring.mail.* namespace. Some SMTP servers require a TLS connection, so the property spring.mail.properties.mail.smtp.starttls.enable is used to enable a TLS-protected connection.

### Gmail SMTP Properties

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

### Amazon SES SMTP Properties

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

## Summary

The Spring Framework presents as an easy to use and highly productive framework. The configuration step is almost completely hidden from developers so they can focus on implementing actual use cases rather than common, repeatable setup steps.

