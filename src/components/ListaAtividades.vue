<template>
<div id="listaAtividades">
<!-- <link rel="stylesheet" href="../../static/css/VueScrollbar.css"> -->
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
import AbracoCampeao_Logo from '../../static/imagens/AbracoCampeao-Logo.jpg'
import AfroLaje from '../../static/imagens/AfroLaje-D.jpg'
import AlexandreFotografia_Logo from '../../static/imagens/AlexandreFotografia-Logo.jpg'
import BrigadeirosLiterarios from '../../static/imagens/BrigadeirosLiterarios.jpg'
import CRJ_Logo from '../../static/imagens/CRJ-Logo.jpg'
import CarolMuniz from '../../static/imagens/CarolMuniz-D.jpg'
import CasaBrota_Logo from '../../static/imagens/CasaBrota-Logo.jpg'
import CasaPrimas_Logo from '../../static/imagens/CasaPrimas-Logo.png'
import ClasseD_Logo from '../../static/imagens/ClasseD-Logo.jpg'
import ClubeLuta_Logo from '../../static/imagens/ClubeLuta-Logo.jpg'
import ContraBandoTeatro_Logo from '../../static/imagens/ContraBandoTeatro-Logo.jpg'
import DancaCiaArt_Logo from '../../static/imagens/DancaCiaArt-Logo.jpg'
import DeboraAmorim_Logo from '../../static/imagens/DeboraAmorim-Logo.jpg'
import DocesMomentos_Logo from '../../static/imagens/DocesMomentos-Logo.jpg'
import EDUCAP from '../../static/imagens/EDUCAP-D.jpg'
import ErikaMartin from '../../static/imagens/ErikaMartin.jpg'
import EstudioAbaete_Logo from '../../static/imagens/EstudioAbaete-Logo.jpg'
import FamiliaPerninha from '../../static/imagens/FamiliaPerninha-D.jpg'
import FavelaFashion_Logo from '../../static/imagens/FavelaFashion-Logo.jpg'
import FavelaGrafia_Logo from '../../static/imagens/FavelaGrafia-Logo.png'
import FotoClubeAlemao_Logo from '../../static/imagens/FotoClubeAlemao-Logo.jpg'
import FuturoMovimento from '../../static/imagens/FuturoMovimento.jpg'
import GAS_Logo from '../../static/imagens/GAS-Logo.jpg'
import GatoMidia_Logo from '../../static/imagens/GatoMidia-Logo.png'
import JogaCria_Logo from '../../static/imagens/JogaCria-Logo.png'
import MarcosCarolinno_Logo from '../../static/imagens/MarcosCarolinno-Logo.png'
import MovimentoVida from '../../static/imagens/MovimentoVida-D.jpg'
import NaveConhecimento_Logo from '../../static/imagens/NaveConhecimento-Logo.png'
import NoixQFaz from '../../static/imagens/NoixQFaz.jpg'
import NovosLideres_Logo from '../../static/imagens/NovosLideres-Logo.jpg'
import OcaCurumins_Logo from '../../static/imagens/OcaCurumins-Logo.jpg'
import PoetasFavelados_Logo from '../../static/imagens/PoetasFavelados-Logo.jpg'
import ProjetoCriancasFelizes_Logo from '../../static/imagens/ProjetoCriancasFelizes-Logo.jpg'
import RaizesMovimento_Logo from '../../static/imagens/RaizesMovimento-Logo.png'
import RecreacaoInfantilEstrelinha from '../../static/imagens/RecreacaoInfantilEstrelinha-D.jpg'
import SambaFavela_Logo from '../../static/imagens/SambaFavela-Logo.jpg'
import SlamLaje_Logo from '../../static/imagens/SlamLaje-Logo.jpg'
import TiaguinhoSilva from '../../static/imagens/TiaguinhoSilva.jpg'
import TocaLobo_Logo from '../../static/imagens/TocaLobo-Logo.jpg'
import VaiNaWeb_Logo from '../../static/imagens/VaiNaWeb-Logo.jpg'
import ViDancar from '../../static/imagens/ViDancar-D.jpg'
// Fim imagens

import VueScrollbar from 'vue2-scrollbar'
// require("vue2-scrollbar/dist/style/vue2-scrollbar.css")
require("../../static/css/VueScrollbar.css")

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
					imagem: BrigadeirosLiterarios,
					nome: 'Brigadeiros Literários',
					segmento: 'Alimentação',
					subSegmento: 'Doceria'
				},
				{
					imagem: CasaPrimas_Logo,
					nome: 'Casa das Primas Doceria',
					segmento: 'Alimentação',
					subSegmento: 'Doceria'
				},
				{
					imagem: DocesMomentos_Logo,
					nome: 'Doces e Momentos',
					segmento: 'Alimentação',
					subSegmento: 'Festas'
				},
				{
					imagem: AfroLaje,
					nome: 'Afro Laje',
					segmento: 'Arte e Cultura',
					subSegmento: 'Dança'
				},
				{
					imagem: NoixQFaz,
					nome: 'Coletivo de Grafite NoixQFaz',
					segmento: 'Arte e Cultura',
					subSegmento: 'Graffiti'
				},
				{
					imagem: ContraBandoTeatro_Logo,
					nome: 'Contra Bando de Teatro',
					segmento: 'Arte e Cultura',
					subSegmento: 'Teatro'
				},
				{
					imagem: CRJ_Logo,
					nome: 'CRJ - Alemão',
					segmento: 'Arte e Cultura',
					subSegmento: 'Educação'
				},
				{
					imagem: FuturoMovimento,
					nome: 'Futuro em Movimento',
					segmento: 'Arte e Cultura',
					subSegmento: 'Dança'
				},
				{
					imagem: ProjetoCriancasFelizes_Logo,
					nome: 'Projeto Crianças Felizes',
					segmento: 'Arte e Cultura',
					subSegmento: 'Eventos'
				},
				{
					imagem: SambaFavela_Logo,
					nome: 'Projeto Samba Favela',
					segmento: 'Arte e Cultura',
					subSegmento: 'Eventos'
				},
				{
					imagem: ViDancar,
					nome: 'Projeto Vidançar',
					segmento: 'Arte e Cultura',
					subSegmento: 'Dança'
				},
				{
					imagem: SlamLaje_Logo,
					nome: 'Slam Laje',
					segmento: 'Arte e Cultura',
					subSegmento: 'Eventos'
				},
				{
					imagem: DeboraAmorim_Logo,
					nome: 'Debora Amorim - Makeup',
					segmento: 'Beleza e Estética',
					subSegmento: 'Maquiagem'
				},
				{
					imagem: FavelaFashion_Logo,
					nome: 'Favela é Fashion',
					segmento: 'Coletivo',
					subSegmento: 'Moda'
				},
				{
					imagem: FavelaGrafia_Logo,
					nome: 'Favelagrafia',
					segmento: 'Coletivo',
					subSegmento: 'Fotografia'
				},
				{
					imagem: FotoClubeAlemao_Logo,
					nome: 'Foto Clube Alemão',
					segmento: 'Coletivo',
					subSegmento: 'Fotografia'
				},
				{
					imagem: GAS_Logo,
					nome: 'GAS - Grupo Alemão Solidário',
					segmento: 'Coletivo',
					subSegmento: 'Assistência Social'
				},
				{
					imagem: PoetasFavelados_Logo,
					nome: 'Poetas Favelados',
					segmento: 'Coletivo',
					subSegmento: 'Poesia'
				},
				{
					imagem: GatoMidia_Logo,
					nome: 'Gato Mídia',
					segmento: 'Educação',
					subSegmento: 'Comunicação'
				},
				{
					imagem: JogaCria_Logo,
					nome: 'Joga Cria',
					segmento: 'Educação',
					subSegmento: 'Tecnologia'
				},
				{
					imagem: NaveConhecimento_Logo,
					nome: 'Nave do Conhecimento de Nova Brasília',
					segmento: 'Educação',
					subSegmento: 'Tecnologia'
				},
				{
					imagem: RecreacaoInfantilEstrelinha,
					nome: 'Recreação Infantil Estrelinha',
					segmento: 'Educação',
					subSegmento: 'Infantil'
				},
				{
					imagem: VaiNaWeb_Logo,
					nome: 'Vai na web',
					segmento: 'Educação',
					subSegmento: 'Tecnologia'
				},
				{
					imagem: ClubeLuta_Logo,
					nome: 'Clube de Luta do Complexo',
					segmento: 'Esporte e Atividade Física',
					subSegmento: 'Artes Marciais'
				},
				{
					imagem: FamiliaPerninha,
					nome: 'Família Perninha Kickboxing',
					segmento: 'Esporte e Atividade Física',
					subSegmento: 'Artes Marciais'
				},
				{
					imagem: AbracoCampeao_Logo,
					nome: 'Associação Abraço Campeão',
					segmento: 'ONG',
					subSegmento: 'Cidania e Desenvolvimento'
				},
				{
					imagem: OcaCurumins_Logo,
					nome: 'Centro Cultural Oca dos Curumins',
					segmento: 'ONG',
					subSegmento: 'Educação e Cultura'
				},
				{
					imagem: EDUCAP,
					nome: 'EDUCAP - Espaço Democrático de União, Convivência e Aprendizagem',
					segmento: 'ONG',
					subSegmento: 'Cidania e Desenvolvimento'
				},
				{
					imagem: RaizesMovimento_Logo,
					nome: 'Instituto Raízes Em Movimento',
					segmento: 'ONG',
					subSegmento: 'Educação e Cultura'
				},
				{
					imagem: NovosLideres_Logo,
					nome: 'Novos Líderes Empreendedores',
					segmento: 'ONG',
					subSegmento: 'Educação e Cultura'
				},
				{
					imagem: MovimentoVida,
					nome: 'Instituto Movimento & Vida',
					segmento: 'Saúde',
					subSegmento: 'Fisioterapia'
				},
				{
					imagem: AlexandreFotografia_Logo,
					nome: 'Alexandre Silva Fotografia',
					segmento: 'Fotografia',
					subSegmento: 'Serviço'
				},
				{
					imagem: CasaBrota_Logo,
					nome: 'Casa Brota - Coworking de favela',
					segmento: 'Serviço',
					subSegmento: 'Coworking'
				},
				{
					imagem: ClasseD_Logo,
					nome: 'Classe D - Ateliê de Ideias',
					segmento: 'Serviço',
					subSegmento: 'Design'
				},
				{
					imagem: DancaCiaArt_Logo,
					nome: 'Dança e Cia Art',
					segmento: 'Serviço',
					subSegmento: 'Dança'
				},
				{
					imagem: ErikaMartin,
					nome: 'Erica Martin Fotografia',
					segmento: 'Serviço',
					subSegmento: 'Fotografia'
				},				
				{
					imagem: EstudioAbaete_Logo,
					nome: 'Estúdio Abaeté',
					segmento: 'Serviço',
					subSegmento: 'Produção'
				},
				{
					imagem: CarolMuniz,
					nome: 'Agência Carol Muniz',
					segmento: 'Serviço',
					subSegmento: 'Gráfica'
				},
				{
					imagem: MarcosCarolinno_Logo,
					nome: 'Marcos Carolino Art',
					segmento: 'Serviço',
					subSegmento: 'Dança'
				},
				{
					imagem: TocaLobo_Logo,
					nome: 'Toca do Lobo Produções',
					segmento: 'Serviço',
					subSegmento: 'Produção'
				},
				{
					imagem: TiaguinhoSilva,
					nome: 'Tiaguinho Silva',
					segmento: 'Transporte',
					subSegmento: 'Moto Táxi'
				}
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
		},
		someMethod(){
			this.$refs.Scrollbar.scrollToY(0)
		}
	},
	components:{ 
    	VueScrollbar
    }
}
</script>

<style scoped>
/*@import '../../static/css/VueScrollbar.css';*/

#listaAtividades{
	width: 40%;
	max-width: 600px;
	height: 90vh;
	margin-right: auto;
	display: flex;
	flex-flow: row wrap;
	justify-content: center;
	align-items: flex-start;	
}
@media (max-width: 640px){
	#listaAtividades{
		width: 90%;
		margin-right: 0;
	}
}
/*The Wrapper*/
.my-scrollbar{
	width: 100%;
	min-width: 300px;
	max-height: 90vh;
	margin-top: 20px;
}
@media (max-width: 640px){
	.my-scrollbar{
		height: 80vh;
		margin-top: 10px;
	}
}
/*@media (max-width: 400px){
	.my-scrollbar{
		height: 80vh;
	}
}*/
.conteudo{
	width:100%;
    min-height: 100vh;
    margin-right: 5px;
    display: flex;
    align-items: flex-start;
}
.conteudo-atividades{
	width: 100%;
	/*margin-top: 20px;*/
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
	padding-right: 20px;
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