<template>
	<div class="container">
		<img alt="Logo" src="../assets/logo.png">

		<h2>Providing lightspeed access to monkey pictures across the globe.</h2>


		<div class="text-center">
			<input placeholder="Search Token Mint" class="form-control">
		</div>

		<h3>Ecosystem</h3>
		<ul>
			<li><a href="https://api.degencdn.com/swagger/index.html" target="_blank">API Docs</a></li>
		</ul>
	</div>
</template>

<script>
export default {
	name: 'HelloWorld',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
	margin: 40px 0 0;
}

ul {
	list-style-type: none;
	padding: 0;
}

li {
	display: inline-block;
	margin: 0 10px;
}

h2 {
	text-transform: uppercase;
}

input:active, input:focus {
	background: transparent;
	box-shadow: none;
}

input::placeholder {
	color: white;
}

input {
	text-align: center;
	width: 60%;
	height: 50px;
	font-size: 40px;

	background: transparent;
	color: white;
	border: 2px solid white;
	margin: auto;
	margin-top: 5%;
}

.container {
	width: 60%;
	margin: auto;
}

.text-center {
	text-align: center;
}

img {
	max-width: 500px;
}
</style>
