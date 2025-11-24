# Task-7-Web
# Fetch & Display Data Using JavaScript Fetch API

This project demonstrates how to **fetch user data from a public API**
using the JavaScript **Fetch API** and display it on a webpage.

------------------------------------------------------------------------

## ✅ Features

-   Fetch data from a public API\
-   Parse JSON response\
-   Display user details (name, email, address)\
-   Responsive card-based layout\
-   Error handling using try--catch\
-   Reload button to refetch data\
-   Works even when internet is disconnected (shows error)

------------------------------------------------------------------------

## 🌐 Public API Used

    https://jsonplaceholder.typicode.com/users

------------------------------------------------------------------------

## 📂 Project Structure

    project/
     └── index.html

------------------------------------------------------------------------

## ▶️ How to Run

1.  Create a new folder\
2.  Create a file named **index.html**\
3.  Paste the provided code into the file\
4.  Open the file in **Chrome or any browser**\
5.  The page will automatically fetch and display user data

To test error handling:\
- Turn off internet and reload page → It will show an error message.

------------------------------------------------------------------------

## 🧾 Full HTML + CSS + JavaScript Code

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Fetch API - User Data</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f4f9;
            padding: 20px;
        }
        h1 {
            text-align: center;
        }
        #users {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        .user-card {
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }
        button {
            display: block;
            margin: 15px auto;
            padding: 10px 20px;
            background: #007bff;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 6px;
        }
        button:hover {
            background: #0056b3;
        }
        .error {
            color: red;
            text-align: center;
            font-weight: bold;
        }
    </style>
</head>

<body>

    <h1>Fetch Users from API</h1>

    <button onclick="fetchUsers()">Reload Users</button>

    <p id="error" class="error"></p>

    <div id="users"></div>

    <script>
        async function fetchUsers() {
            const userContainer = document.getElementById("users");
            const errorBox = document.getElementById("error");

            userContainer.innerHTML = "";   
            errorBox.textContent = "";      

            try {
                const response = await fetch("https://jsonplaceholder.typicode.com/users");

                if (!response.ok) {
                    throw new Error("Failed to fetch users. Server error");
                }

                const users = await response.json();

                users.forEach(user => {
                    const card = document.createElement("div");
                    card.classList.add("user-card");

                    card.innerHTML = `
                        <h3>${user.name}</h3>
                        <p><strong>Email:</strong> ${user.email}</p>
                        <p><strong>Address:</strong> 
                           ${user.address.street}, 
                           ${user.address.city}
                        </p>
                    `;
                    userContainer.appendChild(card);
                });

            } catch (error) {
                errorBox.textContent = "⚠️ " + error.message + " (Check internet)";
            }
        }

        fetchUsers();
    </script>

</body>
</html>
```

------------------------------------------------------------------------

## 🎯 Outcome

You will understand:\
- How Fetch API works\
- How to handle asynchronous operations\
- JSON parsing\
- DOM manipulation\
- Error handling\
- Basic frontend API integration

------------------------------------------------------------------------

## 📌 Author

Generated automatically using ChatGPT.
