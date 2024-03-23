<template>
    <div style="display: flex; flex-direction:column; align-items:center; justify-content:flex-end; ">
        <div style="font-size: 24px; font-weight:bold; color:white;">
            {{ props.mainText }}
        </div>
        <div style="font-size: 14px; font-weight:semi-bold; color:white; padding:10px 0 40px;  white-space: pre-line; text-align:center ">
            {{ props.subText }}
        </div>
    </div>
</template>
<script setup>

const props = defineProps({
    mainText:String,
    subText:String
})
</script>

<style scoped>

</style>