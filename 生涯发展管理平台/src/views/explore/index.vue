<template>
    <div class="">
    	<keep-alive> 
		    <router-view v-if="$route.meta.keepAlive"></router-view> 
		</keep-alive> 
		<router-view v-if="!$route.meta.keepAlive"></router-view>
    </div>
</template>

<script>
    export default {
        name: "index"
    }
</script>

<style scoped>

</style>
