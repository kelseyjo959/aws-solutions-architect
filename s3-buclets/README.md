# S3 Bucket

## Introduction

* One of the oldest AWS Service offerings
* S3 stands for Simple Storage Service
* S3 provides developers and IT teams with secure, durable, highly scaleable object storage
* easy to use web interface to store and retrieve any amount of data from anywhere on the web
* safe place to store objects (flat files)
* stored data is spread across multiple devices and facilities

## Features

* **Object-based storage (think files, only)**
* **files can range from 0 Bytes to 5 TB**
* **unlimited storage**
* **files stored in Buckets (think of a folder)**
* **S3 s a universal name space, names must be unique globally**
  * Must be unique because a **unique** web address will be created
    * **HTTPS** link will consist of the aws region as well as the bucket name
* For file uploading, a **HTTP 200 code** will be received if upload successful
* **NOT** suitable for installing an operating system in a Bucket (use block based instead)

### Key Features

* **tiered storage available**
* **lifecycle management** - move to different tiers
* **versoining**
* **encryption**
* **multi factor authentication for DELETE**
* **secure data with access control lists and bucket policies**

## Key Fundamentals of S3

* Objects are files
* **Key** = name of the object
* **Value** = sequence of bytes that makes up the data
* **Version ID** : allows for multiple versions of a file
* **Metadata** : data about the object being stored
* Subresources
  * **Access Control List** - permissions for object level or bucket level
  * **Torrent**

## S3 Data Consistency Model

* **read after write** consistency after PUTS of new objects - allows for immediate read of uploaded object
* **eventual consistency for overwrite** PUTS and DELETES - small amount of time must pass to propagate the update or delete

## S3 Guarantees

* 99.99% availability
* 99.999999999% durability of information (remember 11 9's)

> **Up Next**: [S3 Bucket Notes](./notes.md)
