<template>
    <div class="container">
      <h1 class="heading">Development Team and Project Overview</h1>
      <div class="section">
        <strong class="section-heading">Introduction:</strong>
        <p>
          We are excited to present our development team's journey and accomplishments throughout the project. Our mission was to create an innovative and user-friendly website that provides users with a delightful cooking and recipe experience. Leveraging the power of modern web technologies, our team combined Vue.js on the frontend and Node.js with Express and MySQL on the server side. Additionally, we integrated the Spoonacular API to offer a comprehensive and dynamic recipe database.
        </p>
      </div>
      <div class="section">
        <strong class="section-heading">Development Team:</strong>
        <p>
          Our talented and dedicated development team comprised skilled professionals with diverse expertise in frontend and backend development, database management, and API integration. The team collaborated seamlessly, focusing on delivering a cohesive and high-quality product that meets our users' needs and exceeds their expectations.
        </p>
      </div>
      <div class="section">
        <strong class="section-heading">Project Overview:</strong>
        <p>
          The core idea behind the project was to create a platform where users could explore and share an extensive collection of recipes, as well as interact with various cooking features. Our primary goal was to provide a user-friendly interface that caters to both cooking enthusiasts and culinary experts.
        </p>
      </div>
  
      <!-- Project Links Section -->
      <h2 class="sub-heading">Previous Projects Links:</h2>
      <ul class="project-links">
        <li>
          <a href="https://github.com/Web-Development-Environments-2023/315786798" target="_blank" rel="noopener">Ron - Project 1: Simple HTML/CSS portfolio website</a>
        </li>
        <li>
          <a href="https://github.com/Web-Development-Environments-2023/205814999" target="_blank" rel="noopener">Idan - Project 1: Simple HTML/CSS portfolio website</a>
        </li>
        <li>
          <a href="https://github.com/Web-Development-Environments-2023/assignment2-315786798_205814999" target="_blank" rel="noopener">Ron & Idan - Project 2: HTML/CSS/JS Game</a>
        </li>
      </ul>
  
      <!-- Conclusion Section -->
      <div class="section">
        <strong class="section-heading">Conclusion:</strong>
        <p>
          In conclusion, our development team poured passion, expertise, and creativity into this project, resulting in a feature-rich and engaging platform for food enthusiasts. We are proud to have created a user-centric website that offers an immersive cooking experience for individuals of all culinary backgrounds. We invite you to explore our platform and discover the joy of cooking with our vast collection of recipes and interactive features.
        </p>
      </div>
      <div class="section">
        <p>
          For more information or inquiries, please feel free to contact us at <a class="email-link" href="mailto:ronvo@post.bgu.ac.il">ronvo@post.bgu.ac.il</a> or <a class="email-link" href="idan7@post.bgu.ac.il">idan7@post.bgu.ac.il</a>.
        </p>
      </div>
      <p class="thanks">Thank you for being a part of our culinary journey!</p>
    </div>
  </template>
  
  <script>
  export default {
    name: "AboutPage",
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 800px;
    margin: 0 auto;
    padding: 30px;
    color:white;
  }
  
  .heading {
    font-size: 32px;
    font-weight: bold;
    text-align: center;
    margin-bottom: 20px;
  }
  
  .section {
    margin-bottom: 20px;
  }
  
  .section-heading {
    font-size: 20px;
    font-weight: bold;
  }
  
  .sub-heading {
    font-size: 24px;
    font-weight: bold;
    margin-top: 30px;
    margin-bottom: 10px;
  }
  
  .project-links {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .project-links li {
    margin-bottom: 10px;
  }
  
  .project-links a {
    color: #007bff;
    text-decoration: none;
  }
  
  .project-links a:hover {
    text-decoration: underline;
  }
  
  .email-link {
    color: #007bff;
    text-decoration: none;
  }
  
  .email-link:hover {
    text-decoration: underline;
  }
  
  .thanks {
    text-align: center;
    font-style: italic;
    margin-top: 30px;
  }
  </style>
  