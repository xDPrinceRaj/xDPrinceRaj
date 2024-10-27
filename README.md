<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prince Raj - Developer & Tech Enthusiast</title>
    <style>
        /* Reset and Basic Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        /* Gradient Background */
        
        body {
            height: 100vh;
            overflow-x: hidden;
            background: linear-gradient(135deg, #091236, #1e215d, #5b247a);
            background-size: 300% 300%;
            animation: gradientBackground 15s ease infinite;
        }

        @keyframes gradientBackground {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Navbar */
        nav {
            width: 100%;
            padding: 20px;
            position: fixed;
            top: 0;
            display: flex;
            justify-content: center;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(10px);
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
        }

        nav a {
            color: #ffffff;
            text-decoration: none;
            padding: 15px 25px;
            font-weight: bold;
            border-radius: 5px;
            transition: background 0.3s ease;
        }

        nav a:hover {
            background: rgba(0, 243, 255, 0.3);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: #00f3ff;
        }

        .hero h1 {
            font-size: 4.5rem;
            margin-bottom: 20px;
            text-shadow: 0 0 10px rgba(0, 243, 255, 0.5);
        }

        .hero p {
            font-size: 1.8rem;
            margin-bottom: 30px;
            border-right: 2px solid #00f3ff;
            white-space: nowrap;
            overflow: hidden;
            animation: typing 4s steps(30) infinite;
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 22ch; }
        }

        .hero button {
            padding: 12px 30px;
            font-size: 1.2rem;
            border: 2px solid #00f3ff;
            color: #00f3ff;
            background: transparent;
            cursor: pointer;
            border-radius: 5px;
            transition: background 0.3s, color 0.3s;
        }

        .hero button:hover {
            background: #00f3ff;
            color: #091236;
        }

        /* Section Styles */
        section {
            padding: 80px 20px;
            color: #ffffff;
            text-align: center;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 1s ease, transform 1s ease;
        }

        section.show {
            opacity: 1;
            transform: translateY(0);
        }

        /* Portfolio Item */
        .portfolio-item {
            background: rgba(30, 33, 93, 0.9);
            padding: 15px;
            margin: 10px;
            border-radius: 10px;
            display: inline-block;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .portfolio-item:hover {
            transform: scale(1.05);
            background: rgba(0, 243, 255, 0.5);
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
            z-index: 1001;
        }

        .modal-content {
            background: #1e215d;
            color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            max-width: 500px;
            text-align: center;
        }

        .close-btn {
            cursor: pointer;
            color: #00f3ff;
            font-size: 1.5rem;
            margin-top: 10px;
        }

        /* Contact Section */
        .contact {
            font-size: 1.2rem;
            color: #00f3ff;
        }

        /* Social Icons */
        .social-icons {
            margin-top: 20px;
        }

        .social-icons a {
            color: #ffffff;
            font-size: 1.5rem;
            transition: transform 0.3s ease;
            margin: 0 15px;
        }

        .social-icons a:hover {
            color: #00f3ff;
            transform: scale(1.2);
        }
    </style>
</head>
<body>

    <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#portfolio">Portfolio</a>
        <a href="#contact">Contact</a>
    </nav>

    <section class="hero" id="home">
        <h1>Prince Raj</h1>
        <p>Developer & Tech Enthusiast</p>
        <button onclick="scrollToSection('about')">Discover More</button>
    </section>

    <section id="about" class="show">
        <h2>About Me</h2>
        <p>I'm Prince Raj, a developer passionate about turning ideas into impactful solutions.</p>
    </section>

    <section id="portfolio" class="show">
        <h2>My Projects</h2>
        <div class="portfolio-item" onclick="openModal('AI-Based App')">AI-Based App</div>
        <div class="portfolio-item" onclick="openModal('Dynamic Website')">Dynamic Website</div>
    </section>

    <section id="contact" class="show">
        <h2>Contact</h2>
        <p>Email me at: contact@princeraj.com</p>
        <div class="social-icons">
            <a href="#" title="LinkedIn">🌐</a>
            <a href="#" title="GitHub">📱</a>
        </div>
    </section>

    <div class="modal" id="modal">
        <div class="modal-content">
            <span id="modalText"></span>
            <div class="close-btn" onclick="closeModal()">Close</div>
        </div>
    </div>

    <script>
        // Smooth Scroll
        function scrollToSection(sectionId) {
            document.getElementById(sectionId).scrollIntoView({ behavior: 'smooth' });
        }

        // Portfolio Modal
        function openModal(projectName) {
            document.getElementById('modalText').innerText = `Details about ${projectName}`;
            document.getElementById('modal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('modal').style.display = 'none';
        }

        // Section Animation on Scroll
        window.addEventListener("scroll", function() {
            document.querySelectorAll("section").forEach(section => {
                const sectionTop = section.getBoundingClientRect().top;
                if (sectionTop < window.innerHeight * 0.75) {
                    section.classList.add("show");
                }
            });
        });

        // Trigger scroll event on page load
        window.dispatchEvent(new Event('scroll'));
    </script>
</body>
</html>


<!---
xDPrinceRaj/xDPrinceRaj is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
