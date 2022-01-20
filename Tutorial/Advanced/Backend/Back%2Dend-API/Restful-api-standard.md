The API configurated by Auto coding in strict compliance with RESTful API specification. There are usually a few APIs below:

[Get a single record](#get-a-single-record)
[List the records by query](#list-the-records-by-query)
[Create a new record](#crete-a-new-record)
[Edit a record](#edit-a-record)
[Remove a record](#remove-a-record)


# Get a single record

If you want to get a specified entity, the method must be `GET` and the URL should be identified to this entity. So the endpoint should be one of the following:

- `GET /entities/{id}`. For multiple record, we must use the plural of the entity name as the path. e.g. `Get /articles/{id}`. 

- `GET /entity`. For single record, we must use the singular of the entity name as the path. e.g. `Get /autoDistributionConfig`. 

- `Get /entities/{id}/extendedEntity`. For extension record, we usually take the name of the extended entity after the URL of the main entity. e.g. `GET /campaigns/{id}/chatWindow`. 


# List the records by query

If you need to list multiple records based on the query criteria, the method must be `GET` and the url must point to the collection of the entities.

- `GET /entities`. In general, we can use the collection of entities directly as the URL. e.g. 

- `GET /parents/{id}/children`. In certain cases, if query the entities must take a condition that is a one-to-many relation with the current entity we can put the condition in path. e.g. `GET /categories/{id}/articles`.

# Create a new record

If we need to create a new record, we usually use the `POST` method and the URL should be the collection of the entity. With on exception, when we create an extended entity of a single record or oneToOneOrZero entity, we cannot know if the entity already exists or not. So we use `PUT` method for creation of replacement of the entity.

- `POST /entiteis`. e.g. `POST /tickets`

- `PUT /entity`. e.g. `PUT /ciscoIntegration`.

- `PUT /entities/{id}/extendedEntity`. e.g. `PUT /tickets/{id}/draft`.

# Edit a record

- `PUT /entities/{id}`

- `PUT /entity`

- `PUT /entities/{id}/extendedEntity` 


# Remove a record

If we need to remove a record, we should use the 'DELETE' method and the URL should be identified to the entity.

- `DELETE /entities/{id}` for


