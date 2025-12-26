<script>
    import "../app.css";
    import { page } from "$app/stores"; // Changed from navigating to page
    import { fade } from "svelte/transition";
    import { base } from "$app/paths";
    // favicon import removed as it's no longer used in svelte:head
</script>

<svelte:head>
    <link rel="icon" href="{base}/favicon.svg" />
    <!-- Assuming favicon.svg is now in static -->
    <title>Manish Acharya | Systems Engineer</title>
</svelte:head>

<!-- Page Content -->
<main class="page-transition">
    <div
        key={$page.url.pathname}
        in:fade={{ duration: 300, delay: 300 }}
        out:fade={{ duration: 300 }}
        class="transition-wrapper"
    >
        <slot />
    </div>
</main>

<!-- Global Footer Navigation -->
<nav class="global-footer">
    <div class="nav-content">
        <a
            href="{base}/"
            class="nav-link"
            class:active={$page.url.pathname === `${base}/` ||
                $page.url.pathname === base}>HOME</a
        >
        <a
            href="{base}/about"
            class="nav-link"
            class:active={$page.url.pathname === `${base}/about`}>ABOUT</a
        >
        <a
            href="{base}/projects"
            class="nav-link"
            class:active={$page.url.pathname === `${base}/projects`}>PROJECTS</a
        >
        <a
            href="{base}/contact"
            class="nav-link"
            class:active={$page.url.pathname === `${base}/contact`}>CONTACT</a
        >
        <span class="sneaky-tag">(BUILT ON SVELTE)</span>
    </div>
</nav>

<style>
    .page-transition {
        /* Ensure main content takes full screen but allows interactions */
        position: relative;
        z-index: 1;
    }

    .transition-wrapper {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }

    /* Global Footer */
    .global-footer {
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
        padding: 4rem 10vw;
        pointer-events: none; /* Let clicks pass through container */
        z-index: 100;
        display: flex;
        justify-content: flex-start; /* Align with padding */
    }

    .nav-content {
        pointer-events: auto; /* Re-enable clicks on links */
        display: flex;
        gap: 3rem;
        /* Optional: Add background or blur if content scrolls behind? 
           User wants seamless, assume content fits or this overlays neatly. */
    }

    .nav-link {
        font-size: 0.85rem;
        font-weight: 700;
        color: var(--text-muted);
        text-decoration: none;
        letter-spacing: 0.1em;
        position: relative;
        transition: color 0.3s;
    }

    .nav-link::after {
        content: "";
        position: absolute;
        bottom: -4px;
        left: 0;
        width: 0;
        height: 1px;
        background: var(--text-primary);
        transition: width 0.3s;
    }

    .nav-link:hover {
        color: var(--text-primary);
    }

    .nav-link:hover::after {
        width: 100%;
    }

    .nav-link.active {
        color: var(--accent-magenta);
    }

    .nav-link.active::after {
        width: 100%;
        background: var(--accent-magenta);
    }

    @media (max-width: 768px) {
        .global-footer {
            justify-content: center;
            padding: 2rem;
            background: rgba(
                29,
                31,
                33,
                0.9
            ); /* Add bg on mobile for legibility */
            backdrop-filter: blur(10px);
        }

        .nav-content {
            gap: 1.5rem;
        }
    }
    .sneaky-tag {
        font-size: 0.6rem;
        color: var(--bg-tertiary);
        margin-left: auto; /* Push to far right if using flex-start on container, or just gap */
        align-self: center;
        opacity: 0.5;
        font-family: var(--font-mono);
        transition: color 0.3s;
        cursor: default;
    }

    .sneaky-tag:hover {
        color: #ff3e00;
        opacity: 1;
    }
</style>
