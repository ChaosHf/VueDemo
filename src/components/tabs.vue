<template>
	<div id="appBox">
		<router-view></router-view>
		<div class="tab">
			<router-link class="invest" to="invest">投资</router-link>
			<router-link class="mine" to="my">我的</router-link>
		</div>
	</div>
</template>
<script>
	export default{
	}
</script>
