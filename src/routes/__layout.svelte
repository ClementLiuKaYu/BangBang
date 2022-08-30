<script>
	import '../styles/global.css';
	import { page } from '$app/stores';
	import logo from '$lib/images/logo.png';
	var style = $page.url.pathname == '/' ? 'width: 80%;' : 'width: 30%;';
	var header = $page.url.pathname == '/' ? 'justify-content: center;' : '';
	var onclick = () => {
		location.href = '/';
	};
</script>

<header style={header}>
	<img class="ms-5" src={logo} alt="" {style} on:click={onclick} />
	<!-- <h1 on:click={onclick}>bANG bANG.gg</h1> -->
</header>

<main>
	<slot />
</main>

<footer>
	<p>Copyright 2022 BangBang.GG</p>
</footer>

<style>
	header {
		display: flex;
	}
	/* h1 {
		font-family: BadBoyAndy;
	} */
	img:hover {
		cursor: pointer;
	}
	main {
		max-width: 80vw;
		margin: 20px auto;
		padding: 0 3vw;
	}
	footer {
		text-align: center;
	}
</style>
