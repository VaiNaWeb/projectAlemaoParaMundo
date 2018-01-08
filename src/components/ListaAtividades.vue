<template>
<div id="listaAtividades">
	<main class="conteudo">
		<section  class="conteudo-atividades">
			<div v-for="atividade in atividadesFiltradas" @click="selecionarAtividade(atividade.nome)">
				<div class="conteudoAtividades-item">
					<img class="atividadesItem-foto" v-bind:src="atividade.imagem">
					<div class="atividadesItem-mask">
						<p class="atividadesItem-nome">{{ atividade.nome }}</p>
						<p class="atividadesItem-seguimento">{{ atividade.subSegmento }}</p>
					</div>
				</div>
			</div>
		</section>
	</main>
</div>
</template>

<script>
export default{
	name:'ListaAtividades',
	props:{
		segmento:{
			type:String,
			required:true,
		},
		subSegmento:String,
		selectAtividade:String,
		nomeAtividade:String
	},
	data(){
		return{

			atividades:[
				{
					imagem:'../static/imagens/Noix Q Faz/noixqfaz1.jpg',
					nome: 'Noix Q Faz',
					segmento: 'Arte e Cultura',
					subSegmento: 'Graffiti'
				},
				{
					imagem:'../static/imagens/VIdançar/vidancar.jpg',
					nome: 'Vidançar',
					segmento: 'Arte e Cultura',
					subSegmento: 'Dança'
				},
				{
					imagem:'../static/imagens/SlamLaje/slamlaje1.jpg',
					nome: 'Slam Laje',
					segmento: 'Coletivo',
					subSegmento: 'Cultura'
				},
				{
					imagem: '../static/imagens/CasaBrota/Casa Brota Coworking de Favela.jpg',
					nome: 'Casa Brota',
					segmento: 'Coletivo',
					subSegmento: 'Coworking'
				},
				{
					imagem: '../static/imagens/Classe D/D - classed1.jpg',
					nome: 'Classe D – Ateliê de Ideias',
					segmento: 'Arte e Cultura',
					subSegmento: 'Graffiti'
				},
				{
					imagem:'../static/imagens/Afro Laje/D - afrolaje1.jpg',
					nome: 'Afro Laje',
					segmento: 'Coletivo',
					subSegmento: 'Cultura'
				},
				{
					imagem:'../static/imagens/projeto-criancas-felizes/Logo Projeto Crianças Felizes.jpg',
					nome: 'Crianças Felizes',
					segmento: 'Coletivo',
					subSegmento: 'Assistência Social'
				},
				{
					imagem:'../static/imagens/Raízes em Movimentos/raizesemmovimento2.jpg',
					nome: 'Instituto Raízes Em Movimento',
					segmento: 'ONG',
					subSegmento: 'Cidania e Desenvolvimento'
				},
				{
					imagem: '../static/imagens/Gato Mídia/12768127_1556038881375883_2486605588657018434_o.jpg',
					nome: 'GatoMÍDIA',
					segmento: 'Educação',
					subSegmento: 'Comunicação'
				}
				,
				{
					imagem: '../static/imagens/instituto movimento e vida/movimentoevida3jpg.jpg',
					nome: 'Instituto Movimento & Vida',
					segmento: 'Esporte e Atividade Física',
					subSegmento: 'Fisioterapia'
				},
				{
					imagem: '../static/imagens/crj/crj1.jpg',
					nome: 'CRJ Alemão',
					segmento: 'Arte e Cultura',
					subSegmento: 'Educação'
				},
				{
					imagem: '../static/imagens/Novos Líderes/novoslideres.jpg',
					nome: 'Novo Líderes',
					segmento: 'ONG',
					subSegmento: 'Cidania e Desenvolvimento'
				},
				{
					imagem: '../static/imagens/favela é fashion/fashion2.jpg',
					nome: 'Favela é FaShion',
					segmento: 'Coletivo',
					subSegmento: 'Moda'
				},
				{
					imagem: '../static/imagens/Brigadeiros Literários/Brigadeiros Literários.jpg',
					nome: 'Brigadeiros Literários',
					segmento: 'Alimentação',
					subSegmento: 'Doceria'
				},
				{
					imagem: '../static/imagens/Clube de lutas do complexo/clubedelutas3.jpg',
					nome: 'Clube de Luta do Complexo',
					segmento: 'Esporte e Atividade Física',
					subSegmento: 'Arte Marcial'
				},
				{
					imagem: '../static/imagens/Nave do Conhecimento/navedoconhecimento.jpg',
					nome: 'Nave do Conhecimento Nova Brasília',
					segmento: 'Educação',
					subSegmento: 'Tecnologia'
				},
				{
					imagem: '../static/imagens/Samba Favela/sambadefavela2.jpg',
					nome: 'Samba Favela',
					segmento: 'Arte e Cultura',
					subSegmento: 'Musica'
				},
				{
					imagem: '../static/imagens/Casa das Primas Doceria/Logo Casa das Primas Doceria.png',
					nome: 'Casa das Primas Doceria',
					segmento: 'Alimentação',
					subSegmento: 'Doceria'
				},
				// {
				// 	imagem: '',
				// 	nome: '',
				// 	segmento: '',
				// 	subSegmento: ''
				// },
			]
		}
	},
	computed:{
		atividadesFiltradas(){
			let atividades = this.atividades

			if (this.segmento){
				atividades = atividades.filter(atividade => atividade.segmento === this.segmento)
				if (this.subSegmento){
					atividades = atividades.filter(atividade => atividade.subSegmento === this.subSegmento)
				}
			}
			if (this.nomeAtividade) {
				atividades = atividades.filter(atividade => atividade.nome.toLowerCase().indexOf(this.nomeAtividade.toLowerCase()) >= 0) 
			}
			if(!this.segmento && !this.nomeAtividade){
				return null
			}
				
			return atividades
		}
	},
	methods:{
		selecionarAtividade(value){
			this.$emit('alterar')
			this.$emit('selectAtividade', value)
		}
	}
}
</script>

<style scoped>
#listaAtividades{
	max-width: 40%;
	min-height: 100vh;
	margin-right: auto;
	display: flex;
	flex-flow: row wrap;
	justify-content: center;
	align-items: flex-start;	
}
@media (max-width: 640px){
	#listaAtividades{
		max-width: 95%;
		margin-right: 0;
	}
}
.conteudo{
	width:100%;
    min-height: 100vh;
    display: flex;
    align-items: flex-start;
}
.conteudo-atividades{
	width: 100%;
	margin-top: 20px;
}
.conteudoAtividades-item{
	width: 100%;
	height: 300px;
	margin: 5px 0;
	overflow: hidden;
	position: relative;
	display: flex;
	justify-content: center;
	align-items: center;
}	
.atividadesItem-foto{
	min-width: 100%;
	max-width: 110%;
	min-height: 300px;
}
.atividadesItem-mask{
	width: 100%;
	height: 300px;
	position: absolute;
	top: 0;
	z-index: 9;
	background-color: rgba(242,101,34, 0.6);
	display: flex;
	justify-content: flex-end;
	align-items: flex-start;
	flex-direction: column;
}
.atividadesItem-mask:hover{
	background-color: rgba(46,49,146, 0.6);
}
.atividadesItem-nome{
	position: relative;
	bottom: 1%;
	left: 5%;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 700;
	font-size: 1.63em;
	color: #ffffff;
	text-align: left;
}
.atividadesItem-seguimento{
	position: relative;
	bottom: 5%;
	left: 5%;
	font-family: ministry, sans-serif;
	font-style: italic;
	font-weight: 400;
	font-size: 1.63em;
	color: #ffffff;
	text-align: left;
}


</style>