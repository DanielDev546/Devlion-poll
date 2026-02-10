<script>
    import PollDetails from "./PollDetails.svelte";

    export let polls = [];
</script>

<div class="polist">
<div class="poll-list">
    {#each polls as poll (poll.id)}
        <div>
            <PollDetails  {poll}  on:vote />
        </div>
    {/each}
</div>
</div>

<style>
    .polist{
        padding: 10px 20px;
    }
    .poll-list{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
        
    }
@media (max-width: 768px) {
    .poll-list{
        display: grid;
        grid-template-columns: 1fr;
        grid-gap: 40px;    
    }
}
</style>