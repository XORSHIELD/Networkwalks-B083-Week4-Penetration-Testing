# 🔒 Mediroza General Hospital — Black-Box Penetration Test

**A full black-box engagement tracing an attack chain from login bypass to a critical data exposure**

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Penetration%20Testing-red?style=flat-square" />
  <img src="https://img.shields.io/badge/Type-Black%20Box-black?style=flat-square" />
  <img src="https://img.shields.io/badge/Duration-5%20Days-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/SQL%20Injection-red?style=flat-square" />
  <img src="https://img.shields.io/badge/Vulnerability%20Assessment-orange?style=flat-square" />
  <br/>
  <img src="https://img.shields.io/badge/Skill-OSINT%20%26%20Recon-red?style=flat-square" />
  <img src="https://img.shields.io/badge/Authorization-Granted-black?style=flat-square" />
  <img src="https://img.shields.io/badge/Status-Completed-green?style=flat-square" />
  <img src="https://img.shields.io/badge/XorShield-black?style=flat-square" />
  <img src="https://img.shields.io/badge/Danjuma%20Yusuf%20Joseph-red?style=flat-square" />
</p>

<!-- ===================== TYPING SVG ========================= -->

<p align="center">
  <img
    src="https://readme-typing-svg.demolab.com/?font=JetBrains+Mono&weight=600&size=24&duration=2500&pause=1000&color=39FF14&center=true&vCenter=true&width=900&lines=Black-Box+Penetration+Testing;SQL+Injection+Exploitation;Authentication+Bypass;PDF+Password+Auditing;John+the+Ripper;QPDF+Document+Decryption;Metadata+Forensics;Database+Exposure+Analysis;Kali+Linux+Security+Lab;Ethical+Hacking"
    alt="Black-box penetration testing, SQL injection, and PDF password auditing"
  />
</p>

---

## 🔒 Project Overview

This project is a **black-box penetration test** against Mediroza General Hospital's patient portal, simulating an external attacker with no prior access or credentials.

The engagement traces a full attack chain — from open-source recon, through an authentication bypass, to a critical plaintext data exposure — and closes with a formal findings report for the client.

## 🎯 Objectives

- Perform reconnaissance against the target domain to identify hidden entry points.
- Test the patient login portal for authentication weaknesses.
- Identify and exploit any injection vulnerabilities to gain unauthorized access.
- Recover and analyze any protected files obtained during the assessment.
- Trace findings back to their root cause using metadata and server analysis.
- Document every vulnerability with risk ratings and remediation guidance.

## 🛡️ Scope & Rules of Engagement

| Item | Detail |
|---|---|
| 🎯 Target | `https://medirozahospital.com` |
| 🧩 Test Type | Full black-box penetration test |
| 📏 Boundaries | Target domain only — no social engineering, no denial-of-service |
| ✅ Authorization | Written authorization granted by the client |
| 🗓️ Timeline | 5 days |

> ⚠️ **Important:** This engagement was performed only against an authorized training target. These techniques must never be applied to any system without explicit written permission from the owner.

## 🏗️ Attack Chain Overview

<img width="1915" height="1005" alt="1  screenshot-robot" src="https://github.com/user-attachments/assets/c1781194-4a3f-46e6-8e8f-c9bf816bcd28" />


The assessment moved through four milestones: initial access, data extraction, deeper server-side exposure, and final reporting.

## ⚙️ Engagement Details

| 🧩 Component | 🧩 Detail |
|---|---|
| 💻 Target | medirozahospital.com |
| 🔴 Entry Point | `/patient/login.php` |
| 🐉 Attack Vector | SQL injection → authentication bypass |
| 🌐 Hidden Paths Found | `/patient/`, `/staff/`, `/old/` (via `robots.txt`) |
| 📮 Files Recovered | 3 encrypted patient PDF reports |
| 🌍 Final Exposure | Plaintext `.sql` database backup (`/old/`) |

## 📖 Methodology

### Milestone 1 — Initial Access

1. Checked `robots.txt` and found disallowed paths pointing to `/patient/` and a suspicious `/old/` folder.
2. Located the patient login page at `/patient/login.php`.
3. Tested for username enumeration — the app returned different error messages for an invalid username vs. an invalid password, confirming `admin` as a valid account.
4. Tested the login form for SQL injection with a single quote — the app returned a raw database error, confirming the field was injectable.
5. Bypassed authentication using a classic `admin' --` payload, logging in without a valid password.
6. Downloaded 3 confidential patient PDF reports from the portal.


<img width="1920" height="998" alt="2 screenshot-login-portal" src="https://github.com/user-attachments/assets/422f41fb-541e-4878-8c88-dc9c961a009f" />
<img width="1920" height="1011" alt="3 screenshot-SQL-Injection" src="https://github.com/user-attachments/assets/87553324-0847-490f-bc5f-833f744ad4f9" />
<img width="1920" height="1034" alt="4 screenshot-patient-report" src="https://github.com/user-attachments/assets/7f3dc241-10ad-4567-a83d-6a3a4cf33c3f" />



---

### Milestone 2 — Data Extraction

1. Extracted a password hash from each PDF using a hash calculator.
2. Cracked two of the three PDFs against a common-password wordlist.
3. The third PDF resisted the default wordlist — switched to a larger list (JTR), which succeeded.
4. Decrypted the third file with `qpdf` to produce a clean, unlocked copy for further analysis.
<img width="1920" height="1014" alt="11 screenshot-pdf3-password-hash" src="https://github.com/user-attachments/assets/c8318c17-303d-44e3-b5a5-0ae5a6fb0df4" />
<img width="1920" height="1009" alt="10 screenshot-pdf2-accessed" src="https://github.com/user-attachments/assets/d3af7a5a-75a4-43f6-b38e-40380aa3bde0" />
<img width="1920" height="1017" alt="9 screenshot-pdf2-password-cracked" src="https://github.com/user-attachments/assets/aa0c6c1b-6d89-45e5-9de2-27a399276ec9" />
<img width="1920" height="1018" alt="8 screenshot-pdf2-password-hash" src="https://github.com/user-attachments/assets/d04f0c7c-d2ef-4cdb-8e05-d0392b9e6c05" />
<img width="1920" height="1014" alt="7 screenshot-pdf1-accessed" src="https://github.com/user-attachments/assets/ab51df1f-a96e-4bb8-8880-1e2bfe09d478" />
<img width="1920" height="1015" alt="6 screenshot-pdf1-password-cracked" src="https://github.com/user-attachments/assets/f9ba4c54-b5e8-4ea8-91fc-1273e366d57c" />
<img width="1920" height="1020" alt="5 screenshot-pdf1-password-hash" src="https://github.com/user-attachments/assets/36fe46ae-7eaa-4e66-b6a1-c93ee5426be2" />

```
qpdf --password='<recovered password>' --decrypt patient_report_3.pdf report3_open.pdf
```
<img width="1920" height="1022" alt="13 screenshoot-report-password-cracked" src="https://github.com/user-attachments/assets/36345350-14d6-4166-91e3-102dea78ad00" />
<img width="1920" height="1012" alt="12 screenshot-report3-wordlist-exhauseted" src="https://github.com/user-attachments/assets/dae1ab17-5f09-4272-824f-cd232b5f6fbe" />
<img width="1920" height="1014" alt="11 screenshot-pdf3-password-hash" src="https://github.com/user-attachments/assets/f23da704-34af-45a3-ba72-2424e92c130d" />

---

### Milestone 3 — Deep Reconnaissance

1. Ran `exiftool` against the unlocked PDF and found an internal note in the metadata referencing a forgotten backup folder.
2. Cross-referenced this against the `/old/` path already flagged during initial recon.
3. Found directory listing enabled on `/old/`, exposing a full database backup file.
4. Downloaded the backup and parsed the `staff` and `shareholders` tables, revealing plaintext salary and shareholder data.
5. Traced the metadata author field back to a specific staff record, completing the chain of evidence.

<img width="1920" height="487" alt="14 screenshoot-exposed-old-directory" src="https://github.com/user-attachments/assets/5069a25d-9253-44de-8104-0b8b029fda67" />
<img width="1920" height="1009" alt="15 screenshoot" src="https://github.com/user-attachments/assets/744bef36-f38c-4d03-948b-e3554a14265e" />



---

### Milestone 4 — Reporting

Compiled all findings into a formal report covering an executive summary, scope and methodology, findings with proof of exploitation, risk ratings, and remediation guidance.

## 🔗 Evidence Correlation — Metadata to Database

The PDF metadata clue and the exposed database backup didn't stay separate findings — they connected into a single chain of evidence:

```
Patient Report 3 → PDF Metadata → Author: j.malik
        ↓
Staff Database → Jameel Malik, IT Systems Administrator
        ↓
PDF comment: "DB backup moved to /old before site migration"
        ↓
/old/ directory → mediroza_db_backup_2019.sql
```

The metadata's `Author: j.malik` field matched an identifier in the recovered staff table, tying the IT administrator directly to the note referencing the forgotten backup — confirming the full path from a single leaked document to a server-side data exposure.

<details>
<summary>📊 View recovered database contents (staff & shareholders)</summary>

**Staff table (excerpt)** — 30 employee records recovered, including names, job titles, departments, and monthly salaries. Sample:

| Name | Job Title | Department | Monthly Salary |
|---|---|---|---|
| Dr. Johan van der Merwe | Medical Director | Management | 160,000 |
| Sarah Botha | Chief Financial Officer | Finance | 152,000 |
| Dr. Rajesh Naidoo | Chief Pathologist | Diagnostics Lab | 138,000 |
| Jameel Malik | IT Systems Administrator | IT | 58,000 |
| Linda Fourie | Receptionist | Front Office | 19,000 |

**Shareholders table (excerpt)** — 10 shareholder records recovered, including ownership percentage and share class. Sample:

| Shareholder | Share % | Share Class |
|---|---|---|
| Dr. Rajesh Naidoo | 18% | Ordinary |
| Cedar Health Holdings (Pty) Ltd | 15% | Ordinary |
| Dr. Johan van der Merwe | 12% | Ordinary |
| Reddy Family Trust | 11% | Ordinary |

*Direct identifiers (ID numbers, phone numbers, emails) are withheld from this public write-up.*

</details>

## 💥 Security Impact

No single weakness here was catastrophic on its own — the impact came from chaining them together:

`Auth bypass` → `confidential reports exposed` → `weak PDF passwords` → `metadata leak` → `directory listing` → `full database backup exposed`

That chain turned a login-page flaw into full exposure of staff salaries and shareholder ownership data — information that should never have been reachable by an unauthenticated external attacker.

## 🐞 Findings Summary

| # | Vulnerability | Location | Risk |
|---|---|---|---|
| 1 | Username enumeration | `/patient/login.php` | Medium |
| 2 | SQL injection — authentication bypass | `/patient/login.php` | **Critical** |
| 3 | Sensitive PDFs exposed post-bypass | `/patient/reports/` | High |
| 4 | Weak, crackable PDF passwords | `patient_report_*.pdf` | High |
| 5 | Sensitive metadata left in PDF files | `patient_report_3.pdf` | Medium |
| 6 | Directory listing on forgotten backup folder | `/old/` | **Critical** |
| 7 | Plaintext salary & shareholder data exposed | `/old/mediroza_db_backup_2019.sql` | **Critical** |

## 🛠️ Recommendations

| Issue | Fix |
|---|---|
| SQL injection | Use parameterized queries / prepared statements |
| Username enumeration | Return a consistent error message regardless of which field is wrong |
| Exposed patient reports | Enforce proper access control — authorized users only |
| Weak PDF passwords | Require strong, unique passwords on encrypted documents |
| Metadata leakage | Sanitize/strip metadata before distributing files |
| Directory listing | Disable directory browsing on all web-accessible folders |
| Exposed backup | Remove backups from public web paths; store with encryption and access control |

## 🧩 Problems Encountered & Solutions

### Problem 1. Default Wordlist Failed on Report 3

The built-in password list exhausted without finding a match for the third encrypted PDF.

**Solution:** Switched to a larger wordlist (JTR), which successfully cracked the password on the next attempt — a reminder that a failed wordlist means trying a broader one, not giving up.

## 💡 What I Learned

- **Recon pays off later** — a path flagged early (`/old/`) only became relevant two milestones later, reinforcing the value of thorough initial reconnaissance.
- **Small input differences leak information** — username enumeration showed how subtle error-message inconsistencies can confirm valid accounts.
- **SQL injection remains highly impactful** — a single unescaped quote was enough to fully bypass authentication.
- **Metadata is an overlooked attack surface** — a file property revealed an internal note that redirected the entire assessment.
- **Wordlist strategy matters** — different passwords required different wordlists; no single list covers every case.
- **Findings must be chained, not listed in isolation** — connecting the metadata clue back to a named staff record made the final report far more convincing.

## ✅ Conclusion

This assessment identified several chained weaknesses in Mediroza Hospital's web application — most significantly, SQL injection leading to full authentication bypass, exposure of confidential patient reports, weak document encryption, metadata leakage, and an exposed database backup containing sensitive staff and shareholder data.

It demonstrates how several individually moderate issues can combine into a critical, high-impact exposure — the core reason defense-in-depth matters.

## 🔐 Security & Ethical Use

This engagement was performed strictly against an authorized training target for educational purposes. These techniques must never be applied to any system without explicit written permission from the owner.

## 🔗 Tools & Resources

- **Recon:** `curl`, `robots.txt` analysis
- **Exploitation:** Manual SQL injection
- **Password Cracking:** Hash extraction + wordlist-based cracking
- **File Analysis:** `qpdf`, `exiftool`
- **Data Retrieval:** `wget`

## 👤 Author

**Danjuma Yusuf Joseph (XorShield)**
Cybersecurity Professional `B083`

LinkedIn: https://www.linkedin.com/in/xorshield/

## 📌 Project Information

**Program Name:** Networkwalks | **Week:** 04 | **Project:** Black-Box Penetration Testing — Mediroza General Hospital | **Repository:** GitHub


