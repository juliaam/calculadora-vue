<template>
	<div id="navbar">
		<nav> 
			<img :src="logo" :alt="alt" id="logo">
		</nav>
	</div>
</template>

<script>

export default ({
	name: "NavBar",
	props: ["logo", "alt"]
})
</script>

<style scoped>
	#navbar {
		background-color: #161515;
		color:aliceblue;
		text-align: center;
		position: flex;
		padding: 10px;
		font-size: large;
	}
	
</style>