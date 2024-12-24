<script>
    import { goto } from '$app/navigation';

    const pages = [
        { name: 'Happy One Year Anniversary', path: '/one-year' },
        { name: 'Merry Christmas 2024', path: '/christmas-24' }
    ];
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@500&display=swap');
</style>

<div class="flex flex-col items-center justify-center min-h-screen bg-gradient-to-r from-yellow-300 via-yellow-500 to-yellow-300 text-gray-800 p-4">
    <!-- Title with Handwritten Font -->
    <h1 
        class="text-center font-extrabold text-gray-900 drop-shadow-lg"
        style="font-family: 'Dancing Script', cursive; font-size: 3rem;"
    >
        Dear Victoria
    </h1>

    <!-- Navigation Buttons -->
    <div class="mt-10 flex flex-col space-y-6 w-full max-w-md">
        {#each pages as { name, path }}
            <button
                on:click={() => goto(path)}
                class="w-full px-6 py-3 text-l rounded-full bg-yellow-600 text-white font-semibold shadow-lg hover:bg-yellow-700 active:scale-95 transition-all"
                style="font-family: 'Poppins', sans-serif;"
                aria-label={`Navigate to ${name}`}
            >
                {name}
            </button>
        {/each}
    </div>
</div>

