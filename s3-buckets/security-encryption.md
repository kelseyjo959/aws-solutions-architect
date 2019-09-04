# Security and Encryption

* **Encryption in Transit**
  * *SSL/TLS*
  * think HTTPS

* **Encryption at Rest**
  * *Server Side*
    * S3 Managed Keys = **SSE-S3** (server side encryption)
      * AWS manages the keys for you
    * AWS Key Management Service, Managed Keys  = **SSE-KMS**
      * AWS and client jointly manage the keys
    * Server Side Encryption with Customer Provided Keys = **SSE-C**
      * give AWS your own created keys
  * *Client Side Encryption*
    * encrypt object yourself and upload the encrypted object to S3

 > *Back to S3 Notes:* [**Back to S3 README**](./README.md)
