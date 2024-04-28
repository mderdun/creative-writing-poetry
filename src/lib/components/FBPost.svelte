<script>
    import ReactionBar from "$lib/components/ReactionBar.svelte";
</script>

<div id="card" class="bg-[#242526] rounded-xl my-2 flex flex-col w-[35rem]">
    <div id="content" class="py-2 px-5">
        <slot />
    </div>
    <div id="reaction" class="pb-1 px-8">
        <ReactionBar />
    </div>
</div>

<style>
    #card {
        line-height: 1.34;
        -webkit-font-smoothing: antialiased;
    }
    #content {
        border-bottom-width: 1px;
        --tw-border-opacity: 1;
        border-bottom-color: rgb(62 64 66 / var(--tw-border-opacity));
    }
</style>