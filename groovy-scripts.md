# Groovy Scripts

The snippets below provide some typical functionality that will help craft useful 
Groovy scripts.

## Loading OSGi Service

```
import com.liferay.portal.template.ServiceLocator;
import my.company.some.service.MyService;
import org.osgi.framework.Bundle;
import org.osgi.framework.FrameworkUtil;
import org.osgi.util.tracker.ServiceTracker;

try
{
		Bundle bundle = FrameworkUtil.getBundle(com.liferay.portal.scripting.groovy.internal.GroovyExecutor.class);
		ServiceTracker<MyService, MyService> myServiceServiceTracker = new ServiceTracker<MyService, MyService>(bundle.getBundleContext(),
			MyService.class, null);
		myServiceServiceTracker.open();
		
		MyService serviceInstance = myServiceServiceTracker.getService();
		
		out.println("Found service.");
		out.println(serviceInstance);

    // Use your service here...
		
		taskRemoteClientTracker.close();
} catch (Exception e) 
{
  out.println("Error: " + e);
}
```

## Sending out a test email message

```
import com.liferay.mail.kernel.service.MailServiceUtil;
import javax.mail.internet.AddressException;
import javax.mail.internet.InternetAddress;
import com.liferay.mail.kernel.model.MailMessage;
import javax.mail.MessagingException;

InternetAddress fromAddress = null;
InternetAddress toAddress = null;

try {
  fromAddress = new InternetAddress("test@company.com");
  toAddress = new InternetAddress("tester@company.com");
  MailMessage mailMessage = new MailMessage();
  mailMessage.setTo(toAddress);
  mailMessage.setFrom(fromAddress);
  mailMessage.setSubject("Testing SMTP");
  mailMessage.setBody("This is a test email");
  MailServiceUtil.sendEmail(mailMessage);
  out.println("Sent email");
} catch (MessagingException e) {
  out.println(e);
}
```
