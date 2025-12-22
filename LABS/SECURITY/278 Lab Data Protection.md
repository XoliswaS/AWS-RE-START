# 🔐 Lab 278: Data Protection & Cryptographic Security

This project documents my technical workflow for securing sensitive information through encryption and data-at-rest protection. **I directed this process** to demonstrate how to transform plain-text data into encrypted formats, ensuring confidentiality and integrity within a Linux environment.

---

## 🎯 Project Objective
To implement robust data protection strategies using the **GnuPG (GPG)** suite, focusing on key generation, file encryption, and secure decryption workflows.

---

## 📑 Detailed Implementation Guide

### Phase 1: Cryptographic Key Management
**I began by establishing a secure identity** through the generation of a cryptographic key pair.
1.  **Entropy Generation:** Initialized the key generation process using `gpg --full-generate-key`.
2.  **Algorithm Selection:** Opted for **RSA and RSA** (default) with a 2048-bit key length to balance security and performance.
3.  **Identity Verification:** Configured the User ID (Name and Email) and set a secure passphrase to protect the private key.



### Phase 2: Securing Data (Encryption)
**I implemented a "Zero-Trust" approach** to sensitive files by ensuring they are never stored in plain-text.
1.  **Target Selection:** Identified the sensitive file (e.g., `sensitive_data.txt`).
2.  **Encryption Execution:** Used the public key to encrypt the file:
    ```bash
    gpg --encrypt --recipient "Your Name" sensitive_data.txt
    ```
3.  **Plain-text Sanitization:** After verifying the creation of the `.gpg` file, **I securely removed the original plain-text file** to prevent data leakage.

### Phase 3: Data Retrieval (Decryption)
**I validated the recovery process** to ensure data availability for authorized users.
1.  **Decryption Request:** Initiated the decryption of the `.gpg` file using the private key.
2.  **Authentication:** Provided the secure passphrase established in Phase 1 to unlock the secret key.
3.  **Integrity Check:** Verified that the decrypted output matched the original data perfectly, ensuring no corruption occurred during the cryptographic process.

> ![Encryption Workflow Placeholder](https://via.placeholder.com/800x200?text=GPG+Workflow:+Encryption+to+Decryption+Validation)

### Phase 4: Public Key Exporting
To facilitate secure communication with others, **I managed the distribution of public keys**.
1.  **Exporting:** Extracted the public key in an ASCII-armored format using `gpg --armor --export`.
2.  **Importing:** Demonstrated the ability to import a collaborator's public key to enable secure multi-user data exchange.

---

## 📊 Security Impact Matrix
| Feature | Implementation | Benefit |
| :--- | :--- | :--- |
| **Confidentiality** | GPG Encryption | Data is unreadable without the private key. |
| **Integrity** | Digital Signatures | Detects any unauthorized modification of files. |
| **Storage Security** | Data-at-Rest | Protects data even if the physical storage is compromised. |

---

## 🧠 Lessons Learned
By completing this lab, **I solidified my understanding of Asymmetric Encryption**. I learned that effective data protection relies as much on **Passphrase Management** and **Private Key Security** as it does on the mathematical strength of the encryption algorithm itself.

