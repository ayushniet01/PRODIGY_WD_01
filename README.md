<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ayush singh</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

         body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
        }

        /* Navigation Styles */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 15px 0;
            transition: all 0.3s ease;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .navbar.scrolled {
            background: rgba(26, 35, 126, 0.95);
            padding: 10px 0;
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.2);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #1a237e;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .navbar.scrolled .logo {
            color: #ffffff;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        .nav-item {
            position: relative;
        }

        .nav-link {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            padding: 8px 16px;
            border-radius: 25px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .navbar.scrolled .nav-link {
            color: #ffffff;
        }

        .nav-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            transition: left 0.3s ease;
            z-index: -1;
        }

        .nav-link:hover::before {
            left: 0;
        }

        .nav-link:hover {
            color: #ffffff;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        /* Mobile Menu Toggle */
        .menu-toggle {
            display: none;
            flex-direction: column;
            cursor: pointer;
            padding: 5px;
        }

        .menu-toggle span {
            width: 25px;
            height: 3px;
            background: #333;
            margin: 3px 0;
            transition: 0.3s;
        }

        .navbar.scrolled .menu-toggle span {
            background: #ffffff;
        }

        /* Content Sections */
        .content-section {
            padding: 100px 20px 50px;
            min-height: 100vh;
            max-width: 1200px;
            margin: 0 auto;
        }

        .hero {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }

        .hero h1 {
            font-size: 3em;
            margin-bottom: 20px;
            animation: fadeInUp 1s ease;
        }

        .hero p {
            font-size: 1.2em;
            margin-bottom: 30px;
            animation: fadeInUp 1s ease 0.3s both;
        }

        .cta-button {
            background: #ff6b6b;
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 25px;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s ease;
            animation: fadeInUp 1s ease 0.6s both;
        }

        .cta-button:hover {
            background: #ff5252;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }

        .section-title {
            font-size: 2.5em;
            margin-bottom: 30px;
            text-align: center;
            color: #1a237e;
        }

        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 50px;
        }

        .card {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .card h3 {
            color: #1a237e;
            margin-bottom: 15px;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-menu {
                position: fixed;
                top: 70px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 70px);
                background: rgba(255, 255, 255, 0.95);
                backdrop-filter: blur(10px);
                flex-direction: column;
                justify-content: flex-start;
                align-items: center;
                padding-top: 50px;
                transition: left 0.3s ease;
            }

            .nav-menu.active {
                left: 0;
            }

            .navbar.scrolled .nav-menu {
                background: rgba(26, 35, 126, 0.95);
            }

            .menu-toggle {
                display: flex;
            }

            .menu-toggle.active span:nth-child(1) {
                transform: rotate(45deg) translate(5px, 5px);
            }

            .menu-toggle.active span:nth-child(2) {
                opacity: 0;
            }

            .menu-toggle.active span:nth-child(3) {
                transform: rotate(-45deg) translate(7px, -6px);
            }

            .hero h1 {
                font-size: 2em;
            }

            .section-title {
                font-size: 2em;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <a href="#home" class="logo">dishank uttam</a>
            <ul class="nav-menu" id="nav-menu">
                <li class="nav-item">
                    <a href="#home" class="nav-link">Home</a>
                </li>
                <li class="nav-item">
                    <a href="#about" class="nav-link">About</a>
                </li>
                <li class="nav-item">
                    <a href="#services" class="nav-link">Services</a>
                </li>
                <li class="nav-item">
                    <a href="#portfolio" class="nav-link">Portfolio</a>
                </li>
                <li class="nav-item">
                    <a href="#contact" class="nav-link">Contact</a>
                </li>
            </ul>
            <div class="menu-toggle" id="menu-toggle">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

  <!-- Hero Section -->
    <section id="home" class="hero content-section">
        <h1>Interactive Navigation</h1>
        <p>Experience smooth scrolling effects and dynamic color changes</p>
        <button class="cta-button">Get Started</button>
    </section>

    <!-- About Section -->
    <section id="about" class="content-section">
        <h2 class="section-title">About Us</h2>
        <div class="card-grid">
            <div class="card">
                <h3>Our Mission</h3>
                <p>We create innovative web experiences that combine beautiful design with smooth functionality. Our navigation menu adapts to user interactions, providing an intuitive browsing experience.</p>
            </div>
            <div class="card">
                <h3>Our Vision</h3>
                <p>To lead the way in interactive web design, making every user interaction meaningful and engaging through thoughtful animations and responsive design.</p>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="content-section">
        <h2 class="section-title">Our Services</h2>
        <div class="card-grid">
            <div class="card">
                <h3>Web Development</h3>
                <p>Custom websites built with modern technologies and interactive elements that engage your audience.</p>
            </div>
            <div class="card">
                <h3>UI/UX Design</h3>
                <p>User-centered design that focuses on creating intuitive and beautiful interfaces.</p>
            </div>
            <div class="card">
                <h3>Mobile Development</h3>
                <p>Responsive applications that work seamlessly across all devices and screen sizes.</p>
            </div>
        </div>
    </section>

    <!-- Portfolio Section -->
    <section id="portfolio" class="content-section">
        <h2 class="section-title">Our Work</h2>
        <div class="card-grid">
            <div class="card">
                <h3>Project Alpha</h3>
                <p>A dynamic e-commerce platform with interactive product showcases and smooth navigation transitions.</p>
            </div>
            <div class="card">
                <h3>Project Beta</h3>
                <p>Corporate website featuring animated scroll effects and color-changing navigation based on section visibility.</p>
            </div>
            <div class="card">
                <h3>Project Gamma</h3>
                <p>Mobile-first application with gesture-based navigation and adaptive color schemes.</p>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="content-section">
        <h2 class="section-title">Get In Touch</h2>
        <div class="card-grid">
            <div class="card">
                <h3>Get In Touch</h3>
                <p>Ready to start your project? Reach out to us and let's create something amazing together.</p>
            </div>
            <div class="card">
                <h3>Connect</h3>
                <p>Stay updated with our latest projects and design insights.</p>
            </div>
        </div>
    </section>

    <script>
        // Get navbar element
        const navbar = document.getElementById('navbar');
        const menuToggle = document.getElementById('menu-toggle');
        const navMenu = document.getElementById('nav-menu');

        // Scroll event listener
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Mobile menu toggle
        menuToggle.addEventListener('click', () => {
            menuToggle.classList.toggle('active');
            navMenu.classList.toggle('active');
        });

        // Close mobile menu when clicking on a nav link
        document.querySelectorAll('.nav-link').forEach(link => {
            link.addEventListener('click', () => {
                menuToggle.classList.remove('active');
                navMenu.classList.remove('active');
            });
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Add scroll-triggered animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe all cards for scroll animations
        document.querySelectorAll('.card').forEach(card => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(30px)';
            card.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
            observer.observe(card);
        });

        // Add dynamic color changes based on scroll position
        window.addEventListener('scroll', () => {
            const scrollPercent = window.scrollY / (document.body.scrollHeight - window.innerHeight);
            const hue = Math.floor(scrollPercent * 360);
            
            // Subtle color change effect on scroll
            if (navbar.classList.contains('scrolled')) {
                navbar.style.background = hsla(${hue}, 70%, 25%, 0.95);
            }
        });
    </script>
</body>
</html>
