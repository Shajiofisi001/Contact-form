<div class="container">
    <div class="header">
        <img src="https://cdn-icons-png.flaticon.com/512/561/561127.png" alt="Chat Icon">
        <h1>contact us</h1>
        <p>Please fill the form in a decent manner</p>
    </div>

    <form id="contactForm">
        <label for="first-name">Full Name <span>*</span></label>
        <div class="name-fields">
            <input type="text" id="first-name" placeholder="First Name" required>
            <input type="text" id="last-name" placeholder="Last Name" required>
        </div>

        <label for="email">E-mail <span>*</span></label>
        <input type="email" id="email" placeholder="example@example.com" required>

        <label for="message">Message <span>*</span></label>
        <textarea id="message" placeholder="Type your message..." required></textarea>

        <button type="submit">SUBMIT</button>
    </form>
</div>/* General Page Styling */
body {
    font-family: Arial, sans-serif;
    background-color: #f2f2f2;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

/* Container Styling */
.container {
    width: 400px;
    background: #EAEAEA;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
    text-align: center;
}

/* Header Styling */
.header img {
    width: 50px;
    margin-bottom: 10px;
}

.header h1 {
    font-size: 24px;
    font-weight: bold;
    margin: 0;
}

.header p {
    font-size: 14px;
    color: #666;
    margin-bottom: 20px;
}

/* Form Styling */
form {
    text-align: left;
}

label {
    font-weight: bold;
    display: block;
    margin-bottom: 5px;
}

span {
    color: red;
}

/* Name Fields */
.name-fields {
    display: flex;
    gap: 10px;
}

.name-fields input {
    width: 48%;
}

/* Input and Textarea Styling */
input, textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 14px;
}

textarea {
    height: 100px;
    resize: none;
}

/* Submit Button */
button {
    width: 100%;
    background: black;
    color: white;
    padding: 12px;
    border: none;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
    border-radius: 5px;
    text-transform: uppercase;
}

button:hover {
    background: #333;
}// Load EmailJS
const script = document.createElement("script");
script.src = "https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js";
document.head.appendChild(script);

document.addEventListener("DOMContentLoaded", function () {
    setTimeout(() => emailjs.init("NLKsF9bfmXk5p4nns"), 2000); // Your Public Key

    const form = document.getElementById("contactForm");

    form.addEventListener("submit", function (event) {
        event.preventDefault(); // Stop the form from submitting normally

        let firstName = document.getElementById("first-name").value.trim();
        let lastName = document.getElementById("last-name").value.trim();
        let email = document.getElementById("email").value.trim();
        let message = document.getElementById("message").value.trim();

        // Validate fields
        if (!firstName || !lastName || !email || !message) {
            alert("Please fill in all fields.");
            return;
        }

        // Prepare email data
        let emailData = {
            name: firstName + " " + lastName,
            email: email,
            message: message
        };

        // Send email using EmailJS
        emailjs.send("service_dq38egl", "template_3aeutg6", emailData)
            .then(() => {
                alert("Form Successfully Submitted! ✅");
                form.reset(); // Clear the form
            })
            .catch(error => {
                alert("Error sending message. Please try again.");
                console.log(error);
            });
    });
});# Contact-form
