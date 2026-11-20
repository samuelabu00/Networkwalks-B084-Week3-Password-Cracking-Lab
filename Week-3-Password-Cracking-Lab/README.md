# Week 3 — Password Cracking Lab

## Lab Details

- **Repository:** `samuelabu00/Networkwalks-B082-Week3-Password-Cracking-Lab`
- **Week:** 3
- **Topic:** Password cracking and PDF password recovery
- **Attack type:** Dictionary attack
- **Environment:** Authorized cybersecurity lab / CTF

## Password Recovery Results

| Target | Password | Method / Wordlist | Status |
|---|---|---|---|
| PDF 1 | `good-luck` | John the Ripper default wordlist | Recovered |
| PDF 2 | `password1` | `rockyou.txt` | Recovered |
| PDF 3 | `1qaz2wsx` | `rockyou.txt` | Recovered |

## Tools Used

- John the Ripper
- `pdf2john`
- RockYou password wordlist
- NetworkWALKs Hash Calculator
- NetworkWALKs Password Cracker

## Workflow

1. Identify the password-protected PDF.
2. Extract its crackable hash with `pdf2john` or the NetworkWALKs Hash Calculator.
3. Run a dictionary attack with John the Ripper or the NetworkWALKs Password Cracker.
4. Test candidate passwords against the extracted hash.
5. Verify the matching password and unlock the PDF.
6. Capture the lab flags and document the results.

## Captured Flags

- `nw{cybersecurity_flag_captured_2608}`
- `nw{networkwalks_persistence_itr_270521}`

## Evidence Summary

The provided screenshots show:

1. A PDF hash entered into the NetworkWALKs password-cracker interface.
2. The password `password1` recovered successfully.
3. The PDF flag `nw{cybersecurity_flag_captured_2608}`.
4. A persistence-related completion screen with `nw{networkwalks_persistence_itr_270521}`.

## Key Findings

- Common passwords can be recovered quickly with dictionary attacks.
- Keyboard-pattern passwords such as `1qaz2wsx` are predictable and vulnerable.
- A strong PDF password should be long, unique, unpredictable, and stored securely.
- John the Ripper and the online NetworkWALKs tools demonstrate the same general password-verification workflow.

## Ethical Use

This exercise was completed in an authorized cybersecurity lab or CTF environment. Password recovery techniques should only be used on files and systems that you own or have explicit permission to test.

## Commands

```bash
pdf2john "My Locked PDF1.pdf" > hash1.txt
john hash1.txt

pdf2john "My Locked PDF2.pdf" > hash2.txt
john --wordlist=rockyou.txt hash2.txt

pdf2john "My Locked PDF3.pdf" > hash3.txt
john --wordlist=rockyou.txt hash3.txt

john --show hash1.txt
```

## Result

```text
3 / 3 PDFs successfully cracked
Success rate: 100%
```
