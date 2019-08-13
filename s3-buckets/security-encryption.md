# Security and Encryption

* Encryption in Transit
  * SSL/TLS

* Encryption at Rest(Server Side)
  * S3 Managed Keys = **SSE-S3** (server side encryption)
    * AWS manages the keys for you
  * AWS Key Management Service, Managed Keys  = **SSE-KMS**
    * AWS and client jointly manage the keys
  * Server Side Encryption with Customer Provided Keys = **SSE-C**
    * give AWS your own created keys

* Client Side Encyption
  * encrypt object yourself and upload the encrpyted object to S3
