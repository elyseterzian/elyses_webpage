# elyses_webpage
Storefront created using html, css, and javaScript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Storefront Sign Up Page</title>
    <link rel="stylesheet" href="256.css">
    <style>
        /* Internal CSS */
        body {
            font-family: Arial, sans-serif;
        }
        header {
            background-color: darkred;
            color: white;
            padding: 20px 0;
        }
        header h1 {
            text-align: center;
            margin: 0;
            font-size: 2em;
        }
        nav ul {
            list-style-type: none;
            text-align: center;
            padding: 0;
            margin-top: 10px;
        }
        nav ul li {
            display: inline;
            margin-right: 20px;
        }
        nav ul li a {
            text-decoration: none;
            color: white;
            font-weight: bold;
        }
        .featured-product, .signup-form {
            background-color: #fff;
            border: 1px solid #ddd;
            padding: 20px;
            margin-top: 20px;
            text-align: center;
        }
        .featured-product h2, .signup-form h2 {
            color: #333;
        }
        .signup-form {
            background-color: #f9f9f9;
            padding: 20px;
            margin-top: 20px;
            border: 1px solid #ddd;
            max-width: 400px;
            margin-left: auto;
            margin-right: auto;
        }
        .signup-form input, .signup-form button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            box-sizing: border-box;
        }
        .signup-form button {
            background-color: darkred;
            color: white;
            border: none;
            cursor: pointer;
        }
        .error {
            color: red;
            font-size: 12px;
        }
        footer {
            text-align: center;
            padding: 10px;
            margin-top: 20px;
            background-color: darkred;
            color: white;
        }
    </style>
</head>
<body>

<header>
    <h1>Elyse's Closet</h1>
    <nav>
        <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">Products</a></li>
            <li><a href="#">About Us</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>
</header>

<section>
    <!-- Keeping featured products to maintain the same look as the storefront -->
    <h2>Featured Products</h2>
    <div class="featured-product">
        <h2>Light Wash Baggy Jeans</h2>
        <img src="https://m.media-amazon.com/images/I/71Aqa67jqkS._AC_SX679_.jpg" width="250" height="400" />
        <p>Price: $49.99</p>
        <button style="background-color: darkred; color: white; border: none; padding: 10px; cursor: pointer;">Buy Now</button>
    </div>

   <div class="featured-product">
        <h2>Oversized Colorful Sweater</h2>
        <img src="https://m.media-amazon.com/images/I/71mttAjyiiL._AC_SX679_.jpg" width="300" height="400" />
        <p>Price: $54.99</p>
        <button style="background-color: darkred; color: white; border: none; padding: 10px; cursor: pointer;">Buy Now</button>
    </div>

  <div class="featured-product">
        <h2>Red Leather Top</h2>
        <img src="https://finesse.us/cdn/shop/files/noidyet_francine-purple-vegan-leather-top_front_model_gray_0.jpg?v=1713962813&width=1680" width="300" height="400" />
        <p>Price: $29.99</p>
        <button style="background-color: darkred; color: white; border: none; padding: 10px; cursor: pointer;">Buy Now</button>
    </div>

   <div class="featured-product">
        <h2>Silver Metallic Pumps</h2>
        <img src="https://inez.com/cdn/shop/files/Altasilverpdp3.jpg?v=1699981005&width=2380" width="300" height="400" />
        <p>Price: $59.99</p>
        <button style="background-color: darkred; color: white; border: none; padding: 10px; cursor: pointer;">Buy Now</button>
    </div>
</section>

<!-- Sign-up Form Section with consistent styling -->
<section>
    <h2>Sign Up</h2>
    <div class="signup-form">
        <form id="signupForm">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
            <span id="nameError" class="error"></span>

  <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <span id="emailError" class="error"></span>

  <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>
            <span id="passwordError" class="error"></span>

   <label for="confirmPassword">Confirm Password:</label>
            <input type="password" id="confirmPassword" name="confirmPassword" required>
            <span id="confirmPasswordError" class="error"></span>

  <button type="submit">Sign Up</button>
        </form>
    </div>
</section>

<footer>
    <p>&copy; Elyse's Closet. All rights reserved.</p>
</footer>

<script>
    // JavaScript for form validation and creating JSON object
    document.getElementById('signupForm').addEventListener('submit', function(event) {
        event.preventDefault(); // Prevent form submission

        let isValid = true;

        // Name validation
        const name = document.getElementById('name').value;
        const nameError = document.getElementById('nameError');
        if (name.trim() === '') {
            nameError.textContent = 'Name is required.';
            isValid = false;
        } else {
            nameError.textContent = '';
        }

        // Email validation
        const email = document.getElementById('email').value;
        const emailError = document.getElementById('emailError');
        const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
        if (!email.match(emailPattern)) {
            emailError.textContent = 'Please enter a valid email.';
            isValid = false;
        } else {
            emailError.textContent = '';
        }

        // Password validation
        const password = document.getElementById('password').value;
        const confirmPassword = document.getElementById('confirmPassword').value;
        const passwordError = document.getElementById('passwordError');
        const confirmPasswordError = document.getElementById('confirmPasswordError');

        if (password.length < 6) {
            passwordError.textContent = 'Password must be at least 6 characters long.';
            isValid = false;
        } else {
            passwordError.textContent = '';
        }

        // Confirm password validation
        if (password !== confirmPassword) {
            confirmPasswordError.textContent = 'Passwords do not match.';
            isValid = false;
        } else {
            confirmPasswordError.textContent = '';
        }

        if (isValid) {
            // Create a JSON object from the form inputs
            const formData = {
                name: name,
                email: email,
                password: password,
                confirmPassword: confirmPassword
            };

            console.log("Form Data as JSON:", JSON.stringify(formData));
        }
    });
</script>

</body>
</html>



