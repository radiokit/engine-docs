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

RadioKit JavaScript API
-----------------------

Official RadioKit JavaScript API provides methods for handling uploads. It
encapsulates them in high-level wrappers and ensures that any future changes
to the underlying architecture will be reflected without necessity to modify
your code.

It encapsulates authentication procedures, provides ability to queue files,
upload them in parallel (but by default it will upload only them one after another),
restart uploads and the most importantly, divide them into chunks. This is a
quite reliable way to create uploader that handles large files even on weak
network connections.

This is the preferred way to do uploads through web browser. Please note that
this API does not handle server-side JavaScript as it needs access to the DOM.

Example
^^^^^^^

.. code-block:: javascript

    import { Data } from "radiokit-api";

    var data = new Data();
    var upload;

    data.on("auth::success", () => {
      upload = data.upload("80332F34-F903-11E5-A3E1-3E19FDC8A409", { autoStart: true })
      upload.assignBrowse(document.getElementById("#uploadButton"));
      upload.assignDrop(document.getElementById("#uploadDropzone"));
      upload.on("added", (_eventName, queue) => { console.log(queue.getQueue()); });
      upload.on("progress", (_eventName, queue) => { console.log(queue.getQueue()); });
      upload.on("retry", (_eventName, queue) => { console.log(queue.getQueue()); });
      upload.on("error", (_eventName, queue) => { console.log(queue.getQueue()); });
    });

    data.signIn(); // This will redirect to the authentication service


Resumable.JS
------------

Vault also provides interface for uploading via `Resumable.JS <http://resumablejs.com/>`_
JavaScript library. This is an alternative way to import files through web browser.
It is however, quite low-level, and especially authentication may be tricky
as you have to get and refresh OAuth2 access token on your own. It is however
still possible if you don't want to use official RadioKit API due to any reason.

Resumable.JS provides ability to queue files, upload them in parallel, restart
uploads and the most importantly, divide them into chunks. This is a quite reliable
way to create uploader that handles large files even on weak network connections.

The endpoint for uploading is https://vault.radiokitapp.org/api/upload/v1.0/resumablejs.
Maximum chunk size is 4MB. Testing if chunks are already present (the `testChunks`
option) is not supported. You must pass some additional headers and parameters
to the requests:

* `Authorization` header with valid OAuth2 access token (see: Authentication)
* `radiokit` query parameter that contains:
    * `record_repository_id` with valid Repository ID (see: Repositories)

Please refer to Resumable.JS documentation for further information.

Example
^^^^^^^

.. code-block:: javascript

    var r = new Resumable({
      target: "https://vault.radiokitapp.org/api/upload/v1.0/resumablejs",
      query: {
        radiokit: {
          record_repository_id: "80332F34-F903-11E5-A3E1-3E19FDC8A409"
        }
      },
      headers: {
        Authorization: "Bearer 123"
      },
      testChunks: false,
    });

    if(!r.support)  {
      alert("Chunked upload is not supported, upgrade your web browser.");
    }

    r.assignDrop(document.getElementById("#uploadDropzone"))
    r.assignBrowse(document.getElementById("#uploadButton"), false);

    r.fileAdded(() => { r.upload() });

.. toctree::
