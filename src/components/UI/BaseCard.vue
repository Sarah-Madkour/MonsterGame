<template>
    <div>
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name : 'BaseCard'
    }
</script>

<style scoped>
div{
    width: 700px;
    min-height: 100px;
    box-shadow: 2px 4px 12px rgba(0,0,0,0.25);
    padding: 2rem 1rem;
    border-radius: 20px;
    margin: 60px auto;
}
</style>