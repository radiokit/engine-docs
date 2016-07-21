Official RadioKit REST API
==========================

Official RadioKit REST API is query-like interface to most of the resources
provided to the users by RadioKit microservices.

Resources
---------
Microservices provide resources stored as records in the database. Records
of particular type are defined by models.

Resources of a given model can be obtained using HTTP methods with an URL
specific for the given model.

URL
---
The general URL specifying both microservice and model:

.. code-block:: rest

    https://<microservice>.backend.url/api/rest/v1.0/<model_path>

For example records for Broadcast.Channel model defined in Agenda microservice
are obtainable via the following URL:

.. code-block:: rest

    https://agenda.backend.url/api/rest/v1.0/broadcast/channel


Listing records
---------------
Listing records corresponds to index action in MVC design pattern and can
be obtained using HTTP GET method on general model URL.

In general HTTP request GET https://agenda.backend.url/api/rest/v1.0/broadcast/channel
should return JSON containing all broadcast channels defined in agenda microservice:

.. code-block:: javascript

    {
      meta: {},
      data: [
        // records here
      ]
    }

The same can be obtained using JavaScript wrapper:

.. code-block:: none

    radiokit
      .query(“agenda”, “Broadcast.Channel”)
      .where(“name”, “eq”, “something”)
      .order(“name”, “asc”)
      .on(“fetch”, (_event, _query, data)) => {
        // data is already wrapped in Immutable.js array
      })
      .fetch();

Please note that at least one data field of the record must be specified in the
request in order to verify this request as correct one.

Request which does not specify any data field is treated as incorrect and is rejected.

Record data
-----------

User can specify which record data should be returned in a response from server
using 'a' parameter.

This allows to modify the server's response to only this data that is of user's
interest.

Documentation for each model specifies which record data can be obtained by the
user.

Example
^^^^^^^

.. code-block:: rest

    GET https://agenda.backend.url/api/rest/v1.0/broadcast/channel?a[]=id

Above HTTP request will return all broadcast channels and each returned record will
have only 'id' field specified.

Example
^^^^^^^

.. code-block:: rest

    GET https://agenda.backend.url/api/rest/v1.0/broadcast/channel?a[]=id&a[]=name

Above HTTP request will return all broadcast channels and each returned record will
have both 'id' and 'name' fields specified.

At least one data field must be specified in the request.


Record Methods
--------------
Some of the records provide methods that can be applied for a given record.

Methods are applied in the same manner as record data and the result of
execution for given method is applied to the server response.

Documentation for each model specifies record methods available for given
model.


Limiting number of returned records by using conditions
-------------------------------------------------------

User can limit number of returned records to the ones that fulfill the condition
specified in the request. Condition can be defined using 'c' parameter.

In order to specify the condition in the request the following syntax should
be used::

    ?c[<field_name>][]=<operator>%20<specified_value>

The following operators can be used in conditions:

+----------+---------------------------------------------------------+
| Operator | Description                                             |
+==========+=========================================================+
| in       | checks if field's value is included in specified_value  |
+----------+---------------------------------------------------------+
| eq       | checks if field's value is equal to specified_value     |
+----------+---------------------------------------------------------+
| neq      | checks if field's value is not equal to specified_value |
+----------+---------------------------------------------------------+
| lt       | checks if field's value is less than specified_value    |
+----------+---------------------------------------------------------+
| gt       | checks if field's value is greater than specified_value |
+----------+---------------------------------------------------------+
| lte      | checks if field's value is less than or equal           |
+----------+---------------------------------------------------------+
| gte      | checks if field's value is greater than or equal        |
+----------+---------------------------------------------------------+
| isnull   | checks if field's value is is null                      |
+----------+---------------------------------------------------------+
| notnull  | checks if field's value is is not null                  |
+----------+---------------------------------------------------------+
| any      |                                                         |
+----------+---------------------------------------------------------+
| deq      |                                                         |
+----------+---------------------------------------------------------+
| dneq     |                                                         |
+----------+---------------------------------------------------------+

Example
^^^^^^^

.. code-block:: rest

    GET https://agenda.backend.url/api/rest/v1.0/broadcast/channel?a[]=id&c[name][]=eq%20Jazz

Above HTTP request will return all broadcast channels for which 'name' field is equal
to 'Jazz' and each returned record will have only 'id' field specified.

Joining other related records
-----------------------------

User can request adding other related records to server response by using
'j' parameter in the request. The following syntax applies::

   ?j[]=<model_name_in_plural>

Example
^^^^^^^

.. code-block:: rest

    GET https://agenda.backend.url/api/rest/v1.0/broadcast/channel?a[]=id&a[]=name&j[]=broadcast_streams

Above HTTP request will return all broadcast channels and each returned record will
have both 'id' and 'name' fields specified. Additionally for each of broadcast records
belonging broadcast streams will be added to the server's response.

.. toctree::
