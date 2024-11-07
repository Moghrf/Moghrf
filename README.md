
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ghofrane ^°^</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8d7e1;
            color: #333;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #f0a6c1;
            text-align: center;
            padding: 20px;
        }
        header h1 {
            font-size: 50px;
            color: black;
        }
        section {
            margin: 20px;
        }
        h2 {
            font-size: 24px;
            color: black;
        }
        .social-links a {
            color: #f06292;
            margin: 10px;
            font-size: 18px;
            text-decoration: none;
        }
        .social-links a:hover {
            text-decoration: underline;
        }
        .latest-drawing img {
            width: 100%;
            max-width: 400px;
            border-radius: 10px;
            display: block;
            margin: 20px auto;
        }
        .message-form {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .message-form textarea {
            width: 100%;
            height: 150px;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        .message-form button {
            background-color: #f06292;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
        }
        .message-form button:hover {
            background-color: #f48fb1;
        }
        .upload-section {
            text-align: center;
            margin: 20px 0;
        }
        .upload-section input[type="file"] {
            display: none;
        }
        .upload-section label {
            background-color: #f06292;
            color: white;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
        }
        .upload-section label:hover {
            background-color: #f48fb1;
        }
        .color-picker {
            margin: 20px;
            text-align: center;
        }
        .color-picker label {
            font-size: 18px;
            margin-right: 10px;
        }
        .color-picker input {
            width: 100px;
            height: 30px;
        }
    </style>
</head>
<body>

<header>
    <h1>ghofrane ^°^</h1>
</header>

<section id="social-media">
    <h2>moghrf' socials</h2>
    <div class="social-links">
        <a href="https://www.instagram.com/ks._2sw?igsh=MWhqMzhjMHd0N3BqNw==" target="_blank">حساب انستغرام</a>
        <a href="https://tiktok.com/@reo4gfrn" target="_blank">حساب تيك توك</a>
    </div>
</section>

<section id="latest-drawing">
    <h2>moghrf's last drawing</h2>
    <div class="latest-drawing">
        <img src="path/to/your/latest-drawing.jpg" alt="آخر رسمه غفران" id="drawingImage">
        <!-- Replace "path/to/your/latest-drawing.jpg" with the actual image path -->
    </div>
    <div class="upload-section">
        <h3>ارفع الصورة</h3>
        <!-- Button that allows the user to select an image -->
        <label for="imageUpload">اختار صورة</label>
        <input type="file" id="imageUpload" accept="image/*" onchange="uploadImage()">
    </div>
</section>

<section id="message">
    <h2>something you want to say</h2>
    <div class="message-form">
        <form action="mailto:zae098.com@gmail.com" method="POST" enctype="multipart/form-data">
            <textarea name="message" placeholder="اكتب هنا رسالتك..."></textarea>
            <button type="submit">إرسال</button>
        </form>
    </div>
</section>

<section id="color-picker" class="color-picker">
    <h2>تغيير ألوان الموقع</h2>
    <label for="headerColor">لون العنوان:</label>
    <input type="color" id="headerColor" onchange="changeHeaderColor(this.value)">
    <br><br>
    <label for="backgroundColor">لون الخلفية:</label>
    <input type="color" id="backgroundColor" onchange="changeBackgroundColor(this.value)">
    <br><br>
    <label for="buttonColor">لون الأزرار:</label>
    <input type="color" id="buttonColor" onchange="changeButtonColor(this.value)">
</section>

<script>
    // Function to upload image
    function uploadImage() {
        const fileInput = document.getElementById('imageUpload');
        const image = fileInput.files[0];
        if (image) {
            const reader = new FileReader();
            reader.onload = function(e) {
                document.getElementById('drawingImage').src = e.target.result;
            }
            reader.readAsDataURL(image);
        }
    }

    // Change header color
    function changeHeaderColor(color) {
        document.querySelector('header').style.backgroundColor = color;
    }

    // Change background color
    function changeBackgroundColor(color) {
        document.body.style.backgroundColor = color;
    }

    // Change button color
    function changeButtonColor(color) {
        const buttons = document.querySelectorAll('button');
        buttons.forEach(button => {
            button.style.backgroundColor = color;
        });
    }
</script>

</body>
</html>
<!--
**Moghrf/Moghrf** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
