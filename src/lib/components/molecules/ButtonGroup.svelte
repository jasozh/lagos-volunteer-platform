<script lang="ts">
  import type { Snippet } from "svelte";

  let { children }: { children: Snippet } = $props();
</script>

<div class="inline-flex space-x-[-1px]" role="group">{@render children()}</div>
