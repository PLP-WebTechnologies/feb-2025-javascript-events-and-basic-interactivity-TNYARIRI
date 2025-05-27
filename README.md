<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Interactive Bundle of Joy</title>
  <link rel="stylesheet" href="style.css"/>
</head>
<body>
  <h1> Welcome to My Interactive Page </h1>

  
  <button id="actionBtn">Click Me please</button>
  <p id="buttonStatus"></p>

  
  <div class="gallery">
    <img src="img1.jpg" class="gallery-img" alt="Image 1"/>
    <img src="img2.jpg" class="gallery-img hidden" alt="Image 2"/>
    <img src="img3.jpg" class="gallery-img hidden" alt="Image 3"/>
    <button id="nextImg">Next Image</button>
  </div>

  
  <div class="tabs">
    <button class="tab" data-tab="1">Tab 1</button>
    <button class="tab" data-tab="2">Tab 2</button>
    <div id="tabContent1" class="tab-content">This is content for Tab 1.</div>
    <div id="tabContent2" class="tab-content hidden">This is content for Tab 2.</div>
  </div>

  <form id="signupForm">
    <label>Email: <input type="email" id="email" required /></label>
    <span id="emailFeedback"></span><br/>
    <label>Password: <input type="password" id="password" required minlength="8"/></label>
    <span id="passwordFeedback"></span><br/>
    <button type="submit">Submit</button>
  </form>

  <script src="script.js"></script>
</body>
</html>





const actionBtn = document.getElementById("actionBtn");
const status = document.getElementById("buttonStatus");

actionBtn.addEventListener("click", () => {
  actionBtn.textContent = "You clicked me!";
  status.textContent = "Button was clicked ✅";
});


actionBtn.addEventListener("dblclick", () => {
  alert("🎉 Secret double-click activated!");
});


let currentImg = 0;
const images = document.querySelectorAll(".gallery-img");
const nextImgBtn = document.getElementById("nextImg");

nextImgBtn.addEventListener("click", () => {
  images[currentImg].classList.add("hidden");
  currentImg = (currentImg + 1) % images.length;
  images[currentImg].classList.remove("hidden");
});


const tabs = document.querySelectorAll(".tab");
tabs.forEach(tab => {
  tab.addEventListener("click", () => {
    document.querySelectorAll(".tab-content").forEach(c => c.classList.add("hidden"));
    document.getElementById(`tabContent${tab.dataset.tab}`).classList.remove("hidden");
  });
});


const email = document.getElementById("email");
const password = document.getElementById("password");
const emailFeedback = document.getElementById("emailFeedback");
const passwordFeedback = document.getElementById("passwordFeedback");

email.addEventListener("input", () => {
  const regex = /^[^@\s]+@[^@\s]+\.[^@\s]+$/;
  emailFeedback.textContent = regex.test(email.value) ? "✅ Valid email" : "❌ Invalid email";
});

password.addEventListener("input", () => {
  passwordFeedback.textContent = password.value.length >= 8
    ? "✅ Strong password"
    : "❌ Must be at least 8 characters";
});

document.getElementById("signupForm").addEventListener("submit", (e) => {
  e.preventDefault();
  alert("Form submitted successfully!");
});



      NOW CSS 

      body {
    font-family: sans-serif;
    padding: 20px;
    background: #fdf6e3;
  }
  
  button {
    margin: 10px;
    padding: 10px 15px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #ffda77;
  }
  
  .hidden {
    display: none;
  }
  
  .gallery-img {
    width: 200px;
    height: auto;
    border-radius: 10px;
    margin-bottom: 10px;
    transition: transform 0.3s ease;
  }
  
  .gallery-img:hover {
    transform: scale(1.05);
  }
  
  .tab-content {
    margin-top: 10px;
  }
  
  input:invalid {
    border: 2px solid red;
  }
  
  input:valid {
    border: 2px solid green;
  }
  
