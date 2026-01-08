# 📉 Serverless Uptime Monitor

A free, self-hosted website monitoring tool that runs entirely on **GitHub Actions**.

This project provides an automated workflow to check your website's availability every 10 minutes. It features smart alerting logic to prevent spam and can detect "soft failures" (like 502 Bad Gateway errors) that standard ping monitors often miss.

## ✨ Features

- **Zero Cost:** Runs 100% free on GitHub's infrastructure.
- **Smart Alerts:**
  - **Immediate Notification:** Alerts you the moment the site goes down.
  - **Anti-Spam Logic:** Only sends reminder emails every 8 hours during extended outages.
  - **Auto-Recovery:** Automatically closes the "Outage" ticket when the site comes back online.
- **Deep Inspection:** Checks page content for specific error keywords (e.g., "Bad Gateway"), catching errors where the server might still return a "200 OK" status code.
- **Redirect Support:** Automatically follows 301/302 redirects to check the final destination URL.

## 🚀 How to Use (3 Steps)

### 1. Fork this Repository

Click the **Fork** button at the top right of this page to create your own copy.

### 2. Configure Secrets

To allow the bot to send emails, you need to provide Gmail credentials.

1.  Go to your repository **Settings** -> **Secrets and variables** -> **Actions**.
2.  Click **New repository secret** and add the following:
    - `MAIL_USERNAME`: Your Gmail address (e.g., `youremail@gmail.com`).
    - `MAIL_PASSWORD`: Your **Google App Password**.
      - _Note: Do not use your login password. Go to [Google Account > Security > 2-Step Verification > App Passwords](https://myaccount.google.com/apppasswords) to generate one._

### 3. Set Your URL

1.  Open the file `.github/workflows/uptime.yml`.
2.  Edit the line under "CONFIGURATION":
    ```bash
    TARGET_URL="[https://your-website.com](https://your-website.com)"
    ```
3.  Commit the changes.

**That's it!** The monitor will now check your site every 10 minutes.

## 🛠 Tech Stack

- **GitHub Actions** (Scheduling & Execution)
- **Bash/Curl** (Network Requests & Content Parsing)
- **JavaScript/Node.js** (Logic & GitHub API Interaction)

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
