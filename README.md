%%html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Proposal</title>
    <style>
        body {
            background-image: url('http://googleusercontent.com/image_collection/image_retrieval/8844835697228833989'); /* Wedding hall image */
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            text-align: center;
            backdrop-filter: blur(4px) brightness(0.8);
            transition: backdrop-filter 1s ease;
        }
        .card {
            background: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
            max-width: 450px;
            width: 90%;
            position: relative;
            z-index: 1;
        }
        .gif-img {
            width: 160px;
            height: auto;
            margin: 15px auto; /* Centered horizontally */
            display: block; /* Ensures margin auto works */
            border-radius: 15px;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }
        .gif-img.loaded {
            opacity: 1;
        }
        .line {
            display: block;
            margin: 15px 0;
            font-size: 1.15rem;
            color: #2c3e50;
            line-height: 1.5;
        }
        .hindi-line {
            font-weight: bold;
            color: #c2185b;
            font-size: 1.25rem;
            border-bottom: 2px dashed #ff80b3;
            padding-bottom: 5px;
        }
        .header-msg {
            margin-top: 30px;
            color: #ff4081;
            font-weight: bold;
            font-size: 1.4rem;
            letter-spacing: 1px;
        }
        .marry-me {
            font-size: 10px;
            text-transform: uppercase;
            margin-bottom: 25px;
            display: block;
            color: #7f8c8d;
            letter-spacing: 2px;
        }
        .btn-container {
            display: flex;
            flex-direction: column;
            gap: 12px;
            align-items: center;
            margin-top: 25px; /* Added margin for spacing */
        }
        button {
            width: 220px;
            padding: 14px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            font-size: 1rem;
            transition: all 0.3s ease;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }
        .yes-btn { background-color: #ff4d94; color: white; }
        .maybe-btn { background-color: #ff80b3; color: white; }
        .anyways-btn { background-color: #ffb3d1; color: white; }

        button:hover {
            transform: translateY(-3px) scale(1.03);
            box-shadow: 0 6px 15px rgba(255, 77, 148, 0.4);
        }

        #final-msg {
            color: #d81b60;
            font-size: 1.4rem;
            font-weight: bold;
            line-height: 1.6;
        }

        /* Slide specific styles */
        .slide {
            display: none; /* All slides hidden by default */
        }
        .slide.active {
            display: block; /* Only active slide is shown */
        }
    </style>
</head>
<body>

<div class="card" id="mainCard">
    <!-- Slide 1 -->
    <div class="slide active" id="slide-0">
        <span class="line">I was going to wait for the right moment to propose… but then I realized you are the right moment. So here I am 😌</span>
        <img src="http://googleusercontent.com/image_collection/image_retrieval/1399072769122713693" class="gif-img" alt="Sobbing" onload="this.classList.add('loaded')">
        <div class="btn-container">
            <button class="yes-btn" onclick="nextSlide()">YES</button>
            <button class="maybe-btn" onclick="nextSlide()">MAYBE YES</button>
            <button class="anyways-btn" onclick="nextSlide()">ANYWAYS YES</button>
        </div>
    </div>

    <!-- Slide 2 -->
    <div class="slide" id="slide-1">
        <span class="line">Roses are red, today’s the day— <br> Be mine forever? I promise I’ll make you smile every single way 💖</span>
        <img src="http://googleusercontent.com/image_collection/image_retrieval/15358379031873569905" class="gif-img" alt="Cat" onload="this.classList.add('loaded')">
        <div class="btn-container">
            <button class="yes-btn" onclick="nextSlide()">YES</button>
            <button class="maybe-btn" onclick="nextSlide()">MAYBE YES</button>
            <button class="anyways-btn" onclick="nextSlide()">ANYWAYS YES</button>
        </div>
    </div>

    <!-- Slide 3 (Final proposal slide) -->
    <div class="slide" id="slide-2">
        <span class="line hindi-line">tum sirf mere ho tumhare bubu bhi aur tumahri pp bhi samze kya</span>
        <img src="http://googleusercontent.com/image_collection/image_retrieval/18301618982902913841" class="gif-img" alt="Wolf" onload="this.classList.add('loaded')">
        <div class="header-msg">HAPPY PROPOSE DAY I LOVE YOU BABE</div>
        <span class="marry-me">will you marry me (trying)</span>
        <div class="btn-container">
            <button class="yes-btn" onclick="celebrate()">YES</button>
            <button class="maybe-btn" onclick="celebrate()">MAYBE YES</button>
            <button class="anyways-btn" onclick="celebrate()">ANYWAYS YES</button>
        </div>
    </div>

</div>

<script>
    let currentSlideIndex = 0;
    const slides = document.querySelectorAll('.slide');
    const totalSlides = slides.length;

    function showSlide(index) {
        slides.forEach((slide, i) => {
            if (i === index) {
                slide.classList.add('active');
            } else {
                slide.classList.remove('active');
            }
        });
        // Ensure image visibility is handled after slide display
        const currentGif = slides[index].querySelector('.gif-img');
        if (currentGif) {
            // Add 'loaded' class after a short delay to ensure the display property has taken effect
            // This ensures the transition effect works correctly even if the image is already loaded in cache.
            setTimeout(() => {
                currentGif.classList.add('loaded');
            }, 50);
        }
    }

    function nextSlide() {
        currentSlideIndex++;
        if (currentSlideIndex < totalSlides) {
            showSlide(currentSlideIndex);
        } else {
            // If nextSlide is called on the last slide, it should trigger celebrate.
            // This condition is a safeguard, as the last slide's buttons directly call celebrate().
            celebrate();
        }
    }

    function celebrate() {
        const card = document.getElementById('mainCard');
        document.body.style.backdropFilter = "blur(0px) brightness(1.1)";

        card.innerHTML = `
            <h1 style="color: #ff4d94; font-size: 2.5rem; margin-bottom: 10px;">SUCCESS! 💍</h1>
            <img src="http://googleusercontent.com/image_collection/image_retrieval/15358379031873569905" style="width:250px; border-radius: 20px; box-shadow: 0 10px 20px rgba(0,0,0,0.2); margin: 15px auto; display: block;">
            <div id="final-msg" style="margin-top: 25px;">
                "Now you have to give me <br>
                <strong>PP and Bubu forever</strong> to me!" ❤️
            </div>
            <p style="margin-top: 15px; color: #555;">(No refunds, no exchanges, you're mine now!)</p>
        `;
    }

    // Initialize: show the first slide when the page loads
    document.addEventListener('DOMContentLoaded', () => {
        showSlide(currentSlideIndex);
    });
</script>

</body>
</html>
