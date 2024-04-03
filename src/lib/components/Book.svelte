<!-- Book.svelte -->
<script>
    import { spring } from 'svelte/motion';

    export let src;
    export let href;

    let lifted = false;
    let y;

    const liftParams = {
        stiffness: 0.05,
        damping: 0.6,
        mass: 1,
    };

    const fallParams = {
        stiffness: 0.05,
        damping: 0.4,
        mass: 1,
    };

    $: y = spring(lifted ? -50 : 0, lifted ? liftParams : fallParams);
</script>

<style>
    .book {
        display: inline-block;
        position: relative;
        margin: 0;
    }

    img {
        vertical-align: bottom;
    }
</style>

<div class="book">
    <a
            href={href}
            on:mouseenter={() => {
      lifted = true;
    }}
            on:mouseleave={() => {
      lifted = false;
    }}
    >
        <img src={src} alt="Book Cover" style="transform: translate(0, {$y}px); transition: transform 0.4s;" />
    </a>
</div>