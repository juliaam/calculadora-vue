<template>
	<div id="navbar">
		<nav> 
			<img :alt="alt" id="logo">
		</nav>
	</div>
</template>

<script>

export default ({
	name: "NavBar",
	data() {
    return {
	src: "", // falta o :src com o link da logo em <img 
    alt: "Calculadora Vue"
    }
  },

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