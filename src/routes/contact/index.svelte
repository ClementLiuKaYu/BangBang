<script>
	import discord from '$lib/images/Discord.png';
	import facebook from '$lib/images/Facebook.png';
	import instagram from '$lib/images/Instagram.png';
	import telegram from '$lib/images/Telegram.png';
	import twitter from '$lib/images/Twitter.png';
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

	var width;

	var onclick = (link) => {
		location.href = link;
	};
</script>

<svelte:window bind:innerWidth={width} />
<div class="contentBox" style={width > 640 ? 'aspect-ratio: 16/9;' : 'aspect-ratio: 9/16;'}>
	<div class="boxTitle">
		<div id="title">
			<div class="paint" id={randomColor()}>
				<div>Contact me daddy~</div>
			</div>
		</div>
	</div>

	<div class="contactRow">
		<div class="contactCol">
			<img
				src={telegram}
				alt=""
				style="transform: rotate(10deg); cursor: pointer;"
				on:click={() => onclick('https://t.me/+QcWRmoVfgUlkMjhl')}
			/>
			<img
				src={discord}
				alt=""
				style="transform: rotate(-10deg); cursor: pointer;"
				on:click={() => onclick('https://discord.gg/Vgzay6QRQv')}
			/>
			<img
				src={instagram}
				alt=""
				style="transform: rotate(-20deg); cursor: pointer;"
				on:click={() => onclick('https://instagram.com/bangbang.gg_nftgallery?igshid=YmMyMTA2M2Y=')}
			/>
		</div>
		<div class="contactCol">
			<img
				src={twitter}
				alt=""
				style="transform: rotate(10deg); cursor: pointer;"
				on:click={() => onclick('https://twitter.com/bang_bang_gg?s=21&t=oBC5oTQTIcBFcLlBbf4teA')}
			/>
			<img
				src={facebook}
				alt=""
				style="transform: rotate(20deg); cursor: pointer;"
				on:click={() =>
					onclick('https://www.facebook.com/Bang-banggg-NFT-Gallery-104860165622105/')}
			/>
		</div>
	</div>
</div>

<style>
	.contentbox {
		position: relative;
		aspect-ratio: 16/9;
		width: 100%;
	}
	.boxTitle {
		display: flex;
		justify-content: center;
		align-items: center;
	}
	#title {
		aspect-ratio: 2000/1218;
		/* width: fit-content; */
		background-image: url('$lib/images/frame.png');
		background-size: cover;
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		font-family: Andrew;
		font-size: medium;
		padding: 20px;
	}
	.paint {
		aspect-ratio: 2000/650;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		text-align: center;
		/* background-image: url('$lib/images/green.png'); */
		background-size: cover;
		padding: 20px;
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
	img {
		width: 90%;
	}
	.contactRow {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.contactCol {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
</style>
