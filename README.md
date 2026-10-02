<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">

<title>CTE FUND RECEIPTS</title>

<script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>

<style>

* {
  font-family: Arial, sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background: #f0f4f8;
  padding: 12px;
  max-width: 100%;
  margin: 0 auto;
}

h1 {
  color: #1a365d;
  text-align: center;
  margin-bottom: 15px;
  font-size: 1.5rem;
}

.tab {
  display: flex;
  gap: 8px;
  margin-bottom: 20px;
  border-bottom: 2px solid #ddd;
  flex-wrap: wrap;
}

.tab-btn {
  flex: 1;
  min-width: 140px;
  padding: 12px 10px;
  border: none;
  background: transparent;
  cursor: pointer;
  font-size: 15px;
  text-align: center;
  touch-action: manipulation;
  position: relative;
  z-index: 10;
}

.tab-btn.active {
  border-bottom: 3px solid #2563eb;
  color: #2563eb;
  font-weight: bold;
}

.card {
  background: white;
  padding: 15px;
  border-radius: 10px;
  margin-bottom: 15px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  position: relative;
  z-index: 1;
  overflow-x: auto;
}

h2 {
  font-size: 1.1rem;
  margin-bottom: 12px;
  color: #333;
}

h3 {
  font-size: 1rem;
  margin: 12px 0 8px;
  color: #444;
}

input,
select {
  width: 100%;
  padding: 12px;
  margin: 6px 0 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 16px;
  position: relative;
  z-index: 2;
}

button {
  padding: 10px 14px;
  border: none;
  border-radius: 8px;
  font-size: 15px;
  cursor: pointer;
  font-weight: bold;
  touch-action: manipulation;
  position: relative;
  z-index: 5;
}

.btn-blue {
  background: #2563eb;
  color: white;
}

.btn-purple {
  background: #7c3aed;
  color: white;
}

.btn-red {
  background: #ef4444;
  color: white;
}

.btn-green {
  background: #22c55e;
  color: white;
}

.btn-orange {
  background: #f97316;
  color: white;
}

.btn-sm {
  padding: 6px 10px;
  font-size: 13px;
  margin: 2px;
}

.hidden {
  display: none !important;
}

.receipt {
  border: 2px solid #22c55e;
  background: #f0fdf4;
  padding: 20px;
  border-radius: 10px;
  margin-top: 15px;
  max-width: 100%;
}

.ref-code {
  font-family: monospace;
  font-size: 18px;
  font-weight: bold;
  color: #1e40af;
  background: #dbeafe;
  padding: 6px 10px;
  border-radius: 6px;
  display: inline-block;
  margin: 6px 0;
}

.fee-box {
  border: 2px solid #7c3aed;
  background: #f5f3ff;
  padding: 12px;
  border-radius: 8px;
  margin: 12px 0;
}

.checkbox-item {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 10px 0;
  cursor: pointer;
  flex-wrap: wrap;
}

.checkbox-item input[type="checkbox"] {
  width: auto;
  transform: scale(1.3);
  margin: 0;
}

.amount-input {
  width: 110px;
  padding: 10px;
  margin-left: auto;
  border: 1px solid #ccc;
  border-radius: 6px;
  flex-shrink: 0;
}

.total {
  font-size: 18px;
  font-weight: bold;
  color: #1e40af;
  margin-top: 12px;
}

.note {
  background: #fef3c7;
  border-left: 4px solid #f59e0b;
  padding: 10px;
  margin: 10px 0;
  border-radius: 4px;
  font-size: 14px;
}

.sub-tab {
  display: flex;
  gap: 6px;
  margin-bottom: 15px;
  flex-wrap: wrap;
  position: relative;
  z-index: 8;
}

.sub-tab-btn {
  flex: 1;
  min-width: 100px;
  padding: 10px 8px;
  border: none;
  background: #eee;
  cursor: pointer;
  border-radius: 8px;
  font-size: 14px;
}

.sub-tab-btn.active {
  background: #2563eb;
  color: white;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
  font-size: 13px;
}

th,
td {
  padding: 8px 6px;
  text-align: left;
  border-bottom: 1px solid #eee;
  vertical-align: middle;
}

th {
  background: #f8fafc;
  font-weight: bold;
  color: #475569;
  font-size: 13px;
}

.status-paid {
  color: #16a34a;
  font-weight: bold;
}

.status-unpaid {
  color: #f59e0b;
  font-weight: bold;
}

.empty {
  text-align: center;
  color: #888;
  padding: 20px;
  font-size: 14px;
}

.search {
  margin-bottom: 12px;
}

.action-col {
  white-space: nowrap;
  width: 130px;
}

.dev-credit {
  text-align: center;
  margin-top: 15px;
  color: #64748b;
  font-size: 13px;
}

.receipt-actions {
  margin-top: 15px;
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.receipt-actions button {
  flex: 1;
  min-width: 200px;
}

p {
  margin: 6px 0;
  font-size: 15px;
}

.download-status {
  margin-top: 10px;
  font-size: 14px;
  color: #2563eb;
  display: none;
}

.firebase-status {
  text-align: center;
  padding: 8px;
  margin-bottom: 10px;
  border-radius: 6px;
  font-size: 13px;
  background: #dcfce7;
  color: #166534;
}

</style>
</head>

<body>

<h1>CTE FUND RECEIPTS</h1>

<p class="dev-credit">
Developed by: BTLE ICT Developers
</p>

<div id="firebaseStatus" class="firebase-status">
Connecting to database...
</div>


<!-- =====================================================
     MAIN TABS
====================================================== -->

<div class="tab">

<button
  type="button"
  class="tab-btn active"
  onclick="switchMainTab('student', this)">
  Student
</button>

<button
  type="button"
  class="tab-btn"
  id="adminTabBtn"
  onclick="switchMainTab('admin', this)">
  CTE-CMETI
</button>

</div>


<!-- =====================================================
     STUDENT PORTAL
====================================================== -->

<div id="studentPortal">

<div class="card">

<h2>Student Account</h2>

<div class="sub-tab">

<button
  type="button"
  class="sub-tab-btn active"
  onclick="switchStudentTab('login', this)">
  Login
</button>

<button
  type="button"
  class="sub-tab-btn"
  onclick="switchStudentTab('register', this)">
  Register
</button>

</div>


<!-- LOGIN -->

<div id="studentLogin">

<input
  type="text"
  id="s_id"
  placeholder="Student ID Number">

<input
  type="password"
  id="s_pass"
  placeholder="Password">

<button
  type="button"
  class="btn-blue"
  onclick="studentLogin()">
  Sign In
</button>

</div>


<!-- REGISTER -->

<div id="studentRegister" class="hidden">

<input
  type="text"
  id="reg_name"
  placeholder="Full Name">

<input
  type="text"
  id="reg_id"
  placeholder="Student ID Number">

<input
  type="password"
  id="reg_pass"
  placeholder="Create Password">

<input
  type="password"
  id="reg_confirm"
  placeholder="Confirm Password">

<button
  type="button"
  class="btn-blue"
  onclick="studentRegister()">
  Register
</button>

</div>

</div>


<!-- STUDENT DASHBOARD -->

<div id="s_dashboard" class="card hidden">

<h2>
Welcome,
<span id="s_name"></span>
</h2>

<button
  type="button"
  class="btn-red"
  onclick="studentLogout()">
  Logout
</button>

<div class="note">
Fees and section are set by CTE-CMETI.
Receipt appears below.
</div>

<p>
<strong>Section:</strong>
<span id="s_sec">-</span>
</p>

<p>
<strong>Fees Selected:</strong>
<span id="s_fees">-</span>
</p>

<p>
<strong>Total Amount:</strong>
PHP <span id="s_total">0.00</span>
</p>


<!-- RECEIPT -->

<div id="s_receipt" class="receipt hidden">

<h3>OFFICIAL DIGITAL RECEIPT</h3>

<p>
<strong>Referral Code:</strong><br>
<span id="s_ref" class="ref-code"></span>
</p>

<p>
<strong>Student Name:</strong>
<span id="disp_name"></span>
</p>

<p>
<strong>Student ID:</strong>
<span id="disp_id"></span>
</p>

<p>
<strong>Section:</strong>
<span id="disp_sec"></span>
</p>

<p>
<strong>Fee(s) Paid:</strong>
<span id="disp_fees"></span>
</p>

<p>
<strong>Total Amount:</strong>
PHP <span id="disp_total"></span>
</p>

<p>
<strong>Date and Time:</strong>
<span id="disp_date"></span>
</p>

<p>
<strong>Status:</strong>
PAID
</p>

</div>


<div id="receiptActions"
     class="receipt-actions hidden">

<button
  type="button"
  class="btn-green"
  id="downloadBtn"
  onclick="downloadReceiptAsImage()">
  Download Receipt Image
</button>

<p
  id="downloadStatus"
  class="download-status">
Preparing download...
</p>

</div>

</div>

</div>


<!-- =====================================================
     ADMIN PORTAL
====================================================== -->

<div id="adminPortal" class="hidden">

<div class="card">

<h2>CTE-CMETI Login</h2>

<input
  type="password"
  id="a_pass"
  placeholder="Enter Password">

<button
  type="button"
  class="btn-purple"
  onclick="adminLogin()">
  Access Control Panel
</button>

</div>


<div id="a_dashboard" class="card hidden">

<h2>CMETI Control Panel</h2>

<button
  type="button"
  class="btn-red"
  onclick="adminLogout()">
  Logout
</button>


<div class="sub-tab">

<button
  type="button"
  class="sub-tab-btn active"
  onclick="switchAdminTab('generate', this)">
  Generate
</button>

<button
  type="button"
  class="sub-tab-btn"
  onclick="switchAdminTab('students', this)">
  Students
</button>

<button
  type="button"
  class="sub-tab-btn"
  onclick="switchAdminTab('paid', this)">
  Paid
</button>

</div>


<!-- GENERATE -->

<div id="adminGenerate">

<h3>1. Load Student</h3>

<input
  type="text"
  id="a_studentId"
  placeholder="Enter Student ID">

<button
  type="button"
  class="btn-blue"
  onclick="loadStudent()">
  Load Student
</button>

<p
  id="a_studentName"
  style="margin:10px 0;font-weight:bold">
</p>


<h3>2. Select Section</h3>

<select id="a_section">

<option value="">
-- Choose Section --
</option>

<option>
BTLE ICT 1st Year
</option>

<option>
BTLE ICT 2nd Year
</option>

<option>
BTLE ICT 3rd Year
</option>

</select>


<h3>
3. Select Fees and Enter Amount
</h3>

<div class="fee-box">


<label class="checkbox-item">

<input
  type="checkbox"
  id="f1"
  onchange="calcTotal()">

Org Membership Fee

<input
  type="number"
  id="amt1"
  class="amount-input"
  min="0"
  step="0.01"
  placeholder="PHP 0.00"
  oninput="calcTotal()">

</label>


<label class="checkbox-item">

<input
  type="checkbox"
  id="f2"
  onchange="calcTotal()">

Organizational Fines

<input
  type="number"
  id="amt2"
  class="amount-input"
  min="0"
  step="0.01"
  placeholder="PHP 0.00"
  oninput="calcTotal()">

</label>


<label class="checkbox-item">

<input
  type="checkbox"
  id="f3"
  onchange="calcTotal()">

Piso Daily

<input
  type="number"
  id="amt3"
  class="amount-input"
  min="0"
  step="0.01"
  placeholder="PHP 0.00"
  oninput="calcTotal()">

</label>


<label class="checkbox-item">

<input
  type="checkbox"
  id="f4"
  onchange="calcTotal()">

Contribution

<input
  type="number"
  id="amt4"
  class="amount-input"
  min="0"
  step="0.01"
  placeholder="PHP 0.00"
  oninput="calcTotal()">

</label>


<p class="total">
Total:
PHP <span id="totalAmt">0.00</span>
</p>

</div>


<button
  type="button"
  class="btn-green"
  onclick="generateReceipt()">
  Generate and Send Receipt
</button>

</div>


<!-- STUDENTS -->

<div id="adminStudents" class="hidden">

<h3>All Registered Students</h3>

<input
  type="text"
  class="search"
  id="searchStudents"
  placeholder="Search by ID..."
  oninput="renderStudentsList()">

<table id="studentsTable">

<thead>

<tr>
<th>#</th>
<th>ID</th>
<th>Status</th>
<th>Actions</th>
</tr>

</thead>

<tbody id="studentsBody">

<tr>
<td colspan="4" class="empty">
No registered students yet.
</td>
</tr>

</tbody>

</table>

</div>


<!-- PAID -->

<div id="adminPaid" class="hidden">

<h3>All Paid Records</h3>

<input
  type="text"
  class="search"
  id="searchPaid"
  placeholder="Search by ID or Ref..."
  oninput="renderPaidList()">

<table id="paidTable">

<thead>

<tr>
<th>Ref</th>
<th>ID</th>
<th>Section</th>
<th>Total</th>
<th>Date</th>
<th>Actions</th>
</tr>

</thead>

<tbody id="paidBody">

<tr>
<td colspan="6" class="empty">
No payment records yet.
</td>
</tr>

</tbody>

</table>

</div>

</div>

</div>


<!-- =====================================================
     FIREBASE + JAVASCRIPT
====================================================== -->

<script type="module">

import {
  initializeApp
} from "https://www.gstatic.com/firebasejs/12.19.0/firebase-app.js";

import {
  getFirestore,
  collection,
  doc,
  getDoc,
  getDocs,
  setDoc,
  updateDoc,
  deleteDoc,
  serverTimestamp
} from "https://www.gstatic.com/firebasejs/12.19.0/firebase-firestore.js";


// ======================================================
// YOUR FIREBASE CONFIG
// ======================================================

const firebaseConfig = {

  apiKey:
    "AIzaSyAUTp9deGmfo3s8yZ-Op2vMJQhG1jaKJBo",

  authDomain:
    "cte-cmeti-student-registration.firebaseapp.com",

  projectId:
    "cte-cmeti-student-registration",

  storageBucket:
    "cte-cmeti-student-registration.firebasestorage.app",

  messagingSenderId:
    "84734206314",

  appId:
    "1:84734206314:web:7704b45746fd9155b0c513",

  measurementId:
    "G-NCR103904X"

};


// ======================================================
// INITIALIZE FIREBASE
// ======================================================

const app = initializeApp(firebaseConfig);

const db = getFirestore(app);


// Database connection message

document.getElementById("firebaseStatus").textContent =
  "Firebase database connected";


let currentStudent = null;

let selectedStudent = null;


// ======================================================
// HASH
// ======================================================

function hash(s) {

  let h = 0;

  for (let i = 0; i < s.length; i++) {

    h =
      ((h << 5) - h) +
      s.charCodeAt(i);

  }

  return Math.abs(h).toString(16);

}


// ======================================================
// REFERENCE CODE
// ======================================================

function refCode(name, id, section) {

  return (

    name.slice(0, 3) +
    "-" +
    id.slice(-3) +
    "-" +
    section.slice(0, 3)

  ).toUpperCase();

}


// ======================================================
// DOWNLOAD RECEIPT
// ======================================================

async function downloadReceiptAsImage() {

  const receipt =
    document.getElementById("s_receipt");

  const button =
    document.getElementById("downloadBtn");

  const status =
    document.getElementById("downloadStatus");


  if (!receipt) return;


  button.disabled = true;

  button.textContent = "Creating...";

  status.style.display = "block";


  try {

    if (typeof html2canvas === "undefined") {

      throw new Error(
        "Wait 3 seconds and try again."
      );

    }


    const canvas =
      await html2canvas(receipt, {

        scale: 2,

        useCORS: true,

        logging: false,

        backgroundColor: "#f0fdf4"

      });


    const link =
      document.createElement("a");


    link.download =
      "CTE-Receipt-" +
      (
        document.getElementById("s_ref")
          .textContent ||
        "Receipt"
      ) +
      ".png";


    link.href =
      canvas.toDataURL(
        "image/png",
        1.0
      );


    document.body.appendChild(link);

    link.click();

    document.body.removeChild(link);


    status.textContent =
      "Download started. Check your Downloads folder.";


  } catch (e) {

    alert(
      "Error: " +
      e.message
    );

    status.textContent =
      "Download failed. Try again.";

  }


  setTimeout(function() {

    button.disabled = false;

    button.textContent =
      "Download Receipt Image";

    status.style.display = "none";

    status.textContent =
      "Preparing download...";

  }, 3000);

}


// ======================================================
// MAIN TAB
// ======================================================

function switchMainTab(tabName, btn) {

  document
    .querySelectorAll(".tab-btn")
    .forEach(function(x) {

      x.classList.remove("active");

    });


  if (btn) {

    btn.classList.add("active");

  }


  if (tabName === "student") {

    document
      .getElementById("studentPortal")
      .classList.remove("hidden");

    document
      .getElementById("adminPortal")
      .classList.add("hidden");

  }

  else {

    document
      .getElementById("studentPortal")
      .classList.add("hidden");

    document
      .getElementById("adminPortal")
      .classList.remove("hidden");

  }

}


// ======================================================
// STUDENT TAB
// ======================================================

function switchStudentTab(tabName, btn) {

  document
    .querySelectorAll(
      "#studentPortal .sub-tab-btn"
    )
    .forEach(function(x) {

      x.classList.remove("active");

    });


  if (btn) {

    btn.classList.add("active");

  }


  if (tabName === "login") {

    document
      .getElementById("studentLogin")
      .classList.remove("hidden");

    document
      .getElementById("studentRegister")
      .classList.add("hidden");

  }

  else {

    document
      .getElementById("studentLogin")
      .classList.add("hidden");

    document
      .getElementById("studentRegister")
      .classList.remove("hidden");

  }

}


// ======================================================
// ADMIN TAB
// ======================================================

async function switchAdminTab(tabName, btn) {

  document
    .querySelectorAll(
      "#adminPortal .sub-tab-btn"
    )
    .forEach(function(x) {

      x.classList.remove("active");

    });


  if (btn) {

    btn.classList.add("active");

  }


  document
    .getElementById("adminGenerate")
    .classList.add("hidden");

  document
    .getElementById("adminStudents")
    .classList.add("hidden");

  document
    .getElementById("adminPaid")
    .classList.add("hidden");


  if (tabName === "generate") {

    document
      .getElementById("adminGenerate")
      .classList.remove("hidden");

  }

  else if (tabName === "students") {

    document
      .getElementById("adminStudents")
      .classList.remove("hidden");

    await renderStudentsList();

  }

  else if (tabName === "paid") {

    document
      .getElementById("adminPaid")
      .classList.remove("hidden");

    await renderPaidList();

  }

}


// ======================================================
// STUDENT REGISTER
// ======================================================

async function studentRegister() {

  const name =
    document
      .getElementById("reg_name")
      .value
      .trim();


  const id =
    document
      .getElementById("reg_id")
      .value
      .trim();


  const pass =
    document
      .getElementById("reg_pass")
      .value;


  const confirmPass =
    document
      .getElementById("reg_confirm")
      .value;


  if (!name || !id || !pass) {

    return alert(
      "Fill all fields."
    );

  }


  if (pass !== confirmPass) {

    return alert(
      "Passwords do not match."
    );

  }


  if (pass.length < 4) {

    return alert(
      "Password must be at least 4 characters."
    );

  }


  try {

    const studentRef =
      doc(
        db,
        "students",
        id
      );


    const studentSnap =
      await getDoc(studentRef);


    if (studentSnap.exists()) {

      return alert(
        "Student ID already exists. Login instead."
      );

    }


    await setDoc(
      studentRef,
      {

        name: name,

        studentId: id,

        pw: hash(pass),

        receipt: null,

        createdAt:
          serverTimestamp()

      }
    );


    alert(
      "Registered successfully.\n\n" +
      "Name: " +
      name +
      "\nID: " +
      id
    );


    document.getElementById("reg_name")
      .value = "";

    document.getElementById("reg_id")
      .value = "";

    document.getElementById("reg_pass")
      .value = "";

    document.getElementById("reg_confirm")
      .value = "";


    switchStudentTab(

      "login",

      document.querySelector(
        "#studentPortal .sub-tab-btn"
      )

    );


  }

  catch (error) {

    console.error(error);

    alert(
      "Registration failed.\n\n" +
      error.message
    );

  }

}


// ======================================================
// STUDENT LOGIN
// ======================================================

async function studentLogin() {

  const id =
    document
      .getElementById("s_id")
      .value
      .trim();


  const pass =
    document
      .getElementById("s_pass")
      .value;


  if (!id || !pass) {

    return alert(
      "Enter ID and password."
    );

  }


  try {

    const studentRef =
      doc(
        db,
        "students",
        id
      );


    const studentSnap =
      await getDoc(studentRef);


    if (!studentSnap.exists()) {

      return alert(
        "Student not found. Register first."
      );

    }


    const user =
      studentSnap.data();


    if (
      user.pw !== hash(pass)
    ) {

      return alert(
        "Wrong password."
      );

    }


    currentStudent = {

      id: id,

      name: user.name

    };


    document.getElementById("s_name")
      .textContent =
      currentStudent.name;


    document
      .querySelector(
        "#studentPortal > .card"
      )
      .classList.add("hidden");


    document
      .getElementById("s_dashboard")
      .classList.remove("hidden");


    await loadReceipt();

  }

  catch (error) {

    console.error(error);

    alert(
      "Login failed.\n\n" +
      error.message
    );

  }

}


// ======================================================
// STUDENT LOGOUT
// ======================================================

function studentLogout() {

  location.reload();

}


// ======================================================
// LOAD RECEIPT
// ======================================================

async function loadReceipt() {

  if (!currentStudent) return;


  try {

    const studentRef =
      doc(
        db,
        "students",
        currentStudent.id
      );


    const studentSnap =
      await getDoc(studentRef);


    if (!studentSnap.exists()) return;


    const user =
      studentSnap.data();


    if (user.receipt) {

      const receipt =
        user.receipt;


      document.getElementById("s_sec")
        .textContent =
        receipt.section;


      document.getElementById("s_fees")
        .textContent =
        receipt.fees;


      document.getElementById("s_total")
        .textContent =
        receipt.total;


      document.getElementById("s_receipt")
        .classList.remove("hidden");


      document.getElementById("receiptActions")
        .classList.remove("hidden");


      document.getElementById("s_ref")
        .textContent =
        receipt.ref;


      document.getElementById("disp_name")
        .textContent =
        receipt.name;


      document.getElementById("disp_id")
        .textContent =
        receipt.id;


      document.getElementById("disp_sec")
        .textContent =
        receipt.section;


      document.getElementById("disp_fees")
        .textContent =
        receipt.fees;


      document.getElementById("disp_total")
        .textContent =
        receipt.total;


      document.getElementById("disp_date")
        .textContent =
        receipt.date;

    }

  }

  catch (error) {

    console.error(error);

    alert(
      "Unable to load receipt.\n\n" +
      error.message
    );

  }

}


// ======================================================
// ADMIN LOGIN
// ======================================================

function adminLogin() {

  if (
    document.getElementById("a_pass").value !==
    "CTEs2026ef"
  ) {

    return alert(
      "Wrong password."
    );

  }


  document
    .querySelector(
      "#adminPortal > .card"
    )
    .classList.add("hidden");


  document
    .getElementById("a_dashboard")
    .classList.remove("hidden");

}


// ======================================================
// ADMIN LOGOUT
// ======================================================

function adminLogout() {

  location.reload();

}


// ======================================================
// LOAD STUDENT
// ======================================================

async function loadStudent() {

  const id =
    document
      .getElementById("a_studentId")
      .value
      .trim();


  if (!id) {

    return alert(
      "Enter Student ID."
    );

  }


  try {

    const studentRef =
      doc(
        db,
        "students",
        id
      );


    const studentSnap =
      await getDoc(studentRef);


    if (!studentSnap.exists()) {

      return alert(
        "Student not found. Ask the student to register first."
      );

    }


    const user =
      studentSnap.data();


    selectedStudent = {

      id: id,

      name: user.name

    };


    document.getElementById("a_studentName")
      .textContent =
      "Student: " + user.name;

  }

  catch (error) {

    console.error(error);

    alert(
      "Could not load student.\n\n" +
      error.message
    );

  }

}


// ======================================================
// CALCULATE TOTAL
// ======================================================

function calcTotal() {

  let total = 0;


  if (
    document.getElementById("f1").checked
  ) {

    total +=
      parseFloat(
        document.getElementById("amt1").value
      ) || 0;

  }


  if (
    document.getElementById("f2").checked
  ) {

    total +=
      parseFloat(
        document.getElementById("amt2").value
      ) || 0;

  }


  if (
    document.getElementById("f3").checked
  ) {

    total +=
      parseFloat(
        document.getElementById("amt3").value
      ) || 0;

  }


  if (
    document.getElementById("f4").checked
  ) {

    total +=
      parseFloat(
        document.getElementById("amt4").value
      ) || 0;

  }


  document.getElementById("totalAmt")
    .textContent =
    total.toFixed(2);

}


// ======================================================
// GENERATE RECEIPT
// ======================================================

async function generateReceipt() {

  if (!selectedStudent) {

    return alert(
      "Load student first."
    );

  }


  const section =
    document.getElementById("a_section")
      .value;


  if (!section) {

    return alert(
      "Select section."
    );

  }


  let fees = [];

  let total = 0;

  let amount = 0;


  if (
    document.getElementById("f1").checked
  ) {

    amount =
      parseFloat(
        document.getElementById("amt1").value
      ) || 0;


    if (amount <= 0) {

      return alert(
        "Enter valid amount for Org Membership Fee."
      );

    }


    fees.push(
      "Org Membership Fee - PHP " +
      amount.toFixed(2)
    );


    total += amount;

  }


  if (
    document.getElementById("f2").checked
  ) {

    amount =
      parseFloat(
        document.getElementById("amt2").value
      ) || 0;


    if (amount <= 0) {

      return alert(
        "Enter valid amount for Organizational Fines."
      );

    }


    fees.push(
      "Organizational Fines - PHP " +
      amount.toFixed(2)
    );


    total += amount;

  }


  if (
    document.getElementById("f3").checked
  ) {

    amount =
      parseFloat(
        document.getElementById("amt3").value
      ) || 0;


    if (amount <= 0) {

      return alert(
        "Enter valid amount for Piso Daily."
      );

    }


    fees.push(
      "Piso Daily - PHP " +
      amount.toFixed(2)
    );


    total += amount;

  }


  if (
    document.getElementById("f4").checked
  ) {

    amount =
      parseFloat(
        document.getElementById("amt4").value
      ) || 0;


    if (amount <= 0) {

      return alert(
        "Enter valid amount for Contribution."
      );

    }


    fees.push(
      "Contribution - PHP " +
      amount.toFixed(2)
    );


    total += amount;

  }


  if (!fees.length) {

    return alert(
      "Select at least one fee."
    );

  }


  const feeSummary =
    fees.join(" | ");


  const totalText =
    total.toFixed(2);


  const ref =
    refCode(
      selectedStudent.name,
      selectedStudent.id,
      section
    );


  const dateText =
    new Date().toLocaleString();


  try {

    const studentRef =
      doc(
        db,
        "students",
        selectedStudent.id
      );


    await updateDoc(
      studentRef,
      {

        receipt: {

          ref: ref,

          name:
            selectedStudent.name,

          id:
            selectedStudent.id,

          section:
            section,

          fees:
            feeSummary,

          total:
            totalText,

          date:
            dateText

        }

      }
    );


    alert(

      "Receipt sent.\n" +

      "Ref: " +
      ref +

      "\nStudent ID: " +
      selectedStudent.id +

      "\nTotal: PHP " +
      totalText

    );


    document.getElementById("a_section")
      .value = "";


    document.getElementById("f1")
      .checked = false;

    document.getElementById("f2")
      .checked = false;

    document.getElementById("f3")
      .checked = false;

    document.getElementById("f4")
      .checked = false;


    document.getElementById("amt1")
      .value = "";

    document.getElementById("amt2")
      .value = "";

    document.getElementById("amt3")
      .value = "";

    document.getElementById("amt4")
      .value = "";


    document.getElementById("totalAmt")
      .textContent = "0.00";


    document.getElementById("a_studentName")
      .textContent = "";


    document.getElementById("a_studentId")
      .value = "";


    selectedStudent = null;

  }

  catch (error) {

    console.error(error);

    alert(
      "Failed to save receipt.\n\n" +
      error.message
    );

  }

}


// ======================================================
// SHOW STUDENTS
// ======================================================

async function renderStudentsList() {

  const body =
    document.getElementById("studentsBody");


  body.innerHTML =
    '<tr><td colspan="4" class="empty">' +
    'Loading...' +
    '</td></tr>';


  const queryText =
    (
      document.getElementById("searchStudents")
        ? document.getElementById("searchStudents").value
        : ""
    )
    .toLowerCase();


  try {

    const snapshot =
      await getDocs(
        collection(
          db,
          "students"
        )
      );


    let entries = [];


    snapshot.forEach(function(docSnap) {

      entries.push({

        id:
          docSnap.id,

        data:
          docSnap.data()

      });

    });


    entries =
      entries.filter(function(entry) {

        return (
          !queryText ||
          entry.id
            .toLowerCase()
            .includes(queryText)
        );

      });


    if (!entries.length) {

      body.innerHTML =
        '<tr><td colspan="4" class="empty">' +
        'No registered students found.' +
        '</td></tr>';

      return;

    }


    body.innerHTML =
      entries.map(
        function(entry, index) {

          const id =
            entry.id;

          const data =
            entry.data;


          const statusHtml =
            data.receipt

              ? '<span class="status-paid">PAID</span>'

              : '<span class="status-unpaid">UNPAID</span>';


          const clearBtn =
            data.receipt

              ? '<button type="button" ' +
                'class="btn-orange btn-sm" ' +
                'onclick="removePaymentRec(\'' +
                id +
                '\')">Clear</button>'

              : "";


          return (

            '<tr>' +

            '<td>' +
            (index + 1) +
            '</td>' +

            '<td>' +
            id +
            '</td>' +

            '<td>' +
            statusHtml +
            '</td>' +

            '<td class="action-col">' +

            clearBtn +

            '<button type="button" ' +
            'class="btn-red btn-sm" ' +
            'onclick="deleteStudentAcc(\'' +
            id +
            '\')">Delete</button>' +

            '</td>' +

            '</tr>'

          );

        }
      ).join("");

  }

  catch (error) {

    console.error(error);

    body.innerHTML =
      '<tr><td colspan="4" class="empty">' +
      'Error loading students.' +
      '</td></tr>';

    alert(
      "Error loading students.\n\n" +
      error.message
    );

  }

}


// ======================================================
// SHOW PAID RECORDS
// ======================================================

async function renderPaidList() {

  const body =
    document.getElementById("paidBody");


  body.innerHTML =
    '<tr><td colspan="6" class="empty">' +
    'Loading...' +
    '</td></tr>';


  const queryText =
    (
      document.getElementById("searchPaid")
        ? document.getElementById("searchPaid").value
        : ""
    )
    .toLowerCase();


  try {

    const snapshot =
      await getDocs(
        collection(
          db,
          "students"
        )
      );


    let users = [];


    snapshot.forEach(function(docSnap) {

      const data =
        docSnap.data();


      if (data.receipt) {

        users.push(data);

      }

    });


    const paid =
      users.filter(function(x) {

        return (

          !queryText ||

          x.receipt.id
            .toLowerCase()
            .includes(queryText) ||

          x.receipt.ref
            .toLowerCase()
            .includes(queryText)

        );

      });


    if (!paid.length) {

      body.innerHTML =
        '<tr><td colspan="6" class="empty">' +
        'No payment records found.' +
        '</td></tr>';

      return;

    }


    body.innerHTML =
      paid.map(function(x) {

        return (

          '<tr>' +

          '<td>' +
          x.receipt.ref +
          '</td>' +

          '<td>' +
          x.receipt.id +
          '</td>' +

          '<td>' +
          x.receipt.section +
          '</td>' +

          '<td>PHP ' +
          x.receipt.total +
          '</td>' +

          '<td>' +
          x.receipt.date +
          '</td>' +

          '<td class="action-col">' +

          '<button type="button" ' +
          'class="btn-orange btn-sm" ' +
          'onclick="removePaymentRec(\'' +
          x.receipt.id +
          '\')">' +
          'Remove' +
          '</button>' +

          '<button type="button" ' +
          'class="btn-red btn-sm" ' +
          'onclick="deleteStudentAcc(\'' +
          x.receipt.id +
          '\')">' +
          'Delete' +
          '</button>' +

          '</td>' +

          '</tr>'

        );

      }).join("");

  }

  catch (error) {

    console.error(error);

    body.innerHTML =
      '<tr><td colspan="6" class="empty">' +
      'Error loading payment records.' +
      '</td></tr>';

  }

}


// ======================================================
// REMOVE PAYMENT
// ======================================================

async function removePaymentRec(id) {

  if (
    !confirm(
      "Remove payment record for ID: " +
      id +
      "?"
    )
  ) {

    return;

  }


  try {

    await updateDoc(

      doc(
        db,
        "students",
        id
      ),

      {

        receipt: null

      }

    );


    alert(
      "Payment record removed."
    );


    await renderStudentsList();

    await renderPaidList();

  }

  catch (error) {

    console.error(error);

    alert(
      "Failed to remove payment.\n\n" +
      error.message
    );

  }

}


// ======================================================
// DELETE STUDENT
// ======================================================

async function deleteStudentAcc(id) {

  if (
    !confirm(
      "Delete all data for ID: " +
      id +
      "? This cannot be undone."
    )
  ) {

    return;

  }


  try {

    await deleteDoc(

      doc(
        db,
        "students",
        id
      )

    );


    alert(
      "Student deleted."
    );


    await renderStudentsList();

    await renderPaidList();

  }

  catch (error) {

    console.error(error);

    alert(
      "Failed to delete student.\n\n" +
      error.message
    );

  }

}


// ======================================================
// MAKE FUNCTIONS AVAILABLE TO HTML
// ======================================================

window.switchMainTab =
  switchMainTab;

window.switchStudentTab =
  switchStudentTab;

window.switchAdminTab =
  switchAdminTab;

window.studentRegister =
  studentRegister;

window.studentLogin =
  studentLogin;

window.studentLogout =
  studentLogout;

window.adminLogin =
  adminLogin;

window.adminLogout =
  adminLogout;

window.loadStudent =
  loadStudent;

window.calcTotal =
  calcTotal;

window.generateReceipt =
  generateReceipt;

window.renderStudentsList =
  renderStudentsList;

window.renderPaidList =
  renderPaidList;

window.removePaymentRec =
  removePaymentRec;

window.deleteStudentAcc =
  deleteStudentAcc;

window.downloadReceiptAsImage =
  downloadReceiptAsImage;

</script>

</body>
</html>
