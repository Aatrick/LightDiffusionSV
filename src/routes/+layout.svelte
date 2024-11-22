<script lang="ts">
	import Header from './Header.svelte';
	import { ModeWatcher } from "mode-watcher";
	import '../app.css';

	let { children } = $props();
</script>

<div class="app">
	<Header />

	<main>
		<ModeWatcher />
		{@render children()}
	</main>

	<footer>
		<p>
			All rights reserved. <a href="https://github.com/Aatrick/LightDiffusion">LightDiffusion.</a> Under GNU General Public License.
		</p>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
