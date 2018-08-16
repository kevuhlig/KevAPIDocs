=============
Shipments
=============

The heart of the Shippo API, a shipment is made up of "to" and "from" addresses and the parcel to be shipped. Once created, a shipment object can be used to retrieve shipping rates and purchase a shipping label. 

--------------------
The Shipments Object
--------------------

.. raw:: html

  <!DOCTYPE html>
  <html>
  <head>
  <style>
  table {
      font-family: arial, sans-serif;
      border-collapse: collapse;
      font-size: 14px;
      width: 86%;
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
      <td>status</td>
      <td>"WAITING", "QUEUED", "SUCCESS", "ERROR"</td>
      <td>"Waiting" shipments have been successfully submitted but not yet been processed. "Queued" shipments are currently being processed. "Success" shipments have been processed successfully, meaning that rate generation has concluded. "Error" does not occur currently and is reserved for future use.</td>
    </tr>
    <tr>
      <td>object_created</td>
      <td>datetime</td>
      <td>Date and time of Shipment creation.</td>
    </tr>
    <tr>
      <td>object_updated</td>
      <td>datetime</td>
      <td>Date and time of last Shipment update.</td>
    </tr>
    <tr>
      <td>object_id</td>
      <td>string</td>
      <td>Unique identifier of the given Shipment object.</td>
    </tr>
    <tr>
      <td>object owner</td>
      <td>string</td>
      <td>Username of the user who created the Shipment object.</td>
    </tr>
    <tr>
      <td>address_from</td>
      <td>string</td>
      <td>ID of the Address object that should be used as sender Address.</td>
    </tr>
     <tr>
      <td>address_to</td>
      <td>string</td>
      <td>ID of the Address object that should be used as recipient Address.</td>
    </tr>
    <tr>
      <td>parcels</td>
      <td>array</td>
      <td>Array of IDs of the Parcel objects to be shipped.</td>
    </tr>
    <tr>
      <td>shipment_date</td>
      <td>datetime (ISO 8601 date)</td>
      <td>Date the shipment will be tendered to the carrier. Must be in the format "2014-01-18T00:35:03.463Z". Defaults to current date and time if no value is provided. Please note that some carriers require this value to be in the future, on a working day, or similar.</td>
    </tr>
    <tr>
      <td>address_return</td>
      <td>string</td>
      <td>ID of the Address object where the shipment will be sent back to if it is not delivered (Only available for UPS, USPS, and Fedex shipments). If this field is not set, your shipments will be returned to the address_form. </td>
    </tr>
    <tr>
      <td>customs_declaration</td>
      <td>string</td>
      <td>ID of the Customs Declarations object for an international shipment.</td>
    </tr>
    <tr>
      <td>carrier_accounts</td>
      <td>array</td>
      <td>An array of object_ids of the carrier account objects to be used for getting shipping rates for this shipment. If no carrier account object_ids are set in this field, Shippo will attempt to generate rates using all the carrier accounts that have the 'active' field set.</td>
    </tr>
    <tr>
      <td>metadata</td>
      <td>string</td>
      <td>A string of up to 100 characters that can be filled with any additional information you want to attach to the object.</td>
    </tr>
    <tr>
      <td>extra</td>
      <td>object</td>
      <td>An object holding optional extra services to be requested for each parcel in a multi-piece shipment. See the <a href="#ShipmentExtrabookmark">Shipment Extra table</a> below for all available services.</td>
    </tr>
    <tr>
      <td>rates</td>
      <td>array</td>
      <td>An array with all available rates. If <span class="codetext">async</span> has been set to <span class="codetext">false</span> in the request, this will be populated with all available rates in the response. Otherwise rates will be created asynchronously and this array will initially be empty.</td>
    </tr>
    <tr>
      <td>messages</td>
      <td>array</td>
      <td>An array containing elements of the following schema: "code" (string): an identifier for the corresponding message (not always available") "message" (string): a publishable message containing further information.</td>
    </tr>
    <tr>
      <td>test</td>
      <td>bool</td>
      <td>Indicates whether the object has been created in test mode</td>
    </tr>

  </table>

  </body>
  </html>

|

.. raw:: html

  <p id="ShipmentExtrabookmark"></p>

----------------
Shipment Extras
----------------

The following values are support for the ``extra`` field of the shipment object. 

.. raw:: html

  <!DOCTYPE html>
  <html>
  <head>
  <style>
  table {
      font-family: arial, sans-serif;
      border-collapse: collapse;
      font-size: 14px;
      width: 86%;
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
      <td>status</td>
      <td>"WAITING", "QUEUED", "SUCCESS", "ERROR"</td>
      <td>"Waiting" shipments have been successfully submitted but not yet been processed. "Queued" shipments are currently being processed. "Success" shipments have been processed successfully, meaning that rate generation has concluded. "Error" does not occur currently and is reserved for future use.</td>
    </tr>
    <tr>
      <td>object_created</td>
      <td>datetime</td>
      <td>Date and time of Shipment creation.</td>
    </tr>
    <tr>
      <td>object_updated</td>
      <td>datetime</td>
      <td>Date and time of last Shipment update.</td>
    </tr>
    <tr>
      <td>object_id</td>
      <td>string</td>
      <td>Username of the user who created the Shipment object.</td>
    </tr>
    <tr>
      <td>address_from</td>
      <td>string</td>
      <td>ID of the Address object that should be used as recipient Address.</td>
    </tr>
    <tr>
      <td>parcels</td>
      <td>array</td>
      <td>Array of IDs of the Parcel objects to be shipped.</td>
    </tr>
     <tr>
      <td>shipment_date</td>
      <td>datetime (ISO 8601 date)</td>
      <td>Date the shipment will be tendered to the carrier. Must be in the format "2014-01-18T00:35:03.463Z". Defaults to current date and time if no value is provided. Please note that some carriers require this value to be in the future, on a working day, or similar.</td>
    </tr>
    <tr>
      <td>address_return</td>
      <td>string</td>
      <td>ID of the Address object where the shipment will be sent back to if it is not delivered (Only available for UPS, USPS, and Fedex shipments). If this field is not set, your shipments will be returned to the address_form. </td>
    </tr>
    <tr>
      <td>customs_declaration</td>
      <td>string</td>
      <td>ID of the Customs Declarations object for an international shipment.</td>
    </tr>
    <tr>
      <td>metadata</td>
      <td>string</td>
      <td>A string of up to 100 characters that can be filled with any additional information you want to attach to the object.</td>
    </tr>
    <tr>
      <td>extra</td>
      <td>object</td>
      <td>An object holding optional extra services to be requested. See the Shipment Extra table below for all available services.</td>
    </tr>
    <tr>
      <td>rates</td>
      <td>array</td>
      <td>An array with all available rates. If <span class="codetext">async</span> has been set to <span class="codetext">false</span> in the request, this will be populated with all available rates in the response. Otherwise rates will be created asynchronously and this array will initially be empty.</td>
    </tr>
    <tr>
      <td>metadata</td>
      <td>string</td>
      <td>A string of up to 100 characters that can be filled with any additional information you want to attach to the object.</td>
    </tr>

  </table>


  </body>
  </html>

|

------------------------------
``POST`` Create a New Shipment
------------------------------

A ``POST`` to the ``/shipment`` resource to allow your application to create a new parcel object.


.. raw:: html 

   <p><span style="color:blue;font-size:18px">/shipments/</span></p>


**BODY PARAMETERS**

.. list-table:: 
   :widths: 10 10 20 
   :header-rows: 1

   * - Attributes
     - Required/Optional
     - Data Type
   * - **address_from**
     - required
     - string or object
   * - **address_to**
     - required
     - string or object
   * - **parcels**
     - required
     - string, object, or array
   * - **shipment_date**
     - optional
     - datetime
   * - **address_return**
     - optional
     - string or object
   * - **customs_declaration**
     - optional
     - string or object
   * - **extra**
     - optional
     - object
   * - **metadata**
     - optional
     - string, up to 50 characters
   * - **async**
     - optional
     - boolean


**EXAMPLE REQUEST (Create a Shipment)**:

.. code-block:: bash

  curl https://api.goshippo.com/shipments/ \
    -H "Authorization: ShippoToken <API_TOKEN>" \
    -H "Content-Type: application/json" \
    -d $'{
        "address_to": {
            "name": "Mr Hippo",
            "street1": "965 Mission St #572",
            "city": "San Francisco",
            "state": "CA",
            "zip": "94103",
            "country": "US",
            "phone": "4151234567",
            "email": "mrhippo@goshippo.com"
        },
        "address_from": {
            "name": "Mrs Hippo",
            "street1": "1092 Indian Summer Ct",
            "city": "San Jose",
            "state": "CA",
            "zip": "95122",
            "country": "US",
            "phone": "4159876543",
            "email": "mrshippo@goshippo.com"
        },
        "parcels": [{
            "length": "10",
            "width": "15",
            "height": "10",
            "distance_unit": "in",
            "weight": "1",
            "mass_unit": "lb"
        }],
        "async": false
    }'


**EXAMPLE RESPONSE (from Create a Shipment)**:

.. literalinclude:: PostShipmentresponse.json 


----------------------------
``GET`` Retrieve a Shipment
----------------------------

A ``GET`` to the ``/shipment`` resource to allow your application to retrieve an existing shipment by object ID.

.. raw:: html 

   <p><span style="color:blue;font-size:18px">/shipments/{shipment object id}</span></p>



**PATH PARAMETERS**

.. list-table:: 
   :widths: 15 10 20 30
   :header-rows: 1

   * - Parameter
     - Required/Optional
     - Data Type
     - Description
   * - **Shipment Object ID**
     - required
     - string
     - shipment object id

**EXAMPLE REQUEST (Retrieve a Shipment)**

.. code-block:: bash

 curl https://api.goshippo.com/shipments/7c47d12aa95a4cbb9d90c167cca7bea7 \
    -H "Authorization: ShippoToken <API_TOKEN>"


**EXAMPLE RESPONSE (from Retrieve a Shipment)**:

.. literalinclude:: RetrieveShipmentResponse.json 


---------------------------
``GET`` List All Shipments
---------------------------

A ``GET`` to the ``/shipment`` resource to allow your application to list all shipment objects. 

.. raw:: html 

   <p><span style="color:blue;font-size:18px">/shipments/</p>

**EXAMPLE REQUEST (List All Shipments)**

.. code-block:: bash

 curl https://api.goshippo.com/shipments/ \
    -H "Authorization: ShippoToken <API_TOKEN>"


**QUERY PARAMETERS**

In order to filter results, you can use the below query parameters. A maximum date range of 90 days is permitted. Provided dates should be ISO 8601 UTC dates.

.. list-table:: 
   :widths: 15 10 20 
   :header-rows: 1

   * - Parameter
     - Data Type
     - Description
   * - **object_created_gt**
     - object
     - object(s) created greater than a provided date time
   * - **object_created_gte**
     - object
     - object(s) created greater than or equal to a provided date time
   * - **object_created_lt**
     - object
     - object(s) created greater less than a provided date time
   * - **object_created_lte**
     - object
     - object(s) created less than or equal to a provided date time

**Date Format Examples:**

``"2017-01-01"``

``"2017-01-01T03:30:30" or "2017-01-01T03:30:30.5"``

``"2017-01-01T03:30:30Z"``


**Example URL with the Query Parameters:**
  
https://api.goshippo.com/shipments/?object_created_gte=2017-01-01T00:00:30&object_created_lt=2017-04-01T00:00:30


**EXAMPLE RESPONSE (from List All Shipments)**

.. literalinclude:: ListShipmentResponse.json