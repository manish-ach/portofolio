<script>
    import HackerText from "$lib/HackerText.svelte";

    let showLabels = $state(false);

    function handleComplete() {
        setTimeout(() => {
            showLabels = true;
        }, 200);
    }
</script>

<!-- Hero Section -->
<section class="hero">
    <div class="hero-content">
        <HackerText
            text={"MANISH\nACHARYA"}
            class="hero-title"
            oncomplete={handleComplete}
        />
        <div class="hero-label">
            <span
                class="label-text static-box"
                class:animate={showLabels}
                style="--delay: 0">DEVELOPER</span
            >
            <span
                class="label-text static-box"
                class:animate={showLabels}
                style="--delay: 1">DESIGNER</span
            >
            <span
                class="label-text static-box"
                class:animate={showLabels}
                style="--delay: 2">CREATOR</span
            >
        </div>
    </div>

    <div class="home-routers" class:animate={showLabels} style="--delay: 3">
        <a href="/about" class="router-link">ABOUT</a>
        <a href="/projects" class="router-link">PROJECTS</a>
        <a href="/contact" class="router-link">CONTACT</a>
    </div>
</section>

<style>
    /* Hero Section */
    .hero {
        min-height: 100vh;
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        position: relative;
    }

    .hero-content {
        text-align: center;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    /* We need to use :global because the class is passed to the component */
    :global(.hero-title) {
        /* Increased size as requested */
        font-size: clamp(5rem, 18vw, 15rem);
        /* font-family handled by h1 global now, but we keep size override */
        line-height: 0.85;
        margin: 0;
        text-shadow: 4px 4px 0px var(--bg-tertiary);
    }

    .hero-label {
        display: flex;
        gap: 2rem;
        justify-content: center;
        margin-top: 2rem;
        flex-wrap: wrap;
    }

    .static-box {
        border: var(--border-width) solid var(--border-color);
        padding: 0.5rem 1rem;
        font-weight: 700;
        text-transform: uppercase;
        background: transparent;
        color: var(--text-primary);
        font-family: var(--font-heading); /* Ensure labels match blocky font */
        letter-spacing: 0.1em;
    }

    .label-text {
        font-size: 1rem;
        /* box/static styling handled by static-box */
        opacity: 0;
        transform: translateY(20px);
        transition: none;
        background: var(
            --bg-primary
        ); /* Ensure button labels obscure lines if needed */
    }

    .label-text.animate {
        animation: slideUpFade 0.6s ease-out forwards;
        animation-delay: calc(var(--delay) * 0.15s);
    }

    /* Home Routers */
    .home-routers {
        position: absolute;
        bottom: 4rem;
        display: flex;
        gap: 4rem;
        opacity: 0;
        transform: translateY(20px);
    }

    .home-routers.animate {
        animation: slideUpFade 0.6s ease-out forwards;
        animation-delay: 0.6s; /* After labels */
    }

    .router-link {
        font-size: 0.85rem;
        color: var(--text-muted);
        text-decoration: none;
        border-bottom: 1px solid var(--text-primary);
        padding-bottom: 0.2rem;
        font-weight: 700;
        letter-spacing: 0.15em;
        transition:
            color 0.2s,
            border-color 0.2s;
    }

    .router-link:hover {
        color: var(--text-primary);
        border-color: var(--accent-magenta);
    }

    @keyframes slideUpFade {
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* Responsive */
    @media (max-width: 768px) {
        .hero-label {
            flex-direction: column;
            align-items: center;
            gap: 1rem;
        }

        .label-text {
            width: 100%;
            max-width: 200px;
            text-align: center;
        }

        .home-routers {
            bottom: 2rem;
            gap: 2rem;
            flex-wrap: wrap;
            justify-content: center;
        }
    }
</style>
