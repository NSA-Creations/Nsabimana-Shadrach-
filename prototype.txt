<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Romans 12 Bible Blog - Nsabimana Shadrach</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" />
    <!-- Favicon and SEO Metadata -->
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>✝</text></svg>" type="image/svg+xml">
    <meta name="description" content="Romans 12 Bible Blog by Nsabimana Shadrach - A visually stunning and spiritually transformative experience.">
    <meta name="keywords" content="Bible, Romans 12, Christian blog, spiritual transformation, Nsabimana Shadrach">
    <meta name="author" content="Nsabimana Shadrach">
    <meta property="og:title" content="Romans 12 Bible Blog - Nsabimana Shadrach">
    <meta property="og:description" content="Explore Romans 12 with high-quality animations, transitions, and interactive features.">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://example.com/romans12">
    <meta property="og:image" content="https://example.com/logo.png">
    <style>
        /* Base Styles */
        :root {
            --gold: #FFD700;
            --deep-blue: #1a2a6c;
            --light-bg: linear-gradient(135deg, #f8f9fa, #e9ecef);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body, html {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            scroll-behavior: smooth;
            background: var(--light-bg);
            color: #333;
            overflow-x: hidden;
            min-height: 100vh;
        }
        
        /* Header Styles */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            padding: 20px 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 15px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(to right, var(--deep-blue), #b21f1f);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo-icon {
            font-size: 2.2rem;
            background: linear-gradient(to right, var(--deep-blue), #b21f1f);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        /* Navigation */
        nav ul {
            display: flex;
            gap: 25px;
            list-style: none;
        }
        
        nav a {
            text-decoration: none;
            color: #333;
            font-weight: 600;
            position: relative;
            padding: 5px 0;
            transition: color 0.3s;
        }
        
        nav a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--gold);
            transition: width 0.3s;
        }
        
        nav a:hover {
            color: var(--deep-blue);
        }
        
        nav a:hover::after {
            width: 100%;
        }
        
        /* Section Styles */
        section {
            min-height: 100vh;
            padding: 100px 20px 80px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.8s, transform 0.8s;
        }
        
        section.active {
            opacity: 1;
            transform: translateY(0);
        }
        
        h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            background: linear-gradient(to right, var(--deep-blue), #b21f1f);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        h2 {
            font-size: 2.5rem;
            margin-bottom: 30px;
            color: var(--deep-blue);
        }
        
        p {
            font-size: 1.2rem;
            line-height: 1.8;
            max-width: 800px;
            margin-bottom: 25px;
        }
        
        /* Verse Styles */
        .verse-container {
            background: rgba(255, 255, 255, 0.7);
            border-radius: 15px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            max-width: 800px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 215, 0, 0.3);
        }
        
        .verse {
            font-style: italic;
            color: #444;
            font-size: 1.4rem;
            line-height: 1.6;
            position: relative;
        }
        
        .verse::before, .verse::after {
            content: '"';
            font-size: 3rem;
            color: var(--gold);
            position: absolute;
            opacity: 0.3;
        }
        
        .verse::before {
            top: -20px;
            left: -15px;
        }
        
        .verse::after {
            bottom: -40px;
            right: -15px;
        }
        
        .verse-ref {
            display: block;
            text-align: right;
            margin-top: 15px;
            font-style: normal;
            font-weight: 600;
            color: var(--deep-blue);
        }
        
        /* Cursor Effects */
        .cursor {
            position: fixed;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: rgba(26, 42, 108, 0.7);
            transform: translate(-50%, -50%);
            pointer-events: none;
            z-index: 9999;
            mix-blend-mode: difference;
            transition: transform 0.2s, background 0.3s;
        }
        
        .cursor-follower {
            position: fixed;
            width: 8px;
            height: 8px;
            background: var(--gold);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            pointer-events: none;
            z-index: 9998;
            transition: width 0.3s, height 0.3s;
        }
        
        /* Animation Effects */
        .animate-section {
            animation: fadeInUp 1s forwards;
        }
        
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
        
        /* Footer */
        footer {
            text-align: center;
            padding: 30px;
            font-size: 1rem;
            color: #777;
            background: rgba(255, 255, 255, 0.9);
            border-top: 1px solid rgba(0,0,0,0.1);
        }
        
        /* Responsive Design */
        @media (max-width: 900px) {
            header {
                flex-direction: column;
                gap: 15px;
                padding: 15px 20px;
            }
            
            h1 {
                font-size: 2.5rem;
            }
            
            h2 {
                font-size: 2rem;
            }
            
            nav ul {
                gap: 15px;
            }
        }
        
        @media (max-width: 600px) {
            .verse {
                font-size: 1.2rem;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <!-- Custom Cursor Elements -->
    <div class="cursor"></div>
    <div class="cursor-follower"></div>
    
    <!-- Header with Logo -->
    <header>
        <div class="logo">
            <span class="logo-icon">✝</span>
            <span>Romans 12</span>
        </div>
        <nav>
            <ul>
                <li><a href="#intro">Home</a></li>
                <li><a href="#living-sacrifice">Sacrifice</a></li>
                <li><a href="#non-conformity">Non-Conformity</a></li>
                <li><a href="#renewal">Renewal</a></li>
                <li><a href="#application">Application</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <!-- Introduction Section -->
        <section id="intro" class="active animate-section">
            <h1>Romans 12: Transformative Living</h1>
            <p>A stunning Bible blog experience by Nsabimana Shadrach</p>
            <div class="verse-container">
                <p class="verse">"Do not conform to the pattern of this world, but be transformed by the renewing of your mind. Then you will be able to test and approve what God's will is—his good, pleasing and perfect will."</p>
                <span class="verse-ref">Romans 12:2 (NIV)</span>
            </div>
        </section>
        
        <!-- Living Sacrifice Section -->
        <section id="living-sacrifice">
            <h2>Living Sacrifice</h2>
            <p>True worship transcends ritual—it's the daily offering of our entire being to God. Paul's call to be a "living sacrifice" represents a radical shift from temple sacrifices to personal surrender.</p>
            <div class="verse-container">
                <p class="verse">"Therefore, I urge you, brothers and sisters, in view of God's mercy, to offer your bodies as a living sacrifice, holy and pleasing to God—this is your true and proper worship."</p>
                <span class="verse-ref">Romans 12:1 (NIV)</span>
            </div>
        </section>
        
        <!-- Non-Conformity Section -->
        <section id="non-conformity">
            <h2>Sacred Non-Conformity</h2>
            <p>In a world of constant pressure to conform, Romans 12 calls Christians to counter-cultural transformation. This isn't mere rejection but proactive alignment with God's design.</p>
            <div class="verse-container">
                <p class="verse">"Do not conform to the pattern of this world, but be transformed by the renewing of your mind."</p>
                <span class="verse-ref">Romans 12:2a (NIV)</span>
            </div>
        </section>
        
        <!-- Renewal of Mind Section -->
        <section id="renewal">
            <h2>Renewed Thinking</h2>
            <p>Transformation begins at the deepest level—our thought patterns. Renewed thinking enables discernment of God's perfect will, creating a foundation for Christ-centered living.</p>
            <div class="verse-container">
                <p class="verse">"Then you will be able to test and approve what God's will is—his good, pleasing and perfect will."</p>
                <span class="verse-ref">Romans 12:2b (NIV)</span>
            </div>
        </section>
        
        <!-- Practical Application Section -->
        <section id="application">
            <h2>Practical Christianity</h2>
            <p>Romans 12 moves from theology to practical application. Paul outlines what transformed living looks like in community: sincere love, spiritual humility, and radical hospitality.</p>
            <div class="verse-container">
                <p class="verse">"Love must be sincere. Hate what is evil; cling to what is good. Be devoted to one another in love. Honor one another above yourselves."</p>
                <span class="verse-ref">Romans 12:9-10 (NIV)</span>
            </div>
        </section>
    </main>
    
    <footer>
        &copy; 2025 Nsabimana Shadrach Bible Blog | Transformative Truths from Romans 12
    </footer>
    
    <script>
        // Intersection Observer for section animations
        const sections = document.querySelectorAll('section');
        
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                }
            });
        }, { threshold: 0.1 });
        
        sections.forEach(section => {
            observer.observe(section);
        });
        
        // Custom Cursor Implementation
        const cursor = document.querySelector('.cursor');
        const follower = document.querySelector('.cursor-follower');
        
        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
            
            setTimeout(() => {
                follower.style.left = e.clientX + 'px';
                follower.style.top = e.clientY + 'px';
            }, 100);
        });
        
        // Interactive hover effects
        document.querySelectorAll('a, .verse-container').forEach(element => {
            element.addEventListener('mouseenter', () => {
                cursor.style.transform = 'scale(3)';
                cursor.style.background = 'rgba(255, 215, 0, 0.5)';
                follower.style.width = '20px';
                follower.style.height = '20px';
            });
            
            element.addEventListener('mouseleave', () => {
                cursor.style.transform = 'scale(1)';
                cursor.style.background = 'rgba(26, 42, 108, 0.7)';
                follower.style.width = '8px';
                follower.style.height = '8px';
            });
        });
        
        // Smooth scrolling for navigation
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetSection = document.querySelector(targetId);
                
                window.scrollTo({
                    top: targetSection.offsetTop,
                    behavior: 'smooth'
                });
                
                // Update active navigation
                document.querySelectorAll('nav a').forEach(link => {
                    link.classList.remove('active');
                });
                this.classList.add('active');
            });
        });
        
        // Page load animation
        window.addEventListener('load', () => {
            document.body.classList.add('loaded');
        });
    </script>
</body>
</html>
