Code for website
2	+
3	+
            <!DOCTYPE html>
4	+
<html lang="en">
5	+
6	+
<head>
7	+
    <meta charset="UTF-8">


8	+
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
9	+
    <title>Password Protected Chat Room</title>
10	+
    <style>
11	+
        body {
12	+
            font-family: courier, serif;
13	+
            margin: 0;
14	+
            padding: 0;
15	+
            display: flex;
16	+
            justify-content: center;
17	+
            align-items: center;
18	+
            height: 100vh;
19	+
            background-color: #000000;
20	+
        }
21	+
22	+
        #login {
23	+
            font-family: courier, serif;
24	+
            display: none;
25	+
            background: white;
26	+
            padding: 20px;
27	+
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
28	+
            border-radius: 8px;
29	+
            width: 100%;
30	+
            max-width: 400px;
31	+
        }
32	+
33	+
        #chatRoom {
34	+
            font-family: courier, serif;
35	+
            display: none;
36	+
            background: white;
37	+
            padding: 20px;
38	+
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
39	+
            border-radius: 8px;
40	+
            width: 90%;
41	+
            max-width: 800px;
42	+
            height: 90%;
43	+
            overflow: scroll;
44	+
        }
45	+
46	+
        #login.active,
47	+
        #chatRoom.active {
48	+
            display: block;
49	+
}
50	+
51	+
#messages {
52	+
            font-family: courier, serif;
53	+
            height: 70%;
54	+
            overflow-y: scroll;
55	+
            border: 1px solid #ccc;
56	+
            padding: 10px;
57	+
            margin-bottom: 10px;
58	+
            background-color: #f9f9f9;
59	+
        }
60	+
61	+
        #messages p {
62	+
            margin: 5px 0;
63	+
        }
64	+
65	+
        input[type="text"],
66	+
        input[type="password"],
67	+
        button {
68	+
            font-family: courier, serif;
69	+
            width: calc(100% - 20px);
70	+
            margin: 5px 0;
71	+
            padding: 10px;
72	+
            font-size: 16px;
73	+
            border: 1px solid #ccc;
74	+
            border-radius: 4px;
75	+
        }
76	+
        button {
77	+
            background-color: #000000;
78	+
            color: white;
79	+
            border: none;
80	+
            cursor: pointer;
81	+
        }
82	+
83	+
        button:hover {
84	+
            background-color: #1f1f1f;
85	+
        }
86	+
    </style>
87	+
</head>
88	+
89	+
<body>
90	+
    <div id="login" class="active">
91	+
92	+
<h2><b>Enter Password</b></h2>
93	+
        <input type="password" id="password" placeholder="Password">
94	+
        <button onclick="checkPassword()"><b>Enter</b></button>
95	+
    </div>
96	+
   <div id="chatRoom">
97	+
        <h2><b>Chat Room</b></h2>
98	+
        <div id="nameInput">
99	+
            <input type="text" id="username" placeholder="Enter your name">
100	+
<button onclick="setUsername()"><b>Join Chat</b></button>
101	+
        </div>
102	+
        <div id="chat" style="display: none;">
103	+
            <div id="messages"></div>
104	+
            <input type="text" id="message" placeholder="Type a message">
105	+
            <button onclick="sendMessage()"><b>Send</b></button>
106	+
        </div>
107	+
    </div>
108	+
109	+
    <script>
110	+
        const validPassword = /^(ppp)$/i; // Regex to accept any capitalization of "ppp"
111	+
112	+
        function checkPassword() {
113	+
            const passwordInput = document.getElementById('password').value;
114	+
            if (validPassword.test(passwordInput)) {
115	+
                document.getElementById('login').classList.remove('active');
116	+
                document.getElementById('chatRoom').classList.add('active');
117	+
            } else {
118	+
                alert('Incorrect Password');
119	+
            }
120	+
        }
121	+
122	+
        function setUsername() {
123	+
            const usernameInput = document.getElementById('username').value.trim();
124	+
            if (usernameInput) {
125	+
                document.getElementById('nameInput').style.display = 'none';
126	+
                document.getElementById('chat').style.display = 'block';
127	+
                document.getElementById('username').dataset.name = usernameInput;
128	+
            } else {
129	+
                alert('Please enter your name');
130	+
            }
131	+
        }
132	+
133	+
        function sendMessage() {
134	+
            const messageInput = document.getElementById('message');
135	+
            const message = messageInput.value.trim();
136	+
            const username = document.getElementById('username').dataset.name;
137	+
138	+
            if (message) {
139	+
                const messagesDiv = document.getElementById('messages');
140	+
                const newMessage = document.createElement('p');
141	+
                newMessage.textContent = `${username}: ${message}`;
142	+
                messagesDiv.appendChild(newMessage);
143	+
                messagesDiv.scrollTop = messagesDiv.scrollHeight; // Scroll to the bottom
144	+
                messageInput.value = '';
145	+
            } else {
146	+
                alert('Please type a message');
147	+
            }
148	+
        }
149	+
    </script>
150	+
</body>
151	+
152	+
</html>
