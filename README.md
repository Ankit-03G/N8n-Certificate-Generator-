# AI Certificate Generator 🤖🎨

This project is an end-to-end, low-code solution for automatically generating beautiful, unique certificate designs using **n8n.io** and the **Google Gemini API**. The system is triggered by a simple web request and returns five unique certificate templates in **Fabric.js** JSON format, which can be rendered in any modern web browser.

The project includes both the powerful n8n automation workflow and a basic HTML/JavaScript front-end to interact with it and display the results.



---

## Features

* **AI-Powered Design:** Leverages the creative power of the Gemini API to generate unique themes, font pairings, and icon suggestions for certificates.
* **Dynamic Backgrounds:** Automatically fetches high-quality, relevant background images for each certificate, ensuring a visually appealing result.
* **Low-Code Backend:** The entire automation is built in n8n, making it easy to understand, modify, and extend without extensive coding.
* **Ready-to-Render Output:** Provides certificate designs in the Fabric.js JSON format, which can be loaded directly onto an HTML canvas.
* **Simple Web UI:** Includes a basic `index.html` file to demonstrate how to call the workflow and render the generated certificates.
* **Error-Proof Logic:** The n8n workflow is designed to be resilient, providing a default certificate design even if the AI service fails intermittently.

---

## How It Works

The system is split into two parts: the n8n backend and the HTML/JS frontend.

1.  A user enters a certificate category (e.g., "AI for Farmers") into the web UI and clicks "Generate".
2.  The browser sends a `POST` request to a unique **n8n Webhook URL**.
3.  The **Webhook Node** in n8n triggers the workflow.
4.  An **HTTP Request Node** fetches a beautiful, random background image from a reliable image service.
5.  A **Gemini Node** receives the category and the background image information and generates 5 unique design themes (fonts, icons, etc.) to complement them.
6.  A **Code (Function) Node** transforms the AI's creative ideas and the background image URL into a robust Fabric.js JSON structure.
7.  A **Respond to Webhook Node** sends the final array of 5 JSON templates back to the web UI.
8.  The JavaScript in the UI receives the JSON and uses the Fabric.js library to render the 5 unique certificates onto the screen.



---

## Prerequisites

Before you begin, you will need the following:

* **A running n8n instance:** This can be a free [n8n Cloud](https://n8n.cloud/) account or a self-hosted instance.
* **A Google AI (Gemini) API Key:** You can get a free key from [Google AI Studio](https://aistudio.google.com/). The free tier is more than sufficient for this project.

---

## Setup Instructions

Setting up this project is quick and easy.

### 1. Set Up the Backend (n8n)

1.  **Import the Workflow:**
    * Download the `workflow.json` file from this repository.
    * In your n8n canvas, go to **Import > From File** and select the `workflow.json` file. The entire workflow will appear on your canvas.

2.  **Add Your Credentials:**
    * In your n8n instance, go to the **Credentials** section.
    * Click **Add Credential**, search for **Google Gemini**, and select it.
    * Give it a name and paste in your API Key from the Google AI Studio.

3.  **Connect Your Credentials:**
    * On the n8n canvas, open the **`Message a model`** node.
    * In the **Credential to connect with** dropdown, select the credential you just created.
    * Click the **Save** button to save your workflow.

4.  **Get Your Production URL:**
    * Open the **`Webhook`** node (the first node).
    * Click on the **Production** tab and copy the URL. This is the URL your UI will call.
    * Finally, make sure your workflow is **Active** using the toggle at the top right of the screen.

### 2. Set Up the Frontend (UI)

1.  **Open the UI File:**
    * Open the `index.html` file in a text editor (like VS Code).

2.  **Add Your Webhook URL:**
    * Find the following line of JavaScript:
        ```javascript
        const n8nWebhookUrl = 'YOUR_N8N_WEBHOOK_URL_HERE';
        ```
    * Replace `YOUR_N8N_WEBHOOK_URL_HERE` with the **Production URL** you copied from your n8n Webhook node.
    * Save the file.

---

## Usage

1.  Make sure your n8n workflow is **Active**.
2.  Open the `index.html` file in a modern web browser (like Chrome or Firefox).
3.  Enter a category for the certificate you want to design.
4.  Click the **Generate** button.
5.  Wait a few moments, and the 5 AI-generated certificate designs will appear on the page!

---

## Project Structure
