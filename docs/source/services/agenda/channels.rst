Broadcast Channel
=================

Broadcast.Channel is a model in Agenda microservice which is a kind of
superior container for broadcast streams and contents.


Broadcast channel records are accessible using `Official RadioKit REST Api`_.
The following URL should be used to obtain Broadcast.Channel records:

.. code-block:: rest

    https://agenda.backend.url/api/rest/v1.0/broadcast/channel


Broadcast channel data
----------------------

The following broadcast channel data fields are available for the user for index
and show MVC action:

+------------------------+----------+--------------------------------------------------+
| Field                  | Type     | Description                                      |
+========================+==========+==================================================+
| id                     | UUID     | Refer to: `Model Common Fields`_.                |
+------------------------+----------+--------------------------------------------------+
| name                   | string   | Refer to: `Model Common Fields`_.                |
+------------------------+----------+--------------------------------------------------+
| slug                   | string   |                                                  |
+------------------------+----------+--------------------------------------------------+
| timezone               | string   | Timezone used for the channel                    |
+------------------------+----------+--------------------------------------------------+
| description            | string   | Channel's description                            |
+------------------------+----------+--------------------------------------------------+
| media_routing_group_id | UUID     |                                                  |
+------------------------+----------+--------------------------------------------------+
| homepage_url           | string   | Homepage's URL                                   |
+------------------------+----------+--------------------------------------------------+
| genre                  | string   | Channel's genre                                  |
+------------------------+----------+--------------------------------------------------+
| references             | map      | Refer to: `Model Common Fields`_.                |
+------------------------+----------+--------------------------------------------------+
| extra                  | map      | Refer to: `Model Common Fields`_.                |
+------------------------+----------+--------------------------------------------------+
| inserted_at            | DateTime | Refer to: `Model Common Fields`_.                |
+------------------------+----------+--------------------------------------------------+
| updated_at             | DateTime | Refer to: `Model Common Fields`_.                |
+------------------------+----------+--------------------------------------------------+


Fields That Can/Must Be Specified During Creation
-------------------------------------------------

During creation of the record user can specify values for some of the fields. Some
of them are required for the creation of the record ad some of them are optional.
Not specifying all the required fields for the creation of the record will result in
request being rejected.

+------------------------+----------+----------+
| Field                  | Type     | Required |
+========================+==========+==========+
| name                   | string   | yes      |
+------------------------+----------+----------+
| slug                   | string   | yes      |
+------------------------+----------+----------+
| timezone               | string   | yes      |
+------------------------+----------+----------+
| description            | string   | no       |
+------------------------+----------+----------+
| media_routing_group_id | UUID     | yes      |
+------------------------+----------+----------+
| homepage_url           | string   | no       |
+------------------------+----------+----------+
| genre                  | string   | no       |
+------------------------+----------+----------+
| references             | map      | no       |
+------------------------+----------+----------+
| extra                  | map      | no       |
+------------------------+----------+----------+


Fields That Can Be Updated After Creation
-----------------------------------------

There are some fields for which the value can be updated after the record is created.
Crucial fields can be assigned a value only during creation and they cannot be
changed later. The following fields can be updated by the user after record creation:

+------------------------+----------+
| Field                  | Type     |
+========================+==========+
| name                   | string   |
+------------------------+----------+
| timezone               | string   |
+------------------------+----------+
| description            | string   |
+------------------------+----------+
| homepage_url           | string   |
+------------------------+----------+
| genre                  | string   |
+------------------------+----------+
| references             | map      |
+------------------------+----------+
| extra                  | map      |
+------------------------+----------+


Fields That Can Be Used in Conditions
-------------------------------------

The following broacast channel data fields can be used in conditions in
index and show MVC actions:

+------------------------+----------+
| Field                  | Type     |
+========================+==========+
| name                   | string   |
+------------------------+----------+
| slug                   | string   |
+------------------------+----------+

Other Records That Can Be Used for Join
---------------------------------------

The following records can be used for join operation in index and show MVC actions:

+------------------------+------------------------------+------------------------------+
| Field                  | Model                        | Description                  |
+========================+==============================+==============================+
| schedule_content_types | Agenda.Broadcast.ContentType | Content types that belong to |
|                        |                              | broadcast channel            |
+------------------------+------------------------------+------------------------------+
| broadcast_streams      | Agenda.Broadcast.Stream      | Broadcast streams that       |
|                        |                              | belong to broadcast channel  |
+------------------------+------------------------------+------------------------------+

.. _Official RadioKit REST Api: http://docs.radiokit.org/projects/engine/en/latest/services/restapi.html
.. _Model Common Fields: http://docs.radiokit.org/projects/engine/en/latest/services/rest/common_fields.html

.. toctree::
