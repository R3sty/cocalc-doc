public_get_directory_listing
============================

-  ``id``: A unique UUID for the query
-  ``project_id``: id of project containing public file to be read
   (required)
-  ``path``: path of directory in target project (required)
-  ``hidden``: show hidden files (default: false)
-  ``time``: sort by timestamp, with newest first (default: false)
-  ``start``: (default: 0)
-  ``limit``: (default: -1)

Given a project id and relative path (i.e. not beginning with a slash),
list all public files and subdirectories under that path. Path is
required, but may be the empty string, in which case a public listing of
the home directory in the target project is returned.

Examples:

Get public directory listing. Directory “Public” is shared and contains
one file “hello.txt” and one subdirectory “p2”.

Security key may be blank.

::

     curl -u : \
       -d path=Public \
       -d project_id=9a19cca3-c53d-4c7c-8c0f-e166aada7bb6 \
       https://cocalc.com/api/v1/public_get_directory_listing
     ==> {"event":"public_directory_listing",
          "id":"3e576b3b-b673-4d5c-9bce-780883f92958",
          "result":{"files":[{"size":41,"name":"hello.txt","mtime":1496430932},
                             {"isdir":true,"name":"p2","mtime":1496461616}]}

