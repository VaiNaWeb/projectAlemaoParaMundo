<template>
<div id="listaAtividades">
	<VueScrollbar class="my-scrollbar" ref="Scrollbar">
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
	</VueScrollbar>
</div>
</template>

<script>
// Import imagens
import NoixQFaz from '../../static/imagens/Noix Q Faz/noixqfaz1.jpg'
import ViDancar from '../../static/imagens/VIdançar/vidancar.jpg'
import SlamLaje from '../../static/imagens/SlamLaje/slamlaje1.jpg'
import CasaBrota from '../../static/imagens/CasaBrota/Casa Brota Coworking de Favela.jpg'
import ClasseD from '../../static/imagens/Classe D/D - classed1.jpg'
import AfroLaje from '../../static/imagens/Afro Laje/D - afrolaje1.jpg'
import CriancasFelizes from '../../static/imagens/projeto-criancas-felizes/Logo Projeto Crianças Felizes.jpg'
import RaizesMovimento from '../../static/imagens/Raízes em Movimentos/raizesemmovimento2.jpg'
import GatoMidia from '../../static/imagens/Gato Mídia/12768127_1556038881375883_2486605588657018434_o.jpg'
import MovimentoVida from '../../static/imagens/instituto movimento e vida/movimentoevida3jpg.jpg'
import CRJ from '../../static/imagens/crj/crj1.jpg'
import NovosLideres from '../../static/imagens/Novos Líderes/novoslideres.jpg'
import FavelaFashion from '../../static/imagens/favela é fashion/fashion2.jpg'
import BrigadeiroLiterario from '../../static/imagens/Brigadeiros Literários/Brigadeiros Literários.jpg'
import ClubeLuta from '../../static/imagens/Clube de lutas do complexo/clubedelutas3.jpg'
import NaveConhecimento from '../../static/imagens/Nave do Conhecimento/navedoconhecimento.jpg'
import SambaFavela from '../../static/imagens/Samba Favela/sambadefavela2.jpg'
import CasaPrima from '../../static/imagens/Casa das Primas Doceria/Logo Casa das Primas Doceria.png'
// Fim imagens

import VueScrollbar from 'vue2-scrollbar'
require("vue2-scrollbar/dist/style/vue2-scrollbar.css")

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
					imagem: NoixQFaz,
					nome: 'Noix Q Faz',
					segmento: 'Arte e Cultura',
					subSegmento: 'Graffiti'
				},
				{
					imagem: ViDancar,
					nome: 'Vidançar',
					segmento: 'Arte e Cultura',
					subSegmento: 'Dança'
				},
				{
					imagem: SlamLaje,
					nome: 'Slam Laje',
					segmento: 'Coletivo',
					subSegmento: 'Cultura'
				},
				{
					imagem: CasaBrota,
					nome: 'Casa Brota',
					segmento: 'Coletivo',
					subSegmento: 'Coworking'
				},
				{
					imagem: ClasseD,
					nome: 'Classe D – Ateliê de Ideias',
					segmento: 'Arte e Cultura',
					subSegmento: 'Graffiti'
				},
				{
					imagem: AfroLaje,
					nome: 'Afro Laje',
					segmento: 'Coletivo',
					subSegmento: 'Cultura'
				},
				{
					imagem: CriancasFelizes,
					nome: 'Crianças Felizes',
					segmento: 'Coletivo',
					subSegmento: 'Assistência Social'
				},
				{
					imagem: RaizesMovimento,
					nome: 'Instituto Raízes Em Movimento',
					segmento: 'ONG',
					subSegmento: 'Cidania e Desenvolvimento'
				},
				{
					imagem: GatoMidia,
					nome: 'GatoMÍDIA',
					segmento: 'Educação',
					subSegmento: 'Comunicação'
				},
				{
					imagem: MovimentoVida,
					nome: 'Instituto Movimento & Vida',
					segmento: 'Esporte e Atividade Física',
					subSegmento: 'Fisioterapia'
				},
				{
					imagem: CRJ,
					nome: 'CRJ Alemão',
					segmento: 'Arte e Cultura',
					subSegmento: 'Educação'
				},
				{
					imagem: NovosLideres,
					nome: 'Novos Líderes',
					segmento: 'ONG',
					subSegmento: 'Cidania e Desenvolvimento'
				},
				{
					imagem: FavelaFashion,
					nome: 'Favela é Fashion',
					segmento: 'Coletivo',
					subSegmento: 'Moda'
				},
				{
					imagem: BrigadeiroLiterario,
					nome: 'Brigadeiros Literários',
					segmento: 'Alimentação',
					subSegmento: 'Doceria'
				},
				{
					imagem: ClubeLuta,
					nome: 'Clube de Luta do Complexo',
					segmento: 'Esporte e Atividade Física',
					subSegmento: 'Arte Marcial'
				},
				{
					imagem: NaveConhecimento,
					nome: 'Nave do Conhecimento Nova Brasília',
					segmento: 'Educação',
					subSegmento: 'Tecnologia'
				},
				{
					imagem: SambaFavela,
					nome: 'Samba Favela',
					segmento: 'Arte e Cultura',
					subSegmento: 'Musica'
				},
				{
					imagem: CasaPrima,
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
	},
	components:{ 
    	VueScrollbar
    }
}
</script>

<style scoped>
#listaAtividades{
	max-width: 40%;
	height: 100vh;
	margin-right: auto;
	display: flex;
	flex-flow: row wrap;
	justify-content: center;
	align-items: flex-start;	
}
/*The Wrapper*/
.my-scrollbar{
	width: 100%;
	min-width: 300px;
	max-height: 100vh;
}
@media (max-width: 640px){
	.my-scrollbar{
		height: 85vh;
	}
}
@media (max-width: 400px){
	.my-scrollbar{
		height: 83vh;
	}
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
    margin-right: 5px;
    display: flex;
    align-items: flex-start;
}
.conteudo-atividades{
	width: 100%;
	margin-top: 20px;
	margin-right: 10px;
}
@media (max-width: 400px){
	.conteudo-atividades{
		margin-top: 0;
	}
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