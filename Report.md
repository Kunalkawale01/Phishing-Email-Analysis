# Phishing Email Analysis Report
**Sample used:** `victim@example.com`

**Date of analysis:** 21/10/2025

## 1. Executive summary
The examined email contains multiple indicators commonly associated with phishing campaigns: sender address spoofing, mismatched link URLs, urgent language requesting credential verification, suspicious attachments, and several spelling/grammar mistakes. These traits strongly suggest the message is malicious and intended to harvest credentials or distribute malware.

## 2. Phishing indicators found (detailed)

1. **Suspicious sender address / spoofing**
- The `From:` name attempts to mimic a legitimate organization (e.g., "ACME Support") but the actual email is from a generic domain (e.g., `acme-support-notify@gmail.com`) or a look-alike domain using homoglyphs.
- Local-part or domain contains extra characters or digits (e.g., `support.acme123@mail.com`).

2. **Header discrepancies**
- Received path shows the message originated from an IP address unrelated to the legitimate vendor. (See `header_analysis.txt` for pasted analyzer output.)
- SPF / DKIM / DMARC failures or `neutral`/`softfail` results.

3. **Suspicious links**
- Visible link text claims to be `https://acme.com/login` but actual `href` points to a different domain or an IP address (e.g., `http://34.201.45.68/login` or `https://acme-login.verify-now.example.com`).
- Use of URL shorteners or redirection chains.

4. **Attachments**
- Presence of attachments with double extensions (`invoice.pdf.exe`) or Office documents with macros (`.doc` / `.docm`).
- Attachments requested to be opened for "verification" — classic vector for malware.

5. **Urgent or threatening language**
- Phrases like "Your account will be closed", "Immediate action required", or "Verify within 24 hours" to create panic and force hasty actions.

6. **Mismatched display name vs email address**
- The display name is reputable but the underlying address is unrelated.

7. **Spelling and grammar errors**
- Multiple typos, awkward phrasing, or oddly capitalized words.

8. **Request for sensitive information**
- The message asks to "confirm username and password" or to provide personal or financial details via an email or web form.

9. **Generic greeting**
- Use of "Dear Customer" instead of the recipient's real name (though not definitive, often present in phishing).


## 3. Risk assessment

- **Likelihood:** High — multiple high-confidence indicators present.
- **Impact if successful:** High — credential compromise, account takeover, or malware infection.
  
## 4. Recommended next steps

1. Do not click any links or open attachments.
2. Report the email to your IT/security team or to your email provider's abuse channel.
3. If any credentials were entered, reset them immediately from the legitimate website (not via links in the email) and enable MFA.
4. Submit the email headers and attachments (if safe) to a sandbox or malware analysis platform.
5. Block the sender domain and add appropriate mail rules; consider submitting the spam/phish sample to public repositories (PhishTank) or vendor blocklists.

## 5. Appendix: Examples and evidence

- **Sample email (redacted):** See `sample_email.txt`.
- **Header analysis notes:** See `header_analysis.txt`.
