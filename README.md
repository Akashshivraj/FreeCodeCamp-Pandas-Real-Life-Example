### rmotr.com
# Data Science with Python Course

This material is created for our [Data Science with Python Course](https://rmotr.com/data-science-python-course)

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sign Up / Login</title>
</head>
<body>
<h1>Sign Up</h1>
<form id="signupForm">
  <label for="username">Username:</label><br>
  <input type="text" id="username" name="username" required><br>
  <label for="password">Password:</label><br>
  <input type="password" id="password" name="password" required><br>
  <label for="name">Name:</label><br>
  <input type="text" id="name" name="name" required><br>
  <label for="email">Email:</label><br>
  <input type="email" id="email" name="email" required><br><br>
  <button type="submit">Sign Up</button>
</form>

<script>
document.getElementById("signupForm").addEventListener("submit", function(event) {
  event.preventDefault(); // Prevent the form from submitting normally
  
  // Get form data
  const formData = new FormData(event.target);
  const data = {};
  formData.forEach((value, key) => {data[key] = value});
  
  // Send data to Google Apps Script
  fetch("google.script.url.getLocation(function(location) {
  console.log(location.parameters);
  console.log(location.hash);
});", {
    method: "POST",
    mode: "no-cors",
    body: JSON.stringify(data)
  }).then(response => {
    console.log("Data sent to Google Sheets");
    // Optionally redirect to another page after successful submission
    // window.location.href = "success.html";
  }).catch(error => {
    console.error("Error sending data to Google Sheets:", error);
  });
});
</script>
</body>
</html>
