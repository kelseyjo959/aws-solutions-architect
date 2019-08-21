# Identity, Access, and Access Management (IAM) Notes

* IAM user sign-in link can be customized. This is a DNS change.  Publicly accessible URL

* IAM does not reside within a single region, the users, groups, and role can be applied to all regions. **Currently universal**
* **Root Account** - is the account created when first setting up the AWS account and has *complete administrator access*.
  * *set up MFA on root account*
  * create and update password *rotation policies*
  * Always turn on multi-factor authentication (MFA) for the *root account* (always good practice for the other users on the AWS Account as well).
* No new users have *any* permissions when created.o
* New users will be able to interact with AWS using their access key ID and secret access key using the API, CLI, or AWS SDKs
  * Are assigned **Access Key ID & Secret Access keys when first created**, which are *not the same as a password*. *Only viewed once* These cannot be used to access the console. AWS access via the APIs and Command Line instead.
    * Types of access for users;
        1. **Console Access** - Through AWS website via a username and password.
        2. **Programmatic Access** - Used for interacting with AWS through code typically via a programming or scripting language.
            * Not the same as the password.
            * Used via the *Access Key ID* and *Secret Access Key*.
            * Cannot be used to log into the console.
            * May view only once, otherwise you will have to regenerate them.
* Ensure you customize smart policies applied to a rotation, types of characters and the length of passwords.

* Billing Alarms can be set up within the CloudWatch Service. Setting up a billing alarm to send alerts to an email address to receive alert when particular threshold is met.

> *Back to IAM Notes* [IAM README](./README.md)
