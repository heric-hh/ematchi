<script lang="ts">
	import { getTwemojiUrl } from './utils'
	import { receive } from './transitions'
	export let found: string[]
</script>

<div class="found">
	{#each found as emoji (emoji)}
		<div class="pair">
			<img
				alt={emoji}
				src={getTwemojiUrl(emoji)}
				in:receive={{ key: `${emoji}:a` }}
			/>
			<img
				alt={emoji}
				src={getTwemojiUrl(emoji)}
				in:receive={{ key: `${emoji}:b` }}
			/>
		</div>
	{/each}
</div>

<style>
	.found {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 0.5em;
		height: 100%;
		filter: drop-shadow(0.2em 0.2em 0.5em rgba(0, 0, 0, 0.3));
	}
	img {
		position: absolute;
		width: 2em;
		height: 2em;
	}

	.pair {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 4em;
		height: 4em;
		background: white;
		border-radius: 50%;
		padding: 1em;
	}
</style>
