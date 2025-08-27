<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  $name = htmlspecialchars($_POST["name"]);
  $email = htmlspecialchars($_POST["email"]);
  $phone = htmlspecialchars($_POST["phone"]);
  $service = htmlspecialchars($_POST["service"]);
  $budget = htmlspecialchars($_POST["budget"]);
  $message = htmlspecialchars($_POST["message"]);

  $to = "samadedamola4@gmail.com";
  $subject = "New Contact Form Submission";
  $body = "Name: $name\nEmail: $email\nPhone: $phone\nService: $service\nBudget: $budget\nMessage:\n$message";
  $headers = "From: $email";

  mail($to, $subject, $body, $headers);
  $success = true;
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Sam Adedamola | Portfolio</title>
  <meta name="description" content="Portfolio of Sam Adedamola, Full-Stack Developer. View projects, contact directly, and explore services." />
  <meta name="keywords" content="Sam Adedamola, Full-Stack Developer, Web Developer Nigeria, Portfolio" />
  <meta name="author" content="Sam Adedamola" />
  <link rel="stylesheet" href="styles.css" />
  <link rel="stylesheet" href="https://unpkg.com/swiper/swiper-bundle.min.css" />
</head>
<body>

<header>
  <h1>Sam Adedamola</h1>
  <p>Full-Stack Developer | Database Specialist</p>
</header>

<section id="about">
  <h2>About Me</h2>
  <div class="about-content">
    <img src="https://about.me/samadedamola/avatar" alt="Sam Adedamola" />
    <p>Hi, I'm Sam—a passionate developer with experience in building scalable web and mobile applications. I specialize in full-stack development, database architecture, and AI integration.</p>
    <p>Visit my full profile: <a href="https://about.me/samadedamola" target="_blank">about.me/samadedamola</a></p>
  </div>
</section>

<section id="projects">
  <h2>Projects</h2>
  <div class="project-card">
    <svg class="icon" viewBox="0 0 64 64"><rect x="10" y="20" width="44" height="24" fill="#007BFF"/></svg>
    <div>
      <h3><a href="https://www.restaurantfurniture.net" target="_blank">RestaurantFurniture.net</a></h3>
      <p>E-commerce platform for commercial-grade furniture with advanced filtering and SEO optimization.</p>
    </div>
  </div>
  <div class="project-card">
    <svg class="icon" viewBox="0 0 64 64"><rect x="8" y="8" width="48" height="48" rx="4" fill="#007BFF"/></svg>
    <div>
      <h3><a href="https://www.oddmenu.com" target="_blank">OddMenu.com</a></h3>
      <p>QR-based digital menu platform with real-time editing and multi-language support.</p>
    </div>
  </div>

  <div class="swiper">
    <div class="swiper-wrapper">
      <div class="swiper-slide">"Sam delivered a seamless experience. Sales increased 30%!" — CEO, RestaurantFurniture.net</div>
      <div class="swiper-slide">"OddMenu transformed our customer experience." — Manager, Café Lumière</div>
      <div class="swiper-slide">"Sam executed our vision flawlessly." — Founder, MenuTech Africa</div>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</section>

<section id="contact">
  <h2>Contact Me</h2>
  <?php if (isset($success)): ?>
    <div class="success-message">Thanks for reaching out! I'll get back to you soon.</div>
  <?php endif; ?>
  <form method="POST">
    <input type="text" name="name" placeholder="Your Name" required />
    <input type="email" name="email" placeholder="Your Email" required />
    <input type="tel" name="phone" placeholder="Phone Number" />
    <select name="service" required>
      <option value="">Select a Service</option>
      <option>Web Development</option>
      <option>Graphics Design</option>
      <option>Brand Marketing</option>
      <option>Complete Package</option>
      <option>Consultation</option>
    </select>
    <select name="budget">
      <option value="">Project Budget</option>
      <option>$30 - $100</option>
      <option>$100 - $250</option>
      <option>$250 - $400</option>
      <option>$400 - $500</option>
      <option>Custom Budget (specify in message)</option>
    </select>
    <textarea name="message" placeholder="Please describe your project, timeline, and any specific requirements..." required></textarea>
    <button type="submit">Send Message</button>
  </form>
</section>

<section id="chatbot">
  <h2>AI Chatbot</h2>
  <iframe src="https://your-chatbot-url.com" width="100%" height="300" frameborder="0">Chatbot loading...</iframe>
</section>

<footer>
  <p>&copy; <?= date("Y") ?> Sam Adedamola</p>
</footer>

<script src="https://unpkg.com/swiper/swiper-bundle.min.js"></script>
<script>
  const swiper = new Swiper('.swiper', {
    loop: true,
    pagination: { el: '.swiper-pagination' },
    autoplay: { delay: 4000 },
  });
</script>
</body>
</html>
/* styles.css */
body {
  font-family: 'Segoe UI', sans-serif;
  background-color: #f0f4f8;
  color: #333;
  margin: 0;
}

header, footer {
  background-color: #1e2a38;
  color: white;
  text-align: center;
  padding: 2rem;
}

section {
  padding: 2rem;
  max-width: 1000px;
  margin: auto;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.05);
  margin-bottom: 2rem;
}

h2 {
  color: #007BFF;
  text-align: center;
  margin-bottom: 1rem;
}

a {
  color: #007BFF;
  text-decoration: none;
}

.about-content {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  align-items: center;
}

.about-content img {
  width: 120px;
  border-radius: 50%;
}

.project-card {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
  align-items: center;
}

.icon {
  width: 60px;
  height: 60px;
}

form input, form select, form textarea {
  width: 100%;
  padding: 0.8rem;
  margin-bottom: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

form button {
  background-color: #007BFF;
  color: white;
  padding: 0.8rem 1.5rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.success-message {
  background-color: #d1fae5;
  color: #065f46;
  padding: 1rem;
  border-radius: 4px;
  margin-bottom: 1rem;
}

.swiper {
  margin-top: 2rem;
}

.swiper-slide {
  background-color: #e6ecf2;
  padding: 1.5rem;
  border-left: 4px solid #007BFF;
  font-style: italic;
  border-radius: 6px;
}
