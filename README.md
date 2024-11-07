<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>moghrf</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-size: cover;
            background-position: center;
            color: #271A17;
            text-align: center;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: rgba(242, 214, 214, 0.8); /* تأثير شفاف لتباين النص */
            padding: 20px;
            font-size: 2em;
        }
        section {
            margin: 20px;
            background-color: rgba(255, 255, 255, 0.8); /* تأثير شفاف على الأقسام */
            border-radius: 8px;
            padding: 20px;
        }
        .social-links {
            margin: 20px;
        }
        .social-links a {
            margin: 0 15px;
            text-decoration: none;
            font-size: 1.5em;
            color: #271A17;
        }
        .image-share {
            margin-top: 30px;
            padding: 10px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .emoji-btn {
            font-size: 2em;
            margin: 10px;
            cursor: pointer;
        }
        .emoji-count {
            font-size: 1.2em;
            margin-left: 5px;
        }
        .previous-images {
            margin-top: 20px;
        }
        .previous-images img {
            width: 100px;
            height: 100px;
            object-fit: cover;
            margin: 5px;
            border-radius: 8px;
        }
        .hidden-text {
            margin-top: 10px;
            font-size: 1.2em;
            background-color: #f0f0f0;
            padding: 10px;
            border-radius: 8px;
            display: none;
        }
        #backgroundUploadSection {
            margin: 20px;
            display: none;
        }
    </style>
</head>
<body>
    <header>
        Welcome to Moghrf's World!
    </header>

    <section>
        <h2>Moghrf's Socials</h2>
        <div class="social-links">
            <a href="https://www.instagram.com/ks._2sw?igsh=MWhqMzhjMHd0N3BqNw==" target="_blank">Instagram</a>
            <a href="https://tiktok.com/@reo4gfrn" target="_blank">TikTok</a>
        </div>
    </section>

    <section class="image-share">
        <h2>Something that Moghrf Wants to Share</h2>
        <div id="imageUploadSection" style="display: none;">
            <input type="file" id="uploadImage" accept="image/*">
        </div>
        <div id="imageDisplay"></div>
        <div>
            <button class="emoji-btn" onclick="addEmoji('🫶🏻')">🫶🏻 <span id="emoji1Count" class="emoji-count">0</span></button>
            <button class="emoji-btn" onclick="addEmoji('💟')">💟 <span id="emoji2Count" class="emoji-count">0</span></button>
            <button class="emoji-btn" onclick="addEmoji('🤨')">🤨 <span id="emoji3Count" class="emoji-count">0</span></button>
        </div>
        <div id="hiddenText" class="hidden-text">
            <textarea id="ownerText" rows="3" cols="30" placeholder="أكتب هنا ما تود أن يراه الجميع..."></textarea>
            <button onclick="saveOwnerText()">حفظ</button>
        </div>
    </section>

    <section class="previous-images">
        <h3>Your Previous Shared Images</h3>
        <div id="imageGallery"></div>
    </section>

    <!-- Section for uploading background image -->
    <section id="backgroundUploadSection">
        <h3>Change Background Image</h3>
        <input type="file" id="uploadBackground" accept="image/*">
    </section>

    <script>
        // Simulate a user check (replace with actual user validation)
        const isOwner = true;  // Set this to true if you're the owner, false otherwise

        // Show the image upload section and background change option only if the user is the owner
        if (isOwner) {
            document.getElementById("imageUploadSection").style.display = "block";
            document.getElementById("hiddenText").style.display = "block";  // Show the text area for the owner
            document.getElementById("backgroundUploadSection").style.display = "block"; // Show background change section
        }

        let emojiCounts = {
            '🫶🏻': 0,
            '💟': 0,
            '🤨': 0
        };

        let emojiToggled = {
            '🫶🏻': false,
            '💟': false,
            '🤨': false
        };

        let sharedImages = [];

        const uploadImage = document.getElementById("uploadImage");
        const imageDisplay = document.getElementById("imageDisplay");
        const imageGallery = document.getElementById("imageGallery");
        const uploadBackground = document.getElementById("uploadBackground");

        // Function to handle image upload and display
        uploadImage.addEventListener("change", (e) => {
            const reader = new FileReader();
            reader.onload = function(event) {
                imageDisplay.innerHTML = `<img src="${event.target.result}" style="max-width: 100%; height: auto; border-radius: 8px;">`;
                // Add image to shared images array
                sharedImages.unshift(event.target.result); // Add to the front
                if (sharedImages.length > 5) {
                    sharedImages.pop(); // Remove the last image if more than 5
                }
                updateImageGallery();
            };
            reader.readAsDataURL(e.target.files[0]);
        });

        // Function to update the image gallery
        function updateImageGallery() {
            imageGallery.innerHTML = "";
            sharedImages.forEach(image => {
                const imgElement = document.createElement("img");
                imgElement.src = image;
                imageGallery.appendChild(imgElement);
            });
        }

        // Function to handle emoji reactions
        function addEmoji(emoji) {
            // If emoji is already toggled (clicked previously), remove it
            if (emojiToggled[emoji]) {
                emojiCounts[emoji]--;
                emojiToggled[emoji] = false;
            } else {
                emojiCounts[emoji]++;
                emojiToggled[emoji] = true;
            }
            document.getElementById(`emoji${getEmojiIndex(emoji)}Count`).innerText = emojiCounts[emoji];
        }

        // Function to get the index of an emoji for the count display
        function getEmojiIndex(emoji) {
            if (emoji === '🫶🏻') return 1;
            if (emoji === '💟') return 2;
            if (emoji === '🤨') return 3;
        }

        // Function to save the owner's text
        function saveOwnerText() {
            const ownerText = document.getElementById("ownerText").value;
            alert("تم حفظ النص: " + ownerText);
        }

        // Function to change the background image
        uploadBackground.addEventListener("change", (e) => {
            const reader = new FileReader();
            reader.onload = function(event) {
                document.body.style.backgroundImage = `url('${event.target.result}')`;
            };
            reader.readAsDataURL(e.target.files[0]);
        });
    </script>
</body>
</html>
