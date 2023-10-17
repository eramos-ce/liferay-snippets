# Blade CLI

Common blade CLI commands.

## Code generation

1. Create a new Liferay workspace
    ```
    blade init --liferay-product dxp --liferay-version dxp-7.4-u86 .
    ```

2. Create a new Liferay mvc portlet
    ```
    blade create -t mvc-portlet -p com.linelio.liferay.portlets -c GuestbookPortlet guestbook-web
    ```

3. List available samples from Liferay.
    ```
    blade samples
    ```

4. Create a working sample module from Liferay samples.
    ```
    blade sample -v 7.3 auto-login
    ```
    
5. Create a module from blade templates
    - Create a service module that implements a specific API. 
        ```
        blade create -t service -s com.liferay.portal.kernel.security.auto.login.AutoLogin -p com.linelio.liferay.autologin -c MyAutoLogin autologin
        ```
