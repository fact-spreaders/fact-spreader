<script lang="ts">
	interface Props {
		class?: string
		onclick: () => void
	}

	let { class: className = '', onclick }: Props = $props()
</script>

<button
	type="button"
	class="variant-filled-success btn-icon btn-icon-sm {className}"
	{onclick}
	aria-label="Add"
>
	<svg class="h-6 w-6" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
		<path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z" />
	</svg>
</button>
