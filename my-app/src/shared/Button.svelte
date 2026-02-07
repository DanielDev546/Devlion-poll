    <script>
        export let type = 'primary';
        export let flat = false;
        export let inverse = false;
    </script>
<button class= {type} class:flat={flat} class:inverse = {inverse}>
   <slot></slot>
</button>

<style>
 button{
    border: 0;
    border-radius: 8px;
    padding: 10px 20px ;
    box-shadow: 0px 2px 4px rgba(125, 122, 122, 0.1);
    margin-left: 40%;
    cursor: pointer;
    margin-top: 20px;
    font-weight: bold;
 }
 .primary{
    background-color: orangered;
    color: white;
 } .secondary{
    background-color: #45c496;
    color: white;
 }
    .flat{
        box-shadow: none;
    }  
    .primary.inverse{
        color: orangered;
        background: white;
        border: 2px solid orangered;
    }
    .secondary.inverse{
        color: #45c496;
        background: white;
        border: 2px solid #45c496;
    }

</style>