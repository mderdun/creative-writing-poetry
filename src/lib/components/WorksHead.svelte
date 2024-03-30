<script>
    export let title;
</script>

<nav class="flex justify-center items-center h-16 relative bottom-2">
    <a href="/" class="absolute left-4 flex">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
        </svg>
        <p class="text-lg">Back</p>
    </a>
    <h1 class="text-2xl">{title}</h1>
</nav>