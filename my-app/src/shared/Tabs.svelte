<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

  export let items;
  export let activeItem;
</script>
<div class="tabs">
 <ul>
    {#each items as item}
        <li on:click={() => dispatch('tabChange', item)}>
            <div class:active={item === activeItem}>
                {item}</div>
        </li>
    {/each}
    
 </ul>
</div>

<style>
    .tabs{
        margin-bottom: 40px;
    }
    ul{
        list-style: none;
        padding: 0;
        display: flex;
        justify-content: center;
        gap: 40px;  
    }
    ul li{
        cursor: pointer;
        font-size: 18px;
        color: #555;
    }   
    .active{
        font-weight: bold;
        color: orangered;
        border-bottom: 2px solid orangered ;
        padding-bottom: 8px;
        display: flex;
    }

</style>