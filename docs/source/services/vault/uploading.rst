Uploading
=========

There are several ways to upload media files into Vault. Depending on the context
and desired integration with other applications you may want to push the whole
file at once, ask service to pull it or upload it in chunks. Each of them has
its benefits and drawbacks, described below.

Please note that uploading refers to action initiated by user or another
application. You also may want to take a look about importing features that
can be used to automatically fetch content from existing applications without
necessity to trigger such operation.

Resumable.JS
------------

Vault provides interface for uploading via `Resumable.JS <http://resumablejs.com/>`_
JavaScript library. This is the preferred way to import files through web browser.
Resumable.JS provides ability to queue files, upload them in parallel, restart
uploads and the most importantly, divide them into chunks. This is a quite reliable
way to create uploader that handles large files even on weak network connections.

The endpoint for uploading is https://vault.radiokitapp.org/api/upload/v1.0/resumablejs.
Maximum chunk size is 4MB. You must pass some additional headers and parameters
to the requests:

* At least `Authorization` header (see: Authentication)
* At least `record_repository_id` parameter (see: Repositories)

Example using plain JavaScript
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

    var r = new Resumable({
      target: 'https://vault.radiokitapp.org/api/upload/v1.0/resumablejs',
      query: {
        radiokit: {
          record_repository_id: '80332F34-F903-11E5-A3E1-3E19FDC8A409'
        }
    });

    if(!r.support)  {
      alert('Chunked upload is not supported, upgrade your web browser.');
    }

.. toctree::
