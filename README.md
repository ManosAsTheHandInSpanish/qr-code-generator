<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Générateur de QR Code pour URL</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        .container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            width: 300px;
        }
        input[type="url"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
        }
        button:hover {
            background-color: #45a049;
        }
        #qrcode {
            margin-top: 20px;
            text-align: center;
        }
        #error {
            color: red;
            margin-top: 10px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Générateur de QR Code pour URL</h1>
        <input type="url" id="url" placeholder="Entrez l'URL ici" required>
        <button onclick="generateQR()">Générer QR Code</button>
        <div id="error">Veuillez entrer une URL valide.</div>
        <div id="qrcode"></div>
    </div>

    <script>
        function generateQR() {
            var url = document.getElementById("url").value;
            var qrcodeContainer = document.getElementById("qrcode");
            var errorElement = document.getElementById("error");

            if (isValidURL(url)) {
                errorElement.style.display = "none";
                qrcodeContainer.innerHTML = "";
                new QRCode(qrcodeContainer, url);
            } else {
                errorElement.style.display = "block";
                qrcodeContainer.innerHTML = "";
            }
        }

        function isValidURL(string) {
            try {
                new URL(string);
                return true;
            } catch (_) {
                return false;
            }
        }
    </script>
</body>
</html>
