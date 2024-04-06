<script>
    let likes = 0;
    let comments = 0;

    function handleLike() {
        likes += 1;
    }

    function handleComment() {
        comments += 1;
    }
</script>

<div class="reaction-bar">
    <button on:click={handleLike}>👍 {likes}</button>
    <button on:click={handleComment}>💬 {comments}</button>
</div>

<style>
    .reaction-bar {
        display: flex;
        justify-content: space-between;
        padding: 10px;
    }

    .reaction-bar button {
        background: none;
        border: none;
        cursor: pointer;
        color: #385898;
    }
</style>