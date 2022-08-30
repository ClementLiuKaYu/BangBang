<script>
	let list = [
		{
			title: 'events',
			link: '',
			id: 'grass',
			pos: 'bottom: 30%; left: 20%; transform: rotate(15deg); width:20%;',
			posMob: 'top: 25%; left: 0%; transform: rotate(-15deg); width:40%;'
		},
		{
			title: 'gallaries',
			link: 'gallery',
			id: 'orange',
			pos: 'top: 15%; left: 35%; transform: rotate(-10deg); width:25%;',
			posMob: 'top: 5%; left: 20%; transform: rotate(-5deg); width:60%;'
		},
		{
			title: 'contact me daddy~',
			link: 'contact',
			id: 'yellow',
			pos: 'top: 5%; left: 60%; transform: rotate(20deg); width:25%;',
			posMob: 'top: 25%; right: 0%; transform: rotate(35deg); width:50%;'
		},
		{
			title: 'bang your news',
			link: '',
			id: 'purple',
			pos: 'top: 35%; left: 70%; transform: rotate(-5deg); width:25%;',
			posMob: 'bottom: 40%; right: 0%; transform: rotate(15deg); width:50%;'
		},
		{
			title: 'merch?',
			link: '',
			id: 'peach',
			pos: 'top: 40%; left: 40%; transform: rotate(10deg); width:30%;',
			posMob: 'top: 40%; left: 10%; transform: rotate(5deg); width:40%;'
		},
		{
			title: 'newsletter',
			link: '',
			id: 'blue',
			pos: 'bottom: 5%; left: 5%; transform: rotate(-10deg); width:25%;',
			posMob: 'bottom: 30%; left: 0%; transform: rotate(-10deg); width:45%;'
		},
		{
			title: "Don't click this button please",
			link: 'https://www.youtube.com/watch?v=xm3YgoEiEDc&t=238s',
			id: 'green',
			pos: 'bottom: 5%; right: 10%; transform: rotate(-10deg); width:30%;',
			posMob: 'bottom: 10%; left: 20%; transform: rotate(-15deg); width:70%;'
		}
	];

	var onclick = (link) => {
		location.href = link;
	};

	var width;
</script>

<svelte:window bind:innerWidth={width} />
<div class="contentbox" style={width > 640 ? 'aspect-ratio: 16/9;' : 'aspect-ratio: 9/16;'}>
	{#each list as item}
		<div
			class="link col"
			style={width > 640 ? item.pos : item.posMob}
			on:click={() => {
				onclick(item.link);
			}}
		>
			<div class="paint" id={item.id}>
				{item.title}
			</div>
		</div>
	{/each}
</div>

<style>
	.contentbox {
		position: relative;
		aspect-ratio: 16/9;
		width: 100%;
	}
	.link {
		aspect-ratio: 2000/1218;
		background-image: url('$lib/images/frame.png');
		background-size: cover;
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		font-family: Andrew;
		font-size: x-large;
		position: absolute;
		padding: 10px;
	}
	@media (max-width: 960px) {
		.link {
			font-size: medium;
		}
	}
	@media (max-width: 640px) {
		.link {
			font-size: medium;
		}
	}
	.link:hover {
		cursor: pointer;
	}
	.paint {
		width: 100%;
		aspect-ratio: 2000/800;
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
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
