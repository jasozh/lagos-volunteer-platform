<script lang="ts">
  import type { Snippet } from "svelte";

  let {
    children,
    size = "md",
    variant = "light",
    position = "standard",
  }: {
    children: Snippet;
    size?: "icon" | "xs" | "sm" | "md" | "lg" | "xl";
    variant?: "light";
    position?: "standard" | "start" | "middle" | "end";
  } = $props();

  const dimensions = {
    icon: "p-2.5",
    xs: "px-3 py-2 text-xs font-medium",
    sm: "px-3 py-2 text-sm font-medium",
    md: "px-5 py-2.5 text-sm font-medium",
    lg: "px-5 py-3 text-base font-medium",
    xl: "px-6 py-3.5 text-base font-medium",
  }[size];

  const color = {
    light:
      "text-gray-900 bg-white border-gray-300 focus:outline-none hover:bg-gray-100 active:bg-gray-200 focus-visible:ring-4 focus-visible:ring-gray-100 dark:bg-gray-800 dark:text-white dark:border-gray-600 dark:hover:bg-gray-700 dark:hover:border-gray-600 dark:focus-visible:ring-gray-700 dark:active:bg-gray-600",
  }[variant];

  const border = {
    standard: "rounded-lg",
    start: "rounded-s-lg",
    middle: "",
    end: "rounded-e-lg",
  }[position];
</script>

<button
  type="button"
  class={[
    "inline-flex items-center border text-center focus-visible:z-10",
    dimensions,
    color,
    border,
  ]}
>
  {@render children()}
</button>
