<template>
	<!-- <div id="navbar"> -->
				<ul>
					<li>
						<img src="../icons/logo.png">
					</li>
					<li>
						<span>
							Calculadora Vue
						</span>
					</li>
				</ul>
	<!-- </div> -->
</template>

<script>

export default ({
	name: "NavBar",
	data() {
		return {
		}
	},

})
</script>

<style scoped>

li {
	float: center;
}
li span {
	display: block;
	font-family: 'Lucida Console';
	margin-left: 5px;
}

ul {
	white-space: nowrap;
	display: flex;
	align-items: center;
	align-content: center;
	justify-content: center;
	overflow: hidden;
	list-style-type: none;
	background-color: #33363a;
	color: aliceblue;
	text-align: center;
	margin: 0;
	font-size: large;
}
</style>