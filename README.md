# Okta Java Micronaut Example


## Prerequisites

Before running this sample, you will need the following:

* An Okta Developer Account, you can sign up for one at https://developer.okta.com/signup/.
* An Okta Application, configured for Web mode. This is done from the Okta Developer Console and you can find instructions [here](https://developer.okta.com/docs/guides/implement-auth-code/overview/#1-setting-up-your-application).
* In the above application, configure `http://localhost:8080/oauth/callback/okta` as `Login redirect URI` and
  configure `http://localhost:8080/logout` as `Logout redirect URI`. 
* The source code from this repository:
  
  ```bash
  git clone https://github.com/okta/samples-java-micronaut.git
  cd samples-java-micronaut
  ```

## Running This Example

There is a `pom.xml` at the root of this project, that helps build the project.

You also need to gather the following information from the Okta Developer Console:

- **Client ID** and **Client Secret** - These can be found on the "General" tab of the Web application that you created earlier in the Okta Developer Console.

- **Issuer** - This is the URL of the authorization server that will perform authentication.  All Developer Accounts have a "default" authorization server.  The issuer is a combination of your Org URL (found in the upper right of the console home page) and `/oauth2/default`. For example, `https://dev-1234.oktapreview.com/oauth2/default`.

Plug these values into the `mvn` commands used to start the application.

```bash
export OKTA_OAUTH2_ISSUER=https://{yourOktaDomain}/oauth2/default # e.g. https://dev-1234.oktapreview.com/oauth2/default
export OKTA_OAUTH2_CLIENTID={clientId}
export OKTA_OAUTH2_CLIENTSECRET={clientSecret}

mvn clean mn:run
```

(or)

```bash
mvn -DOKTA_OAUTH2_ISSUER=https://{yourOktaDomain}/oauth2/default \
    -DOKTA_OAUTH2_CLIENTID={clientId} \
    -DOKTA_OAUTH2_CLIENTSECRET={clientSecret} clean mn:run
```

> **NOTE:** Putting secrets on the command line should ONLY be done for examples, do NOT do this in production. Instead, update the project's `application.yml`.

Now, navigate to `http://localhost:8080` in your browser.

If you see a home page that prompts you to login, then things are working! Clicking the **Login** button will redirect you to the Okta hosted sign-in page.

You can login with the same account that you created when signing up for your Developer Org, or you can use a known username and password from your Okta Directory.
