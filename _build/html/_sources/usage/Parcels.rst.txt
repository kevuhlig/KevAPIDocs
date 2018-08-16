=============
Parcels
=============

-------------------
The Parcels Object
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
      <td>object_state</td>
      <td>"VALID"</td>
      <td>A Parcel will only be valid when all required values have been sent and validated successfully.</td>
    </tr>
    <tr>
      <td>object_created</td>
      <td>datetime</td>
      <td>Date and time of Address creation.</td>
    </tr>
    <tr>
      <td>object_updated</td>
      <td>datetime</td>
      <td>Date and time of last Parcel update. Since you cannot update Parcels after they were created, this time stamp reflects the time when the Parcel was changed by Shippo's systems for the last time, e.g., during sorting the dimensions given.</td>
    </tr>
    <tr>
      <td>object_id</td>
      <td>string</td>
      <td>Unique identifier of the given Parcel object. This ID is required to create a Shipment object.</td>
    </tr>
    <tr>
      <td>object owner</td>
      <td>string</td>
      <td>Username of the user who created the Parcel object.</td>
    </tr>
    <tr>
      <td>length</td>
      <td>decimal (10,4)</td>
      <td>Length of the Parcel. Up to six digits in front and four digits after the decimal separator are accepted.</td>
    </tr>
     <tr>
      <td>width</td>
      <td>decimal (10,4)</td>
      <td>Width of the Parcel. Up to six digits in front and four digits after the decimal separator are accepted.</td>
    </tr>
    <tr>
      <td>height</td>
      <td>decimal (10,4)</td>
      <td>Height of the parcel. Up to six digits in front and four digits after the decimal separator are accepted.</td>
    </tr>
    <tr>
      <td>distance_unit</td>
      <td>"cm", "in", "ft", "mm", "m", "yd"</td>
      <td>The unit used for length, width and height.</td>
    </tr>
    <tr>
      <td>weight</td>
      <td>decimal (10,4)</td>
      <td>Weight of the parcel. Up to six digits in front and four digits after the decimal separator are accepted.</td>
    </tr>
    <tr>
      <td>mass_unit</td>
      <td>"g", "oz", "lb", "kg"</td>
      <td>The unit used for weight.</td>
    </tr>
    <tr>
      <td>template</td>
      <td>string</td>
      <td>A <a href="https://goshippo.com/docs/reference#parcel-templates" target="_blank">parcel template</a> is a predefined package used by one or multiple carriers. See the <a href="https://goshippo.com/docs/reference#parcel-templates" target="_blank">parcel template</a> table for all available values and the corresponding tokens. When a template is given, the parcel dimensions have to be sent, but will not be used for the Rate generation. The dimensions below will instead be used. The parcel weight is not affected by the use of a template.</td>
    </tr>
    <tr>
      <td>metadata</td>
      <td>string</td>
      <td>A string of up to 100 characters that can be filled with any additional information you want to attach to the object.</td>
    </tr>
    <tr>
      <td>extra</td>
      <td>object</td>
      <td>An object holding optional extra services to be requested for each parcel in a multi-piece shipment. See the <a href="#ParcelExtrabookmark">Parcel Extra table</a> below for all available services.</td>
    </tr>

  </table>

  </body>
  </html>

.. raw:: html

  <p id="ParcelExtrabookmark"></p>

-------------
Parcel Extras
-------------

The following values are support for the ``extra`` field of the parcel object. 

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
      <th>Value</th>
      <th>Data Type</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>COD</td>
      <td>object</td>
      <td>Specify collection on delivery details (UPS, and FedEx only)</td>
    </tr>
    <tr>
      <td>COD.amount</td>
      <td>string</td>
      <td>Amount to be collected</td>
    </tr>
    <tr>
      <td>COD.currency</td>
      <td>ISO 4217 currency code (string)</td>
      <td>Currency for the amount to be collected. Currently only USD is supported for FedEx and UPS.</td>
    </tr>
    <tr>
      <td>COD.payment_method</td>
      <td>"SECURED_FUNDS", "CASH", "ANY"</td>
      <td>Secured funds include money orders, certified cheques and others (see <a href="https://www.ups.com/us/en/shipping/services/value-added/cod.page" target="_blank">UPS</a> and <a href="http://www.fedex.com/ca_english/services/addservopt/groundcod.html" target="_blank">FedEx</a> for details). If no payment_method inputted the value defaults to "ANY".)</td>
    </tr>
    <tr>
      <td>insurance</td>
      <td>object</td>
      <td>Specify collection on delivery details (UPS, and FedEx only).</td>
    </tr>
    <tr>
      <td>insurance.amount</td>
      <td>string</td>
      <td>Amount to be collected.</td>
    </tr>
     <tr>
      <td>insurance.currency</td>
      <td>ISO 4217 currency code (string)</td>
      <td>Currency for the amount to be collected. Currently only USD is supported for FedEx and UPS.</td>
    </tr>
    <tr>
      <td>insurance.provider</td>
      <td>"FEDEX", "UPS"</td>
      <td>Specify the carrier insurance to have Insurance provided by the carrier directly.</td>
    </tr>
    <tr>
      <td>insurance.content</td>
      <td>string</td>
      <td>Specify package content for insurance.</td>
    </tr>

  </table>

  </body>
  </html>

|

-----------------------------
``POST`` Create a New Parcel
-----------------------------

A ``POST`` to the ``/parcel`` resource to allow your application to create a new parcel object.


.. raw:: html 

   <p><span style="color:blue;font-size:18px">/parcels/</span></p>


**BODY PARAMETERS**

.. list-table:: 
   :widths: 10 10 20 
   :header-rows: 1

   * - Attributes
     - Required/Optional
     - Data Type
   * - **length**
     - required
     - decimal (10, 4)
   * - **width**
     - required
     - decimal (10, 4)
   * - **height**
     - required
     - decimal (10, 4)
   * - **distance_unit**
     - required
     - "cm", "in", "ft", "mm", "m", "yd"
   * - **weight**
     - required
     - decimal (10, 4)
   * - **mass_unit**
     - required
     - "g", "oz", "lb", "kg"
   * - **template**
     - optional
     - string
   * - **extra**
     - optional
     - object
   * - **metadata**
     - optional
     - string


**EXAMPLE REQUEST (Create a Parcel)**:

.. literalinclude:: PostParcel.txt


**EXAMPLE RESPONSE (from Create a Parcel)**:

.. literalinclude:: PostParcelresponse.json 


---------------------------
``GET`` Retrieve a Parcel
---------------------------

A ``GET`` to the ``/parcel`` resource to allow your application to retrieve an existing parcel by object ID.

.. raw:: html 

   <p><span style="color:blue;font-size:18px">/parcels/{parcel object id}</span></p>



**PATH PARAMETERS**

.. list-table:: 
   :widths: 15 10 20 30
   :header-rows: 1

   * - Parameter
     - Required/Optional
     - Data Type
     - Description
   * - **Parcel Object ID**
     - required
     - string
     - parcel object id

**EXAMPLE REQUEST (Retrieve a Parcel)**

.. code-block:: bash

 curl https://api.goshippo.com/parcels/7df2ecf8b4224763ab7c71fae7ec8274/ \
    -H "Authorization: ShippoToken <API_TOKEN>"


**EXAMPLE RESPONSE (from Retrieve a Parcel)**:

.. literalinclude:: RetrieveParcelResponse.json 


--------------------------
``GET`` List All Parcels
--------------------------

A ``GET`` to the ``/parcel`` resource to allow your application to list all parcel objects. 

.. raw:: html 

   <p><span style="color:blue;font-size:18px">/parcels/</p>

**EXAMPLE REQUEST (List All Parcels)**

.. code-block:: bash

 curl https://api.goshippo.com/parcels/ \
    -H "Authorization: ShippoToken <API_TOKEN>"

**EXAMPLE RESPONSE (from List All Parcels)**

.. literalinclude:: ListAddressResponse.json