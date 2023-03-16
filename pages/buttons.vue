<template lang="pug">
#ButtonsPage
    Buttons {{"Hello"}}
</template>

<script>
export default {
    components:{
        buttons: ()=>import("@/components/Buttons.vue")
    }
}
</script>