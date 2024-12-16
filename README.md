            <!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Protected Chat Room</title>
    <style>
        body {
            font-family: courier, serif;
            margin: 0;
            padding: 0;    display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #000000;
        }
                #login {
            font-family: courier, serif;
            display: none;
            background: white;
            padding: 20px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            width: 100%;
            max-width: 400px;
        }
                #chatRoom {
            font-family: courier, serif;
            display: none;
            background: white;
            padding: 20px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            width: 90%;
            max-width: 800px;
            height: 90%;
            overflow: scroll;
                }
                #login.active,
        #chatRoom.active {
            display: block;
            }
#messages {
            font-family: courier, serif;
            height: 70%;
            overflow-y: scroll;
            border: 1px solid #ccc;
            padding: 10px;
            margin-bottom: 10px;
            background-color: #f9f9f9;
        }
        #messages p {
            margin: 5px 0;
        }
        input[type="text"],
        input[type="password"],
        button {
            font-family: courier, serif;
            width: calc(100% - 20px);
            margin: 5px 0;
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: #000000;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #1f1f1f;
        }
    </style>
</head>

<body>
    <div id="login" class="active">

<h2><b>Enter Password</b></h2>
        <input type="password" id="password" placeholder="Password">
        <button onclick="checkPassword()"><b>Enter</b></button>
    </div>
   <div id="chatRoom">
        <h2><b>Chat Room</b></h2>
        <div id="nameInput">
            <input type="text" id="username" placeholder="Enter your name">
<button onclick="setUsername()"><b>Join Chat</b></button>
        </div>
        <div id="chat" style="display: none;">
            <div id="messages"></div>
            <input type="text" id="message" placeholder="Type a message">
            <button onclick="sendMessage()"><b>Send</b></button>
        </div>
    </div>
    <script>
        const validPassword = /^(ppp)$/i; // Regex to accept any capitalization of "ppp"
function checkPassword() {
            const passwordInput = document.getElementById('password').value;
            if (validPassword.test(passwordInput)) {
                document.getElementById('login').classList.remove('active');
                document.getElementById('chatRoom').classList.add('active');
            } else {
                alert('Incorrect Password');
            }
        }
function setUsername() {
            const usernameInput = document.getElementById('username').value.trim();
            if (usernameInput) {
                document.getElementById('nameInput').style.display = 'none';
                document.getElementById('chat').style.display = 'block';
                document.getElementById('username').dataset.name = usernameInput;
            } else {
                alert('Please enter your name');
            }
        }
 function sendMessage() {
            const messageInput = document.getElementById('message');
            const message = messageInput.value.trim();
            const username = document.getElementById('username').dataset.name;
if (message) {
                const messagesDiv = document.getElementById('messages');
                const newMessage = document.createElement('p');
                newMessage.textContent = `${username}: ${message}`;
                messagesDiv.appendChild(newMessage);
                messagesDiv.scrollTop = messagesDiv.scrollHeight; // Scroll to the bottom
                messageInput.value = '';
            } else {
                alert('Please type a message');
            }
        }
    </script>
</body>

</html>
