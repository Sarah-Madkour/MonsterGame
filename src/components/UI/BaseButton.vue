<template>
    <button>
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name : 'BaseButton',
    }
</script>

<style scoped>
button {
    background-color: #661919;
    padding: 1rem 2rem;
    border-color: #661919;
    color: #fff;
    border-radius: 20px;
    text-transform: capitalize;
    width: 200px;
    margin: 20px 60px;
    text-transform: uppercase;
    cursor: pointer;
}
button:hover {
    background-color: #4f0202 ;
}
button:disabled{
    background-color: gray;
    color: #000;
    border: none;
}

</style>