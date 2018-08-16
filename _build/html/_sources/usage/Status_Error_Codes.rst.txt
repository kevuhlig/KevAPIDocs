========================
Status and Error Codes
========================

The Status and Error codes should be on their own standalone page. A standalone code allows you to expand on each code wiht more detail without crowding the other documentation. 

Standard status codes don’t usually need much documentation, but custom status and error codes specific to your API definitely do. Error codes in particular help with troubleshooting bad requests. When documenting the codes, provide descriptions that provide more information, potentially assisting with error recovery. 

With a ``GET`` request, it’s pretty easy to tell if the request is successful because you get back the expected response. But suppose you’re making a ``POST``, ``PUT``, or ``DELETE`` call, where you’re changing data contained in the resource. How do you know if the request was successfully processed and received by the API? HTTP response codes in the header of the response will indicate whether the operation was successful. Status codes appear in the response header, which you might not see by default. In curl, to get the response header, add the ``-i``. 

.. code-block:: python

  curl -I -X GET "http://api.openweathermap.org/data/2.5/weather?zip=95050%2Cus&appid=fd4698c940c6d1da602a70ac34f0b147&units=imperial"


The response header looks as follows:

.. code:: python

 HTTP/1.1 200 OK
 Server: openresty
 Date: Mon, 02 Apr 2018 01:14:13 GMT
 Content-Type: application/json; charset=utf-8
 Content-Length: 441
 Connection: keep-alive
 X-Cache-Key: /data/2.5/weather?units=imperial&zip=95050%2cus
 Access-Control-Allow-Origin: *
 Access-Control-Allow-Credentials: true
 Access-Control-Allow-Methods: GET, POST


Put the codes into a table. 

.. list-table:: **Status and Error Codes**
   :widths: 10 10 50 10
   :header-rows: 1

   * - Code
     - Title
     - Description
     - Extra
   * - 200
     - OK
     - The request was successful.
     - fdsa
   * - 201
     - Created
     - The resource was successfully created. 
     - fdfasf
   * - 202
     - Async created
     - The resource was asynchronously created. 
     - fff
   * - 400
     - Bad request
     - Bad request
     - fdsa
   * - 401
     - Unauthorized
     - Your API key is invalid
     - uuu
   * - 402
     - Over quota
     - Over plan quota on this endpoint.
     - 22
   * - 404 
     - Not found
     - The resource does not exist.
     - oo
   * - 422
     - Validation error
     - A validation error occurred.
     - 899
   * - 50x
     - Internal Server Error
     - An error occurred with our API.
     - 334


---------
Examples
---------

Clearbit - <https://clearbit.com/docs?python#errors>

Twitter - <https://developer.twitter.com/en/docs/basics/response-codes>

MailChimp - <http://developer.mailchimp.com/documentation/mailchimp/guides/error-glossary/>