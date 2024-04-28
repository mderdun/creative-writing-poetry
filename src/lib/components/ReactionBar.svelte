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
    <button on:click={handleLike}>
        <i data-visualcompletion="css-img" class="invert" style="background-image: url(&quot;https://static.xx.fbcdn.net/rsrc.php/v3/yd/r/f83B_g19MgN.png&quot;); background-position: 0px -739px; background-size: 25px 1427px; width: 20px; height: 20px; background-repeat: no-repeat; display: inline-block;"></i>
    </button>
    <button>
        <i data-visualcompletion="css-img" class="invert" style="background-image: url(&quot;https://static.xx.fbcdn.net/rsrc.php/v3/yd/r/f83B_g19MgN.png&quot;); background-position: 0px -550px; background-size: 25px 1427px; width: 20px; height: 20px; background-repeat: no-repeat; display: inline-block;"></i>
    </button>
    <button>
        <i data-visualcompletion="css-img" class="invert" style="background-image: url(&quot;https://static.xx.fbcdn.net/rsrc.php/v3/yd/r/f83B_g19MgN.png&quot;); background-position: 0px -886px; background-size: 25px 1427px; width: 20px; height: 20px; background-repeat: no-repeat; display: inline-block;"></i>
    </button>
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
        cursor: none;
    }

    .invert {
        vertical-align: -0.15em;
        filter: invert(62%) sepia(98%) saturate(12%) hue-rotate(175deg) brightness(90%) contrast(96%);
    }
</style>