[portfolio.html](https://github.com/user-attachments/files/23187905/portfolio.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Md. Saif | Photography Portfolio</title>
<style>
    /* Reset and base styles */
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f9f9f9; color: #333; line-height: 1.6; }
    a { text-decoration: none; color: inherit; }
    button { cursor: pointer; }

    /* Header & Navigation */
    header {
        position: relative;
        height: 400px;
        display: flex;
        justify-content: center; /* horizontal center */
        align-items: center;     /* vertical center */
        text-align: center;
        background: #222;
        color: white;
    }

    header img.cover {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: -1;
        cursor: pointer;
        transition: 0.3s;
    }

    .profile-container {
        display: flex;
        flex-direction: column; /* stack profile photo and name vertically */
        align-items: center;
    }

    header img.profile {
        width: 160px;
        height: 160px;
        border-radius: 50%;
        border: 4px solid white;
        object-fit: cover;
        cursor: pointer;
        margin-bottom: 10px; /* space between photo and name */
        transition: transform 0.3s;
    }
    header img.profile:hover {
        transform: scale(1.05);
    }

    header h1 {
        font-size: 2rem;
        margin: 0;
    }

    nav {
        display: flex;
        justify-content: center;
        gap: 20px;
        background: #fff;
        padding: 10px 0;
        box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        position: sticky;
        top: 0;
        z-index: 10;
    }
    nav a {
        padding: 8px 15px;
        border-radius: 5px;
        transition: 0.3s;
    }
    nav a:hover {
        background: #333;
        color: white;
    }

    main {
        max-width: 1000px;
        margin: auto;
        padding: 100px 20px 50px;
    }

    section { margin-bottom: 50px; }
    section h2 {
        font-size: 1.8rem;
        margin-bottom: 15px;
        border-bottom: 2px solid #333;
        display: inline-block;
        padding-bottom: 5px;
    }

    .edit-btn {
        margin-top: 10px;
        padding: 5px 10px;
        background: #333;
        color: #fff;
        border: none;
        border-radius: 4px;
        font-size: 14px;
    }

    .bio p { font-size: 1rem; margin-top: 10px; }

    .gallery {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 15px;
    }
    .gallery img {
        width: 100%;
        height: 200px;
        object-fit: cover;
        border-radius: 8px;
        transition: transform 0.3s;
    }
    .gallery img:hover { transform: scale(1.05); }

    ul { list-style-type: disc; padding-left: 20px; }
    li { margin-bottom: 8px; }

    input[type="file"] { display: none; }

    @media(max-width: 600px){
        header h1 { font-size: 1.5rem; }
        nav { flex-wrap: wrap; gap: 10px; }
        .gallery img { height: 150px; }
    }
</style>
</head>
<body>

<!-- Header -->
<header>
    <img id="coverPhoto" class="cover" src="https://via.placeholder.com/1200x400?text=Cover+Photo" alt="Cover Photo">
    <input type="file" id="coverInput" accept="image/*">

    <div class="profile-container">
        <img id="profilePhoto" class="profile" src="https://via.placeholder.com/160?text=Profile" alt="Profile Photo">
        <input type="file" id="profileInput" accept="image/*">
        <h1 id="ownerName">Md. Saif</h1>
    </div>
</header>

<!-- Navigation -->
<nav>
    <a href="#about">About</a>
    <a href="#photography">Photography</a>
    <a href="#experience">Experience</a>
    <a href="#education">Education</a>
    <a href="#contact">Contact</a>
</nav>

<main>
    <!-- About Section -->
    <section id="about">
        <h2>About Me</h2>
        <p id="bioText">Welcome to my professional photography portfolio! I am passionate about capturing moments and sharing my journey in the photography club.</p>
        <button class="edit-btn" onclick="editText('bioText')">Edit Bio</button>
    </section>

    <!-- Photography Section -->
    <section id="photography">
        <h2>Photography Gallery</h2>
        <button class="edit-btn" onclick="document.getElementById('photoInput').click()">Upload Photo</button>
        <input type="file" id="photoInput" accept="image/*" multiple>
        <div class="gallery" id="gallery"></div>
    </section>

    <!-- Experience Section -->
    <section id="experience">
        <h2>Experience</h2>
        <ul id="experienceList">
            <li>"I spend my days capturing moments through my camera, focusing on portraits, landscapes, and candid shots. I have developed my skills by photographing events, nature, and everyday life, constantly experimenting with light, composition, and angles. My work reflects my passion for storytelling through photography and my commitment to improving with each shot."</li>
        </ul>
        <button class="edit-btn" onclick="addListItem('experienceList')">Add Experience</button>
    </section>

    <!-- Education Section -->
    <section id="education">
        <h2>Education</h2>
        <ul id="educationList">
            <li>High School - School Of Laureates International</li>
 	    <li>College - Kushtia Govt. Central College</li>
	    <li>University - American International University-Bangladesh (BSC in CSE)</li>
        </ul>
        <button class="edit-btn" onclick="addListItem('educationList')">Add Education</button>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <h2>Contact Info</h2>
        <ul id="contactList">
            <li>Email: mdsaif.05.007@gmail.com</li>
            <li>Phone: +8801728139990</li>
	    <li>Instagram: mr_acid_10 (https://www.instagram.com/mr_acid_10/)</li>
        </ul>
        <button class="edit-btn" onclick="addListItem('contactList')">Edit Contact Info</button>
    </section>
</main>

<script>
    // Profile Photo Change
    const profilePhoto = document.getElementById('profilePhoto');
    const profileInput = document.getElementById('profileInput');
    profilePhoto.addEventListener('click', () => profileInput.click());
    profileInput.addEventListener('change', function() {
        const file = this.files[0];
        if(file){
            profilePhoto.src = URL.createObjectURL(file);
        }
    });

    // Cover Photo Change
    const coverPhoto = document.getElementById('coverPhoto');
    const coverInput = document.getElementById('coverInput');
    coverPhoto.addEventListener('click', () => coverInput.click());
    coverInput.addEventListener('change', function() {
        const file = this.files[0];
        if(file){
            coverPhoto.src = URL.createObjectURL(file);
        }
    });

    // Edit text
    function editText(elementId){
        const element = document.getElementById(elementId);
        const newText = prompt("Edit your text:", element.innerText);
        if(newText !== null){
            element.innerText = newText;
        }
    }

    // Upload photos to gallery
    const photoInput = document.getElementById('photoInput');
    const gallery = document.getElementById('gallery');
    photoInput.addEventListener('change', function() {
        const files = Array.from(this.files);
        files.forEach(file => {
            const reader = new FileReader();
            reader.onload = function(e){
                const img = document.createElement('img');
                img.src = e.target.result;
                gallery.appendChild(img);
            }
            reader.readAsDataURL(file);
        });
    });

    // Add items to lists
    function addListItem(listId){
        const list = document.getElementById(listId);
        const newItem = prompt("Enter new item:");
        if(newItem){
            const li = document.createElement('li');
            li.innerText = newItem;
            list.appendChild(li);
        }
    }
</script>

</body>
</html>
