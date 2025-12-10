<script>
    import { onMount } from "svelte";

    let { text, class: className = "", oncomplete } = $props();

    let displayText = $state(text);
    const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    let interval = null;

    function hackerEffect() {
        let iterations = 0;

        clearInterval(interval);

        interval = setInterval(() => {
            displayText = text
                .split("")
                .map((letter, index) => {
                    if (index < iterations) {
                        return text[index];
                    }

                    if (letter === " " || letter === "\n") {
                        return letter;
                    }

                    return letters[Math.floor(Math.random() * 26)];
                })
                .join("");

            if (iterations >= text.length) {
                clearInterval(interval);
                if (oncomplete) oncomplete();
            }

            iterations += 1 / 3;
        }, 30);
    }

    onMount(() => {
        hackerEffect();
    });
</script>

<h1 class={className} role="presentation">
    {#each displayText.split("\n") as line, i}
        {#if i > 0}<br />{/if}{line}
    {/each}
</h1>

<style>
    h1 {
        user-select: none;
        white-space: pre-wrap;
    }
</style>
