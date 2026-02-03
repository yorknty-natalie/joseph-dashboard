# Daily Retail & X Trends Routine

**Schedule: Every day at 01:00 AM UTC**

### Tasks:
1.  **Search Google Trends** for "US Retail" top searches over the last 24 hours.
2.  **Search News** for the following 10 retailers (last 24 hours):
    - Kohl's, Target, Macy's, Dillard's, Belk, Bealls, Walmart, Ross, Burlington, TJ Maxx.
3.  **Search X Trends** for the top 10 sustained topics over the last 48 hours.
4.  **Update `Project/Dashboard/RETAIL_HISTORY.md`**: Append a new section for the date with the findings.
5.  **Update `Project/Dashboard/retail_data.js`**: Add a new entry to the `retailHistory` object for the current date with the latest trends, news summaries, and the top 10 X trends. (Keep all previous dates in the file).
6.  **Gemini Image Generation**:
    *   Open Google Gemini in Chrome.
    *   **Select the "玻璃產品生成" Gem** from the sidebar.
    *   **Switch the model to "Pro"**.
    *   Generate an image using the logic: 10 trends as custom-shaped molded glass ornaments, vibrant colors, #tag names printed underneath.
    *   Download the generated image.
    *   Move the downloaded image to `Project/Dashboard/Gemini Photo/`.
    *   **Upload the image to Google Drive** in the "image tracker" folder (inside "Natalie Assistant") using `gog`.
    *   **Capture the file ID** from the upload result and update `Project/Dashboard/retail_data.js` with the corresponding `imageUrl` (formatted for direct display: `https://drive.google.com/uc?export=view&id=FILE_ID`).
7.  **Push Updates**: Commit and push text-based changes (data and history) to GitHub. (Note: Images in `Gemini Photo/` are ignored by Git and will remain local only).
8.  **Final Notification**:
    *   Send a message to Joseph on Telegram: "Daily update complete. Dashboard is live at https://yorknty-natalie.github.io/joseph-dashboard/"
    *   **Send the latest image from `Project/Dashboard/Gemini Photo/`** to Joseph as a media attachment.
    *   Include the Google Drive link for the new image in the message.
