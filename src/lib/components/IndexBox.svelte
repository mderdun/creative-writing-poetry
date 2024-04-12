<script>
    import { fade } from 'svelte/transition';
    export let n;
    export let title;
    export let c1;
    export let c2;
</script>

<div class="card" style="background-color: {c2}; color: {c1};">
    <a href="/works/{n}">
    <div class="numeral">{n}</div>
    <div class="title" in:fade={{duration: 200}} out:fade={{duration: 200}}>{title}</div>
    </a>
</div>

<style>
    .card {
        width: 20vw;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: background-color 0.3s, color 0.3s;
        cursor: none;
        margin: 3px;
    }

    .card:hover .numeral {
        display: none;
    }

    .card:hover .title {
        display: block;
    }

    .numeral, .title {
        font-size: 2em;
        text-align: center;
    }

    .title {
        display: none;
        margin: 0 20px;
    }
</style>