<template lang="pug">
#TransferPage
    Transfer(:data="'Hello'")
</template>

<script>
export default {
    components:{
        Transfer:()=>import("@/components/Transfer/Transfer.vue")
    }
}
</script>