<template>
	<div id="appHome">
		<header class="cabecalho">
			<aside class="cabecalho-container">
				<img class="cabecalhoContainer-logo" src="../../static/assets/alemao-para-o-mundo_logo.svg" @click="resetSegmento">
				<form class="cabecalhoContainer-form" @click="reset">
					<input
						class="cabecalhoContainerForm-entrada"
						type="text" 
						placeholder="o que você procura?"
						v-model="nomeAtividade"
					>
					<img class="cabecalhoContainerForm-icon" src="../../static/assets/Lupa-busca.svg">
				</form>
				<nav class="cabecalhoContainer-menu">
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Alimentação')">
						alimentação
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/alimentacao.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Arte e Cultura')">
						arte e cultura
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/arteEcultura.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Beleza e Estética')">
						beleza e estética
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/belezaEestetica.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Coletivo')">
						coletivos
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/coletivos.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Educação')">
						educação
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/educacao.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Esporte e Atividade Física')">
						esportes e atividades
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/esportes.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('ONG')">
						ong's
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/ongs.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Saúde')">
						saúde
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/saude.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Serviço')">
						serviços
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/servicos.svg">
						</div>
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Transporte')">
						transportes
						<div class="containerMenuItem-icon">
							<img class="menuItem-icon" src="../../static/assets/transporte.svg">
						</div>
					</button>
				</nav>
			</aside>
			<ListaAtividades
				:segmento="segmento"
				:subSegmento="subSegmento"
				:selectAtividade="selectAtividade"
				:nomeAtividade="nomeAtividade"
				v-show="segmento"
				v-if="alterar" 
				@alterar="selecionarAtividades"
				@selectAtividade="value => {selectAtividade = value}" 
			></ListaAtividades>	
			<Atividade
				:selectAtividade="selectAtividade"
				@alterar="value => {alterar = value}"
				v-else
			></Atividade>
			<section 
				class="cabecalhoContainer-filtros"
				v-show='subSegmentosFiltrados'
			>
				<p class="cabecalhoContainerFiltros-item"
					v-for="subSegmento in subSegmentosFiltrados"
					@click="setsubSegmento(subSegmento)"
				>{{ subSegmento }}</p>
			</section>
		</header>
		<header class="cabecalhoMobile" v-if="ok">
			<img class="cabecalhoContainer-logo" 
				src="../../static/assets/alemao-para-o-mundo_logo.svg">
			<form class="cabecalhoMobile-form" @click="reset">
				<input class="cabecalhoContainerForm-entrada" 
					type="text"
					placeholder="O que você procura?"
					v-model="nomeAtividade"
					@keyup.enter="ok=false">
				<img class="cabecalhoContainerForm-icon" src="../../static/assets/Lupa-busca.svg" @click="ok=false">
			</form>
			<nav class="cabecalhoMobile-menu">
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Alimentação')"> 
					<div class="cabecalhoMobileMenuBtn-div">
						<img class="menuBtnDiv-icon" src="../../static/assets/alimentacao.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">alimentação</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Arte e Cultura')">
					<div class="cabecalhoMobileMenuBtn-div">
						<img class="menuBtnDiv-icon" src="../../static/assets/arteEcultura.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">arte e cultura</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Beleza e Estética')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/belezaEestetica.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">beleza e estética</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Coletivo')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/coletivos.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">coletivo</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Educação')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/educacao.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">educação</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Esporte e Atividade Física')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/esportes.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">esportes e atividades</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('ONG')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/ongs.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">ong's</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Saúde')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/saude.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">saúde</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Serviço')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/servicos.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">serviços</span>
				</button>
				<button class="cabecalhoMobileMenu-btn" v-on:click="setSegmento('Transporte')">
					<div class="cabecalhoMobileMenuBtn-div">
					<img class="menuBtnDiv-icon" src="../../static/assets/transporte.svg">
					</div>
					<span class="cabecalhoMobileMenuBtn-segmento">transportes</span>
				</button>
			</nav>
		</header>
		<main class="containerAtividade" v-else>
			<h1 class="containerAtividade-titulo" v-show="alterar">
				{{ segmento.toLowerCase() }}
				<span class="containerAtividade-btnClose" @click="resetSegmento()">X</span>
			</h1>
			<form class="cabecalhoMobile-form" @click="reset" v-show="alterar">
				<input class="cabecalhoContainerForm-entrada" type="text" placeholder="O que você procura?" v-model="nomeAtividade">
				<p 
					class="glyphicon glyphicon-menu-hamburger cabecalhoMobileForm-menuHamburger"
					@click="mudarDrop"
				></p>
				<nav class="menuHamburger-drop" v-show="drop">
					<div class="menuHamburgerDrop-Item"
						v-for="subSegmento in subSegmentosFiltrados" 
						@click="setsubSegmento(subSegmento)"
					>
					<p>{{ subSegmento }}</p>
					</div>
				</nav>
			</form>
			<ListaAtividades
				:segmento="segmento"
				:subSegmento="subSegmento"
				:selectAtividade="selectAtividade"
				:nomeAtividade="nomeAtividade"
				v-if="alterar" 
				@alterar="selecionarAtividades"
				@selectAtividade="value => {selectAtividade = value}" 
			></ListaAtividades>	
			<Atividade
				:selectAtividade="selectAtividade"
				@alterar="value => {alterar = value}"
				v-else
			></Atividade>
		</main>
		<main class="homeDescricao" v-if="ocultarDescricao">
			<section class="homeDescricao-texto">
				<h1 class="homeDescricao-titulo">COMO SURGIU O<br>ALEMÃO PARA<br>O MUNDO</h1>
				<p class="homeDescricao-parag">
					O Alemão para o mundo é o resultado do projeto final dos estudantes do Vai Na Web, cujo os quais em sua maioria são residentes desse conjunto de favelas.
				</p>
				<p class="homeDescricao-parag">
					Após três meses de aprendizado técnicos e praticos, eles mapaearam iniciativas sociais, culturais, empreendedoras, para mostrar a potencialidade, talentos, resistência existente no Complexo do Alemão.
				</p>
			</section>
			<section class="homeDescricao-vnw">
				<img class="homeDescricaoVnw-logo" src="../../static/assets/vai-na-web_logo.svg">
				<p class="homeDescricao-parag">
					O Vai na Web é um curso de programação e desenvolvimento web
					realizado dentro de organizações de base comunitária para jovens de
					16 a 29 anos. Atualmente, acontece em dois polos: Complexo do
					Alemão (Educap) e Morro dos Prazeres (Proa), contando com 53
					alunos capacitados até o momento. Dos 12 formados pela turma piloto,
					4 foram contratados e já estão trabalhando na área.
				</p>
				<p class="homeDescricao-parag">
					As aulas do programa 100% financiado pela 1STi e realizado em
					parceria com o Instituto Precisa Ser constituem uma base pedagógica
					de conteúdos compatíveis com as ferramentas utilizadas pelo mercado
					de TI – CSS, HTML, design responsivo – e abrangem a preocupação
					com a formação socioemocional do aluno. Além do aprendizado
					técnico, o Vai na Web apresenta aulas de comunicação não violenta,
					meditação, liderança, postura profissional e respeito à diversidade.
				</p>
				<a class="homeDescricaoVnw-link" href="http://www.vainaweb.com.br/" target="_blank">fique por dentro</a>
			</section>
			<footer class="homeDescricao-rodape">
				<a class="rodape-linkIcon" href="http://www.1sti.com.br/" target="_blank">
					<img class="rodape-logo1sti" src="../../static/assets/1sti_logo.svg">
				</a>
				<a class="rodape-linkIcon" href="https://www.facebook.com/educap.org/" target="_blank">
					<img class="rodape-logoEducap" src="../../static/assets/educap_logo.svg">
				</a>
				<a class="rodape-linkIcon" href="https://www.facebook.com/precisaser/" target="_blank">
					<img class="rodape-logoPrecisa" src="../../static/assets/precisa-ser_logo.svg">
				</a>
			</footer>
		</main>
		<footer class="rodape" v-else>
				<a class="rodape-linkIcon" href="http://www.1sti.com.br/" target="_blank">
					<img class="rodape-logo1sti" src="../../static/assets/1sti_logo.svg">
				</a>
				<a class="rodape-linkIcon" href="https://www.facebook.com/educap.org/" target="_blank">
					<img class="rodape-logoEducap" src="../../static/assets/educap_logo.svg">
				</a>
				<a class="rodape-linkIcon" href="https://www.facebook.com/precisaser/" target="_blank">
					<img class="rodape-logoPrecisa" src="../../static/assets/precisa-ser_logo.svg">
				</a>
			</footer>
	</div>
</template>
<script>
import ListaAtividades from './ListaAtividades.vue' 
import Atividade from './Atividade.vue' 

export default{
	name:'Home',
	data(){
		return{
			segmento: '',
			subSegmento:'',
			alterar:true,
			ok:true,
			drop:false,
			ocultarDescricao:true,
			selectAtividade: '',
			nomeAtividade:'',
			segmentos: [
					{
						nome: 'Alimentação',
						subSegmentos: [
							'Restaurante', 
							'Lanches', 
							'Doceria',
							'Festas'
						]
					},
					{
						nome: 'Arte e Cultura',
						subSegmentos: [ 
							'Graffiti', 
							'Musica',
							'Dança',
							'Poesia',
							'Teatro',
							'Fotografia',
							'Educação',
							'Eventos'
						]
					},
					{
						nome: 'Beleza e Estética',
						subSegmentos: [
							'Cabelo',
							'Maquiagem',
							'Corpo'				
						]
					},
					{
						nome: 'Coletivo',
						subSegmentos: [
							'Coworking',
							'Design',
							'Fotografia',
							'Assistência Social',
							'Produção',
							'Cultura',
							'Moda',
							'Poesia'
						]
					},
					{
						nome: 'Educação',
						subSegmentos: [
							'Tecnologia',
							'Infantil',
							'Comunicação'
						]
					},
					{
						nome: 'Esporte e Atividade Física',
						subSegmentos: [
							'Arte Marcial',
							'Academia',
							'Futebol',
							'Funcional'
						]
					},
					{
						nome: 'ONG',
						subSegmentos: [
							'Cidania e Desenvolvimento',
							'Educação e Cultura',
							'Assistencia Social'
						]
					},
					{
						nome: 'Saúde',
						subSegmentos: [
							'Fisioterapia',
							'Laboratorio',
							'Clinica'
						]
					},
					{
						nome: 'Serviço',
						subSegmentos: [
							'Coworking',
							'Dança',
							'Design',
							'Fotografia',
							'Gráfica',
							'Produção'
						]
					},
					{
						nome: 'Transporte',
						subSegmentos: [
							'Moto Táxi',
							'Táxi',
							'Ônibus',
							'Van',
							'Kombi'
						]
					}
				]
			}
			},
		computed:{
			subSegmentosFiltrados(){
				const segmento = this.segmentos.find(segmento => segmento.nome === this.segmento)	

				if(segmento){
					return segmento.subSegmentos
				}

				return null
			}
		},
	methods:{
		setSegmento(value){
			this.segmento = value
			this.subSegmento = ''
			this.ok = false
			this.ocultarDescricao = false
			this.reset()
		},
		reset(){
			this.alterar = true
		},
		resetSegmento(){
			this.segmento = ''
			this.subSegmento = ''
			this.ok = true
			this.ocultarDescricao = true
			this.reset()
		},
		setsubSegmento(value){
			this.subSegmento = value
			
			if(this.alterar === false){
				this.alterar = true
			}
		},
		selecionarAtividades(){
			this.alterar = !this.alterar
		},
		mudarDrop(){
			this.drop = !this.drop
		}
	},
	components:{
		ListaAtividades,
		Atividade
	}
}	  
</script>

<style scoped>
#appHome{
	width: 100%;
	min-height: 100vh;
	background-color: #fcae1b;
	display: flex;
	flex-flow: row wrap;
	justify-content: flex-start;
	align-items: flex-start;
}
.cabecalho{
	width: 100%;
	min-height: 100vh;
	padding-bottom: 10%;
	border-bottom: 2px solid #f26522;
	background: url(../../static/assets/background.svg) center bottom no-repeat;
	background-size: 100%;
	display: flex;
	justify-content: flex-start;
	align-items: flex-start;
	flex-direction: row;
	border-bottom: 2px solid #f26522;
}
@media(max-width: 640px){
	.cabecalho{
		display: none;
	}
}
.cabecalho-container{
	max-width: 32%;
	min-width: 350px;
	min-height: 70vh;
	margin: 16px 2%;
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
	align-items: flex-start;
}
.cabecalhoContainer-logo{
	width: 100%;
	margin-bottom: 24px;
}
@media (max-width: 640px){
	.cabecalhoContainer-logo{
		width: 65%;
		margin-top: 10px;
	}
}
.cabecalhoContainer-form{
	width: 100%;
	height: 50px;
	padding: 2% 5%;
	border-radius: 30px;
	background: #fff;
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.cabecalhoContainerForm-entrada{
	width: 80%;
	border-style: none;
	border-radius:30px;
	font-size: 1.30em;
	color: #2e3192;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 400;
}
.cabecalhoContainerForm-entrada:focus{
	outline: none;
}
.cabecalhoContainerForm-icon{
	width: 28px;
	border-top: 10px;
}
.cabecalhoContainer-menu{
	width: 100%;
	min-height: 60vh;
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
	align-items: flex-start;
}
.cabecalhoContainerMenu-item{
	width: 100%;
	height: 60px;
	padding: 1% 24px;
	padding-right: 10px;
	border: solid 7px #fcae1b;
	border-radius: 30px;
	font-size: 1.10em;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 400;
	color: #fff;
	text-align: left;
	background-color: #f26522;
	display: flex;
	justify-content: space-between;
	align-items: center;
	
}
.cabecalhoContainerMenu-item:hover,
.cabecalhoContainerMenu-item:focus{
	background-color: #2e3192;
	outline: none;
}
.containerMenuItem-icon{
	width: 39px;
	display: flex;
	justify-content: center;
}
.menuItem-icon{
	height: 22px;
	/*margin-right: 10px;*/
	
}
.cabecalhoContainer-filtros{
	width: 250px;
	min-height: 130px;
	padding: 10px;
	margin: 180px 30px 0 30px;
	border-radius: 20px;
	background:#fff;
	display: flex;
	flex-flow: row wrap;
	align-items: flex-start;
	align-content: space-around;
	justify-content: flex-start;
}
@media (max-width: 1000px) and (min-width: 640px){
	.cabecalhoContainer-filtros{
		display: none;
	}
}
.cabecalhoContainerFiltros-item{
	min-width:47%;
	max-width: 51%;
	min-height: 10px; 
	padding: 5px 10px;
	cursor:pointer;
	border-radius: 20px;
	font-family: ministry, sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 1.13em;
	color: #2e3192;
	text-align: left;
	text-decoration: none;
}
.cabecalhoContainerFiltros-item:hover{
 	color: #fff;
	background-color: #f26122;
}
.cabecalhoMobile{
	background: url(../../static/assets/background.svg) center bottom no-repeat;
	background-size: auto;
	width: 100%;
	min-height: 100vh;
	padding-bottom: 180px;
	display: none;
	flex-flow: row wrap;
	justify-content: center;
	align-items: center;
	align-content: flex-start;
}
@media(max-width: 640px){
	.cabecalhoMobile{
		display: flex;
	}
}
.cabecalhoMobile-menu{
	width: 100%;
	min-height: 55vh;
	margin-top: 28px;
	display: flex;
	flex-flow: row wrap;
	justify-content: space-around;
	align-items: flex-start;
}
.cabecalhoMobileMenu-btn{
	width: 49%;
	height: 70px;
	padding: 1% 24px;
	border: none;
	border-radius: 50px;
	font-size: 1.30em;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 400;
	color: #fff;
	text-align: left;
	background-color: transparent;
	display: flex;
	justify-content: space-between;
	align-items: center;
}
.cabecalhoMobileMenu-btn:focus{
	background-color: #f26522;
	outline:none;
}
@media(max-width: 400px){
	.cabecalhoMobileMenu-btn{
		width: 48%;
		max-width: auto;
		margin:5px 0;
	}
}
.cabecalhoMobileMenuBtn-div{
	width: 25%;
	display: flex;
	justify-content: center;
	align-items: center;
}
@media(max-width: 640px){
	.cabecalhoMobileMenuBtn-div{
		width: 25%;
	}
}
.menuBtnDiv-icon{
	height: 40px;
	margin: 10px;
}
@media(max-width: 640px){
	.menuBtnDiv-icon{
		height: 33px;
		margin: 0;
	}
}
.cabecalhoMobileMenuBtn-segmento{
	width: 75%;
	padding-left: 20%;
	font-family: ministry, sans-serif;
	font-weight: 600;
	font-size: 0.80em;
	color:#fff;
	text-align: left;
}
@media(max-width: 640px){
	.cabecalhoMobileMenuBtn-segmento{
		width: 90%;
		padding-left: 12%;
		font-size: 0.75em;
	}
}

/* Atividade */
.containerAtividade{
	width: 100%;
	min-height: 100vh;
	background: url(../../static/assets/background.svg) center bottom no-repeat;
	background-size: auto;
	display: none;
	flex-flow: column nowrap;
	justify-content: flex-start;
	align-items: center;
}
@media(max-width: 640px){
	.containerAtividade{
		display: flex;
	}
}
.containerAtividade-titulo{
	width: 100%;
	height: 52px;
	margin-top: 0;
	background-color: #f26523;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 400;
	color: #ffffff;
	text-align: center;
	position: relative;
	display:flex;
	justify-content: center;
	align-items: center;
}
.containerAtividade-btnClose{
	width: 25px;
	height: 25px;
	border-radius: 50%;
	background-color: #fff;
	cursor:pointer;
	position: absolute;
	right: 10px;
	top:16px;
	font-family: ministry, sans-serif;
	font-weight: 900;
	font-size: 0.5em;
	color: rgb(244, 100, 36);
	display: flex;
	align-items: center;
	justify-content: center;
}
.cabecalhoMobile-form{
	width: 85%;
	min-height: 45px;
	padding: 2% 5%;
	margin-bottom: 15px;
	border-radius: 30px;
	background: #fff;
	position: relative;
	display: flex;
	flex-flow: row wrap;
	align-items: center;
	justify-content: space-between;
}
.cabecalhoMobileForm-menuHamburger{''
	width: 5%;
	margin: 0 auto;
	color:#000;
	font-size: 19px;
}
.menuHamburger-drop{
	min-height: 130px;
	padding: 10px;
	display: flex;
	flex-flow: row wrap;
	align-items: flex-start;
	justify-content: flex-start;
}
.menuHamburgerDrop-Item{
	min-width:35%;
	max-width: 51%;
	min-height: 10px; 
	padding: 3px; 
	padding-left: 10px;
	margin: 0 5px;
	border-radius: 20px;
	font-family: ministry, sans-serif;
	font-weight: 400;
	font-style: italic;
	font-size: 1.4em;
	color: #2e3192;
	display: flex;
	align-items: center;
	justify-content: flex-start;
}
.menuHamburgerDrop-Item:hover{
	background-color: #f26522;
}
.menuHamburgerDrop-Item p{
	margin: 0; 
}

/* main */

.homeDescricao{
	width: 100%;
	min-height: 70vh;
	display: flex;
	flex-flow: row wrap;
	justify-content: center;
	align-items: flex-start;
	background-color: #f26522;

}
.homeDescricao-texto{
	width: 32%;
	min-width: 400px;
	margin: 3%;
}
@media(max-width: 640px){
	.homeDescricao-texto{
		min-width: 90%;
	}
}
.homeDescricao-titulo{
	font-size: 2.30em;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 700;
	color: #2e3192;
	text-align: left;
	margin-bottom: 21px;
}
.homeDescricao-vnw{
	width: 32%;
	min-width: 400px;
	margin: 2% 5%;
	display: flex;
	flex-flow: column nowrap;
	align-items: center;
	justify-content: flex-start;
}
@media(max-width: 640px){
	.homeDescricao-vnw{
		min-width: 90%;
	}
}
.homeDescricaoVnw-logo{
	width: 50%;
	margin: 12px;
}
.homeDescricao-parag{
	font-size: 1em;
	font-family: ff-basic-gothic-pro, sans-serif;
	font-style: normal;
	font-weight: 300;
	color: #fff;
	text-align: left;
}
@media(max-width: 640px){
	.homeDescricao-parag{
		width: 100%;
		margin: 0 auto;
	}
}
.homeDescricaoVnw-link{
	width: 259px;
	height: 55px;
	margin-top: 10%;  
	border: solid 5px #fff;
	border-radius: 40px;
	text-decoration: none;
	text-align: center;
	font-size: 1.30em;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 700;
	color: #fff;
	display: flex;
	justify-content: center;
	align-items: center;
}
.rodape,
.homeDescricao-rodape{
	width: 20%;
	min-width: 200px;
	min-height: 70vh;
	padding: 2%;
	background-color: #f26522;
	display: flex;
	flex-flow: row wrap;
	align-items: center;
	justify-content: center;
}
.rodape{
	width: 100%;
	min-height: 20vh;
	flex-wrap: nowrap;	
}
@media(max-width: 1250px){
	.homeDescricao-rodape{
		width: auto;
		min-width: auto;
		max-width: 100%;
		min-height: 30vh;
		justify-content: center;
		align-items: center;
		align-content: flex-start;
	}
}
/*@media(max-width: 640px){
	.rodape{
		max-width: 90%;
	}
}*/
.rodape-linkIcon{
	margin: 20%;
	display: flex;
	justify-content: center;
	align-items: center;
}
.rodape .rodape-linkIcon{
	margin:0;
}
@media(max-width: 1250px){
	.rodape-linkIcon{
		margin: 10px auto;
	}
}
.rodape-logo1sti{
	width: 40%;
	min-width: 70px;
}
@media(max-width: 1250px){
	.rodape-logo1sti{
		min-width: auto;
	}
}
.rodape-logoEducap{
	width: 70%;
	min-width: 150px;
}
@media(max-width: 1250px){
	.rodape-logoEducap{
		min-width: auto;
	}
}
.rodape-logoPrecisa{
	width: 70%;
	min-width: 150px;
}
@media(max-width: 1250px){
	.rodape-logoPrecisa{
		min-width: auto;
	}
}
</style>