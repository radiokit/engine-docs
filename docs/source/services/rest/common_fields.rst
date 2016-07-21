Model Common Fields
===================

There is a number of fields that are common for all the models in all the RadioKit microservices.
This chapter describes those fields in details.

+-------------+-------------+-----------------------------------------------------------+
| Field       | Type        | Description                                               |
+=============+=============+===========================================================+
| id          | UUID string | Unique identifier of each record.                         |
|             |             |                                                           |
|             |             | For more information about UUID type refer to             |
|             |             | `Ecto.UUID <https://hexdocs.pm/ecto/Ecto.UUID.html>`_.    |
+-------------+-------------+-----------------------------------------------------------+
| name        | string      | Name of record                                            |
+-------------+-------------+-----------------------------------------------------------+
| references  | map         | ID of the record in another microservice. Used to express |
|             |             | relation between records in different microservices       |
+-------------+-------------+-----------------------------------------------------------+
| extra       | map         | Container used to store all data that do not fit to       |
|             |             | predefined fields of the model                            |
+-------------+-------------+-----------------------------------------------------------+
| inserted_at | DateTime    | Date and time of the last udpate for the record           |
+-------------+-------------+-----------------------------------------------------------+
| updated_at  | DateTime    | Date and time when the record was created                 |
+-------------+-------------+-----------------------------------------------------------+

.. toctree::
