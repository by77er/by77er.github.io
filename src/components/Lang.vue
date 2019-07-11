<template>
    <div id="wrap"  @click="$parent.showLangDetail(lang)">
        <span>{{lang.name}}</span>
    </div>
</template>

<script>
export default {
    name: 'Lang',
    props: {
        lang: Object
    }
}
</script>

<style scoped>
#wrap {
    margin: 5px;
    padding: 6px;
    border-color: #E8E7DD;
    background-color: #101011;
    border-width: 1px;
    border-style: solid;
    border-radius: 4px;
}
#wrap:hover {
    cursor: pointer;
    background-color: var(--theme-color);
    border-color: var(--theme-color);
    color: var(--alt-color);
    transition: color .3s;
}
</style>
