<script lang="ts">
  let { size = "md" }: { size?: "sm" | "md" } = $props();

  const styles = {
    sm: "h-5 w-5",
    md: "h-6 w-6",
  }[size];
</script>

<svg
  class="{styles} text-gray-800 dark:text-white"
  aria-hidden="true"
  xmlns="http://www.w3.org/2000/svg"
  width="24"
  height="24"
  fill="none"
  viewBox="0 0 24 24"
>
  <path
    stroke="currentColor"
    stroke-linecap="round"
    stroke-linejoin="round"
    stroke-width="2"
    d="M8 18V6l8 6-8 6Z"
  />
</svg>
