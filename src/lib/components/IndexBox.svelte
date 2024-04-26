<script>
    export let n;
    export let title;
</script>

<div class="card">
    <a href="/works/{n}">
    <div class="numeral">{n}</div>
    <div class="title">{title}</div>
    </a>
</div>

<style>
    .card {
        width: 20vw;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 5%;
        background-color: white;
        color: black;
        transition: all 0.3s ease;
        cursor: none;
        margin: 3px;
    }

    .card:hover {
        background-color: var(--c2);
        color: var(--c1);
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