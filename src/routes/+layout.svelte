<script>
    export const prerender = true;

    import "../app.css";
    import { navigating } from "$app/stores";
    import { fade } from "svelte/transition";
    import favicon from "$lib/assets/favicon.svg";

    let { children } = $props();
</script>

<svelte:head>
    <link rel="icon" href={favicon} />
    <title>Manish Acharya</title>
</svelte:head>

<main class="transition-container">
    {#key $navigating}
        <div
            class="transition-item"
            in:fade={{ duration: 300 }}
            out:fade={{ duration: 300 }}
        >
            {@render children()}
        </div>
    {/key}
</main>

<style>
    .transition-container {
        display: grid;
        grid-template-areas: "content";
        min-height: 100vh;
        width: 100%;
        position: relative;
    }

    .transition-item {
        grid-area: content;
        width: 100%;
        min-height: 100vh;
    }
</style>
