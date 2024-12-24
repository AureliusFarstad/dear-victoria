<script>
    import "../app.css";
    import { page } from '$app/stores'; // Import the page store
</script>

<style>
    /* Back button styling */
    .back-button {
        position: fixed;
        top: 1.1rem;
        left: 1rem;
        font-size: 2.5rem;
        font-weight: bold;
        color: gold;
        cursor: pointer;
        text-decoration: none;
        transition: color 0.3s, transform 0.2s;
        z-index: 1000; /* Ensure it's on top of other elements */
    }

    /* On hover, make the color brighter and scale up */
    .back-button:hover {
        color: #ffd700;
        transform: scale(1.1);
    }

    /* When the button is clicked, scale it down slightly */
    .back-button:active {
        transform: scale(0.95);
    }

    /* Ensure the SVG icon fits correctly */
    .back-button svg {
        width: 30px; /* Adjust size of the icon */
        height: 30px;
    }
</style>

<!-- Main Layout -->
{#if $page.url.pathname !== '/'} <!-- Show only on subpages -->
    <a class="back-button" href="/" aria-label="Go back to the homepage">
        <!-- New Chevron Left SVG icon -->
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
            <path d="M15 19l-7-7 7-7"></path>
        </svg>
    </a>
{/if}

<slot />
