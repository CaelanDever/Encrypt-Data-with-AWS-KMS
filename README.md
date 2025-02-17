# Encrypt Data with AWS KMS

**Author:** Caelan Dever  
**Email:** caelanwd@gmail.com

---

<img width="499" alt="5a" src="https://github.com/user-attachments/assets/cf72420c-d6a9-4427-b006-db4afe3ba725" />

---

## Introducing Today's Project!

In this project, I will demonstrate how to create encryption keys with AWS KMS (Key Management Service). The goal is to observe how AWS stops unauthorized access to your data.

### Tools and concepts

Services I used include KMS, IAM, DynamoDB. Key concepts I learnt include encryption, observing how AWS stops unauthorized access to your data, and adding and retrieve data from your database to test your encryption.

### Project reflection

This project took me approximately 45 minutes. The most challenging part was trying to log in to the test user on the incognito tab. It was most rewarding to be able to see how the encrypted data did not allow the test user to see the data. 

I did this project to further improve my AWS security and encryption skills. It definately met my goals. 

---

## Encryption and KMS

Encryption is the process of using algorithms to convert data into a secure format called ciphertext. Companies and developers do this to to secure user data, transactions, files and more. Encryption keys look like cipher text.

AWS KMS is a secure vault for your encryption keys. Key management systems are important because they help you manage all your encryption keys, like what it encrypts or who has access, in one place. Your keys are safe in a KMS

Encryption keys are broadly categorized as AWS managed keys and customer managed keys. I set up a symmetric key because they are generally faster and more efficient for encrypting large amounts of data, which is why we're using one for our DynamoDB.

<img width="770" alt="6j" src="https://github.com/user-attachments/assets/9ee057ca-3e57-4b96-8a30-c214c322e4fe" />



---

## Encrypting Data

My encryption key will safeguard data in DynamoDB, which is a fast and flexible way to store your data, which makes it a great choice for applications that need quick access to large volumes of data e.g. games.

The different encryption options in DynamoDB include Owned by Amazon DynamoDB, AWS managed key, Stored in your account, and owned and managed by you. Their differences are based on different encryption options. I selected owned and managed by you.

<img width="861" alt="2w" src="https://github.com/user-attachments/assets/8e5f30ec-a0f5-4f46-a006-dd647c4fe0a3" />


---

## Data Visibility

Rather than controlling who has access to the key, KMS manages user permissions by having only those with the right permissions can use it to do specific actions like encryption or decryption.

Despite encrypting my DynamoDB table, I could still see the table's items because I as a user have permissions to use the encryption key in KMS. DynamoDB uses transparent data encryption, which means your data is secure at rest, yet still accessible.

<img width="489" alt="5j" src="https://github.com/user-attachments/assets/6a3a0990-2f3e-4ac8-ab92-0ffed2b753a0" />

---

## Denying Access

I configured a new IAM user to  to check if a user without access to our KMS key can view the data in DynamoDB. The permission policies I granted this user are AmazonDynamoDBFullAccess but not admin permissions. 

After accessing the DynamoDB table as the test user, I encountered 'You don't have permission to kms:Decrypt' because myuser isn’t allowed to decrypt the data. This confirmed  how KMS works - and that the data was safely encrypted. 


<img width="499" alt="5a" src="https://github.com/user-attachments/assets/2cefb572-7976-480c-af12-74487b7c32d1" />

---

## EXTRA: Granting Access

To let my test user use the encryption key, I scroll down the Key policy tab, and select Add next to Key users. My key's policy was updated to Key users.

Using the test user, I retried accessing that database. I observed that I was able to see the decrypted data which confirmed that I was able to give the test user the correct permissions. 

Encryption secures data instead of roles preventing access to a resource I could combine encryption with security groups or permission policies to add a layer of security.

<img width="390" alt="4s" src="https://github.com/user-attachments/assets/a9fb11e4-2558-43a1-87c2-735832c8dbef" />

---

---
