# Java Snippets

This article contains some common Java code blocks useful for writting modules for 
Liferay

## Wait for the Portal to be completely initialized

At times, we must ensure all Liferay portal components are properly initialized before out 
Components should attempt to execute due to runtime dependencies.  This snippet allows your 
Component to not be activated until your OSGi dependencies are met and the Portal is 
done initializing.

```
@Component
public class MyXyz implements XyzApi {

    // Plain old OSGi service
    @Reference
    private SomeOsgiService _someOsgiService;

    // Liferay lifecycle service
    @Reference(target = ModuleServiceLifecycle.PORTAL_INITIALIZED)
    private ModuleServiceLifecycle _portalInitialized;

    @Activate
    public void doSomething() {
        // `@Activate` method is only executed once all of
        // `_someOsgiService` and
        // `_portalInitialized`
        // are set.
    }
}
```

### References

* https://help.liferay.com/hc/en-us/articles/360018168631-Waiting-on-Lifecycle-Events
