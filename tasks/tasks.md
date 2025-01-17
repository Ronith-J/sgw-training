# Tasks

## Task 1

### Description

- Setup SGW using setup 1
- Use Postman to check if SGW is working (use Admin PORT)

### Observations

just add
```
  "api": {
    "admin_interface": "0.0.0.0:4985"
  },
  to the config file
```
  then add auth to the postman request
  
## Task 2

### Description

- Setup SGW using setup 2
- Create a Database using Postman
- Create a Document using Postman
- Get the document using Postman

### Observations
--added using 
--add autherization 
--replace hostname with 0.0.0.0
--doc created and retrieved

--
```
{
    "_id": "1",
    "_rev": "1-15d03b6aba15a752154baffff6054abc",
    "key2": "value2",
    "name": "ronith"
}
```
## Task 3

### Description

- This task continues from the previous task
- Create a dummy document from CB UI
- Get the document contents using Postman
- Delete the document using Postman


### Observations

-- created a doc 
--change the 2 parameters while creating the db 
```
{
  "bucket": "test",
  "name": "db1",
  "import_docs": true,
  "enable_shared_bucket_access":true,
  "num_index_replicas":0
}
```

--pulled doc:
```
{
    "_id": "2",
    "_rev": "1-4ca9e6601a234d750e68c3d3d48e0def",
    "dummy": "doc"
}
```
## Task 4

### Description

- Create a document from Couchbase Server UI
- Review the revision IDs and explain the different values in revision IDs

### Observations
on adding a doc to the ui and get the doc:
```
{
    "_id": "4",
    "_rev": "1-5955d30616e288f716c07e48e4073488",
    "data": 4
}
```

then on updating the doc :
```
{
    "_id": "4",
    "_rev": "2-c23509409417448f4c9ba80f8b61d1fc",
    "data": 4,
    "edit": 2
}
```

thus prolly the 1st part changes the the 2nd part is a hash...


**Meta and Sync Gateway Layers**

The document in Couchbase has two layers of metadata:
Meta: Couchbase-level metadata, managed by the Couchbase Server.
Xattrs: Sync Gateway-managed metadata, specifically the _sync property.
These layers store details like the revision history, CAS (Check-And-Set) tokens, and Sync Gateway-specific information (e.g., channels, sequence).

**Revision (rev)**

The rev field in the Sync Gateway (_sync.rev) represents the latest revision of the document that Sync Gateway tracks.
The rev in the response from Sync Gateway (via Postman or API) only includes the latest revision identifier and does not expose the entire revision history to simplify client interaction.


## Task 5

### Description

- Test the following configurations of SGW database:

```
1. enable_shared_bucket_access: false, import_docs: false
2. enable_shared_bucket_access: false, import_docs: true
3. enable_shared_bucket_access: true, import_docs: false
4. enable_shared_bucket_access: true, import_docs: true
```

### Observations

<img width="503" alt="image" src="https://github.com/user-attachments/assets/cb45e48c-6186-4219-860f-9c2086edfa15" />


