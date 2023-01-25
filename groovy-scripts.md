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
