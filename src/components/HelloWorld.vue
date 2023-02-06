<template>
	<div class="container">
		<h1 class="mb-4">DegenCDN</h1>

		<h2 class="mb-4">Providing lightspeed access to monkey pictures across the globe.</h2>

		<img ref="previewImage" id="previewImage" :src="previewImage" alt="" onload="this.style.opacity = 1;">

		<div class="text-center">
			<form @submit="onSearch">
				<input required minlength="44" maxlength="44" type="text" v-model="search" placeholder="Search Token Address" class="form-control">
				<div class="row">
					<div class="col"></div>
					<div class="col">
						<button type="submit" class="btn btn-outline-light mt-3 w-100">FIND IMAGE</button>
					</div>
					<div class="col">
						<button @click="onRandom" class="btn btn-outline-light mt-3 w-100">RANDOM IMAGE</button>
					</div>
					<div class="col"></div>
				</div>
			</form>
		</div>
	</div>
</template>

<script>
export default {
	name: 'HelloWorld',
	data() {
		return {
			search: "",
			stats: {
				files_served: 0,
				images_stored: 0,
				requests_served: 0,
			},
			previewIdx: 0,
			randomMints: [
				"8JXwdjngz3Tkqap4j2CvwBdBfPnG2zxRqTxhqACu2Dw8",
				"655qdz9PH7XSxQpppxv3s5DR6i3RdT5t95GMdvVKu3Rk",
				"6ALCPSGeL6g8WLyPc7vxwvcGdUg9YETuCrA27UX7PGXb",
				"G1ZsvtoRboggVwtLeXzFX7eXrcKdTEzHnnnboh5khh25",
				"DWVb3bAfc6rqVtDEK22BrUbJihsxbCeDSbTwZnpo7ytS",
				"BUzRgZi3ehVEWxoVCuPfjkT1c2Ru471tdtMtj6vM8Dgw",
			]
		}
	},
	computed: {
		previewImage: function () {
			return `https://api.degencdn.com/v1/nfts/${this.randomMints[this.previewIdx]}/image.jpg`
		}
	},
	methods: {
		onRandom: function (e) {
			e.preventDefault()

			this.search = this.randomMints[Math.floor(Math.random() * this.randomMints.length)]

			this.$router.push(`/search/${this.search}`)
		},

		onSearch: function (e) {
			e.preventDefault()
			if (this.search.length < 16)
				return

			this.$router.push(`/search/${this.search}`)
		},
		getStats: function () {
			fetch("https://api.degencdn.com/stats").then(r => r.json()).then(r => {
				this.stats = r
			}).catch(e => {
				console.log(e)
			})
		}
	},
	mounted() {
		this.getStats()
		setInterval(() => {
			this.$refs.previewImage.style.opacity = 0
			setTimeout(() => {
				this.previewIdx++
				if (this.previewIdx >= this.randomMints.length)
					this.previewIdx = 0
			}, 600)
		}, 5000)
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#previewImage {
	transition: all 0.8s ease;
	opacity: 0;
	border-radius: 7px;
}

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
	font-size: 1.5rem;

	background: transparent;
	color: white;
	border: 2px solid white;
	margin: auto;
	margin-top: 5%;
}

.text-center {
	text-align: center;
}

img {
	max-width: 400px;
}
</style>
