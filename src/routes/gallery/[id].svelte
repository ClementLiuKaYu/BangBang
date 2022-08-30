<script>
	import { page } from '$app/stores';
	import nft1 from '$lib/images/NFT_1.png';
	import nft2 from '$lib/images/NFT_2.png';
	import nft3 from '$lib/images/NFT_3.png';
	import nft4 from '$lib/images/NFT_4.png';

	var getNFT = (item) => {
		switch (item) {
			case 'nft1':
				return nft1;
			case 'nft2':
				return nft2;
			case 'nft3':
				return nft3;
			case 'nft4':
				return nft4;
			default:
				return nft1;
		}
	};

	var colors = ['green', 'blue', 'grass', 'peach', 'yellow', 'orange', 'purple'];

	var last;
	var randomColor = () => {
		var color = colors[Math.floor(Math.random() * colors.length)];
		if (color == last) {
			return randomColor();
		}
		last = color;
		return color;
	};
</script>

<div class="d-flex justify-content-center mb-3">
	<h1 class="paint" id={randomColor()} style="text-align: center; width: fit-content;">
		{$page.params.id}
	</h1>
</div>

<div>
	<div class="col-8 offset-2">
		<img src={getNFT($page.params.id)} alt="" />
		<br /><br />
		<!-- <h3 class="paint" id={randomColor()} style="width: fit-content;">some text</h3> -->
		<br />
		<p>
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad ea fugit, dignissimos odio
			possimus quidem illo tempora natus provident nostrum consectetur perferendis voluptates
			voluptatum sequi aliquam? Harum magni ipsum veniam itaque, earum architecto commodi illum
			exercitationem accusamus quis atque. Tempora voluptas hic maiores reprehenderit magnam rem,
			suscipit dicta quis cumque!
		</p>
	</div>
</div>

<style>
	img {
		width: 100%;
	}
	p {
		padding: 0 8%;
	}
	#grass {
		background-image: url('$lib/images/green.png');
		background-size: cover;
	}
	#orange {
		background-image: url('$lib/images/orange.png');
		background-size: cover;
	}
	#yellow {
		background-image: url('$lib/images/yellow.png');
		background-size: cover;
	}
	#purple {
		background-image: url('$lib/images/purple.png');
		background-size: cover;
	}
	#peach {
		background-image: url('$lib/images/peach.png');
		background-size: cover;
	}
	#blue {
		background-image: url('$lib/images/blue.png');
		background-size: cover;
	}
	#green {
		background-image: url('$lib/images/green.png');
		background-size: cover;
	}
</style>
