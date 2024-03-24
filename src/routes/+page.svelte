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
        <Book href="/works/vol1" src="src/lib/imgs/bookshelf/vol1.png" title="Streetlamps" />
        <Book href="/works/vol2" src="src/lib/imgs/bookshelf/vol2.png" title="Summoning Words" />
        <Book href="/works/vol3" src="src/lib/imgs/bookshelf/vol3.png" title="Ode on Ode on a Grecian Urn" />
        <Book href="/works/vol4" src="src/lib/imgs/bookshelf/vol4.png" title="I Feel Like ASCII-ng" />
        <Book href="/works/vol5" src="src/lib/imgs/bookshelf/vol5.png" title="How to Get Home" />
        <Book href="/works/vol6" src="src/lib/imgs/bookshelf/vol6.png" title="Deansdon Community Noticeboard" />
        <Book href="/works/vol7" src="src/lib/imgs/bookshelf/vol7.png" title="Concrete and Clothes" />
    </div>
</div>