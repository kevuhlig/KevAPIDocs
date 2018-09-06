================
Getting Started
================

The Getting Started topic is somewhat like the typical Hello World tutorial in developer documentation, but with an API. The tutorial holds a user’s hand from start to finish in producing the simplest possible output with the system. For Hello World tutorials, the simplest output might just be a message that says “Hello World.” For an API, it might be a successful response from the most basic request.

How long would it take a developer to get the simplest possible response using the API? The developer needs to get a sense of how it works, and feel productive.

As an example, you could take a common, basic use case for your API and show how to construct a request, as well as what response returns. If a developer can make that call successfully, he or she can probably be successful with the other calls too.


.. contents:: 
   :local:
   :depth: 3
   :backlinks: top


---------------------------------
Signing up for an account (Maybe)
---------------------------------

---------------------------------------------------
Prerequisite Information / Before you Start (Maybe)
---------------------------------------------------

---------------------------------
Get familiar with the App (Maybe)
---------------------------------

If you're not familiar with the App, get familiar with it and experiment with the user interface before starting to code. 


--------------------------------
Authentication and Authorization
--------------------------------

*	Authentication – proves correct identity.
*	Authorization – allows a certain action.


In API documentation, you don’t need to explain how your authentication works in detail to outside users. In fact, not explaining the internal details of your authentication process is probably a best practice as it would make it harder for hackers to abuse the API. However, you do need to explain some basic information such as:

*	How to get API keys
*	How to authenticate requests
*	Error messages related to invalid authentication
*	Rate limits with API requests
*	Potential costs surrounding API request usage
*	Token expiration times


KevAPI uses `OAuth`__ to provide authorized access to its API. 

.. __: https://oauth.net/ 

One popular method for authenticating and authorizing users is OAuth 2.0. This approach relies on an authentication server to communicate with the API server in order to grant access. It works as follows:

1. The KevAPI generates a set of OAuth client ID and secret credentials for you app for both the sandbox and live environments.

2. You pass these credentials in the ``Authorization`` header in a ``get access token`` request.

3. When the KevAPI receives the credentials, the KevAPI issues access tokens called a *bearer token*. The ``access_token`` field in the response contains the bearer token, as per below. 

.. code:: python
 
  {
   "scope": "scope",
   "nonce": "nonce",
   "access_token": "Access-Token",
   "token_type": "Bearer",
   "app_id": "APP-80W284485P519543T",
   "expires_in": 32398
  }

4. Use the bearer token in the ``Authorization`` header when making a standard REST API request, as per below:

.. code:: python

 curl -v -X GET https://api.sandbox.paypal.com/v1/invoicing/invoices?page=3&page_size=4&total_count_required=true \
  -H "Content-Type:application/json" \
  -H "Authorization: Bearer Access-Token"

---------------------------------
What's Included in an API Request
---------------------------------

Add a section that gives perspective of what must be included in an API request. This will be the following: 


* The HTTP Method:

 * GET - Requests data from a resource
 * POST - Submits data to a resource
 * PUT - Updates a resource
 * PATCH - Partially updates a resource
 * DELETE - Deletes a resource

* The URL to the API Service. Example: https://api.paypal.com
* The Endpoint.
* Query Parameters.
* HTTP Request Headers - includes the ``Authorization`` header, and the ``Accept`` header, which specifies the response format (e.g., ``application/json``. The ``Content-Type`` is required for operations with a request body being submitted (e.g., ``application/json``).
* If the Method is a POST, PUT, or PATCH, then the Request Body parameters. 

Then show a sample request code (in curl):

.. code:: python

 curl -v -X POST https://api.sandbox.paypal.com/v1/payments/billing-agreements/I-1TJ3GAGG82Y9/cancel \
  -H "Content-Type:application/json" \
  -H "Authorization: Bearer Access-Token" \
  -d '{
    "note": "Canceling the profile."
    }'

---------------
Example Request
---------------

Show example request code in curl (Kevin: You can generate this from Postman)

.. code:: bash

 curl -X GET \
  'http://api.openweathermap.org/data/2.5/weather?id=6087824&units=metric&appid=5f41365262b067e009b2115887c09706' \
  

-----------------------------
Try out Request with Postman
-----------------------------

Integrate some endpoints in Postman and then create the **Run in Postman** button. This provides interactivity to try it out. 

Put in a `Run in Postman`__ button. 


.. __: http://idratherbewriting.com/learnapidoc/docapis_doc_getting_started_section.html


----------
Responses
----------

Show example of response. `Aeris`_ has good example.

.. _Aeris: https://www.aerisweather.com/support/docs/api/getting-started/responses/

Most successful responses from any endpoint action of the Aeris Weather API will be in the following form, where the ``response`` object will be an array of results as objects:


.. code-block:: Javascript

 {
    "success": true,
    "error": null,
    "response": {
        "id": "KBFI",
        "loc": {
            "long": -122.31666666667,
            "lat": 47.55
        },
        "place": {
            "name": "seattle/boeing",
            "state": "wa",
            "country": "us"
        },
        "obTimestamp": 1326552780,
        "obDateTime": "2012-01-14T06:53:00-08:00",
        "ob": {
            "tempC": 3,
            ....
        },
        "raw": "KBFI 141453Z 14010KT 8SM -RA OVC018 03/01 A2995",
        "relativeTo": {
            "lat": 47.60621,
            ...
        }
    }
 }


-----------
Rate Limits
-----------

Rate limits determine how frequently you can call a particular endpoint. Usually companies have different tiers (for example, free versus pro) and licenses (open-source, business, commercial) corresponding to different capabilities or rate limits with the API. Companies with APIs make money by charging for access to the API, but they usually distinguish between low usage and high usage, often making the low usage options free so that developers can explore and experiment with the API.

Pricing details related to rate limiting is probably information that's within the marketing domain rather than the documentaiton domain. However, developers will still want to knwo a few key behaviours around the rate limiting thresholds. 

* When you exceed the threshold, do your calls get throttled with slower responses?
* Do you get overcharges for every extra call?
* Do the responses simply return a particular status code (if so, which one)?

Also, when developers implement the code into their applications or web pages, how are they implementing code for responses that don’t provide data (due to the threshold being exceeded)? Are there conditions and checks to handle these scenarios? Does the widget (or whatever might be implementing the API) simply freeze or hang, display empty or crash?

**Examples**

GitHub - <https://developer.github.com/v3/#rate-limiting>

Linkedin - <https://developer.linkedin.com/docs/guide/v2/concepts/rate-limits>


---------------------------
Examples of Getting Started
---------------------------

`Adsense`_

`PayPal`_

`Twitter`_

.. _Adsense: https://developers.google.com/adsense/management/getting_started

.. _PayPal: https://developer.paypal.com/docs/api/overview 

.. _Twitter: https://developer.twitter.com/en/docs/basics/getting-started



