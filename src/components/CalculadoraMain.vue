<template>
	<div class="container">
		<!-- <p class="display"> {{ this.display }} </p> -->
		<div class="calculadora">
			<div class="placeholder"> {{ valores }}</div>
			<div class="corpo">
				<button type="submit" class="botaoCalc clear span-3" @click="apagar"> &larr; </button>
				<button type="submit" class="botaoCalc" @click="apagarTudo"> C </button>
				<button type="submit" class="botaoCalc" @click="clickExibirOp('+')"> + </button>
				<button v-for="number in ['7', '8', '9'] " :key="number" class="botaoCalc" @click="clickExibirNum(number)">
					{{ number }} </button>
				<button type="button" class="botaoCalc" @click="clickExibirOp('-')"> - </button>
				<button v-for="number in ['4', '5', '6'] " :key="number" class="botaoCalc" @click="clickExibirNum(number)">
					{{ number }}</button>
				<button type="button" class="botaoCalc" @click="clickExibirOp('*')"> * </button>
				<button v-for="number in ['1', '2', '3'] " :key="number" class="botaoCalc" @click="clickExibirNum(number)">
					{{ number }} </button>
				<button type="button" class="botaoCalc" @click="clickExibirOp('/')"> / </button>
				<button type="button" class="botaoCalc span-3" @click="clickExibirOp(0)"> {{ 0 }} </button>
				<button type="button" class="botaoCalc" @click="clickExibirOp('.')"> . </button>
				<button type="button" class="botaoCalc" @click="operacao()"> = </button>
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
			valoresOuvir: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
			sinais: ['+', '-', '/', '*', '.'],
			novoValue: '',
		}
	},
	mounted() {
		this.ouvir(),
		this.impedirSinalRep()
	},
	methods: {
		apagarTudo() {
			this.valores = ''
		},
		apagar() {
			this.valores = this.valores.toString().split('').slice(0, -1).join('')
		},

		// Ouvir teclado
		ouvir() {
			const verificacao = (e) => {
				let valor = (this.valoresOuvir.find(value => value == e.key) || this.sinais.find(value => value == e.key))
				if (this.sinais.some(x => x === e.key)) {
					this.impedirSinalRep()
				}
				if (valor) {
					this.valores = this.valores + valor
				}
				if (e.key == 'Backspace') {
					this.apagar()
				}
				if (e.key == 'Enter'
				) {
					this.operacao()
				}	
			}
			document.addEventListener("keydown", function (e) {
				verificacao(e)

			})
		},
		operacao() { // fazer a soma com a função eval()
			this.valores = eval(this.valores)
		},
		clickExibirNum(number) {
			this.valores = this.valores + number
		},
		clickExibirOp(value) {
			if (this.sinais.some(x => x === value)) {
				this.impedirSinalRep()
			}
			this.valores = this.valores + value
		},
		impedirSinalRep() {
			const ultimoC = this.valores.substring(this.valores.length - 1, this.valores.length)
			const sinal = this.sinais.filter(sinal => sinal === ultimoC)
			if (this.valores.includes(sinal[0])) {
				this.apagar()
			}
		},
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
	min-width: 300px;
	max-width: 300px;
	background: #eee;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}

.span-2 {
	grid-column: span 2;
}

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
