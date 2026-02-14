# Daily Retail & X Trends Routine

**Schedule: Every day at 01:00 AM UTC**

### Tasks:
1.  **Search Google Trends** for "US Retail" top searches over the last 24 hours.
    - Use headless browser (`openclaw` profile) to access `https://trends.google.com/trending?geo=US&hours=24`
    - If blocked by CAPTCHA, fallback to `web_fetch` on trends24.in
2.  **Search News** for the following 10 retailers (last 24 hours):
    - Kohl's, Target, Macy's, Dillard's, Belk, Bealls, Walmart, Ross, Burlington, TJ Maxx.
    - Use `web_fetch` on RetailDive: `https://www.retaildive.com/`
3.  **Search X Trends** using `bird` CLI:
    ```bash
    bird trending --json
    ```
    - This returns AI-curated trending topics with headlines, categories, and post counts.
    - Select top 10 most relevant trends for the dashboard.
4.  **Update `Project/Dashboard/RETAIL_HISTORY.md`**: Append a new section for the date with the findings.
5.  **Update `Project/Dashboard/retail_data.js`**: Add a new entry to the `retailHistory` object for the current date with the latest trends, news summaries, and the top 10 X trends. (Keep all previous dates in the file).
6.  **Gemini Image Generation**:
    *   **Check Existing Tabs**: Use `browser.tabs` to see if Gemini is already open. If yes, use `browser.focus` on the existing `targetId`. Only open a new tab if none exist.
    *   **Stable Handshake**: After opening/focusing, if `snapshot` returns "tab not found", **Wait 5 seconds and retry** on the same ID. Do not open a new URL until 3 retries fail.
    *   Open Google Gemini in Chrome Browser Relay.
    *   **Select the "玻璃產品生成" Gem** from the sidebar.
    *   **Switch the model to "Pro"**.
    *   Generate an image using the logic: 10 trends as custom-shaped molded glass ornaments, vibrant colors, #tag names printed underneath.
    *   **Verification**: Ensure the generation finished by checking for the image element before attempting download.
    *   **Click on the generated image** to open lightbox view.
    *   **Click "下載原尺寸圖片"** button to download the full-resolution image (NOT screenshot!).
    *   Find downloaded file in system Downloads folder and copy to `Project/Dashboard/Gemini Photo/`.
    *   **Teardown**: Close all Gemini tabs used during the session to keep the browser clean.
    *   **Upload the image to Google Drive** in the "x trend photo" folder using `gog`.
    *   **Capture the file ID** from the upload result and update `Project/Dashboard/retail_data.js` with the corresponding `imageUrl` (formatted for direct display: `https://drive.google.com/uc?export=view&id=FILE_ID`).
7.  **Push Updates**: Commit and push text-based changes (data and history) to GitHub. (Note: Images in `Gemini Photo/` are ignored by Git and will remain local only).
8.  **Final Notification**:
    *   Send a message to Joseph on Telegram: "Daily update complete. Dashboard is live at https://yorknty-natalie.github.io/joseph-dashboard/"
    *   **Send the latest image from `Project/Dashboard/Gemini Photo/`** to Joseph as a media attachment.
    *   Include the Google Drive link for the new image in the message.
