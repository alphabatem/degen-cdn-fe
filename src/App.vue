<template>
	<div id="app">
		<nav>
			<router-link to="/">Home</router-link>
			|
			<router-link to="/pricing">Pricing</router-link>
			|
			<a href="https://api.degencdn.com/swagger/index.html" target="_blank">Docs</a>
		</nav>
		<router-view/>
		<Footer></Footer>
	</div>
</template>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
}

nav {
	padding: 30px;
}

nav a {
	font-weight: bold;
	color: white;
}

nav a.router-link-exact-active {
	color: cornflowerblue;
}

a {
	color: cornflowerblue;
	text-decoration: none;
}

html, body {
	font-family: 'Inter', serif;
	background: black;
	color: white;
}

h1, h2, h3, h4, h5, h6, p, i {
	font-family: 'Inter', serif;
	color: white;
}

</style>
<script>
import Footer from "@/Footer";
export default {
	components: {Footer}
}
</script>