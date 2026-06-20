# CodeAlpha_ImageGallery
Responsive Image Gallery with Lightbox and Navigation.


 <!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Image Gallery</title>

    <link rel="stylesheet" href="gallery.css">
</head>

<body>

    <h1>Image Gallery</h1>

    <!-- Gallery Container -->
    <div class="gallery">

        <img src="images/image1.avif" alt="" onclick="openLightbox(0)">
        <img src="images/image2.avif" alt="" onclick="openLightbox(1)">
        <img src="images/image3.jpeg" alt="" onclick="openLightbox(2)">
        <img src="images/image4.avif" alt="" onclick="openLightbox(3)">
        <img src="images/image5.avif" alt="" onclick="openLightbox(4)">
        <img src="images/image6.avif" alt="" onclick="openLightbox(5)">

    </div>

    <!-- Lightbox -->
    <div class="lightbox" id="lightbox">

        <span class="close" onclick="closeLightbox()">×</span>

        <button class="prev" onclick="changeImage(-1)">❮</button>

        <img id="lightbox-img">

        <button class="next" onclick="changeImage(1)">❯</button>

    </div>

    <script src="gallery.js"></script>

</body>

</html>



* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial;
    background: #b3b0b0;
    text-align: center;
    padding: 20px;
}

h1 {
    margin-bottom: 20px;
}

/* Gallery Layout */

.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 15px;
}

.gallery img {
    width: 100%;
    height: 250px;
    object-fit: cover;
    border-radius: 10px;
    cursor: pointer;
    transition: 0.4s;
}

/* Hover Effect */

.gallery img:hover {
    transform: scale(1.05);
}

/* Lightbox */

.lightbox {
    display: none;
    position: fixed;
    z-index: 1000;
    padding-top: 10px;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.9);
}

.lightbox img {
    width: 70%;
    height: 90%;
    max-width: 700px;
    border-radius: 10px;
}

/* Close Button */

.close {
    position: absolute;
    top: 20px;
    right: 40px;
    color: white;
    font-size: 40px;
    cursor: pointer;
}

/* Navigation Buttons */

.prev,
.next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255,255,255,0.2);
    color: white;
    border: none;
    padding: 15px;
    font-size: 30px;
    cursor: pointer;
}

.prev {
    left: 50px;
}

.next {
    right: 50px;
}

.prev:hover,
.next:hover {
    background: rgba(255,255,255,0.5);
}

/* Responsive */

@media(max-width: 768px) {

    .lightbox img {
        width: 90%;
    }

    .prev,
    .next {
        padding: 10px;
        font-size: 24px;
    }
}







const images = [
    "images/image1.avif",
    "images/image2.avif",
    "images/image3.jpeg",
    "images/image4.avif",
    "images/image5.avif",
    "images/image6.avif"
];

let currentIndex = 0;

const lightbox = document.getElementById("lightbox");
const lightboxImg = document.getElementById("lightbox-img");

function openLightbox(index) {

    currentIndex = index;

    lightbox.style.display = "block";

    lightboxImg.src = images[currentIndex];
}

function closeLightbox() {

    lightbox.style.display = "none";
}

function changeImage(direction) {

    currentIndex += direction;

    if (currentIndex < 0) {
        currentIndex = images.length - 1;
    }

    if (currentIndex >= images.length) {
        currentIndex = 0;
    }

    lightboxImg.src = images[currentIndex];
}
