<script>
    import { goto } from "$app/navigation";
    import HackerText from "$lib/HackerText.svelte";
</script>

<section class="page">
    <div class="page-content">
        <!-- Top Row: Header + Stats -->
        <div class="header-row">
            <HackerText text="ABOUT" class="page-title" />
            <div class="stats-mini">
                <div class="stat-group">
                    <span class="stat-val">RUST</span>
                    <span class="stat-label">CORE</span>
                </div>
                <div class="stat-group">
                    <span class="stat-val">85%</span>
                    <span class="stat-label">OPTIMIZATION</span>
                </div>
            </div>
        </div>

        <!-- Main Grid: Intro + Exp -->
        <div class="content-grid">
            <div class="bio-col">
                <p class="headline">
                    SYSTEMS PROGRAMMING.<br />
                    HIGH PERFORMANCE.<br />
                    WEB INFRASTRUCTURE.
                </p>
                <div class="bio-text">
                    <p>
                        Focused on building efficient scalable solutions.
                        Specializing in Rust backend development and network
                        programming.
                    </p>
                </div>

                <div class="toolkit-area">
                    <div class="col-label">TOOLKIT</div>
                    <div class="toolkit-grid">
                        <span class="tool">RUST</span>
                        <span class="tool">TYPESCRIPT</span>
                        <span class="tool">SVELTEKIT</span>
                        <span class="tool">GO</span>
                        <span class="tool">POSTGRES</span>
                        <span class="tool">DOCKER</span>
                        <span class="tool">C++</span>
                        <span class="tool">LINUX</span>
                    </div>
                </div>
            </div>

            <div class="exp-col">
                <div class="col-label">EXPERIENCE</div>
                <div class="exp-list">
                    <div class="exp-item">
                        <div class="exp-head">
                            <span class="role">TEAM LEADER</span>
                            <span class="date">JUNE 2025</span>
                        </div>
                        <h3 class="company">Team Modulens</h3>
                        <p class="details">
                            Rust-PHP FFI Integration. 3rd Place Finish.
                        </p>
                    </div>

                    <div class="exp-item">
                        <div class="exp-head">
                            <span class="role">TEAM MEMBER</span>
                            <span class="date">JULY 2025</span>
                        </div>
                        <h3 class="company">Team Nascent</h3>
                        <p class="details">
                            SyncBridge Platform. Interactive Tech Winner.
                        </p>
                    </div>
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
        width: 100%;
        max-width: 1600px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        gap: 3rem; /* Standard Gap */
        max-height: 800px;
        flex: 1; /* Allow content to stretch */
    }

    /* Header Row */
    .header-row {
        display: flex;
        justify-content: space-between;
        align-items: flex-end;
        border-bottom: 2px solid var(--text-primary);
        padding-bottom: 1rem;
        min-height: 8rem; /* Reserve space for title */
    }

    :global(.page-title) {
        font-size: clamp(4rem, 8vw, 6rem); /* Standard Size */
        margin: 0;
        line-height: 0.8;
        color: var(--text-primary);
    }

    .stats-mini {
        display: flex;
        gap: 2rem;
        text-align: right;
    }

    .stat-group {
        display: flex;
        flex-direction: column;
    }

    .stat-val {
        font-weight: 900;
        font-size: 1.25rem;
    }

    .stat-label {
        font-size: 0.75rem;
        color: var(--text-muted);
        letter-spacing: 0.1em;
    }

    /* Content Grid */
    .content-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 4rem;
        flex: 1; /* Fill remaining height */
    }

    /* Bio Column */
    .bio-col {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    .headline {
        font-size: clamp(1.5rem, 2.5vw, 2.5rem);
        line-height: 1;
        font-weight: 900;
        margin: 0;
        color: var(--text-primary);
        letter-spacing: -0.03em;
    }

    .bio-text {
        font-size: 1rem;
        line-height: 1.4;
        color: var(--text-secondary);
        max-width: 400px;
    }

    /* Experience Column */
    .exp-col {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        border-left: 1px solid var(--bg-tertiary);
        padding-left: 2rem;
    }

    .col-label {
        font-size: 0.75rem;
        letter-spacing: 0.1em;
        color: var(--text-muted);
        margin-bottom: 1rem;
    }

    .exp-list {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    .exp-item {
        display: flex;
        flex-direction: column;
        gap: 0.25rem;
    }

    .exp-head {
        display: flex;
        justify-content: space-between;
        font-size: 0.75rem;
        color: var(--text-muted);
    }

    .role {
        font-weight: 700;
        color: var(--accent-magenta);
    }

    .company {
        font-size: 1.25rem;
        font-weight: 900;
        margin: 0;
        color: var(--text-primary);
    }

    .details {
        font-size: 0.9rem;
        margin: 0;
        color: var(--text-secondary);
    }

    /* Toolkit Styles */
    .toolkit-area {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        margin-top: auto; /* Push to bottom if space permits */
    }

    .toolkit-grid {
        display: flex;
        flex-wrap: wrap;
        gap: 0.75rem;
    }

    .tool {
        font-size: 0.75rem;
        font-weight: 700;
        background: var(--bg-secondary);
        color: var(--text-muted);
        padding: 0.25rem 0.5rem;
        border: 1px solid transparent;
    }

    @media (max-width: 968px) {
        .content-grid {
            grid-template-columns: 1fr;
            gap: 2rem;
        }

        .exp-col {
            border-left: none;
            padding-left: 0;
            border-top: 1px solid var(--bg-tertiary);
            padding-top: 1rem;
        }

        .page {
            height: auto;
            min-height: 100vh;
            padding: 4rem 2rem;
            overflow-y: auto; /* Allow scroll on small devices if needed */
        }
    }
</style>
