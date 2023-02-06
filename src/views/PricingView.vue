<template>
	<div class="container mb-5">
		<h1 class="">Pricing</h1>


		<div class="row mt-4">
			<div class="col-sm-12 col-lg-4 mb-3 mb-lg-0">
				<div class="card h-100">
					<div class="card-header">
						<h3>FREE</h3>
					</div>
					<div class="card-body pt-0">
						<ul>
							<li>Public API Access</li>
							<li>60 Calls / Minute</li>
							<li>Verified collections</li>
						</ul>
					</div>
					<div class="card-footer">
						<h4>FREE!</h4>
					</div>
				</div>
			</div>
			<div class="col-sm-12 col-lg-4 mb-3 mb-lg-0">
				<div class="card h-100">
					<div class="card-header">
						<h3>BUILDER</h3>
					</div>
					<div class="card-body pt-0">
						<ul>
							<li>Public API Access</li>
							<li>600 Calls / Minute</li>
							<li>All collections</li>
							<li>Media Queries</li>
						</ul>
					</div>
					<div class="card-footer">
						<h4><img alt="USDC" src="/img/usdc.png" height="28px"> USDC 10 / Month</h4>
					</div>
				</div>
			</div>
			<div class="col-sm-12 col-lg-4 mb-3 mb-lg-0">
				<div class="card h-100">
					<div class="card-header">
						<h3>ENTERPRISE</h3>
					</div>
					<div class="card-body pt-0">
						<ul>
							<li>Public API Access</li>
							<li>Unlimited Calls / Minute</li>
							<li>All collections</li>
							<li>Media Queries</li>
							<li>Customer Support</li>
						</ul>
					</div>
					<div class="card-footer">
						<h4><img alt="USDC" src="/img/usdc.png" height="28px"> USDC 40 / Month</h4>
					</div>
				</div>
			</div>
		</div>

		<h2 class="mt-5 text-start">Collections</h2>
		<div class="row mt-3">
			<div class="card">
				<div class="card-body text-start">
					<h5 class=""><img alt="" src="/img/verify.png" height="24px"> Verification</h5>
					<p>Verify your collection to enable access via our free plan by providing a hash list of all your collections NFT's. All verified collections will receive priority
						delivery over unverified collections.</p>

					<h5 class="mt-4"><i class="fa fa-download fa-fw"></i> Preload</h5>
					<p>Starting a collection and want to ensure all your images are delivered at lightning pace? Our preload platform allows collections to pay a small fee for all of
						their images to be pre-loaded into the CDN ready for delivery! This only ever needs to be done one per collection and is not a requirement for your collection to be
					on the CDN.</p>

					<h5 class="mt-4"><i class="fa fa-bolt fa-fw"></i> Dynamic Collections</h5>
					<p>Doing something cool with NFTs, Or just regularly updating your art? Upgrade to dynamic delivery to ensure your collection is always updated any time you make a
						change. Stale images & pre-reveal are a thing of a past!</p>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "PricingView"
}
</script>

<style scoped>
.card {
	background: #111;
}

ul {
	color: white;
	list-style: none;
}

li {
	font-weight: bold;
	margin: 1rem;
}

h5 i {
	color: #1D9BF0;
}
</style>