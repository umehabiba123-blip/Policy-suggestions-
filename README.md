# Policy-suggestions-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Policy Suggestion Portal</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background-color: #ffffff;
        color: #004d26;
        margin: 0;
        padding: 0;
    }
    header {
        background-color: #006633;
        color: white;
        padding: 15px;
        text-align: center;
        font-size: 1.5em;
        font-weight: bold;
    }
    .container {
        max-width: 800px;
        margin: 20px auto;
        padding: 15px;
    }
    select, textarea, button {
        width: 100%;
        padding: 10px;
        margin-top: 10px;
        font-size: 1em;
        border: 1px solid #ccc;
        border-radius: 5px;
    }
    button {
        background-color: #006633;
        color: white;
        cursor: pointer;
        border: none;
    }
    button:hover {
        background-color: #004d26;
    }
    .suggestions {
        margin-top: 20px;
    }
    .suggestion {
        border: 1px solid #ccc;
        border-left: 5px solid #006633;
        padding: 10px;
        margin-bottom: 10px;
        background: #f9f9f9;
    }
</style>
</head>
<body>

<header>Shape the Future — Your Policy Ideas Matter</header>

<div class="container">
    <h2>Submit Your Suggestion</h2>
    <select id="department">
        <option value="">Select Department</option>
        <option>Education</option>
        <option>Health</option>
        <option>Infrastructure</option>
        <option>Security</option>
        <option>Transport</option>
        <option>Energy</option>
        <option>Environment</option>
        <option>Economy</option>
    </select>
    <textarea id="opinion" placeholder="Write your policy suggestion here..." rows="4"></textarea>
    <button onclick="submitOpinion()">Submit</button>

    <h2>View Suggestions</h2>
    <select id="viewDept" onchange="viewSuggestions()">
        <option value="">Select Department</option>
        <option>Education</option>
        <option>Health</option>
        <option>Infrastructure</option>
        <option>Security</option>
        <option>Transport</option>
        <option>Energy</option>
        <option>Environment</option>
        <option>Economy</option>
    </select>
    
    <div class="suggestions" id="suggestionsList"></div>
</div>

<script>
    let data = {};

    function submitOpinion() {
        const dept = document.getElementById('department').value;
        const opinion = document.getElementById('opinion').value.trim();
        
        if (!dept || !opinion) {
            alert("Please select a department and write your suggestion.");
            return;
        }
        
        if (!data[dept]) data[dept] = [];
        data[dept].push(opinion);
        
        document.getElementById('opinion').value = "";
        alert("Your suggestion has been added!");
    }

    function viewSuggestions() {
        const dept = document.getElementById('viewDept').value;
        const listDiv = document.getElementById('suggestionsList');
        listDiv.innerHTML = "";
        
        if (!dept || !data[dept] || data[dept].length === 0) {
            listDiv.innerHTML = "<p>No suggestions yet for this department.</p>";
            return;
        }
        
        data[dept].forEach(op => {
            const div = document.createElement('div');
            div.className = 'suggestion';
            div.textContent = op;
            listDiv.appendChild(div);
        });
    }
</script>

</body>
</html>
