<script>
    import { goto } from "$app/navigation";
    import HackerText from "$lib/HackerText.svelte";
</script>

<svelte:window />

<section class="page">
    <div class="page-content">
        <div class="header-row">
            <HackerText text="CONTACT" class="page-title" />
            <a href="/" class="return-link">// RETURN</a>
        </div>

        <div class="panes">
            <!-- Left Pane: Connect Links -->
            <div class="pane connect-pane stager-1">
                <div class="pane-header">CHANNELS</div>
                <div class="link-list">
                    <a
                        href="mailto:contact@manishacharya.name.np"
                        class="link-item"
                    >
                        <span class="link-label">EMAIL</span>
                        <span class="link-val"
                            >CONTACT@MANISHACHARYA.NAME.NP</span
                        >
                    </a>
                    <a
                        href="https://github.com/manish-ach"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="link-item"
                    >
                        <span class="link-label">GITHUB</span>
                        <span class="link-val">@MANISH-ACH</span>
                    </a>
                    <a
                        href="https://www.linkedin.com/in/manish-acharya-08345a260"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="link-item"
                    >
                        <span class="link-label">LINKEDIN</span>
                        <span class="link-val">MANISH ACHARYA</span>
                    </a>
                    <a
                        href="https://www.instagram.com/manishacharya715/"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="link-item"
                    >
                        <span class="link-label">INSTAGRAM</span>
                        <span class="link-val">@MANISHACHARYA715</span>
                    </a>
                </div>
            </div>

            <!-- Right Pane: Status & Info -->
            <div class="pane status-pane stager-2">
                <div class="pane-header">STATUS</div>
                <div class="status-content">
                    <div class="status-row">
                        <span class="status-label">AVAILABILITY</span>
                        <span class="status-val highlight">OPEN FOR WORK</span>
                    </div>
                    <div class="status-row">
                        <span class="status-label">LOCATION</span>
                        <span class="status-val">NEPAL</span>
                    </div>
                    <div class="status-row">
                        <span class="status-label">TIMEZONE</span>
                        <span class="status-val">GMT+5:45</span>
                    </div>
                </div>

                <div class="pane-footer">
                    <p>
                        Specializing in high-performance systems and robust web
                        infrastructure. Ready to collaborate on ambitious
                        projects.
                    </p>
                </div>
            </div>
        </div>
    </div>
</section>

<style>
    .page {
        height: 100vh;
        width: 100%;
        padding: 4rem 10vw; /* Standard Padding */
        display: flex;
        flex-direction: column;
        justify-content: center;
        overflow: hidden;
    }

    .page-content {
        max-width: 1600px;
        width: 100%;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        gap: 3rem; /* Standard Gap */
        max-height: 800px;
        flex: 1;
    }

    /* Header Row */
    .header-row {
        display: flex;
        justify-content: space-between;
        align-items: flex-end;
        position: relative;
        padding-bottom: 2rem;
        min-height: 8rem;
    }

    /* Draw Header Line */
    .header-row::after {
        content: "";
        position: absolute;
        bottom: 0;
        left: 0;
        height: 2px;
        background: var(--text-primary);
        width: 0;
        animation: drawWidth 1s ease-out forwards;
    }

    .return-link {
        margin-bottom: 0.5rem;
        text-decoration: none;
        color: var(--text-muted);
        font-size: 0.85rem;
        font-weight: 700;
        letter-spacing: 0.1em;
        transition: color 0.2s;
        opacity: 0;
        animation: fadeScale 0.5s ease-out 0.8s forwards;
    }

    .return-link:hover {
        color: var(--accent-magenta);
    }

    :global(.page-title) {
        font-size: clamp(4rem, 8vw, 6rem); /* Standard Size */
        margin: 0;
        line-height: 0.8;
        color: var(--text-primary);
        opacity: 0;
        animation: fadeScale 0.8s ease-out forwards;
        display: block;
        padding-bottom: 0;
    }

    .panes {
        display: grid;
        grid-template-columns: 1.5fr 1fr;
        gap: 4rem;
        /* Remove top border here since Header Row has it */
        /* border-top: 1px solid var(--text-primary); */
        /* padding-top: 3rem; */
        flex: 1;
    }

    .stager-1 {
        opacity: 0;
        animation: slideInUp 0.6s ease-out 0.4s forwards;
    }
    .stager-2 {
        opacity: 0;
        animation: slideInUp 0.6s ease-out 0.6s forwards;
    }

    .pane {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    .pane-header {
        font-size: 0.85rem;
        font-weight: 700;
        letter-spacing: 0.1em;
        color: var(--text-muted);
    }

    /* Link List Styles */
    .link-list {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
    }

    .link-item {
        display: flex;
        flex-direction: column;
        text-decoration: none;
        gap: 0.25rem;
        border-left: 2px solid transparent;
        padding-left: 0;
        transition:
            padding-left 0.2s,
            border-color 0.2s;
    }

    .link-item:hover {
        padding-left: 1rem;
        border-left-color: var(--accent-cyan);
    }

    .link-label {
        font-size: 0.75rem;
        font-weight: 700;
        color: var(--text-muted);
    }

    .link-val {
        font-size: 1.25rem;
        font-weight: 900;
        color: var(--text-primary);
    }

    /* Status Pane Styles */
    .status-content {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
    }

    .status-row {
        display: flex;
        justify-content: space-between;
        align-items: baseline;
        border-bottom: 1px solid var(--bg-tertiary);
        padding-bottom: 0.5rem;
    }

    .status-label {
        font-size: 0.85rem;
        font-weight: 700;
        color: var(--text-muted);
    }

    .status-val {
        font-family: var(--font-mono);
        font-weight: 700;
        color: var(--text-primary);
    }

    .highlight {
        color: var(--accent-green);
    }

    .pane-footer p {
        font-size: 1rem;
        line-height: 1.5;
        color: var(--text-secondary);
        margin: 0;
    }

    @media (max-width: 968px) {
        .panes {
            grid-template-columns: 1fr;
            gap: 3rem;
        }

        .page-content {
            gap: 2rem;
        }

        .page {
            overflow-y: auto; /* Fallback */
            justify-content: flex-start;
            padding-top: 6rem;
        }
    }
</style>
