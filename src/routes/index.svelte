<script>
	import { Geolocation } from '@capacitor/geolocation';

	let loc = null;
	async function getCurrentPosition() {
		const res = await Geolocation.getCurrentPosition();
		loc = res;
	}

	import { Camera, CameraResultType } from '@capacitor/camera'; 
	let image_src = null;
	async function getImage() {
		const image = await Camera.getPhoto({
			quality: 90,
			allowEditing: true,
			resultType: CameraResultType.Uri
		});
		image_src = image.webPath;
		
	}
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<div>
	<h1>Geolocation</h1>
	<p>Your location is:</p>
	<p>Latitude: {loc?.coords.latitude}</p>
	<p>Longitude: {loc?.coords.longitude}</p>

	<button class="bg-green-500" on:click={getCurrentPosition}> Get Current Location </button>
</div>

<div>
	<h1>Camera</h1>
	<img src="{image_src}" alt="" />
	<button class="bg-green-500" on:click="{getImage}">getImage</button>
</div>