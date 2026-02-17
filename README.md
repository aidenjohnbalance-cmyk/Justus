<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Just Us Link Fixer</title>
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<style>
  body {
    font-family: 'Roboto', sans-serif;
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    margin: 0;
    padding: 50px 20px;
    overflow-x: hidden;
  }

  h1 {
    font-family: 'Pacifico', cursive;
    font-size: 3em;
    color: #fff;
    text-shadow: 2px 2px 5px #0003;
    margin-bottom: 30px;
    text-align: center;
  }

  .social-logos {
    position: relative;
    width: 100%;
    max-width: 600px;
    height: 80px;
    margin-bottom: 40px;
  }

  .social-logos img {
    position: absolute;
    width: 60px;
    height: 60px;
    animation: floatSide 8s ease-in-out infinite alternate;
  }

  .social-logos img:nth-child(1) { left: 0; animation-delay: 0s; }
  .social-logos img:nth-child(2) { left: 80px; animation-delay: 2s; }
  .social-logos img:nth-child(3) { left: 160px; animation-delay: 4s; }
  .social-logos img:nth-child(4) { left: 240px; animation-delay: 6s; }

  @keyframes floatSide {
    0% { transform: translateX(0px); }
    50% { transform: translateX(20px); }
    100% { transform: translateX(0px); }
  }

  .link-box {
    background: rgba(255, 255, 255, 0.9);
    padding: 30px;
    border-radius: 20px;
    max-width: 500px;
    width: 100%;
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    text-align: center;
  }

  input[type="text"] {
    width: 90%;
    padding: 15px;
    margin-bottom: 20px;
    border-radius: 10px;
    border: none;
    font-size: 1em;
  }

  button {
    padding: 12px 25px;
    font-size: 1em;
    border: none;
    border-radius: 10px;
    background: #ff758c;
    color: white;
    cursor: pointer;
    transition: 0.3s;
    margin: 5px;
  }

  button:hover {
    background: #ff7eb3;
  }

  #fixedLink {
    margin-top: 20px;
    word-break: break-all;
    font-weight: bold;
    color: #333;
  }
</style>
</head>
<body>

<h1>Just Us Link Fixer</h1>

<div class="social-logos">
  <img src="https://upload.wikimedia.org/wikipedia/commons/0/09/YouTube_full-color_icon_%282017%29.svg" alt="YouTube">
  <img src="https://upload.wikimedia.org/wikipedia/commons/5/51/Facebook_f_logo_%282019%29.svg" alt="Facebook">
  <img src="https://upload.wikimedia.org/wikipedia/commons/e/e7/Instagram_logo_2016.svg" alt="Instagram">
  <img src="https://upload.wikimedia.org/wikipedia/en/a/a9/TikTok_logo.svg" alt="TikTok">
</div>

<div class="link-box">
  <input type="text" id="userLink" placeholder="Paste your link here...">
  <br>
  <button onclick="fixLink()">Fix Link</button>
  <div id="fixedLink"></div>
  <button id="copyBtn" onclick="copyLink()" style="display:none;">Copy to Clipboard</button>
</div>

<script>
function fixLink() {
  const link = document.getElementById('userLink').value.trim();
  if(!link) {
    alert('Please paste a link first!');
    return;
  }

  // Example "fix": just adds https://fixed.example.com/?url=encodedLink
  const fixed = 'https://fixed.example.com/?url=' + encodeURIComponent(link);

  const display = document.getElementById('fixedLink');
  display.textContent = fixed;

  const copyBtn = document.getElementById('copyBtn');
  copyBtn.style.display = 'inline-block';
}

function copyLink() {
  const fixed = document.getElementById('fixedLink').textContent;
  navigator.clipboard.writeText(fixed).then(() => {
    alert('Copied to clipboard!');
  });
}
</script>

</body>
</html>
