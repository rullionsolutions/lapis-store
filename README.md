# lapis-store
Document Store








## Apache CouchDB Cheatsheet

|Method  |Path    |Description      |
|--------|--------|-----------------|
|GET     |/       |ping the server|
|PUT     |/{db}   |create database|
|DELETE  |/{db}   |delete database|
|PUT     |/{db}/{docid}   |create document {json document in request body}, see Note 1|
|GET     |/_uuids[?count={number}]   |get a new uuid|
|GET     |/{db}/{docid}   |retrieve document {json document in response body}|
|DELETE  |/{db}/{docid}   |delete document|
|COPY    |/{db}/{docid}   |copy document|
|PUT     |/{db}/{docid}/{filename}?rev={doc revision} |add attachment {'Content-Type' header, binary data in request body}|
|GET     |/{db}/_design/{ddoc}   |returns the contents of the design document specified with the name of the design document and from the specified database from the URL. Unless you request a specific revision, the latest revision of the document will always be returned|
|PUT     |/{db}/_design/{ddoc}   |creates a new named design document, or creates a new revision of the existing design document, see Note 2|
|DELETE  |/{db}/_design/{ddoc}   ||
|COPY    |/{db}/_design/{ddoc}   ||
|GET     |/{db}/_design/{ddoc}/_show/{func}   |apply {func} show function for a null document|
|POST    |/{db}/_design/{ddoc}/_show/{func}   |
|GET     |/{db}/_design/{ddoc}/_show/{func}/{docid}[?format={format}] apply {func} show function for the specified document|
|POST    |/{db}/_design/{ddoc}/_show/{func}/{docid}   ||
|GET     |/{db}/_design/{ddoc}/_list/{func}/{view}    |apply list function for the view function from the same design document|
|POST    |/{db}/_design/{ddoc}/_list/{func}/{view}    ||
|GET     |/{db}/_design/{ddoc}/_list/{func}/{other-ddoc}/{view}  |apply list function for the view function from the other design document|
|POST    |/{db}/_design/{ddoc}/_list/{func}/{other-ddoc}/{view}  ||
|POST    |/{db}/_design/{ddoc}/_update/{func}/{docid}  |execute {func} update function on server side for the specified document, using the request body as required|

### Note 1:
update document - same as create, except json doc MUST include '_rev' revision number property, whose value MUST match the latest doc revision in the database

### Note 2:
* language (string): Defines Query Server key to process design document functions
* options (object): View’s default options
* filters (object): Filter functions definition
* lists (object): List functions definition
* rewrites (array): Rewrite rules definition
* shows (object): Show functions definition
* updates (object): Update functions definition
* validate_doc_update (string): Validate document update function source
* views (object): View functions definition.
