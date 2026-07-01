# Arham · Job Apply

A lightweight, mobile-first Progressive Web App (PWA) designed to compile and send job applications instantly via Gmail. The app features dynamic templates, automatic clipboard actions, and native file attachment capabilities on mobile devices.

---

## 🚀 Key Features

*   **Dynamic Role Selection:** Easily switch between pre-configured templates for **Odoo Developer** and **Python Backend Engineer** positions.
*   **Automatic Resume Attachment:** Leverages the native **Web Share API** on mobile devices to open Gmail with the corresponding PDF resume (`arham_odoo_2y.pdf` or `arham_python_2y.pdf`) pre-attached.
*   **Smart Clipboard Sync:** Automatically copies the email body to your clipboard (as a backup) and the recipient's "To" address (so you can paste it directly when sharing).
*   **Desktop Fallback:** Automatically detects desktop browsers and insecure HTTP contexts, falling back to a clean `mailto:` composing workflow with instructions to attach files manually.
*   **Network-First Service Worker:** Uses a service worker (`sw.js`) with a network-first fallback caching strategy, ensuring your phone always loads the latest resume PDFs and template updates when online.

---

## 📁 File Structure

```text
├── CNAME                  # Custom domain configuration for GitHub Pages
├── index.html             # Core application layout, styling, and application logic
├── sw.js                  # PWA service worker (handles caching and network requests)
├── manifest.json          # PWA metadata configuration
├── arham_odoo_2y.pdf      # PDF resume for Odoo Developer applications
└── arham_python_2y.pdf    # PDF resume for Python Backend applications
```

---

## 📲 How to Use & Deploy

### 1. Git Deployment to GitHub Pages
To make the site available on your mobile phone, commit and push your changes to GitHub:

```bash
git add .
git commit -m "Update templates and service worker caching"
git push
```

### 2. Enabling SSL/HTTPS on GitHub Pages (Crucial)
Chrome requires a **Secure Context (HTTPS)** to allow file attachments and clipboard APIs. 
1. Open your repository on GitHub.
2. Go to **Settings** -> **Pages**.
3. Under the **Custom Domain** section, wait for the TLS certificate DNS check to succeed.
4. Once provisioned, check **Enforce HTTPS**.
5. Access your site securely at `https://jobapply.mohdarham.in/`.

---

## 🛠️ Local Mobile Testing & Debugging

If you are developing locally or running your page over standard `http://` (unsecure connection), Chrome disables the file-sharing APIs. Use one of these methods to test:

### Method A: Use Chrome Flags on Your Phone (Fastest)
1. Open Chrome on your Android device.
2. Navigate to: `chrome://flags/#unsafely-treat-insecure-origin-as-secure`
3. Enter your domain: `http://jobapply.mohdarham.in` (or local IP like `http://192.168.1.100:8000`).
4. Select **Enabled** and tap **Relaunch**.

### Method B: Use `ngrok` (Secure local tunnel)
1. Launch your local server on your computer:
   ```bash
   python3 -m http.server 8000
   ```
2. Start an `ngrok` secure tunnel:
   ```bash
   ngrok http 8000
   ```
3. Open the secure `https://...` link on your phone.

---

## 🧹 Clearing PWA Cache on Mobile
PWAs cache pages to work offline. If you deploy changes to your resume or HTML text and they aren't showing up on your phone:
1. Open Chrome on your phone and go to your site.
2. Tap the **Lock icon** (left of the URL) -> **Site settings**.
3. Tap **Clear & reset** to wipe the PWA cache.
4. Reload the page to fetch the latest changes.
