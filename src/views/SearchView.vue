<template>
	<div class="container">
		<h1>{{ $route.params.id }}</h1>

		<div class="row">
			<div class="img-container">
				<img alt="" :src="previewLink" class="img-fluid">
			</div>
			<div class=" mt-2">
				<button @click="toggleOriginal" class="btn btn-outline-light">Original</button>
			</div>
		</div>

		<div class="row mt-5">
			<div class="col-8 offset-2 text-start">

				<p class="mb-0">Original Image Link: </p>
				<code>{{ imageFileUri || 'N/A' }}</code>

				<p class="mb-0 mt-3">Original Media Link: </p>
				<code class="mt-5">{{ mediaUri || 'N/A' }}</code>

				<p class="mb-0 mt-3">Direct Image Link: </p>
				<code>{{ directLink + '/image' || 'N/A' }}</code>

				<p class="mb-0 mt-3">Direct Media Link: </p>
				<code class="mt-5">{{ mediaUri ? directLink + '/media' : 'N/A' }}</code>
			</div>
		</div>

	</div>
</template>

<script>
export default {
	name: "SearchView",
	data() {
		return {
			showOriginal: false,
			media: {}
		}
	},
	computed: {
		previewLink: function () {
			if (this.showOriginal)
				return this.imageFileUri

			return this.directLink + '/image';
		},
		imageFileUri: function () {
			return this.media?.imageUri
		},
		mediaUri: function () {
			return this.media?.mediaUri
		},
		directLink: function () {
			return `https://api.degencdn.com/v1/nfts/${this.$route.params.id}`
		}
	},
	methods: {
		toggleOriginal: function () {
			this.showOriginal = !this.showOriginal
		},

		getMedia: function (tokenMint) {

			fetch(`https://api.degencdn.com/v1/nfts/${tokenMint}`).then((r) => r.json()).then(r => {
				this.media = r
			}).catch(e => {
				console.error("Error", e)
			})
		}
	},
	mounted() {
		this.getMedia(this.$route.params.id)
	}
}
</script>

<style scoped>
.img-fluid {
	max-width: 500px;
}

p {
	color: white;
}
</style>