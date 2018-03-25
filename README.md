[![Build Status](https://semaphoreapp.com/api/v1/projects/d4cca506-99be-44d2-b19e-176f36ec8cf1/128505/shields_badge.svg)](https://semaphoreapp.com/boennemann/badges)
[![](https://images.microbadger.com/badges/version/anir37/anirban-mule.svg)](https://microbadger.com/images/anir37/anirban-mule "Get your own version badge on microbadger.com")
# Anirban-Custom-Oauth-Policy
It contains the Custom Oauth policy works extremely well with Mule external Oauth provider or with any Mule custom Oauth provider

![94a0a117494a8e9f1332f1b6e54f61d8](https://user-images.githubusercontent.com/1582548/30781889-3b15342e-a145-11e7-99a6-f574388789e4.jpeg)

## Steps of installation

* If we click the custom policies link of API Manager, we will able to upload the policies:

![1](https://user-images.githubusercontent.com/1582548/37570420-8e6e71a8-2b15-11e8-8864-acb2b4f76bb7.png)

* Once the Add Custom Policy dialogue box appears, we will be able to upload the XML and the YAML files to install the Custom Policy on our platform:

![21](https://user-images.githubusercontent.com/1582548/37570528-dcf75ce4-2b16-11e8-826b-e6a3fb6932de.png)

* After we upload both the files, we can see the custom policy is installed and is ready to use!:

![22](https://user-images.githubusercontent.com/1582548/37570521-bff7d83a-2b16-11e8-870d-1e3c9cec2a8a.png)


## Configuring the policy with an existing API:

Once the policy is installed and ready, we can configure it and protect any number of APIs with OAuth system. When we select an API to apply the policy, we can see the Custom policy is visible on the list to select:

![5](https://user-images.githubusercontent.com/1582548/37570543-1e8c3d5a-2b17-11e8-8880-016e03275498.png)

Once applied, the policy will be ready to be configured as per our need:

![dd](https://user-images.githubusercontent.com/1582548/37570556-5213a76c-2b17-11e8-8bd9-0c8355642726.png)

The first field is the validation URL, which is a mandatory field, where we need to put the validation URL of our Mule external OAuth provider.

The second field is the list of Client ID separated by spaces, which we want to allow to access the API. This is an optional field and if nothing is mentioned or left blank, then it will allow all the Client ID registered with the API to access it. This is an optional but yet powerful additional layer of security where we can allow any particular or a list of Clients to access the API even though they have registered for API access in that group.

**An important point to note:**
To execute this **custom policy** with Mule's external OAuth provider flawlessly, the validation flow component of the provider, on the other hand, should be configured to throw the exception as follows:

`<oauth2-provider:validate throwExceptionOnUnaccepted="true"/>`

The Client ID, Scope, and Username will be available to the backend API application as an inbound property as **client_id**, **username**, and **scope** respectively
