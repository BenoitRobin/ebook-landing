<script>
    let { children, ...props } = $props();
</script>

<button {...props} >{@render children()}</button>


<style>
    button {
        background-color: #000;
        color: #fff;
        padding: 20px 24px;
        font-weight: normal;
        font-size: 22px;
        text-transform: uppercase;
        border: 1px solid #fff;
        transition: all .3s;
    }

    button:hover {
        background-color: #fff;
        color: #000;
    }
</style>