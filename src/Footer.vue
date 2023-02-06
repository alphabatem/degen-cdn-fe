<template>
	<footer class="py-1 small grey container-fluid">
		<div class="row">
			<div class="d-none d-md-block col text-start order-first">
				<span>v1.0.0 BETA</span>
			</div>
			<div class="col-sm-12 col-md-auto order-last order-md-1"><a target="_blank" href="https://alphabatem.com">Powered By AlphaBatem Labs</a></div>
			<div class="d-none d-md-block col text-end order-1 order-md-last">
				<a href="https://twitter.com/alpha_batem" target="_blank"><img alt="twitter" src="/img/twitter.png" style="filter: invert(1)" height="22px" ></a>
			</div>
		</div>
	</footer>
</template>

<script>
export default {
	name: "Footer"
}
</script>

<style scoped>
footer {
	background: #222;
	position: fixed;
	bottom: 0;
	color: grey;
	font-weight: bold;
}


a {
	text-decoration: none;
	text-underline: none;
	color: grey;
	transition: color 0.3s ease-in-out;
	animation: flicker 10s infinite;
}

a:hover {
	color: white;
}


@keyframes flicker {
	80% {
		color: grey;
	}
	90% {
		color: white;
	}
	100% {
		color: grey;
	}
}
</style>