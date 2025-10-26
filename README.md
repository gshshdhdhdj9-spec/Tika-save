
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>TikDown Video Downloader</title>
  <style>
    body {
      background: #0a0f24;
      font-family: 'Poppins', sans-serif;
      color: #e8f0ff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      margin: 0;
      padding: 20px;
    }
    .container {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 16px;
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4);
      padding: 30px;
      max-width: 600px;
      width: 100%;
      text-align: center;
    }
    h1 {
      font-size: 26px;
      margin-bottom: 12px;
      background: linear-gradient(90deg, #00c6ff, #0072ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    p {
      font-size: 14px;
      color: #a8b6d4;
      margin-bottom: 24px;
    }
    input[type="text"] {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 10px;
      background: rgba(255, 255, 255, 0.1);
      color: white;
      font-size: 15px;
      margin-bottom: 12px;
      outline: none;
    }
    button {
      padding: 12px 20px;
      border: none;
      border-radius: 10px;
      background: linear-gradient(90deg, #00d4ff, #0066ff);
      color: white;
      font-weight: bold;
      cursor: pointer;
      margin: 6px;
      transition: 0.3s;
    }
    button:hover {
      transform: scale(1.05);
      background: linear-gradient(90deg, #00b0ff, #004cff);
    }
    video {
      width: 100%;
      border-radius: 10px;
      margin-top: 20px;
      display: none;
    }
    .footer {
      margin-top: 30px;
      color: #7d91b3;
      font-size: 13px;
    }
    .footer a {
      color: #00aaff;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>TikDown Downloader 🎬</h1>
    <p>Paste a valid direct video URL (MP4 link) or a demo link below and click download.</p>

    <input id="videoUrl" type="text" placeholder="Enter direct video URL (https://...)" />
    <input id="fileName" type="text" placeholder="Optional: file name (e.g., myvideo.mp4)" />

    <div>
      <button id="previewBtn">Preview</button>
      <button id="downloadBtn">Download</button>
    </div>

    <video id="videoPlayer" controls></video>

    <div class="footer">
      ⚠️ Use this only with authorized or public domain videos.<br>
      Created for educational use — <a href="#">TikDown Demo</a>
    </div>
  </div>

  <script>
    const videoUrlInput = document.getElementById("videoUrl");
    const fileNameInput = document.getElementById("fileName");
    const videoPlayer = document.getElementById("videoPlayer");
    const previewBtn = document.getElementById("previewBtn");
    const downloadBtn = document.getElementById("downloadBtn");

    // Preview button
    previewBtn.addEventListener("click", () => {
      const url = videoUrlInput.value.trim();
      if (!url.startsWith("http")) {
        alert("Enter a valid direct video URL (https://...)");
        return;
      }
      videoPlayer.src = url;
      videoPlayer.style.display = "block";
      videoPlayer.load();
      videoPlayer.play();
    });

    // Download button
    downloadBtn.addEventListener("click", () => {
      const url = videoUrlInput.value.trim();
      if (!url.startsWith("http")) {
        alert("Enter a valid direct video URL first!");
        return;
      }

      // Optional filename
      let fileName = fileNameInput.value.trim();
      if (!fileName) {
        fileName = "video.mp4";
      }

      // Start download
      const a = document.createElement("a");
      a.href = url;
      a.download = fileName;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    });
  </script>
</body>
</html>
