<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Nsabimana Shadrach | Web Designer & Developer</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet" />
  <style>
    /* Reset and base */
    * {
      margin: 0; padding: 0; box-sizing: border-box;
      scroll-behavior: smooth;
    }
    body {
      font-family: 'Poppins', sans-serif;
      background: #f0f0f3;
      color: #222;
      overflow-x: hidden;
      transition: background 0.5s, color 0.5s;
    }
    a {
      text-decoration: none;
      color: inherit;
    }

    /* Dark mode */
    body.dark {
      background: #121212;
      color: #eee;
    }

    /* Container */
    .container {
      max-width: 1200px;
      margin: auto;
      padding: 0 20px;
    }

    /* Header & Navigation */
    header {
      position: fixed;
      width: 100%;
      top: 0; left: 0;
      background: rgba(255,255,255,0.9);
      backdrop-filter: blur(10px);
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      z-index: 999;
      transition: background 0.5s;
    }
    body.dark header {
      background: rgba(18,18,18,0.9);
    }
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 20px;
    }
    .logo {
      font-weight: 700;
      font-size: 1.5rem;
      letter-spacing: 2px;
      color: #ff5722;
      cursor: pointer;
      user-select: none;
      position: relative;
      overflow: hidden;
    }
    .logo::after {
      content: '';
      position: absolute;
      width: 100%;
      height: 3px;
      background: #ff5722;
      bottom: 0;
      left: -100%;
      transition: left 0.4s ease;
    }
    .logo:hover::after {
      left: 0;
    }
    ul.nav-links {
      list-style: none;
      display: flex;
      gap: 30px;
    }
    ul.nav-links li a {
      font-weight: 600;
      font-size: 1rem;
      position: relative;
      padding-bottom: 4px;
      transition: color 0.3s;
    }
    ul.nav-links li a::after {
      content: '';
      position: absolute;
      width: 0%;
      height: 2px;
      background: #ff5722;
      bottom: 0;
      left: 0;
      transition: width 0.3s;
    }
    ul.nav-links li a:hover::after {
      width: 100%;
    }
    ul.nav-links li a:hover {
      color: #ff5722;
    }

    /* Hamburger Menu for Mobile */
    .hamburger {
      display: none;
      flex-direction: column;
      cursor: pointer;
      gap: 5px;
    }
    .hamburger div {
      width: 25px;
      height: 3px;
      background: #ff5722;
      border-radius: 3px;
      transition: all 0.3s ease;
    }
    .hamburger.active div:nth-child(1) {
      transform: rotate(45deg) translate(5px, 5px);
    }
    .hamburger.active div:nth-child(2) {
      opacity: 0;
    }
    .hamburger.active div:nth-child(3) {
      transform: rotate(-45deg) translate(5px, -5px);
    }
    @media (max-width: 768px) {
      ul.nav-links {
        position: fixed;
        top: 65px;
        right: -100%;
        background: #fff;
        height: calc(100vh - 65px);
        width: 250px;
        flex-direction: column;
        padding: 40px 20px;
        box-shadow: -2px 0 10px rgba(0,0,0,0.1);
        transition: right 0.4s ease;
        z-index: 998;
      }
      body.dark ul.nav-links {
        background: #222;
      }
      ul.nav-links.open {
        right: 0;
      }
      .hamburger {
        display: flex;
      }
    }

    /* Hero Section */
    .hero {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      position: relative;
      overflow: hidden;
      background: linear-gradient(135deg, #ff5722 0%, #ff8a50 100%);
      color: white;
    }
    .hero h1 {
      font-size: 4rem;
      font-weight: 900;
      margin-bottom: 10px;
      letter-spacing: 4px;
      animation: fadeInDown 1.5s ease forwards;
      opacity: 0;
    }
    .hero p {
      font-size: 1.5rem;
      font-weight: 500;
      margin-bottom: 30px;
      animation: fadeInUp 1.5s ease forwards;
      opacity: 0;
      animation-delay: 0.8s;
    }
    .hero .btn-primary {
      background: white;
      color: #ff5722;
      padding: 15px 40px;
      font-weight: 700;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 6px 15px rgba(255, 87, 34, 0.4);
      transition: background 0.3s, color 0.3s;
      animation: fadeInUp 1.5s ease forwards;
      animation-delay: 1.2s;
      border: none;
    }
    .hero .btn-primary:hover {
      background: #ff8a50;
      color: white;
      box-shadow: 0 8px 20px rgba(255, 138, 80, 0.7);
    }

    /* Animated floating circles background */
    .floating-circles {
      position: absolute;
      top: 0; left: 0; width: 100%; height: 100%;
      pointer-events: none;
      overflow: hidden;
      z-index: 0;
    }
    .circle {
      position: absolute;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.15);
      animation-timing-function: linear;
      animation-iteration-count: infinite;
      opacity: 0.7;
    }
    .circle.small {
      width: 40px; height: 40px;
      animation-name: floatUp;
      animation-duration: 15s;
    }
    .circle.medium {
      width: 80px; height: 80px;
      animation-name: floatUp;
      animation-duration: 20s;
    }
    .circle.large {
      width: 120px; height: 120px;
      animation-name: floatUp;
      animation-duration: 25s;
    }
    @keyframes floatUp {
      0% {
        transform: translateY(100vh) translateX(0);
        opacity: 0;
      }
      10% {
        opacity: 0.7;
      }
      100% {
        transform: translateY(-150px) translateX(50px);
        opacity: 0;
      }
    }

    /* Services Section */
    section.services {
      padding: 80px 0;
      background: #fff;
      color: #222;
    }
    body.dark section.services {
      background: #1e1e1e;
      color: #ddd;
    }
    section.services h2 {
      text-align: center;
      font-size: 2.8rem;
      margin-bottom: 60px;
      font-weight: 700;
      color: #ff5722;
      text-transform: uppercase;
      letter-spacing: 3px;
    }
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit,minmax(280px,1fr));
      gap: 40px;
      max-width: 1100px;
      margin: auto;
    }
    .service-card {
      background: #f9f9f9;
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.05);
      text-align: center;
      transition: transform 0.4s ease, box-shadow 0.4s ease;
      cursor: default;
      position: relative;
      overflow: hidden;
    }
    body.dark .service-card {
      background: #2a2a2a;
      box-shadow: 0 8px 20px rgba(0,0,0,0.5);
    }
    .service-card:hover {
      transform: translateY(-15px);
      box-shadow: 0 15px 35px rgba(255, 87, 34, 0.35);
    }
    .service-icon {
      font-size: 4rem;
      color: #ff5722;
      margin-bottom: 20px;
      transition: transform 0.4s ease;
    }
    .service-card:hover .service-icon {
      transform: rotate(15deg) scale(1.2);
    }
    .service-title {
      font-size: 1.6rem;
      font-weight: 700;
      margin-bottom: 15px;
    }
    .service-desc {
      font-size: 1rem;
      line-height: 1.5;
      color: #555;
    }
    body.dark .service-desc {
      color: #bbb;
    }

    /* Portfolio Section */
    section.portfolio {
      padding: 80px 0;
      background: #f0f0f3;
      color: #222;
    }
    body.dark section.portfolio {
      background: #121212;
      color: #eee;
    }
    section.portfolio h2 {
      text-align: center;
      font-size: 2.8rem;
      margin-bottom: 60px;
      font-weight: 700;
      color: #ff5722;
      text-transform: uppercase;
      letter-spacing: 3px;
    }
    .portfolio-filters {
      text-align: center;
      margin-bottom: 40px;
    }
    .portfolio-filters button {
      background: transparent;
      border: 2px solid #ff5722;
      color: #ff5722;
      padding: 10px 20px;
      margin: 0 10px;
      font-weight: 600;
      border-radius: 30px;
      cursor: pointer;
      transition: background 0.3s, color 0.3s;
    }
    .portfolio-filters button.active,
    .portfolio-filters button:hover {
      background: #ff5722;
      color: white;
    }
    .portfolio-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit,minmax(300px,1fr));
      gap: 30px;
      max-width: 1100px;
      margin: auto;
    }
    .portfolio-item {
      position: relative;
      overflow: hidden;
      border-radius: 20px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.1);
      cursor: pointer;
      transition: transform 0.3s ease;
      background: white;
    }
    body.dark .portfolio-item {
      background: #222;
      box-shadow: 0 8px 20px rgba(0,0,0,0.7);
    }
    .portfolio-item:hover {
      transform: scale(1.05);
      box-shadow: 0 12px 30px rgba(255, 87, 34, 0.4);
    }
    .portfolio-item img {
      width: 100%;
      display: block;
      border-radius: 20px 20px 0 0;
      transition: transform 0.3s ease;
    }
    .portfolio-item:hover img {
      transform: scale(1.1);
    }
    .portfolio-info {
      padding: 20px;
      text-align: center;
    }
    .portfolio-info h3 {
      font-size: 1.4rem;
      font-weight: 700;
      margin-bottom: 10px;
      color: #ff5722;
    }
    .portfolio-info p {
      font-size: 1rem;
      color: #555;
    }
    body.dark .portfolio-info p {
      color: #ccc;
    }

    /* Modal for Portfolio Details */
    .modal {
      position: fixed;
      top: 0; left: 0;
      width: 100vw; height: 100vh;
      background: rgba(0,0,0,0.8);
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
      z-index: 1000;
    }
    .modal.active {
      opacity: 1;
      pointer-events: auto;
    }
    .modal-content {
      background: white;
      border-radius: 20px;
      max-width: 800px;
      width: 90%;
      max-height: 90vh;
      overflow-y: auto;
      padding: 30px;
      position: relative;
      box-shadow: 0 10px 40px rgba(0,0,0,0.3);
      animation: modalFadeIn 0.4s ease forwards;
    }
    body.dark .modal-content {
      background: #222;
      color: #eee;
    }
    .modal-close {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 2rem;
      font-weight: 700;
      color: #ff5722;
      cursor: pointer;
      transition: color 0.3s;
    }
    .modal-close:hover {
      color: #ff8a50;
    }
    .modal-content img {
      max-width: 100%;
      border-radius: 15px;
      margin-bottom: 20px;
    }
    .modal-content h3 {
      margin-bottom: 15px;
      font-size: 2rem;
      color: #ff5722;
    }
    .modal-content p {
      font-size: 1.1rem;
      line-height: 1.6;
      color: #555;
    }
    body.dark .modal-content p {
      color: #ccc;
    }

    /* Testimonials Section */
    section.testimonials {
      padding: 80px 0;
      background: #fff;
      color: #222;
      text-align: center;
    }
    body.dark section.testimonials {
      background: #1e1e1e;
      color: #ddd;
    }
    section.testimonials h2 {
      font-size: 2.8rem;
      margin-bottom: 60px;
      font-weight: 700;
      color: #ff5722;
      text-transform: uppercase;
      letter-spacing: 3px;
    }
    .testimonial-slider {
      max-width: 800px;
      margin: auto;
      position: relative;
      overflow: hidden;
    }
    .testimonial-slide {
      opacity: 0;
      transform: translateX(100%);
      transition: opacity 0.5s ease, transform 0.5s ease;
      padding: 20px 40px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.05);
      border-radius: 20px;
      background: #fafafa;
      color: #333;
      user-select: none;
    }
    body.dark .testimonial-slide {
      background: #2a2a2a;
      color: #ddd;
      box-shadow: 0 8px 20px rgba(0,0,0,0.5);
    }
    .testimonial-slide.active {
      opacity: 1;
      transform: translateX(0);
      position: relative;
      z-index: 1;
    }
    .testimonial-avatar {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      margin: 0 auto 20px;
      border: 4px solid #ff5722;
      overflow: hidden;
      box-shadow: 0 4px 10px rgba(255, 87, 34, 0.3);
    }
    .testimonial-avatar img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .testimonial-text {
      font-style: italic;
      font-size: 1.2rem;
      margin-bottom: 15px;
    }
    .testimonial-author {
      font-weight: 700;
      font-size: 1rem;
      color: #ff5722;
    }
    /* Testimonial nav buttons */
    .testimonial-nav {
      margin-top: 30px;
      display: flex;
      justify-content: center;
      gap: 20px;
    }
    .testimonial-nav button {
      background: #ff5722;
      border: none;
      padding: 10px 20px;
      border-radius: 30px;
      color: white;
      font-weight: 700;
      cursor: pointer;
      transition: background 0.3s;
    }
    .testimonial-nav button:hover {
      background: #ff8a50;
    }

    /* Contact Section */
    section.contact {
      padding: 80px 0;
      background: #ff5722;
      color: white;
      text-align: center;
    }
    section.contact h2 {
      font-size: 2.8rem;
      margin-bottom: 40px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      text-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }
    form.contact-form {
      max-width: 600px;
      margin: auto;
      display: flex;
      flex-direction: column;
      gap: 20px;
    }
    form.contact-form input,
    form.contact-form textarea {
      padding: 15px 20px;
      border-radius: 30px;
      border: none;
      font-size: 1.1rem;
      outline: none;
      transition: box-shadow 0.3s ease;
    }
    form.contact-form input::placeholder,
    form.contact-form textarea::placeholder {
      color: #ffccbc;
    }
    form.contact-form input:focus,
    form.contact-form textarea:focus {
      box-shadow: 0 0 10px 3px rgba(255, 255, 255, 0.7);
      background: rgba(255, 255, 255, 0.15);
      color: white;
    }
    form.contact-form textarea {
      resize: vertical;
      min-height: 120px;
    }
    form.contact-form button {
      background: white;
      color: #ff5722;
      padding: 15px;
      font-weight: 700;
      border-radius: 30px;
      border: none;
      cursor: pointer;
      box-shadow: 0 6px 15px rgba(255, 255, 255, 0.5);
      transition: background 0.3s, color 0.3s;
      font-size: 1.2rem;
    }
    form.contact-form button:hover {
      background: #ff8a50;
      color: white;
      box-shadow: 0 8px 20px rgba(255, 138, 80, 0.7);
    }

    /* Footer */
    footer {
      padding: 40px 0;
      text-align: center;
      background: #222;
      color: #ccc;
      font-size: 0.9rem;
    }
    body.dark footer {
      background: #111;
      color: #999;
    }

    /* Animations */
    @keyframes fadeInDown {
      0% {opacity: 0; transform: translateY(-40px);}
      100% {opacity: 1; transform: translateY(0);}
    }
    @keyframes fadeInUp {
      0% {opacity: 0; transform: translateY(40px);}
      100% {opacity: 1; transform: translateY(0);}
    }
    @keyframes modalFadeIn {
      from {opacity: 0; transform: scale(0.8);}
      to {opacity: 1; transform: scale(1);}
    }

    /* Custom cursor */
    body {
      cursor: none;
    }
    .custom-cursor {
      position: fixed;
      top: 0; left: 0;
      width: 20px;
      height: 20px;
      border: 2px solid #ff5722;
      border-radius: 50%;
      pointer-events: none;
      transform: translate(-50%, -50%);
      transition: transform 0.15s ease, background-color 0.3s ease, border-color 0.3s ease;
      z-index: 10000;
      mix-blend-mode: difference;
      background-color: transparent;
    }
    .custom-cursor.hover {
      background-color: #ff5722;
      transform: translate(-50%, -50%) scale(1.8);
      border-color: transparent;
    }
  </style>
</head>
<body>

  <!-- Custom Cursor -->
  <div class="custom-cursor" id="cursor"></div>

  <!-- Header -->
  <header>
    <nav class="container">
      <div class="logo" tabindex="0">Nsabimana Shadrach</div>
      <ul class="nav-links" id="nav-links">
        <li><a href="#hero">Home</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#portfolio">Portfolio</a></li>
        <li><a href="#testimonials">Testimonials</a></li>
        <li><a href="#contact">Contact</a></li>
        <li>
          <button id="darkModeToggle" aria-label="Toggle Dark Mode" style="background:none;border:none;cursor:pointer;font-size:1.2rem;color:#ff5722;">
            🌙
          </button>
        </li>
      </ul>
      <div class="hamburger" id="hamburger" aria-label="Menu" role="button" tabindex="0">
        <div></div>
        <div></div>
        <div></div>
      </div>
    </nav>
  </header>

  <!-- Hero Section -->
  <section class="hero" id="hero" aria-label="Introduction">
    <div class="floating-circles" aria-hidden="true">
      <div class="circle small" style="left: 10%; animation-delay: 0s;"></div>
      <div class="circle medium" style="left: 30%; animation-delay: 3s;"></div>
      <div class="circle large" style="left: 60%; animation-delay: 5s;"></div>
      <div class="circle small" style="left: 80%; animation-delay: 2s;"></div>
      <div class="circle medium" style="left: 90%; animation-delay: 4s;"></div>
    </div>
    <h1>Nsabimana Shadrach</h1>
    <p>Creative Web Designer & Developer</p>
    <button class="btn-primary" onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'})">
      Hire Me
    </button>
  </section>

  <!-- Services Section -->
  <section class="services" id="services" aria-label="Services Offered">
    <h2>My Services</h2>
    <div class="services-grid">
      <div class="service-card" tabindex="0" aria-describedby="service1-desc">
        <div class="service-icon" aria-hidden="true">🎨</div>
        <h3 class="service-title">UI/UX Design</h3>
        <p class="service-desc" id="service1-desc">Crafting intuitive and beautiful user interfaces that engage and delight users.</p>
      </div>
      <div class="service-card" tabindex="0" aria-describedby="service2-desc">
        <div class="service-icon" aria-hidden="true">💻</div>
        <h3 class="service-title">Web Development</h3>
        <p class="service-desc" id="service2-desc">Building fast, responsive, and scalable websites and web apps using modern technologies.</p>
      </div>
      <div class="service-card" tabindex="0" aria-describedby="service3-desc">
        <div class="service-icon" aria-hidden="true">🛒</div>
        <h3 class="service-title">eCommerce Solutions</h3>
        <p class="service-desc" id="service3-desc">Creating secure and user-friendly online stores that convert visitors into customers.</p>
      </div>
      <div class="service-card" tabindex="0" aria-describedby="service4-desc">
        <div class="service-icon" aria-hidden="true">⚙️</div>
        <h3 class="service-title">Custom Web Apps</h3>
        <p class="service-desc" id="service4-desc">Developing tailored web applications to meet your unique business needs.</p>
      </div>
      <div class="service-card" tabindex="0" aria-describedby="service5-desc">
        <div class="service-icon" aria-hidden="true">🚀</div>
        <h3 class="service-title">SEO Optimization</h3>
        <p class="service-desc" id="service5-desc">Boosting your website’s visibility and ranking on search engines to attract more traffic.</p>
      </div>
    </div>
  </section>

  <!-- Portfolio Section -->
  <section class="portfolio" id="portfolio" aria-label="Portfolio Projects">
    <h2>My Work</h2>
    <div class="portfolio-filters" role="tablist" aria-label="Filter Portfolio Projects">
      <button class="active" data-filter="all" role="tab" aria-selected="true" tabindex="0">All</button>
      <button data-filter="web" role="tab" aria-selected="false" tabindex="-1">Websites</button>
      <button data-filter="apps" role="tab" aria-selected="false" tabindex="-1">Apps</button>
      <button data-filter="ecommerce" role="tab" aria-selected="false" tabindex="-1">eCommerce</button>
    </div>
    <div class="portfolio-grid" role="tabpanel">
      <div class="portfolio-item" data-category="web" tabindex="0" aria-describedby="proj1-desc" aria-label="Project: Portfolio Website">
        <img src="https://images.unsplash.com/photo-1506765515384-028b60a970df?auto=format&fit=crop&w=600&q=80" alt="Portfolio Website Screenshot" />
        <div class="portfolio-info">
          <h3>Portfolio Website</h3>
          <p id="proj1-desc">A personal portfolio site showcasing my skills and projects with smooth animations.</p>
        </div>
      </div>
      <div class="portfolio-item" data-category="apps" tabindex="0" aria-describedby="proj2-desc" aria-label="Project: Task Manager App">
        <img src="https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=600&q=80" alt="Task Manager App Screenshot" />
        <div class="portfolio-info">
          <h3>Task Manager App</h3>
          <p id="proj2-desc">A productivity app with real-time collaboration and intuitive UI.</p>
        </div>
      </div>
      <div class="portfolio-item" data-category="ecommerce" tabindex="0" aria-describedby="proj3-desc" aria-label="Project: Online Store">
        <img src="https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=600&q=80" alt="Online Store Screenshot" />
        <div class="portfolio-info">
          <h3>Online Store</h3>
          <p id="proj3-desc">A fully functional eCommerce platform with payment integration and user accounts.</p>
        </div>
      </div>
      <div class="portfolio-item" data-category="web" tabindex="0" aria-describedby="proj4-desc" aria-label="Project: Blog Website">
        <img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&w=600&q=80" alt="Blog Website Screenshot" />
        <div class="portfolio-info">
          <h3>Blog Website</h3>
          <p id="proj4-desc">A modern blog platform with CMS integration and SEO optimization.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Modal for Portfolio Details -->
  <div class="modal" id="modal" aria-hidden="true" role="dialog" aria-modal="true" aria-labelledby="modal-title" aria-describedby="modal-desc">
    <div class="modal-content">
      <span class="modal-close" id="modal-close" role="button" tabindex="0" aria-label="Close Modal">&times;</span>
      <img src="" alt="" id="modal-img" />
      <h3 id="modal-title"></h3>
      <p id="modal-desc"></p>
    </div>
  </div>

  <!-- Testimonials Section -->
  <section class="testimonials" id="testimonials" aria-label="Client Testimonials">
    <h2>What Clients Say</h2>
    <div class="testimonial-slider" aria-live="polite">
      <div class="testimonial-slide active" tabindex="0">
        <div class="testimonial-avatar">
          <img src="65.jpg" alt="Client Jane Doe" />
        </div>
        <p class="testimonial-text">“Nsabimana transformed our website into a beautiful and user-friendly platform. Highly recommended!”</p>
        <p class="testimonial-author">- Jane Doe</p>
      </div>
      <div class="testimonial-slide" tabindex="0">
        <div class="testimonial-avatar">
          <img src="43.jpg" alt="Client John Smith" />
        </div>
        <p class="testimonial-text">“Professional, talented, and timely. The custom app he built boosted our productivity tremendously.”</p>
        <p class="testimonial-author">- John Smith</p>
      </div>
      <div class="testimonial-slide" tabindex="0">
        <div class="testimonial-avatar">
          <img src="44.jpg" alt="Client Alice Johnson" />
        </div>
        <p class="testimonial-text">“Excellent SEO work that helped us rank on the first page of Google in just a few months.”</p>
        <p class="testimonial-author">- Alice Johnson</p>
      </div>
    </div>
    <div class="testimonial-nav" aria-label="Testimonial Navigation">
      <button id="prevTestimonial" aria-label="Previous Testimonial">Prev</button>
      <button id="nextTestimonial" aria-label="Next Testimonial">Next</button>
    </div>
  </section>

  <!-- Contact Section -->
  <section class="contact" id="contact" aria-label="Contact Form">
    <h2>Get In Touch</h2>
    <form class="contact-form" id="contact-form" novalidate>
      <input type="text" id="name" name="name" placeholder="Your Name" required aria-required="true" aria-describedby="name-error" />
      <span id="name-error" style="color:#ffccbc; font-size:0.9rem; display:none;">Please enter your name</span>

      <input type="email" id="email" name="email" placeholder="Your Email" required aria-required="true" aria-describedby="email-error" />
      <span id="email-error" style="color:#ffccbc; font-size:0.9rem; display:none;">Please enter a valid email</span>

      <textarea id="message" name="message" placeholder="Your Message" required aria-required="true" aria-describedby="message-error"></textarea>
      <span id="message-error" style="color:#ffccbc; font-size:0.9rem; display:none;">Please enter your message</span>

      <button type="submit">Send Message</button>
    </form>
  </section>

  <!-- Footer -->
  <footer>
    &copy; 2025 Nsabimana Shadrach. All rights reserved.
  </footer>

  <!-- JavaScript -->
  <script>
    // Hamburger Menu Toggle
    const hamburger = document.getElementById('hamburger');
    const navLinks = document.getElementById('nav-links');

    hamburger.addEventListener('click', () => {
      hamburger.classList.toggle('active');
      navLinks.classList.toggle('open');
    });

    // Close menu on link click (mobile)
    navLinks.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        if (navLinks.classList.contains('open')) {
          hamburger.classList.remove('active');
          navLinks.classList.remove('open');
        }
      });
    });

    // Dark Mode Toggle
    const darkModeToggle = document.getElementById('darkModeToggle');
    darkModeToggle.addEventListener('click', () => {
      document.body.classList.toggle('dark');
      if(document.body.classList.contains('dark')) {
        darkModeToggle.textContent = '☀️';
      } else {
        darkModeToggle.textContent = '🌙';
      }
    });

    // Portfolio Filtering
    const filterButtons = document.querySelectorAll('.portfolio-filters button');
    const portfolioItems = document.querySelectorAll('.portfolio-item');

    filterButtons.forEach(btn => {
      btn.addEventListener('click', () => {
        // Update active button
        filterButtons.forEach(b => {
          b.classList.remove('active');
          b.setAttribute('aria-selected', 'false');
          b.tabIndex = -1;
        });
        btn.classList.add('active');
        btn.setAttribute('aria-selected', 'true');
        btn.tabIndex = 0;

        const filter = btn.dataset.filter;
        portfolioItems.forEach(item => {
          if(filter === 'all' || item.dataset.category === filter) {
            item.style.display = 'block';
            setTimeout(() => {
              item.style.opacity = 1;
              item.style.transform = 'scale(1)';
            }, 10);
          } else {
            item.style.opacity = 0;
            item.style.transform = 'scale(0.8)';
            setTimeout(() => {
              item.style.display = 'none';
            }, 300);
          }
        });
      });
    });

    // Portfolio Modal
    const modal = document.getElementById('modal');
    const modalImg = document.getElementById('modal-img');
    const modalTitle = document.getElementById('modal-title');
    const modalDesc = document.getElementById('modal-desc');
    const modalClose = document.getElementById('modal-close');

    portfolioItems.forEach(item => {
      item.addEventListener('click', () => {
        const imgSrc = item.querySelector('img').src;
        const title = item.querySelector('h3').textContent;
        const desc = item.querySelector('p').textContent;

        modalImg.src = imgSrc;
        modalImg.alt = title + ' Screenshot';
        modalTitle.textContent = title;
        modalDesc.textContent = desc;

        modal.classList.add('active');
        modal.setAttribute('aria-hidden', 'false');
        modalClose.focus();
      });
    });

    modalClose.addEventListener('click', () => {
      modal.classList.remove('active');
      modal.setAttribute('aria-hidden', 'true');
    });

    // Close modal on outside click
    modal.addEventListener('click', e => {
      if(e.target === modal) {
        modal.classList.remove('active');
        modal.setAttribute('aria-hidden', 'true');
      }
    });

    // Close modal on ESC key
    document.addEventListener('keydown', e => {
      if(e.key === 'Escape' && modal.classList.contains('active')) {
        modal.classList.remove('active');
        modal.setAttribute('aria-hidden', 'true');
      }
    });

    // Testimonials Slider
    const slides = document.querySelectorAll('.testimonial-slide');
    const prevBtn = document.getElementById('prevTestimonial');
    const nextBtn = document.getElementById('nextTestimonial');
    let currentSlide = 0;

    function showSlide(index) {
      slides.forEach((slide, i) => {
        slide.classList.toggle('active', i === index);
        slide.tabIndex = i === index ? 0 : -1;
      });
    }

    prevBtn.addEventListener('click', () => {
      currentSlide = (currentSlide - 1 + slides.length) % slides.length;
      showSlide(currentSlide);
    });

    nextBtn.addEventListener('click', () => {
      currentSlide = (currentSlide + 1) % slides.length;
      showSlide(currentSlide);
    });

    // Auto slide every 8 seconds
    setInterval(() => {
      currentSlide = (currentSlide + 1) % slides.length;
      showSlide(currentSlide);
    }, 8000);

    // Custom Cursor
    const cursor = document.getElementById('cursor');

    document.addEventListener('mousemove', e => {
      cursor.style.left = e.clientX + 'px';
      cursor.style.top = e.clientY + 'px';
    });

    // Cursor hover effects on clickable elements
    const hoverElements = 'a, button, .service-card, .portfolio-item, .hamburger';

    document.querySelectorAll(hoverElements).forEach(el => {
      el.addEventListener('mouseenter', () => {
        cursor.classList.add('hover');
      });
      el.addEventListener('mouseleave', () => {
        cursor.classList.remove('hover');
      });
    });

    // Form Validation
    const form = document.getElementById('contact-form');
    const nameInput = form.name;
    const emailInput = form.email;
    const messageInput = form.message;

    form.addEventListener('submit', e => {
      e.preventDefault();
      let valid = true;

      // Name validation
      if(!nameInput.value.trim()) {
        showError('name-error');
        valid = false;
      } else {
        hideError('name-error');
      }

      // Email validation (simple regex)
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if(!emailRegex.test(emailInput.value.trim())) {
        showError('email-error');
        valid = false;
      } else {
        hideError('email-error');
      }

      // Message validation
      if(!messageInput.value.trim()) {
        showError('message-error');
        valid = false;
      } else {
        hideError('message-error');
      }

      if(valid) {
        alert('Thank you for your message! I will get back to you soon.');
        form.reset();
      }
    });

    function showError(id) {
      document.getElementById(id).style.display = 'block';
    }
    function hideError(id) {
      document.getElementById(id).style.display = 'none';
    }
  </script>
</body>
</html>
