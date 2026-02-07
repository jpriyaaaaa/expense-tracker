<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Smart Expense Tracker</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(135deg, #4facfe, #00f2fe);
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }

    .container {
        background: #fff;
        width: 350px;
        padding: 20px;
        border-radius: 10px;
        box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }

    h2 {
        text-align: center;
        color: #333;
    }

    input {
        width: 100%;
        padding: 8px;
        margin: 5px 0;
        border-radius: 5px;
        border: 1px solid #ccc;
    }

    button {
        width: 100%;
        padding: 10px;
        background: #2563eb;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        margin-top: 8px;
    }

    button:hover {
        background: #1e40af;
    }

    ul {
        list-style: none;
        padding: 0;
        margin-top: 10px;
    }

    li {
        display: flex;
        justify-content: space-between;
        background: #f3f4f6;
        padding: 8px;
        border-radius: 5px;
        margin-bottom: 5px;
    }

    .delete {
        color: red;
        cursor: pointer;
        font-weight: bold;
    }

    .total {
        text-align: center;
        margin-top: 10px;
        font-weight: bold;
    }
</style>
</head>
<body>

<div class="container">
    <h2>Expense Tracker</h2>

    <input type="text" id="title" placeholder="Expense Title">
    <input type="number" id="amount" placeholder="Amount">

    <button onclick="addExpense()">Add Expense</button>

    <ul id="list"></ul>

    <div class="total">
        Total: ₹ <span id="total">0</span>
    </div>
</div>

<script>
    let total = 0;

    function addExpense() {
        const title = document.getElementById("title").value;
        const amount = document.getElementById("amount").value;

        if (title === "" || amount === "") {
            alert("Please enter all details");
            return;
        }

        const li = document.createElement("li");
        li.innerHTML = `${title} - ₹${amount} 
        <span class="delete" onclick="removeExpense(this, ${amount})">×</span>`;

        document.getElementById("list").appendChild(li);

        total += parseInt(amount);
        document.getElementById("total").innerText = total;

        document.getElementById("title").value = "";
        document.getElementById("amount").value = "";
    }

    function removeExpense(element, amount) {
        element.parentElement.remove();
        total -= amount;
        document.getElementById("total").innerText = total;
    }
</script>

</body>
</html>
