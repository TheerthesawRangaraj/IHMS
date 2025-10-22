<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smart Hostel Management 2.0</title>
<style>
body {
  font-family: Arial, sans-serif;
  background: #eef3f7;
  margin: 0;
  padding: 0;
  text-align: center;
}
header {
  background: #004b8d;
  color: white;
  padding: 15px;
}
section {
  margin: 20px auto;
  background: white;
  padding: 20px;
  border-radius: 10px;
  width: 80%;
  max-width: 600px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}
input, textarea, button {
  margin: 5px;
  padding: 8px;
  border-radius: 5px;
  border: 1px solid #ccc;
  width: 80%;
}
button {
  background: #004b8d;
  color: white;
  cursor: pointer;
}
button:hover {
  background: #0066cc;
}
#chatBox, #chatBoxWarden {
  background: #f4f4f4;
  height: 150px;
  overflow-y: auto;
  margin-top: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  text-align: left;
  padding: 5px;
}
#heatmapGrid {
  display: grid;
  grid-template-columns: repeat(5, 40px);
  gap: 5px;
  justify-content: center;
}
.room-cell {
  width: 40px;
  height: 40px;
  border-radius: 5px;
  background: #c1e1c1;
}
#studentTodo, #wardenTodo {
  background: #fff;
  padding: 15px;
  border-radius: 10px;
  margin-top: 20px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
#studentTaskList li, #wardenTaskList li {
  list-style: none;
  padding: 6px;
  border-bottom: 1px solid #ddd;
  display: flex;
  justify-content: space-between;
}
#studentTaskList button, #wardenTaskList button {
  border: none;
  background: #eef;
  margin-left: 5px;
  cursor: pointer;
  border-radius: 5px;
}
</style>
</head>
<body>

<header>
  <h1>🏠 Smart Hostel Management System 2.0</h1>
</header>

<!-- Home Section -->
<section id="home">
  <h2>Welcome to SmartHostel</h2>
  <button onclick="showSection('studentRegister')">Student Portal</button>
  <button onclick="showSection('wardenRegister')">Warden Portal</button>
</section>

<!-- Student Register -->
<section id="studentRegister" style="display:none;">
  <h2>Student Registration</h2>
  <input id="regName" placeholder="Full Name"><br>
  <input id="regEmail" placeholder="Email"><br>
  <input id="regPass" placeholder="Password" type="password"><br>
  <button onclick="registerStudent()">Register</button>
  <button onclick="showSection('studentLogin')">Already Registered? Login</button><br>
  <button onclick="goBack('studentRegister','home')">⬅️ Back</button>
</section>

<!-- Student Login -->
<section id="studentLogin" style="display:none;">
  <h2>Student Login</h2>
  <input id="loginEmail" placeholder="Email"><br>
  <input id="loginPass" placeholder="Password" type="password"><br>
  <button onclick="loginStudent()">Login</button>
  <button onclick="goBack('studentLogin','home')">⬅️ Back</button>
</section>

<!-- Student Dashboard -->
<section id="studentDashboard" style="display:none;">
  <h2>👩‍🎓 Student Dashboard</h2>
  <button onclick="goBack('studentDashboard','home')">Logout</button>

  <h3>🏘 Room Booking</h3>
  <input id="room" placeholder="Enter Room Number">
  <input id="group" placeholder="Enter Group Members (comma)">
  <button onclick="bookRoom()">Book Room</button>
  <p id="bookingStatus"></p>

  <h3>🧰 Service Request</h3>
  <input id="serviceRoom" placeholder="Enter Room Number">
  <input id="serviceType" placeholder="Enter Service Type">
  <button onclick="requestService()">Submit Request</button>
  <p id="serviceStatus"></p>

  <h3>🕒 Leave Request</h3>
  <input type="datetime-local" id="leaveStart">
  <input type="datetime-local" id="leaveEnd">
  <textarea id="leaveReason" placeholder="Reason"></textarea><br>
  <button onclick="requestLeave()">Request Leave</button>

  <h3>💬 Chat with Warden</h3>
  <input id="chatInput" placeholder="Type message">
  <button onclick="sendChat()">Send</button>
  <button onclick="voiceToText('student')">🎙 Voice</button>
  <div id="chatBox"></div>

  <h3>📝 Student To-Do List</h3>
  <div id="studentTodo">
    <input type="text" id="studentTask" placeholder="Enter a new task">
    <button onclick="addStudentTask()">Add Task</button>
    <ul id="studentTaskList"></ul>
  </div>
</section>

<!-- Warden Register -->
<section id="wardenRegister" style="display:none;">
  <h2>Warden Registration</h2>
  <input id="wName" placeholder="Full Name"><br>
  <input id="wEmail" placeholder="Email"><br>
  <input id="wPass" placeholder="Password" type="password"><br>
  <button onclick="registerWarden()">Register</button>
  <button onclick="showSection('wardenLogin')">Already Registered? Login</button><br>
  <button onclick="goBack('wardenRegister','home')">⬅️ Back</button>
</section>

<!-- Warden Login -->
<section id="wardenLogin" style="display:none;">
  <h2>Warden Login</h2>
  <input id="loginWEmail" placeholder="Email"><br>
  <input id="loginWPass" placeholder="Password" type="password"><br>
  <button onclick="loginWarden()">Login</button>
  <button onclick="goBack('wardenLogin','home')">⬅️ Back</button>
</section>

<!-- Warden Dashboard -->
<section id="wardenDashboard" style="display:none;">
  <h2>🧑‍🏫 Warden Dashboard</h2>
  <button onclick="goBack('wardenDashboard','home')">Logout</button>

  <h3>🔥 Technician Heatmap</h3>
  <div id="heatmapGrid"></div>

  <h3>📋 Pending Leave Requests</h3>
  <div id="wardenRequests"></div>

  <h3>💬 Chat with Students</h3>
  <input id="wardenChatInput" placeholder="Type message">
  <button onclick="sendChatWarden()">Send</button>
  <button onclick="voiceToText('warden')">🎙 Voice</button>
  <div id="chatBoxWarden"></div>

  <h3>📋 Warden To-Do List</h3>
  <div id="wardenTodo">
    <input type="text" id="wardenTask" placeholder="Enter a new task">
    <button onclick="addWardenTask()">Add Task</button>
    <ul id="wardenTaskList"></ul>
  </div>
</section>

<script>
let students=[],wardens=[],rooms=[],services=[],leaveRequests=[],chatHistory=[],studentTasks=[],wardenTasks=[];

function showSection(id){document.querySelectorAll('section').forEach(s=>s.style.display='none');document.getElementById(id).style.display='block';}
function goBack(current,target){document.getElementById(current).style.display='none';document.getElementById(target).style.display='block';}

// Student functions
function
