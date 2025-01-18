<script lang="ts">
    let {label} = $props();
</script>

<button>
    {label}
</button>

<style>
    button {
        background-color: #52ADF0;
        border: none;
        box-shadow: 0 3px 0 #6A99BC;
        border-radius: 8px;
        min-height: 44px;

        color: white;
        font-family: Helvetica, Arial, sans-serif;
        font-size: 13px;
        font-weight: bold;
    }

    button:active {
        background-color: #4486b5;
    }
</style>
