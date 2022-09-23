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

		const querySnapshot = await getDocs(collection(db, 'media'));
		querySnapshot.forEach(async (doc) => {
			console.log(doc.data().link);
			// getDownloadURL(ref(storage, doc.data().img))
			data.push({ ...doc.data(), id: doc.id });
		});

		for (let i = 0; i < data.length; i++) {
			const url = await getDownloadURL(ref(storage, data[i].img));
			data[i].img = url;
		}

		return { props: { data } };
	}
</script>

<script>
	export let data;

	var onclick = (link) => {
		location.href = 'gallery/' + link;
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
		<div class="paint" id={randomColor()}>media exposure</div>
	</div>
</div>
<br />
<br />
<div>
	<div class="row row-cols-lg-3 row-cols-md-2 row-cols-1 gx-5">
		{#each data as nft}
			<div class="imgCard col">
				<a href={nft.link} target="_blank">
					<img src={nft.img} alt="" />
				</a>
				<br /> <br />
				<div class="paint paintSub" id={randomColor()} style="width: fit-content;">
					<h3>{nft.title}</h3>
				</div>
				<br />
				{#each nft.info as item}
					<p>{item}</p>
				{/each}
				<br />
			</div>
		{/each}
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
		font-size: 35px;
		padding: 20px;
	}
	.paint {
		aspect-ratio: 2000/650;
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		background-size: contain;
		padding: 0px;
	}

	.paintSub {
		width: 100%;
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
		font-size: large;
	}
	@media (max-width: 960px) {
		p {
			font-size: medium;
		}
	}
	@media (max-width: 640px) {
		p {
			font-size: medium;
		}
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
