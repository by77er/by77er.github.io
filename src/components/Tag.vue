<template>
    <div id="wrap">
        <span>{{cont}}</span>
    </div>
</template>

<script>
export default {
    name: 'Tag',
    props: {
        cont: String
    }
}
</script>

<style scoped>
#wrap {
    font-size: 17px;
    border-style: solid;
    border-width: 1px;
    border-radius: 4px;
    border-color: #444444;
    padding: 3px;
    margin: 3px;
}
</style>
