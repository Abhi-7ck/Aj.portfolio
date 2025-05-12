# Aj.portfolio
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Animated Portfolio</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            overflow: hidden;
        }
        .slide-container {
            position: relative;
            width: 100%;
            height: 100vh;
        }
        .slide {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 100%;
            opacity: 0;
            transition: all 0.8s ease-in-out;
        }
        .slide.active {
            left: 0;
            opacity: 1;
        }
        .slide.inactive {
            left: -100%;
            opacity: 0;
        }
        .nav-buttons {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 10px;
        }
        .nav-buttons button {
            padding: 10px 20px;
            border: none;
            background-color: #007BFF;
            color: white;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
        }
        .nav-buttons button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <h1>Welcome to My Portfolio</h1>
    <div class="slide-container">
        <!-- Slide 1 -->
        <div class="slide active">
            <object type="image/svg+xml" data="slide1.svg" aria-label="Slide 1"></object>
        </div>
        <!-- Slide 2 -->
        <div class="slide">
            <object type="image/svg+xml" data="slide2.svg" aria-label="Slide 2"></object>
        </div>
        <!-- Slide 3 -->
        <div class="slide">
            <object type="image/svg+xml" data="slide3.svg" aria-label="Slide 3"></object>
        </div>
    </div>
    <div class="nav-buttons">
        <button id="prev">Previous</button>
        <button id="next">Next</button>
    </div>

    <script>
        const slides = document.querySelectorAll('.slide');
        let currentSlide = 0;

        function showSlide(index) {
            slides.forEach((slide, i) => {
                slide.classList.remove('active', 'inactive');
                if (i === index) {
                    slide.classList.add('active');
                } else if (i < index) {
                    slide.classList.add('inactive');
                }
            });
        }

        document.getElementById('prev').addEventListener('click', () => {
            currentSlide = (currentSlide > 0) ? currentSlide - 1 : slides.length - 1;
            showSlide(currentSlide);
        });

        document.getElementById('next').addEventListener('click', () => {
            currentSlide = (currentSlide < slides.length - 1) ? currentSlide + 1 : 0;
            showSlide(currentSlide);
        });
    </script>
</body>
</html>
