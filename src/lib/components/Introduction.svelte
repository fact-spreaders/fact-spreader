<script lang="ts">
	import L from '../state/L.svelte'

	interface Props {
		onclick: () => void
	}

	let { onclick }: Props = $props()
	let introductionHtml = $derived(L.introduction())
</script>

<div class="overflow-scroll p-4">
	<!-- eslint-disable-next-line svelte/no-at-html-tags -->
	{@html introductionHtml}
	<div class="pt-2 text-center">
		<button class="variant-filled btn" {onclick} data-testid="intro-lets-go-btn">
			{L.letsGo()}
		</button>
	</div>
</div>
