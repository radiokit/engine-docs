Broadcast Channel
=================

Broadcast.Channel is a model in Agenda microservice which gathers all
data for a given audio channel.

Broadcast channel records are accessible using `Official RadioKit REST Api <http://docs.radiokit.org/projects/engine/en/latest/services/restapi.html>`_.
The following URL should be used to obtain Broadcast.Channel records:

.. code-block:: rest

    http://agenda.backend.url/api/rest/v1.0/broadcast/channel


Broadcast channel data
----------------------

The following broadcast channel data fields are available for the user for index
and show MVC action:

+------------------------+--------------------------------------------------+
| Field                  | Description                                      |
+========================+==================================================+
| id                     | Channel id                                       |
+------------------------+--------------------------------------------------+
| name                   | Name of the channel                              |
+------------------------+--------------------------------------------------+
| slug                   |                                                  |
+------------------------+--------------------------------------------------+
| timezone               | Timezone used for the channel                    |
+------------------------+--------------------------------------------------+
| description            | Channel's description                            |
+------------------------+--------------------------------------------------+
| media_routing_group_id |                                                  |
+------------------------+--------------------------------------------------+
| homepage_url           | Homepage's URL                                   |
+------------------------+--------------------------------------------------+
| genre                  | Channel's genre                                  |
+------------------------+--------------------------------------------------+
| references             |                                                  |
+------------------------+--------------------------------------------------+
| extra                  |                                                  |
+------------------------+--------------------------------------------------+
| inserted_at            | Date and time of the last udpate for the record  |
+------------------------+--------------------------------------------------+
| updated_at             | Date and time whien the record was created       |
+------------------------+--------------------------------------------------+

Condition Fields
----------------
The following broacast channel data fields can be used in conditions in
index and show MVC actions:

+------------------------+--------------------------------------------------+
| Field                  | Description                                      |
|                        |                                                  |
+========================+==================================================+
| name                   | Name of the channel                              |
+------------------------+--------------------------------------------------+
| slug                   |                                                  |
+------------------------+--------------------------------------------------+

Channel Broadcast Methods
-------------------------
Model Brodacast.Channel does not provide any methods.

.. toctree::