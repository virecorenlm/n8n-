# 🤖 n8n Workflow Collection

A collection of ready-to-use n8n workflow JSON files. Download any workflow and import it directly into your n8n instance in minutes.

---

## 📥 How to Import a Workflow

### Step 1 — Download the JSON File

1. Browse the repository and open the workflow folder or file you want.
2. Click on the `.json` file to open it.
3. Click the **Raw** button in the top-right corner of the file preview.
4. Right-click anywhere on the page and select **Save As...** (or press `Ctrl+S` / `Cmd+S`).
5. Save the file somewhere easy to find (e.g. your Downloads folder). Make sure the file ends in `.json`.

> **Tip:** You can also click the download icon (⬇) on the Raw page in some browsers.

---

### Step 2 — Open n8n

1. Open your n8n instance in your browser.
   - If you're on n8n Cloud, go to [app.n8n.cloud](https://app.n8n.cloud)
   - If you're self-hosted, go to your local URL (e.g. `http://localhost:5678`)
2. Log in if prompted.

---

### Step 3 — Import the Workflow

1. From the **n8n dashboard**, click the **"+"** button or **"New Workflow"** to open the workflow editor.
2. In the top-right corner of the editor, click the **three-dot menu (⋯)** or the **"..."** icon.
3. Select **"Import from File..."** from the dropdown.
4. In the file picker, navigate to where you saved the `.json` file and select it.
5. The workflow will load automatically in the editor.

---

### Step 4 — Configure Credentials

Most workflows use external services (APIs, databases, etc.) that require credentials.

1. Look for any nodes with a **red warning icon** — these need credentials set up.
2. Click on the node to open its settings.
3. Click the **"Credential"** dropdown and select **"Create New"** or choose an existing one.
4. Enter your API keys, tokens, or login details as required.
5. Click **Save**.

Repeat this for each node that requires credentials.

---

### Step 5 — Activate and Test

1. Click **"Save"** in the top-right to save the workflow to your n8n instance.
2. Click **"Execute Workflow"** (▶) to do a manual test run and make sure everything works.
3. Once you're happy with it, toggle the **"Active"** switch in the top-right to turn on automatic execution.

---

## 🗂️ Workflows

| Workflow | Description |
|----------|-------------|
| *(Add your workflows here)* | *(Brief description)* |

---

## 🛠️ Requirements

- [n8n](https://n8n.io/) — self-hosted or cloud
- Relevant API credentials for the services used in each workflow

---

## 🙋 Need Help?

- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community Forum](https://community.n8n.io/)

---

> Made with ❤️ — feel free to fork, modify, and build on these workflows.
