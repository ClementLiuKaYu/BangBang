<script context="module">
	import { initializeApp } from 'firebase/app';
	import { getFirestore, collection, getDocs } from 'firebase/firestore';
	import { getStorage, ref, getDownloadURL } from 'firebase/storage';

	const firebaseConfig = {
		apiKey: 'AIzaSyBVCSuGuWCt95tEKRGBYaFuZQErHIlHfIM',
		authDomain: 'bang-bang-website.firebaseapp.com',
		projectId: 'bang-bang-website',
		storageBucket: 'bang-bang-website.appspot.com',
		messagingSenderId: '540414532551',
		appId: '1:540414532551:web:4811ef1fdc640390dcd7e2',
		measurementId: 'G-HKKMVXR8XH'
	};
	const app = initializeApp(firebaseConfig);
	const db = getFirestore(app);
	const storage = getStorage(app);

	export async function load() {
		let data = [];

		const querySnapshot = await getDocs(collection(db, 'gallery'));
		querySnapshot.forEach(async (doc) => {
			// getDownloadURL(ref(storage, doc.data().img))
			data.push({ ...doc.data() });
		});

		for (let i = 0; i < data.length; i++) {
			const url = await getDownloadURL(ref(storage, data[i].img));
			data[i].img = url;
		}

		return { props: { data } };
	}
</script>

<script>
	import nft1 from '$lib/images/NFT_1.png';
	import nft2 from '$lib/images/NFT_2.png';
	import nft3 from '$lib/images/NFT_3.png';
	import nft4 from '$lib/images/NFT_4.png';
	import { each } from 'svelte/internal';

	export let data;

	var onclick = (link) => {
		location.href = link;
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

<div class="boxTitle">
	<div id="title">
		<div class="paint" id={randomColor()}>gallery</div>
	</div>
</div>
<br />
<br />
<div>
	<div class="row row-cols-md-2 row-cols-1 gx-5">
		{#each data as nft}
			<div class="imgCard col">
				<img src={nft.img} alt="" on:click={() => onclick('gallery/nft1')} />
				<br /> <br />
				<div class="paint" id={randomColor()} style="width: fit-content;">
					<h3>{nft.title}</h3>
				</div>
				<br />
				{#each nft.info as item}
					<p>{item}</p>
				{/each}
				<br />
			</div>
		{/each}
		<!-- <div class="imgCard col">
			<img src={nft2} alt="" on:click={() => onclick('gallery/nft2')} />
			<br /> <br />
			<div class="paint" id={randomColor()} style="width: fit-content;">
				<h3>some text</h3>
			</div>
			<br />
			<p>
				some description for this nft Lorem ipsum dolor sit amet consectetur adipisicing elit. Sit
				impedit pariatur recusandae repellat sunt reprehenderit nobis optio voluptate, dolorum ea et
				reiciendis cum consequatur consequuntur accusamus ratione molestias facere quidem?
			</p>
		</div>
		<div class="imgCard col">
			<img src={nft3} alt="" on:click={() => onclick('gallery/nft3')} />
			<br /><br />
			<div class="paint" id={randomColor()} style="width: fit-content;">
				<h3>some text</h3>
			</div>
			<br />
			<p>
				some description for this nft Lorem ipsum dolor sit amet consectetur adipisicing elit. Sit
				impedit pariatur recusandae repellat sunt reprehenderit nobis optio voluptate, dolorum ea et
				reiciendis cum consequatur consequuntur accusamus ratione molestias facere quidem?
			</p>
		</div>
		<div class="imgCard col">
			<img src={nft4} alt="" on:click={() => onclick('gallery/nft4')} />
			<br /><br />
			<div class="paint" id={randomColor()} style="width: fit-content;">
				<h3>some text</h3>
			</div>
			<br />
			<p>
				some description for this nft Lorem ipsum dolor sit amet consectetur adipisicing elit. Sit
				impedit pariatur recusandae repellat sunt reprehenderit nobis optio voluptate, dolorum ea et
				reiciendis cum consequatur consequuntur accusamus ratione molestias facere quidem?
			</p>
		</div> -->
	</div>
</div>

<style>
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
		font-size: x-large;
		padding: 20px;
	}
	.paint {
		aspect-ratio: 2000/650;
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		/* background-image: url('$lib/images/green.png'); */
		background-size: cover;
		padding: 20px;
	}
	.imgCard {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	img {
		width: 100%;
	}
	img:hover {
		cursor: pointer;
	}
	h3 {
		font-family: Andrew;
		text-align: center;
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
