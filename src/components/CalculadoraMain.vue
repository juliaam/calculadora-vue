<template>
	<div class="container">
		<!-- <p class="display"> {{ this.display }} </p> -->
		<div class="calculadora">
			<input class="placeholder" type="number" v-model="valores">
			<div class="corpo">
				<button type="submit" class="botaoCalc clear span-3" @click="apagar"> &larr; </button>
				<button type="submit" class="botaoCalc" @click="apagarTudo" > C </button>
				<button type="submit" class="botaoCalc" @click="clickExibir()" > {{ '+' }} </button>
				<button v-for="number in ['7', '8', '9'] " :key="number" class="botaoCalc" @click="clickExibirNum(number)"> {{ number }} </button>
				<button type="button" class="botaoCalc" @click="clickExibir(value)" value="-" > - </button>
				<button v-for="number in ['4', '5', '6'] " :key="number" class="botaoCalc" @click="clickExibirNum(number)"> {{ number }}</button>
				<button type="button" class="botaoCalc" @click="clickExibir(value)" value="*"> * </button>
				<button v-for="number in ['1', '2', '3'] " :key="number" class="botaoCalc" @click="clickExibirNum(number)"> {{ number }} </button>
				<button type="button" class="botaoCalc" @click="NumclickExibir" value="/"> / </button>
				<button type="button" class="botaoCalc span-3" @click="clickExibirNum" :key="0"> {{ 0 }} </button>
				<button type="button" class="botaoCalc" @click="clickExibir" value=","> , </button>
				<button type="button" class="botaoCalc" @click="clickExibir" value="="> = </button> 
			</div>
		</div>
	</div>
</template>

<script>
//Parte dos cálculos

export default ({
	name: "CalculadoraMain",
	data() {
		return {
			valores: '',
			// display: '',
		}
	},
	mounted() {
		this.ouvir()
	},
	methods: {
		apagarTudo() {
			this.valores = ''
		},
		apagar() {
			this.valores = this.valores.toString().split('').slice(0, -1).join('')
			console.log(this.valores)
		},
		// Ouvir teclado
		ouvir() {
			document.addEventListener("keydown", function () {
			})
		},

		// Funcoes de adicionar caracteres
		clickExibirNum(number){
			this.valores = this.valores + number
		},
		clickExibir(value){
			this.valores = this.valores + value
		}
	}
})
</script>

<style scoped>
.container {
	justify-content: center;
	align-items: center;
}

* {
	box-sizing: border-box;
}

.corpo {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	border: 0;
}

.calculadora {
	max-width: 320px;
	background: #eee;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}

.span-2 {
	grid-column: span 2;
}

/* .display {
	background: #33363a;
	height: 40px;
	width: 150px;
	font-size: 40px;
	text-align: right;
	color: #a1a3a2;
	font-family: 'Courier New', Courier, monospace;
} */

.placeholder {
	width: 100%;
	height: 100px;
	background: #33363a;
	border-bottom-color: black;
	border-bottom-width: 10px;
	border-right-color: black;
	border-right-width: 1px;
	font-size: 40px;
	text-align: right;
	padding: 0.3em;
	font-family: 'Courier New', Courier, monospace;
	color: white;
	grid-column: span 3;
}

.span-3 {
	grid-column: span 2;
}

.botaoCalc {
	height: 65px;
	border: 1px solid black;
	background: #33363a;
	font-size: 50px;
	color: white;
	transition: 0.3s;

}

.botaoCalc:hover {
	background: #726d6d;
}

.placeholder::-webkit-inner-spin-button {
	-webkit-appearance: none;
}

.placeholder {
	-moz-appearance: textfield;
	appearance: textfield;
}
</style>
