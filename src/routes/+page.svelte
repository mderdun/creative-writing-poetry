<!-- +page.svelte -->
<script>
    import Book from '$lib/components/Book.svelte';
</script>

<style>
    .bookshelf {
        display: flex;
        justify-content: center;
        align-items: flex-end;
        background-color: white;
    }
</style>

<div class="h-screen flex flex-col justify-center items-center">
    <div>
        <p class="text-4xl">The Collected</p>
        <p class="text-7xl">Works of</p>
        <p class="text-9xl">Low-Ki</p>
    </div>
    <div class="bookshelf">
        <Book href="/works/vol1" src="/imgs/bookshelf/vol2.png" />
        <Book href="/works/vol2" src="/imgs/bookshelf/vol2.png" />
        <Book href="/works/vol3" src="/imgs/bookshelf/vol3.png" />
        <Book href="/works/vol4" src="imgs/bookshelf/vol4.png" />
        <Book href="/works/vol5" src="/imgs/bookshelf/vol5.png" />
        <Book href="/works/vol6" src="/imgs/bookshelf/vol6.png" />
        <Book href="/works/vol7" src="/imgs/bookshelf/vol7.png" />
    </div>
</div>