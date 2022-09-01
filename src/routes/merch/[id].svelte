<script context="module">
</script>

<script>
	import { page } from '$app/stores';
	import { initializeApp } from 'firebase/app';
	import { getFirestore, getDoc, doc } from 'firebase/firestore';
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

	let title = '';
	let imgUrl = '';
	let details = [];

	getDoc(doc(db, 'merch', $page.params.id)).then((doc) => {
		console.log(doc.data());
		title = doc.data().title;
		details = doc.data().details;
		getDownloadURL(ref(storage, doc.data().img)).then((str) => {
			imgUrl = str;
		});
	});

	// var getNFT = (item) => {
	// 	switch (item) {
	// 		case 'nft1':
	// 			return nft1;
	// 		case 'nft2':
	// 			return nft2;
	// 		case 'nft3':
	// 			return nft3;
	// 		case 'nft4':
	// 			return nft4;
	// 		default:
	// 			return nft1;
	// 	}
	// };

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
		{title}
	</h1>
</div>

<div>
	<div class="col-8 offset-2">
		<img src={imgUrl} alt="" />
		<br /><br />
		<!-- <h3 class="paint" id={randomColor()} style="width: fit-content;">some text</h3> -->
		<br />
		{#each details as detail}
			<p>{detail}</p>
		{/each}
	</div>
</div>

<style>
	img {
		width: 100%;
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
