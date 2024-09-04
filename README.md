Hello 
```
<!DOCTYPE html>
<html>
<head>
	<title>Loan App</title>
	<style>
		/* Add your CSS styles here */
		body {
			font-family: Arial, sans-serif;
		}
		.loan-form {
			max-width: 300px;
			margin: 40px auto;
		}
		label {
			display: block;
			margin-bottom: 10px;
		}
		input[type="number"] {
			width: 100%;
			height: 30px;
			margin-bottom: 20px;
			padding: 10px;
			box-sizing: border-box;
		}
		button[type="submit"] {
			width: 100%;
			height: 40px;
			background-color: #4CAF50;
			color: #fff;
			padding: 10px;
			border: none;
			border-radius: 5px;
			cursor: pointer;
		}
		button[type="submit"]:hover {
			background-color: #3e8e41;
		}
	</style>
</head>
<body>
	<h1>Loan App</h1>
	<form class="loan-form">
		<label for="loan-amount">Loan Amount:</label>
		<input type="number" id="loan-amount" required>
		<label for="interest-rate">Interest Rate (%):</label>
		<input type="number" id="interest-rate" required>
		<label for="loan-term">Loan Term (years):</label>
		<input type="number" id="loan-term" required>
		<button type="submit">Calculate</button>
	</form>
	<div id="loan-results">
		<!-- Loan results will be displayed here -->
	</div>
	<script>
		// Loan calculator variables
		let loanAmount = 0;
		let interestRate = 0;
		let loanTerm = 0;
		
		// Calculate monthly payment
		function calculateMonthlyPayment() {
			let monthlyInterestRate = interestRate / 1200;
			let months = loanTerm * 12;
			let monthlyPayment = loanAmount * monthlyInterestRate * Math.pow(1 + monthlyInterestRate, months) / (Math.pow(1 + monthlyInterestRate, months) - 1);
			return monthlyPayment.toFixed(2);
		}
		
		// Handle form submission
		document.querySelector('.loan-form').addEventListener('submit', (e) => {
			e.preventDefault();
			loanAmount = document.getElementById('loan-amount').value;
			interestRate = document.getElementById('interest-rate').value;
			loanTerm = document.getElementById('loan-term').value;
			let monthlyPayment = calculateMonthlyPayment();
			document.getElementById('loan-results').innerHTML = 'Monthly Payment: $' + monthlyPayment;
		});
	</script>
</body>
</html>
```
