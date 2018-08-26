# Big Data DevOps (Part 2): Schemas!

_Captured: 2018-03-29 at 14:36 from [dzone.com](https://dzone.com/articles/big-data-devops-part-2-schemas?edition=370196&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-03-29)_

Access NoSQL and Big Data through SQL using standard drivers (ODBC, JDBC, ADO.NET). [Free Download ](https://dzone.com/go?i=250345&u=https%3A%2F%2Fwww.cdata.com%2Ftech%2Fbigdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbump3%2520)

Since we can process records in Apache NiFi, Streaming Analytics Manager, Apache Kafka, and any tool that can work with a schema, we have a real need to use a Schema Registry. I have mentioned them before. One thing that is important is to be able to automate the management of schemas. Today, we will be listing and exporting them for backup and migration purposes. We will also cover how to upload new schemas and version of schemas.

The steps to back up schemas with Apache NiFi 1.5+ is easy.

  1. **GetHTTP**: Get the list of schemas for SR via GET.
  2. **SplitJson**: Turn the list into individual records.
  3. **EvaluateJsonPath**: Get the schema name.
  4. **InvokeHTTP**: Get the schema body.
  5. **EvaluateJsonPath**: Turn the schema text into a separate flow file.
  6. Rename and save both the full JSON record from the registry and the schema only.

NiFi flow:

![](https://community.hortonworks.com/storage/attachments/62812-nififlow.png)

> _Initial call to list all schemas:_

![](https://community.hortonworks.com/storage/attachments/62798-listschemas.png)

> _Get the schema name:_

![](https://community.hortonworks.com/storage/attachments/62799-grabschemaname.png)

Example schema with text:

![](https://community.hortonworks.com/storage/attachments/62800-oneschemagrabbed.png)

> _An example of JSON schema text:_

![](https://community.hortonworks.com/storage/attachments/62803-schematextdataprovenance.png)

> _Build a new flow file from the schema text JSON:_

![](https://community.hortonworks.com/storage/attachments/62804-buildschemafile.png)

Get the latest version of the schema text for this schema by name:

![](https://community.hortonworks.com/storage/attachments/62805-get.png)

> _The list returned:_

![](https://community.hortonworks.com/storage/attachments/62809-schemalist.png)

Swagger documentation for SR:

![](https://community.hortonworks.com/storage/attachments/62801-createanewschemanobody.png)

![](https://community.hortonworks.com/storage/attachments/62802-registryanewschemaversiontext.png)

![](https://community.hortonworks.com/storage/attachments/62806-swaggerdocs.png)

![](https://community.hortonworks.com/storage/attachments/62807-confluentschemalist.png)

![](https://community.hortonworks.com/storage/attachments/62808-confluentswaggertest.png)

> _Schema list JSON formatting:_
    
    
    "entities" : [ { "schemaMetadata" : { "type" : "avro", "schemaGroup" : "Kafka", "name" : "adsb", "description" : "adsb", "compatibility" : "BACKWARD", "validationLevel" : "ALL", "evolve" : true }, "id" : 3, "timestamp" : 1520460239420

[Get Schema List REST URL (GET)](http://server:7788/api/v1/schemaregistry/schemas).

.

If you wish, you can use the Confluent Style API against SR and against the Confluent Schema Registry. It is slightly different but it's easy to change our REST calls to process this.

[The fastest databases need the fastest drivers](https://dzone.com/go?i=250346&u=https%3A%2F%2Fwww.cdata.com%2Fblog%2Fnews%2F20170601-bigquery-driver-comparison%3Futm_source%3Ddzone%26utm_medium%3Dbump4) \- learn how you can leverage CData Drivers for high performance NoSQL & Big Data Access.

Opinions expressed by DZone contributors are their own.
