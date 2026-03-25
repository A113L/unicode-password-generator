# UNICODE Password Utility

A modern, cryptographically secure password generator built with HTML, Tailwind CSS, and JavaScript. This tool allows you to generate high-entropy passwords using customizable Unicode character sets, with real-time entropy calculation and security feedback.

---

## Features

- Cryptographically secure password generation using `window.crypto`
- Support for extensive Unicode character sets
- Real-time entropy calculation (bits)
- Strength rating based on entropy
- Adjustable password length (8–128)
- Bulk password generation (up to 10,000)
- Download generated passwords as `.txt`
- Copy-to-clipboard functionality
- Rate-limited generation to prevent abuse
- Interactive UI with Tailwind CSS
- Built-in Bash file encryption utility (OpenSSL + PBKDF2)

---

## Character Sets

Selectable character pools include:

- Latin (Standard)
- Latin (Extended)
- Cyrillic
- Asian (CJK, Hiragana, Katakana)
- Greek / Coptic / Hebrew
- Math & Symbols
- Box Drawing & Geometric
- Dingbats & Misc Symbols
- Emoji

At least one character set must be selected to generate passwords.

---

## Usage

1. Open the HTML file in your browser:

```bash
open index.html
```

2. Configure settings:
   - Password length
   - Number of passwords
   - Character sets

3. Click **Generate Passwords**

4. Copy or download results

---

## Entropy Calculation

Entropy is calculated using:

```
H = L * log2(N)
```

Where:
- `L` = password length
- `N` = character pool size

### Strength Ratings

| Entropy (bits) | Strength |
|----------------|---------|
| < 40           | Very Weak |
| 40–60          | Weak |
| 60–80          | Moderate |
| 80–100         | Strong |
| > 100          | Very Strong |

---

## Security Features

### Cryptographic Randomness

Uses:

```javascript
window.crypto.getRandomValues()
```

This ensures:
- Non-predictable output
- Suitable for high-security use cases

---

### Large Batch Handling

- Displays summary instead of rendering >25 passwords
- Prevents UI lag for large outputs

---

## Download Feature

- Exports generated passwords as `.txt`
- One password per line
- File name includes password count

---

## Built-in Bash Encryption Script

Includes a ready-to-use Bash script for encrypting files securely.

### Features

- AES-256-CBC encryption
- PBKDF2 key derivation
- Optional secure deletion using `shred`
- Interactive CLI interface

### Usage

```bash
chmod +x file_protector.sh
./file_protector.sh
```

### Requirements

- `openssl`
- `shred` (optional but recommended)

---

## UI Features

- Fully responsive layout
- Tailwind CSS styling
- Interactive sliders and inputs
- Copy-to-clipboard buttons
- Visual feedback and notifications

---

## File Structure

```
index.html   # Main application file
```

---

## Limitations

- Runs entirely client-side (no backend)
- Browser must support `window.crypto`
- Very large Unicode pools may affect performance slightly
- No persistent storage (by design for security)

---

## Security Recommendations

- Use a password manager such as:
  - KeePass
  - Bitwarden
- Enable Full Disk Encryption (FDE):
  - BitLocker (Windows)
  - FileVault (macOS)
  - LUKS (Linux)
- Never store passwords in plain text

---

## License

MIT License

---

## Disclaimer

This tool is intended for security research and personal use. Always follow best practices for password storage and management.
