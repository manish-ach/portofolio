<script>
    import { goto } from "$app/navigation";
    import HackerText from "$lib/HackerText.svelte";

    const projects = [
        {
            title: "BROWRS",
            year: "2025",
            desc: "Terminal based browser in Rust",
            tags: ["RUST", "TUI"],
            url: "https://github.com/manish-ach/browrs",
        },
        {
            title: "M-OSH",
            year: "2025",
            desc: "Custom shell implementation",
            tags: ["RUST", "SYSTEMS"],
            url: "https://github.com/manish-ach/m-osh",
        },
        {
            title: "SUCKLESS",
            year: "2024",
            desc: "Custom DWM build & dots",
            tags: ["C", "LINUX"],
            url: "https://github.com/manish-ach/suckless",
        },
        {
            title: "QUICC-MODULE",
            year: "2025",
            desc: "QUIC protocol implementation",
            tags: ["RUST", "NET"],
            url: "https://github.com/manish-ach/quicc-module",
        },
        {
            title: "GIP",
            year: "2025",
            desc: "Package manager",
            tags: ["RUST", "CLI"],
            url: "https://github.com/manish-ach/gip",
        },
        {
            title: "SODO",
            year: "2025",
            desc: "Native macOS Todo app",
            tags: ["SWIFT", "MACOS"],
            url: "https://github.com/manish-ach/SoDo",
        },
        {
            title: "NETOS",
            year: "2025",
            desc: "Web Desktop Mockup",
            tags: ["TS", "WEB"],
            url: "https://github.com/manish-ach/netOS",
        },
        {
            title: "RSOLVER",
            year: "2025",
            desc: "DNS Resolver",
            tags: ["RUST", "DNS"],
            url: "https://github.com/manish-ach/rsolver",
        },
        {
            title: "THEME",
            year: "2025",
            desc: "Editor Color Scheme",
            tags: ["THEME", "UI"],
            url: "https://github.com/manish-ach/editor-theme",
        },
    ];
</script>

<svelte:window />

<section class="page">
    <div class="page-content">
        <HackerText text="PROJECTS" class="page-title" />

        <div class="matrix-grid">
            {#each projects as project}
                <a
                    href={project.url}
                    target="_blank"
                    rel="noopener noreferrer"
                    class="matrix-cell"
                >
                    <div class="cell-head">
                        <span class="cell-title">{project.title}</span>
                        <span class="cell-year">{project.year}</span>
                    </div>
                    <div class="cell-info">
                        <p class="cell-desc">{project.desc}</p>
                        <div class="cell-tags">
                            {#each project.tags as tag}
                                <span class="tag">{tag}</span>
                            {/each}
                        </div>
                    </div>
                    <div class="corner-marker"></div>
                </a>
            {/each}
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

    :global(.page-title) {
        font-size: clamp(4rem, 8vw, 6rem); /* Standard Size */
        margin: 0;
        line-height: 0.8;
        color: var(--text-primary);
        opacity: 0.9;
        min-height: 8rem; /* Reserve space key for alignment */
        display: flex;
        align-items: flex-end;
        padding-bottom: 2rem; /* Align baseline */
    }

    /* Matrix Grid Layout */
    .matrix-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-template-rows: repeat(3, 1fr);
        /* Use gap with background color to simulate borders? 
           Or strict borders on cells. Let's do Borders. */
        border: 2px solid var(--text-primary);
        flex: 1;
        overflow: hidden; /* Ensure 9 items stay put */
    }

    .matrix-cell {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        padding: 1.5rem;
        text-decoration: none;
        position: relative;
        border-right: 1px solid var(--bg-tertiary);
        border-bottom: 1px solid var(--bg-tertiary);
        transition: background-color 0.1s;
    }

    /* Remove right borders for last column */
    .matrix-cell:nth-child(3n) {
        border-right: none;
    }

    /* Remove bottom borders for last row (7, 8, 9) */
    .matrix-cell:nth-child(n + 7) {
        border-bottom: none;
    }

    .matrix-cell:hover {
        background-color: var(--bg-secondary);
    }

    .matrix-cell:hover .cell-title {
        color: var(--accent-cyan);
    }

    .cell-head {
        display: flex;
        justify-content: space-between;
        align-items: baseline;
    }

    .cell-title {
        font-size: 1.25rem;
        font-weight: 900;
        color: var(--text-primary);
    }

    .cell-year {
        font-size: 0.75rem;
        font-family: var(--font-mono);
        color: var(--text-muted);
    }

    .cell-info {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
    }

    .cell-desc {
        font-size: 0.85rem;
        color: var(--text-secondary);
        margin: 0;
        line-height: 1.3;

        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        overflow: hidden;
    }

    .cell-tags {
        display: flex;
        gap: 0.5rem;
        flex-wrap: wrap;
    }

    .tag {
        font-size: 0.65rem;
        color: var(--text-muted);
        background: var(
            --bg-tertiary
        ); /* Darker tags for contrast inside cell */
        padding: 0.1rem 0.3rem;
    }

    /* Decorative corner marker for "tech" feel */
    .corner-marker {
        position: absolute;
        bottom: 0;
        right: 0;
        width: 10px;
        height: 10px;
        border-bottom: 2px solid transparent;
        border-right: 2px solid transparent;
        transition: border-color 0.2s;
    }

    .matrix-cell:hover .corner-marker {
        border-color: var(--accent-magenta);
    }

    @media (max-width: 968px) {
        .matrix-grid {
            grid-template-columns: repeat(2, 1fr);
            grid-template-rows: auto; /* Allow flow */
            overflow-y: auto;
        }

        .page {
            overflow: auto;
            justify-content: flex-start;
            padding-top: 6rem;
        }

        /* Reset borders for mobile grid logic if hard to manage, or just keep simple */
        .matrix-cell {
            border: 1px solid var(--bg-tertiary);
        }
    }

    @media (max-width: 600px) {
        .matrix-grid {
            grid-template-columns: 1fr;
        }
    }
</style>
