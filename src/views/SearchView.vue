<template>
	<div class="container">
		<h1>{{ $route.params.id }}</h1>

		<div class="row mt-5">
			<div class="col text-start">
				<h3>Details</h3>

				<p class="mb-0 mt-3">Token Mint:</p>
				<code>{{ media.mint }}</code>

				<p class="mb-0 mt-3">Direct Image Link: </p>
				<code>{{ directLink + '/image' + (media.imageType ? `.${media.imageType}` : '') || 'N/A' }}</code>

				<p class="mb-0 mt-3">Direct Media Link: </p>
				<code class="mt-5">{{ mediaUri ? directLink + '/media' + (media.mediaType ? `.${media.mediaType}` : '') : 'N/A' }}</code>

				<p class="mb-0 mt-3">Original Image Link: </p>
				<code>{{ imageFileUri || 'N/A' }}</code>

				<p class="mb-0 mt-3">Original Media Link: </p>
				<code class="mt-5">{{ mediaUri || 'N/A' }}</code>
			</div>
			<div class="col">
				<div class="img-container">
					<img id="preview-img" alt="" :src="previewLink" class="img-fluid loading" @load="toggleImageLoading">
				</div>
				<div class=" mt-2" v-if="media.imageType !== 'gif'">
					<router-link to="/" class="btn btn-outline-light me-3">Back</router-link>
					<button @click="toggleOriginal" class="btn btn-outline-light">Original</button>
				</div>
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
		toggleImageLoading: function () {
			document.getElementById('preview-img').classList.toggle('loading')
		},

		toggleOriginal: function () {
			this.showOriginal = !this.showOriginal
			this.toggleImageLoading()
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
	min-height: 500px;
	min-width: 500px;
	background: rgba(255, 255, 255, 0.6);
	transition: all 0.3s ease;
	border-radius: 7px;
}

.img-fluid.loading {
	opacity: 0;
	animation: fadeBg 3s ease-in-out infinite;
}

@keyframes fadeBg {
	0% {
		opacity: 0.4;
	}
	50% {
		opacity: 1;
	}
	100% {
		opacity: 0.4;
	}
}

p {
	color: white;
}

</style>