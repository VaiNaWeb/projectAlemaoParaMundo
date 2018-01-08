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
						<img class="MenuItem-icon" src="../../static/assets/alimentacao.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Arte e Cultura')">
						arte e cultura
						<img class="MenuItem-icon" src="../../static/assets/arteEcultura.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Beleza e Estética')">
						beleza e estética
						<img class="MenuItem-icon" src="../../static/assets/belezaEestetica.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Coletivo')">
						coletivos
						<img class="MenuItem-icon" src="../../static/assets/coletivos.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Educação')">
						educação
						<img class="MenuItem-icon" src="../../static/assets/educacao.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Esporte e Atividade Física')">
						esportes e atividades físicas
						<img class="MenuItem-icon" src="../../static/assets/esportes.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('ONG')">
						ong's
						<img class="MenuItem-icon" src="../../static/assets/ongs.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Saúde')">
						saúde
						<img class="MenuItem-icon" src="../../static/assets/saude.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Serviço')">
						serviços
						<img class="MenuItem-icon" src="../../static/assets/servicos.svg">
					</button>
					<button class="cabecalhoContainerMenu-item" v-on:click="setSegmento('Transporte')">
						transportes
						<img class="MenuItem-icon" src="../../static/assets/transporte.svg">
					</button>
				</nav>
			</aside>
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
			<section 
				class="cabecalhoContainer-filtros"
				v-show='subSegmentosFiltrados'
			>
				<p 
					class="cabecalhoContainerFiltros-item"
					v-for="subSegmento in subSegmentosFiltrados"
					@click="setsubSegmento(subSegmento )"
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
					v-model="nomeAtividade">
				<img class="cabecalhoContainerForm-icon" src="../../static/assets/Lupa-busca.svg">
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
				<span class="containerAtividade-btnClose" @click="resetSegmento">X</span>
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
		<main class="homeDescricao" v-show="ocultarDescricao">
			<section class="homeDescricao-texto">
				<h1 class="homeDescricao-titulo">COMO SURGIU O ALEMÃO PARA O MUNDO</h1>
				<p class="homeDescricao-parag">
						Lorem ipsum dolor sit amet, consectetur adipiscin
					quam. Fusce velit mauris, posuere euismod sollicitudin eget, bibendum
					eget felis. Nulla vitae orci tempus, varius libero vehicula.
					Praesent convallis sem at quam congue, at accumsan diam tempus.
					Aenean finibus mauris at lorem tristique, eget auctor nisi efficitur.
					Vivamus eu dignissim justo, eu efficitur sem. Curabitur imperdiet
					vehicula nisi, eu vestibulum justo pretium a. Pellentesque habitant
					morbi tristique senectus et netus et malesuada fames ac turpis
					egestas. Vestibulum sodales sodales ex id congue. Proin vestibulum
					eros nec porttitor ullamcorper. Duis ut gravida nisl. Fusce elementum
					semper est, eget porttitor orci tempor consequat.
				</p>
				<p class="homeDescricao-parag">
						Cras vel consequat erat, tempus sagittis lorem. Nam pellentesque in
					sem ac consequat. Vestibulum vel leo a nisl rutrum accumsan tempor
					at lorem. Integer lobortis tempus mi eget commodo. Nunc a erat varius,
					dapibus neque nec, maximus sapien. Nullam pulvinar at elit imperdiet
					auctor. Vestibulum vel dolor egestas, ultricies ligula at, blalorem.
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
				<a class="homeDescricaoVnw-link" href="#">fique por dentro</a>
			</section>
			<footer class="rodape">
				<img class="rodape-logo1sti" src="../../static/assets/1sti_logo.svg">
				<img class="rodape-logoEducap" src="../../static/assets/educap_logo.svg">
				<img class="rodape-logoPrecisa" src="../../static/assets/precisa-ser_logo.svg">
			</footer>
		</main>
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
							'Bolos Festa'
						]
					},
					{
						nome: 'Beleza e Estética',
						subSegmentos: [
							'Cabelo',
							'Maquiagem',
							'Estética'				
						]
					},
					{
						nome: 'Arte e Cultura',
						subSegmentos: [
							'Cinema', 
							'Graffiti', 
							'Musica',
							'Dança',
							'Poesia',
							'Teatro',
							'Fotografia',
							'Educação'
						]
					},
					{
						nome: 'Coletivo',
						subSegmentos: [
							'Coworking',
							'Design',
							'Gráfica',
							'Fotografia',
							'Assistência Social',
							'Produção',
							'Cultura',
							'Moradia',
							'Moda',
							'Meio Ambiente'
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
			this.reset()
		},
		setsubSegmento(value){
			this.subSegmento = value
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
	width: 90%;
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
.MenuItem-icon{
	height: 22px;
	/*margin-left: 10px;*/
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
	background-color: #f26522;
}
.cabecalhoMobile{
	background: url(../../static/assets/background.svg) center bottom no-repeat;
	background-size: auto;
	width: 100%;
	min-height: 100vh;
	padding-bottom: 180px;
	/*padding-bottom: 10%;*/
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
	width: 90%;
	min-height: 55vh;
	margin-top: 28px;
	display: flex;
	flex-flow: row wrap;
	justify-content: flex-end;
	align-items: flex-start;
}
@media(max-width: 400px){
	.cabecalhoMobile-menu{
		flex-direction: column;
		align-items: center;
		justify-content: flex-start;
	}
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
	background-color: #f26522
}

@media(max-width: 400px){
	.cabecalhoMobileMenu-btn{
		width: 90%;
		margin:5px 0;
	}
}
.cabecalhoMobileMenuBtn-div{
	width: 25%;
	display: flex;
	justify-content: center;
	align-items: center;
}
.menuBtnDiv-icon{
	height: 45px;
	margin: 10px;
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

/* Atividade */

.containerAtividade{
	width: 100%;
	min-height: 100vh;
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
	/*align-content: space-around;*/
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
	/*background-color: #0f0;*/
	margin: 0; 
}
/*.cabecalhoMobileForm-menuHamburger:hover .menuHamburger-drop{
	display: block;
}

.cabecalhoContainerFiltros-item{
	min-width:47%;
	max-width: 51%;
	min-height: 10px; 
	padding: 5px 10px;
	border-radius: 20px;
	font-family: ministry, sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 1.13em;
	color: #2e3192;
	text-align: left;
	text-decoration: none;
}*/

/* menu */

.homeDescricao{
	width: 100%;
	min-height: 100vh;
	display: flex;
	flex-flow: row wrap;
	justify-content: center;
	align-items: flex-start;
	background-color: #f26522;

}
@media(max-width: 640px){
	.conteudo{
		/*min-width: 100%;*/
	}
}
.homeDescricao-texto{
	width: 32%;
	min-width: 400px;
	margin: 3%;
}
@media(max-width: 640px){
	.conteudo-texto{
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
	.conteudo-vnw{
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
.homeDescricaoVnw-link{
	width: 259px;
	height: 55px;
	margin-top: 10%;  
	padding-top: 4px; 
	border: solid 7px #fff;
	border-radius: 40px;
	text-decoration: none;
	text-align: center;
	font-size: 1.30em;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 700;
	color: #fff;
}
.rodape{
	width: 20%;
	min-width: 200px;
	min-height: 100vh;
	padding: 2%;
	background-color: #f26522;
	display: flex;
	flex-flow: row wrap;
	align-items: center;
	justify-content: flex-end;

	/*background-color: red;*/
}
@media(max-width: 1250px){
	.rodape{
		width: auto;
		min-width: auto;
		max-width: 50%;
		min-height: 30vh;
		justify-content: center;
		align-items: center;
		align-content: flex-start;
	}
}
@media(max-width: 640px){
	.rodape{
		max-width: 90%;
	}
}
.rodape-logo1sti{
	width: 40%;
	min-width: 100px;
	margin: 20%;
}
@media(max-width: 1250px){
	.rodape-logo1sti{
		width: 20%;
		min-width: auto;
		margin: 10px auto;
	}
}
.rodape-logoEducap{
	width: 70%;
	min-width: 150px;
	margin: 20%;
}
@media(max-width: 1250px){
	.rodape-logoEducap{
		width: 35%;
		min-width: auto;
		margin: 10px auto;
	}
}
.rodape-logoPrecisa{
	width: 70%;
	min-width: 150px;
	margin: 20%;
}
@media(max-width: 1250px){
	.rodape-logoPrecisa{
		width: 35%;
		min-width: auto;
		margin: 10px auto;
	}
}


</style>