# 📉 Serverless Multi-Site Uptime Monitor

A free, self-hosted website monitoring tool that runs entirely on **GitHub Actions**.

This project can monitor **multiple websites** simultaneously. It checks availability every 10 minutes and uses smart alerting logic to prevent spam.

## ✨ Features

- **Multi-Site Monitoring:** Checks as many websites as you list in the configuration.
- **Zero Cost:** Runs 100% free on GitHub's infrastructure.
- **Smart Alerts:**
  - **Immediate Notification:** Alerts you the moment a site goes down.
  - **Anti-Spam Logic:** Only sends reminder emails every 8 hours during extended outages.
  - **Independent Timers:** If Site A goes down, and Site B goes down 2 hours later, both get their own independent alerts.
  - **Auto-Recovery:** Automatically closes the "Outage" ticket when the site comes back online.
- **Deep Inspection:** Checks page content for specific error keywords (e.g., "Bad Gateway").

## 🚀 How to Use

### 1. Fork this Repository

Click the **Fork** button at the top right to create your own copy.

### 2. Configure Secrets

To allow the bot to send emails, you need to provide Gmail credentials.

1.  Go to your repository **Settings** -> **Secrets and variables** -> **Actions**.
2.  Click **New repository secret** and add:
    - `MAIL_USERNAME`: Your Gmail address.
    - `MAIL_PASSWORD`: Your **Google App Password**.
      - _(Do not use your login password. Generate one at [Google Account > Security > App Passwords](https://myaccount.google.com/apppasswords))_

### 3. Add Your Websites

1.  Open `.github/workflows/uptime.yml`.
2.  Look for the `matrix:` section.
3.  Add your websites in this format:

    ```yaml
    - name: "My Personal Site"
      url: "[https://mysite.com](https://mysite.com)"
      id: "mysite"

    - name: "Client Project"
      url: "[https://client.com](https://client.com)"
      id: "client-project"
    ```

    _Note: The `id` must be unique for each site and should not contain spaces._

4.  Commit the changes.

## 📄 License

This project is licensed under the MIT License.
