# 🔐 PDF Password Recovery Lab — John the Ripper

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red)
![Tool](https://img.shields.io/badge/Tool-John%20the%20Ripper-blue)
![Attack](https://img.shields.io/badge/Attack-Dictionary%20Attack-orange)
![Platform](https://img.shields.io/badge/Platform-Linux-black)
![Status](https://img.shields.io/badge/Status-Completed-success)

A hands-on cybersecurity lab demonstrating the analysis and password recovery of **three password-protected PDF files** using **John the Ripper**, `pdf2john`, dictionary attacks, the `rockyou.txt` wordlist, and NetworkWALKs online cybersecurity tools.

> ⚠️ **Educational Use Only:** This project was performed in an authorized cybersecurity/CTF lab environment. The techniques demonstrated here should only be used against files and systems for which you have explicit permission.

# 🔎 Overview

The purpose of this lab was to understand how password-protected PDF documents can be analyzed and how weak passwords can be recovered using **dictionary-based password attacks**.

Three encrypted PDF files were provided:

```text
My Locked PDF1.pdf
My Locked PDF2.pdf
My Locked PDF3.pdf
````

Each PDF was converted into a crackable hash format using `pdf2john`.

The extracted hashes were then attacked using **John the Ripper**.

Different wordlists were used depending on the target:

| PDF   | Wordlist                         |
| ----- | -------------------------------- |
| PDF 1 | John the Ripper default wordlist |
| PDF 2 | `rockyou.txt`                    |
| PDF 3 | `rockyou.txt`                    |

All three PDF passwords were successfully recovered.

The same general process was also tested using NetworkWALKs' online **Hash Calculator** and **Password Cracker** tools.

---

# 🎯 Objectives

The main objectives of this lab were:

* Understand PDF password protection.
* Extract password hashes from encrypted PDF files.
* Learn how `pdf2john` works.
* Use John the Ripper for dictionary attacks.
* Understand the importance of password wordlists.
* Use the `rockyou.txt` password dictionary.
* Verify recovered passwords.
* Compare local password cracking with online tools.
* Understand why weak passwords are vulnerable to dictionary attacks.
* Capture and verify the provided CTF/lab flags.

---

# 💻 Lab Environment

| Category               | Details                            |
| ---------------------- | ---------------------------------- |
| Operating System       | Linux                              |
| Shell                  | Bash                               |
| Password Recovery Tool | John the Ripper                    |
| Hash Extraction        | `pdf2john`                         |
| Attack Type            | Dictionary Attack                  |
| Wordlist 1             | John default wordlist              |
| Wordlist 2             | `rockyou.txt`                      |
| Target                 | Password-protected PDF files       |
| Environment            | Authorized Cybersecurity / CTF Lab |

---

# 🛠️ Tools Used

## John the Ripper

John the Ripper is an open-source password security auditing and password recovery tool.

In this lab it was used to perform dictionary-based attacks against the extracted PDF password hashes.

---

## pdf2john

`pdf2john` is used to extract password-related hash information from password-protected PDF documents so that John the Ripper can process them.

Example:

```bash
pdf2john "My Locked PDF1.pdf" > hash1.txt
```

---

## RockYou Wordlist

`rockyou.txt` is a commonly used password dictionary in cybersecurity labs and CTF environments.

It contains a large collection of commonly used passwords and is useful for demonstrating dictionary attacks.

---

## NetworkWALKs Hash Calculator

The NetworkWALKs Hash Calculator was used as an additional method of extracting a crackable hash from an encrypted PDF.

The tool identifies PDF encryption and generates a hash that can be used with password-cracking tools.

---

## NetworkWALKs Password Cracker

The NetworkWALKs Password Cracker was used to perform a dictionary attack against the extracted PDF hash.

The online result was compared with the password recovered using John the Ripper.

---

# 🧪 Attack Methodology

The overall methodology followed these steps:

```text
1. Identify encrypted PDF
          ↓
2. Extract PDF hash using pdf2john
          ↓
3. Save hash to a text file
          ↓
4. Select appropriate password wordlist
          ↓
5. Run John the Ripper
          ↓
6. Recover password
          ↓
7. Verify password using john --show
          ↓
8. Unlock/validate PDF
          ↓
9. Verify lab flag
```

---

# 🔓 PDF 1 - Default Wordlist

The first PDF was processed using `pdf2john`.

### Hash Extraction

```bash
pdf2john "My Locked PDF1.pdf" > hash1.txt
```

The resulting hash was stored in:

```text
hash1.txt
```

### Dictionary Attack

John the Ripper was then executed using its default wordlist:

```bash
john hash1.txt
```

John successfully identified the password.

### 🔑 Recovered Password

```text
good-luck
```

### Password Verification

The recovered password was verified using:

```bash
john --show hash1.txt
```

The output showed:

```text
My Locked PDF1.pdf:good-luck

1 password hash cracked, 0 left
```

### Result

```text
✅ PDF 1 successfully cracked
```

---

# 🔓 PDF 2 - RockYou Wordlist

The second PDF was processed using `pdf2john`.

### Hash Extraction

```bash
pdf2john "My Locked PDF2.pdf" > hash2.txt
```

### Dictionary Attack

The RockYou wordlist was used:

```bash
john --wordlist=rockyou.txt hash2.txt
```

John the Ripper successfully recovered the password.

### 🔑 Recovered Password

```text
password1
```

### Result

```text
✅ PDF 2 successfully cracked
```

---

# 🔓 PDF 3 - RockYou Wordlist

The third PDF was processed in the same way.

### Hash Extraction

```bash
pdf2john "My Locked PDF3.pdf" > hash3.txt
```

### Dictionary Attack

```bash
john --wordlist=rockyou.txt hash3.txt
```

The password was successfully recovered.

### 🔑 Recovered Password

```text
1qaz2wsx
```

### Result

```text
✅ PDF 3 successfully cracked
```

---

# 📊 Results

| Target               | Hash File   | Attack     | Wordlist      | Recovered Password | Status    |
| -------------------- | ----------- | ---------- | ------------- | ------------------ | --------- |
| `My Locked PDF1.pdf` | `hash1.txt` | Dictionary | Default John  | `good-luck`        | ✅ Cracked |
| `My Locked PDF2.pdf` | `hash2.txt` | Dictionary | `rockyou.txt` | `password1`           | ✅ Cracked |
| `My Locked PDF3.pdf` | `hash3.txt` | Dictionary | `rockyou.txt` | `1qaz2wsx`         | ✅ Cracked |

### Overall Success Rate

```text
3 / 3 PDFs successfully cracked

Success Rate: 100%
```

---

# 🌐 NetworkWALKs Hash Calculator

As an additional approach, the NetworkWALKs Hash Calculator was used to process the encrypted PDF.

The general workflow was:

```text
Encrypted PDF
     ↓
Upload PDF
     ↓
Detect PDF Encryption
     ↓
Extract Crackable Hash
     ↓
Copy / Download Hash
     ↓
Use Hash for Dictionary Attack
```

The tool generated a PDF hash compatible with password-cracking workflows.

### Observation

The hash extraction process demonstrates that the PDF password does not need to be directly visible or stored in plaintext.

Instead, password verification information can be extracted and tested against candidate passwords.

### Evidence

Screenshot:

```text
screenshots/NW-HashCalc.png
```

---

# 🌐 NetworkWALKs Password Cracker

The extracted PDF hash was also tested using the NetworkWALKs Password Cracker.

The tool performs a dictionary attack by testing candidate passwords from a wordlist against the supplied hash.

The demonstrated attack successfully recovered:

```text
good-luck
```

The result matched the password recovered locally using John the Ripper.

### Attack Process

```text
PDF Hash
   ↓
Select Wordlist
   ↓
Start Dictionary Attack
   ↓
Test Password Candidates
   ↓
Password Match
   ↓
Password Recovered
```

### Evidence

```text
screenshots/NW-PasswordCracker.png
```

---

# 🏆 Flags

The lab provided flag confirmation after successful password recovery.

## Flag 1

```text
nw{cybersecurity_flag_captured_2608}
```

---

## Flag 2

The supplied Flag 2 screenshot confirms the successful unlock visually, but the actual flag text is not readable in the provided evidence.

Therefore, the Flag 2 value has **not been guessed or fabricated**.

---

## Flag 3

```text
nw{networkwalks_flag_260821_1}
```
---

# 🔬 Technical Analysis

## Why Does the Attack Work?

A password-protected PDF uses encryption and password verification mechanisms to prevent unauthorized access.

A password-cracking tool does not simply "read" the password from the PDF.

Instead, the general process is:

```text
Candidate Password
        ↓
Password Processing
        ↓
Encryption / Verification Calculation
        ↓
Compare With Extracted PDF Hash
        ↓
       Match?
      /     \
    YES      NO
     ↓        ↓
 Password    Try Next
 Recovered   Candidate
```

When a candidate password produces the expected verification result, the password is considered successfully recovered.

---

# 🧠 Key Observations

## 1. Weak Passwords Can Be Recovered Quickly

The second PDF used:

```text
password1
```

This is an extremely common password and is therefore highly likely to exist in password dictionaries.

---

## 2. Keyboard Patterns Are Predictable

The third PDF used:

```text
1qaz2wsx
```

This follows a recognizable keyboard pattern.

Predictable patterns can make passwords more susceptible to dictionary and rule-based attacks.

---

## 3. Wordlists Are Important

The choice of wordlist has a major impact on dictionary attacks.

For example:

```text
Default John Wordlist
        ↓
       PDF 1
        ↓
    good-luck
```

Whereas:

```text
rockyou.txt
        ↓
   PDF 2 / PDF 3
        ↓
password1 / 1qaz2wsx
```

---

## 4. Online and Offline Approaches Can Follow the Same Concept

Both John the Ripper and the NetworkWALKs tools followed the same general concept:

```text
Extract Hash
     ↓
Obtain Wordlist
     ↓
Test Candidates
     ↓
Find Matching Password
```

The primary difference is where the password recovery process is performed.

---

# 🛡️ Security Implications

This lab demonstrates why weak passwords should not be used for protecting sensitive documents.

Passwords based on:

* Common words
* Common numeric combinations
* Keyboard patterns
* Predictable phrases
* Frequently leaked passwords
* Short passwords
* Reused passwords

are more susceptible to dictionary-based attacks.

A password-protected PDF should therefore use a strong, unique password.

---

# 🔐 Security Recommendations

For better PDF security:

### Use Long Passwords

Prefer long passwords or passphrases rather than short passwords.

### Avoid Common Passwords

Avoid passwords such as:

```text
password1
password
admin
qwerty
```

### Avoid Keyboard Patterns

Avoid predictable patterns such as:

```text
1qaz2wsx
qwerty123
```

### Use Unique Passwords

Do not reuse the same password for multiple files or services.

### Use a Password Manager

A password manager can generate and securely store strong random passwords.

### Use Strong Random Passwords

A randomly generated password provides substantially better resistance against dictionary attacks than a predictable password.

---

# 📚 Lessons Learned

Through this lab, the following cybersecurity concepts were practiced:

* PDF encryption analysis
* Hash extraction
* `pdf2john`
* John the Ripper
* Dictionary attacks
* Password wordlists
* RockYou wordlist
* Linux command-line operations
* Password verification
* CTF flag verification
* Online hash analysis
* Password security awareness

---

# 🧩 Commands Used

### Extract PDF Hash

```bash
pdf2john "My Locked PDF1.pdf" > hash1.txt
```

```bash
pdf2john "My Locked PDF2.pdf" > hash2.txt
```

```bash
pdf2john "My Locked PDF3.pdf" > hash3.txt
```

### John Default Wordlist

```bash
john hash1.txt
```

### John with RockYou

```bash
john --wordlist=rockyou.txt hash2.txt
```

```bash
john --wordlist=rockyou.txt hash3.txt
```

### Display Cracked Passwords

```bash
john --show hash1.txt
```

---

# 📈 Attack Summary

```text
                  PDF 1
                    │
                    ▼
              pdf2john
                    │
                    ▼
               hash1.txt
                    │
                    ▼
          Default John Wordlist
                    │
                    ▼
              good-luck
                    │
                    ▼
                 CRACKED


                  PDF 2
                    │
                    ▼
              pdf2john
                    │
                    ▼
               hash2.txt
                    │
                    ▼
              rockyou.txt
                    │
                    ▼
                password1
                    │
                    ▼
                 CRACKED


                  PDF 3
                    │
                    ▼
              pdf2john
                    │
                    ▼
               hash3.txt
                    │
                    ▼
              rockyou.txt
                    │
                    ▼
               1qaz2wsx
                    │
                    ▼
                 CRACKED
```

---

# ✅ Final Conclusion

This practical lab successfully demonstrated the recovery of passwords from three password-protected PDF documents using dictionary-based attacks.

The final recovered passwords were:

```text
PDF 1 → good-luck
PDF 2 → password1
PDF 3 → 1qaz2wsx
```

All three PDF password hashes were successfully recovered using John the Ripper.

The NetworkWALKs Hash Calculator and Password Cracker were additionally used to demonstrate an online implementation of the same general workflow.

The most important security takeaway from this exercise is:

> **A password-protected document is only as secure as the password protecting it.**

Using common, short, predictable, or dictionary-based passwords can significantly reduce the security of encrypted documents.

Strong, unique, and unpredictable passwords should always be used when protecting sensitive information.

---

# ⚖️ Ethical and Legal Disclaimer

This project is intended **only for authorized educational and cybersecurity testing purposes**.

The techniques demonstrated in this repository should only be used against:

* Your own files
* Authorized laboratory environments
* CTF challenges
* Systems where you have explicit permission to perform security testing

Unauthorized password recovery or access to protected files may be illegal.

The author assumes no responsibility for misuse of the information contained in this repository.

---

# ⭐ Skills Demonstrated

```text
Cybersecurity
├── Linux
├── PDF Security
├── Hash Extraction
├── John the Ripper
├── pdf2john
├── Dictionary Attacks
├── Password Wordlists
├── RockYou
├── Password Security
├── CTF Methodology
└── Security Documentation
```

---

## 📌 Project Status

**Completed ✅**

**3/3 PDF Passwords Recovered**

**Dictionary Attack Successfully Demonstrated**
