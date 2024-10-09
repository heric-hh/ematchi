<script lang="ts">
	import { getTwemojiUrl } from './utils'
	import { send } from './transitions'

	export let emoji: string
	export let selected: boolean
	export let found: boolean
	export let group: 'a' | 'b'
</script>

<div class="square" class:flipped={selected || found}>
	<button on:click />
	<div class="background" />
	{#if !found}
		<img
			alt={emoji}
			src={getTwemojiUrl(emoji)}
			out:send={{ key: `${emoji}:${group}` }}
		/>
	{/if}
</div>

<style>
	.square {
		display: flex;
		justify-content: center;
		align-items: center;
		transform-style: preserve-3d;
		transition: transform 0.4s;
	}

	.flipped {
		transform: rotateY(180deg);
	}

	.background {
		position: absolute;
		background: #eee;
		transform: rotateY(180deg);
		backface-visibility: hidden;
		width: 100%;
		height: 100%;
	}

	button {
		position: absolute;
		width: 100%;
		height: 100%;
		backface-visibility: hidden;
		background: white;
		border: 0.5em solid #eee;
		border-radius: 1em;
		font-size: inherit;
	}

	img {
		width: 6em;
		height: 6em;
		pointer-events: none;
		transform: rotateY(180deg);
		backface-visibility: hidden;
	}
</style>
