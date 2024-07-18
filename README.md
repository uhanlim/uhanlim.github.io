<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>업로드 페이지</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 8px;
            background-color: #f9f9f9;
        }
        .header {
            font-size: 24px;
            margin-bottom: 20px;
        }
        .content {
            font-size: 18px;
            margin-bottom: 20px;
        }
        .upload-section {
            margin-bottom: 20px;
        }
        textarea, input[type="file"] {
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            padding: 10px 20px;
            border: none;
            background-color: #4CAF50;
            color: white;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">업로드 페이지</div>

        <div class="content">
            <div class="upload-section">
                <label for="menu">점심 메뉴:</label>
                <textarea id="menu" placeholder="여기에 점심 메뉴를 입력하세요..."></textarea>
                <button onclick="uploadText()">업로드</button>
            </div>

            <div class="upload-section">
                <label for="weather">날씨:</label>
                <input type="file" id="weather" accept="image/*">
                <button onclick="uploadImage()">업로드</button>
            </div>

            <div id="result"></div>
        </div>
    </div>

    <script>
        function uploadText() {
            const menuText = document.getElementById('menu').value;
            document.getElementById('result').innerHTML = `<h3>업로드된 점심 메뉴:</h3><p>${menuText}</p>`;
        }

        function uploadImage() {
            const fileInput = document.getElementById('weather');
            const file = fileInput.files[0];

            if (file) {
                const reader = new FileReader();
                reader.onload = function (e) {
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    img.style.maxWidth = '100%';
                    document.getElementById('result').innerHTML = '<h3>업로드된 날씨 이미지:</h3>';
                    document.getElementById('result').appendChild(img);
                };
                reader.readAsDataURL(file);
            } else {
                document.getElementById('result').innerHTML = '<p>이미지가 선택되지 않았습니다.</p>';
            }
        }
    </script>
</body>
</html>

