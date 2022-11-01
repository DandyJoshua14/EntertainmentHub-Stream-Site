<script lang="js">
	import { error } from '@sveltejs/kit';

	import { Button, Input } from 'sveltestrap';

	let authloginCode = 3772;
	let authentication = false;
	let focused = false;
	/**
	 * @type {number}
	 */
	let logincode;
	async function auth() {
		if (parseInt(`${logincode}`) === authloginCode) {
			alert('Login Successful');
			setTimeout(() => {
				authentication = true;
				console.log('Success');
			});
		} else {
			alert('Authentication Failed X');
			authentication = false;
			console.log('Auth Failed');
			throw new Error('Auth Failed');
		}
	}
</script>

<body>
	{#if authentication === true}
		<section id="section">
			<div style="padding:75% 0 0 0;position:relative;">
				<iframe
					src="https://player.vimeo.com/video/766036370?h=c082b4f122&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479"
					frameborder="0"
					allow="autoplay; fullscreen; picture-in-picture"
					allowfullscreen
					style="position:absolute;top:0;left:0;width:100%;height:100%;"
					title="Meeting Video.mp4"
				/>
			</div>
			<script src="https://player.vimeo.com/api/player.js"></script>
		</section>
	{:else if authentication === false}
		<center class="login">
			<h3>Please Enter security code</h3>
			<form on:submit|preventDefault={auth}>
				<input
					class:promo={focused}
					on:focus={() => (focused = true)}
					bind:value={logincode}
					style="width:500px; heigth: 50px; border: 4px solid; font-size: 2rem; text-align: center; padding: 10px;"
				/>
				<p>If your done kindly press "ENTER"</p>
				<button color="btn-btn-success">Submit</button>
			</form>
		</center>
	{/if}
</body>

<style>
	button {
		background-color: aqua;
		border: 2px solid black;
		width: 80px;
		height: 50px;
		border-radius: 10px;
		box-shadow: none;
		font-size: large;
		transition: 1s;
	}

	button:hover {
		transition: 0.5s;
		background-color: aqua;
		border: 3px solid royalblue;
		border-radius: 10px;
		box-shadow: none;
		font-size: large;
	}
	#section {
		transition: 2s;
	}

	.login {
		transition: 2s;
	}
</style>
