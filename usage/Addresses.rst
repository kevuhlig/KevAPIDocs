=============
Addresses
=============

-------------------
The Address Object
-------------------

.. raw:: html

   <!DOCTYPE html>
   <html>
   <head>
   <style>
   table {
      font-family: arial, sans-serif;
      border-collapse: collapse;
      font-size: 14px;
      width: 100%;
   }

   td, th {
     border: 1px solid #dddddd;
     text-align: left;
     padding: 8px;
   }

   tr:nth-child(even) {
     background-color: #f2f2f2;
   }

   .codetext {
     color: red;
   }

  </style>
  </head>
  <body>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Data Type</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>is_complete</td>
      <td>boolean</td>
      <td>Complete addresses contain all required values. Incomplete addresses have failed one or multiple validations. Incomplete Addresses are eligible for requesting rates but lack at least one required value for purchasing labels.</td>
    </tr>
    <tr>
      <td>object_created</td>
      <td>datetime</td>
      <td>Date and time of Address creation.</td>
    </tr>
    <tr>
      <td>object_updated</td>
      <td>datetime</td>
      <td>Date and time of last Address update. Since you cannot update Addresses after they were created, this time stamp reflects the time when the Address was changed by Shippo's systems for the last time, e.g., during the approximation of one or more values.</td>
    </tr>
    <tr>
      <td>object_id</td>
      <td>string</td>
      <td>Unique identifier of the given Address object. This ID is required to create a Shipment object.</td>
    </tr>
    <tr>
      <td>object owner</td>
      <td>string</td>
      <td>Username of the user who created the Address object.</td>
    </tr>
    <tr>
      <td>name</td>
      <td>string</td>
      <td>First and Last Nameo of the addressee</td>
    </tr>
     <tr>
      <td>company</td>
      <td>string</td>
      <td>Company Name</td>
    </tr>
    </tr>
    <tr>
      <td>street1</td>
      <td>string</td>
      <td>First street line, 35 character limit. Usually street number and street name (except for DHL Germany, see street_no).</td>
    </tr>
    <tr>
      <td>street_no</td>
      <td>string</td>
      <td>Street number of the addressed building. This field can be included in street1 for all carriers except for DHL Germany.</td>
    </tr>
    <tr>
      <td>street2</td>
      <td>string</td>
      <td>Second street line, 35 character limit.</td>
    </tr>
    <tr>
      <td>street3</td>
      <td>string</td>
      <td>Third street line, 35 character limit. Only accepted for USPS international shipments, UPS domestic and UPS international shipments.</td>
    </tr>
    <tr>
      <td>city</td>
      <td>string</td>
      <td>Name of a city. When creating a Quote Address, sending a city is optional but will yield more accurate Rates. Please bear in mind that city names may be ambiguous (there are 34 Springfields in the US). Pass in a state or a ZIP code (see below), if known, it will yield more accurate results.</td>
    </tr>
    <tr>
      <td>zip</td>
      <td>string</td>
      <td>Postal code of an Address. When creating a Quote Addresses, sending a ZIP is optional but will yield more accurate Rates.</td>
    </tr>
    <tr>
      <td>state</td>
      <td>string</td>
      <td>State values are only required for shipments from the United States and Canada (most carriers only accept two-character state abbreviations). However, to receive more accurate quotes, passing it is generally recommended.</td>
    </tr>
    <tr>
      <td>country</td>
      <td>ISO 2 country code</td>
      <td>Example: 'US' or 'DE'. All accepted values can be found on the <a href="https://www.iso.org/home.html" target="_blank">Official ISO Website</a>. Sending a country is always required.</td>
    </tr>
    <tr>
      <td>phone</td>
      <td>string</td>
      <td>Addresses containing a phone number allow carriers to call the recipient when delivering the Parcel. This increases the probability of delivery and helps to avoid accessorial charges after a Parcel has been shipped.</td>
    </tr>
    <tr>
      <td>email</td>
      <td>email</td>
      <td>E-mail address of the contact person, RFC3696/5321-compliant.</td>
    </tr>
    <tr>
      <td>is_residential</td>
      <td>nullable boolean</td>
      <td>Indicates whether the address provided is a residential address or not.</td>
    </tr>
    <tr>
      <td>validate</td>
      <td>nullable boolean</td>
      <td>Set to true to validate Address object.</td>
    </tr>
    <tr>
      <td>metadata</td>
      <td>string</td>
      <td>A string of up to 100 characters that can be filled with any additional information you want to attach to the object.</td>
    </tr>
   <tr>
      <td>test</td>
      <td>bool</td>
      <td>Indicates whether the object has been created in test mode.</td>
    </tr>
   <tr>
      <td>validation_results</td>
      <td>object</td>
      <td>object that contains information regarding if an address had been validated or not. Also contains any messages generated during validation. Children keys are <span class="codetext">is_valid</span> (boolean) and <span class="codetext">messages</span> (array).</td>
    </tr>

  </table>

  </body>
  </html>

|

-----------------------------
``POST`` Create a New Address
-----------------------------

A ``POST`` to the ``/addresses`` resource to allow your application to create a new address object. Hello. Hello


.. raw:: html 

   <p><span style="color:blue;font-size:18px">/addresses/</span></p>


**BODY PARAMETERS**

.. list-table:: 
   :widths: 15 10 20 30
   :header-rows: 1

   * - Parameter
     - Required/Optional
     - Data Type
     - Description
   * - **name**
     - optional
     - string
     - name of purchaser
   * - **company**
     - optional
     - string
     - name of company
   * - **street1**
     - required
     - string
     - street name
   * - **street_no**
     - optional
     - string
     - building number
   * - **street2**
     - optional
     - string
     - street name (secondary)
   * - **city**
     - required
     - string
     - name of the city
   * - **zip**
     - required
     - string
     - zip (USA) or postal (Canada) code
   * - **state**
     - required
     - string
     - name of state (USA) or province (Canada)
   * - **country**
     - required
     - ISO 2 country code
     - name of country
   * - **phone**
     - optional
     - string
     - phone number
   * - **email**
     - optional
     - email
     - email address contact
   * - **is_residential**
     - optional
     - boolean
     - is residential?
   * - **validate**
     - optional
     - boolean
     - for potential validation
   * - **metadata**
     - optional
     - string
     - any metadata to pass along

|

**EXAMPLE REQUEST (Create a New Address)**:

.. literalinclude:: PostAddress.txt


**EXAMPLE RESPONSE (from Create a New Address)**:

.. literalinclude:: PostAddressresponse.json 


---------------------------
``GET`` Retrieve an Address
---------------------------

A ``GET`` to the ``/addresses`` resource to allow your application to retrieve an existing address by object ID.

.. raw:: html 

   <p><span style="color:blue;font-size:18px">/addresses/{address object id}</span></p>



**PATH PARAMETERS**

.. list-table:: 
   :widths: 15 10 20 30
   :header-rows: 1

   * - Parameter
     - Required/Optional
     - Data Type
     - Description
   * - **Address Object ID**
     - required
     - string
     - address object id

**EXAMPLE REQUEST (Retrieve an Address)**

.. code-block:: bash

  curl https://api.goshippo.com/addresses/d799c2679e644279b59fe661ac8fa488/ \
    -H "Authorization: ShippoToken <API_TOKEN>"


**EXAMPLE RESPONSE (from Retrieve an Address)**:

.. literalinclude:: RetrieveAddressResponse.json 

---------------------------
``GET`` Validate an Address
---------------------------

A ``GET`` to the ``/address`` resource to allow your application to validate an address object. 

.. raw:: html 

   <p><span style="color:blue;font-size:18px">/addresses/{address object id}/validate/</span></p>

**PATH PARAMETERS**

.. list-table:: 
   :widths: 15 10 20 30
   :header-rows: 1

   * - Parameter
     - Required/Optional
     - Data Type
     - Description
   * - **Address Object ID**
     - required
     - string
     - address object id

**EXAMPLE REQUEST (Validate an Address)**

.. code-block:: bash

  curl https://api.goshippo.com/addresses/d799c2679e644279b59fe661ac8fa488/validate/ \
    -H "Authorization: ShippoToken <API_TOKEN>"

**EXAMPLE RESPONSE (from Validate an Address)**

.. literalinclude:: ValidateAddressResponse.json


--------------------------
``GET`` List All Addresses
--------------------------

A ``GET`` to the ``/address`` resource to allow your application to list all addresses. 

.. raw:: html 

   <p><span style="color:blue;font-size:18px">/addresses/</p>

**EXAMPLE REQUEST (List All Addresses)**

.. code-block:: bash

  curl https://api.goshippo.com/addresses/ \
    -H "Authorization: ShippoToken <API_TOKEN>"

**EXAMPLE RESPONSE (from List All Addresses)**

.. literalinclude:: ListAddressResponse.json