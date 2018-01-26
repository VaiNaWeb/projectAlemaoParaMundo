<template>
	<div id="atividade">
		<main class="atividade-container" v-for="atividade in atividadesSelecionadas">	
			<section class="atividadeContainer-foto">
				<h1 class="atividadeContainerFoto-titulo">
					{{ atividade.nome }}
					<span class="atividadeContainerFoto-btnClose" @click="resetAtividade">X</span>
				</h1>
				<div class="atividadeContainerFoto-format formatDesktop">
					<img class="atividadeContainerFoto-imagemDesktop" :src="atividade.imagem">
				</div>
				<div class="atividadeContainerFoto-format formatMobile">
					<img class="atividadeContainerFoto-imagemMobile" :src="atividade.imagemMobile">
				</div>
			</section>
			<section class="atividadeContainer-info">
				<h3 class="atividadeContainerInfo-aba" 
					:style="{backgroundColor: bgColorSobre}"
					v-on:click="selecionarAbaSobre"
					>Sobre</h3>
				<h3 class="atividadeContainerInfo-aba"
					:style="{backgroundColor: bgColorLocal}"
					v-on:click="selecionarAbaLocal"
					>Local</h3>
				<div class="atividadeContainerInfo-sobre" v-if="mostarAbaSobre">
					<div class="atividadeContainerInfoSobre-conteudo">
						<div class="infoSobreConteudo-div">
							<p class="atividadesobre-texto" v-for="value in atividade.sobre">{{ value }}</p>
						</div>
						<div class="infoSobreConteudo-div sobreConteudo-divIcon">
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/email.svg" v-show="atividade.email">
							<p class="infoSobreConteudoDiv-text" v-show="atividade.email">
								{{ atividade.email }}
							</p>
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/telefone.svg" v-show="atividade.telefone">
							<p class="infoSobreConteudoDiv-text" v-show="atividade.telefone">
								{{ atividade.telefone }}
							</p>
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/facebook.svg" v-show="atividade.facebook">
							<a href="" class="infoSobreConteudoDiv-text" v-show="atividade.facebook"> {{ atividade.facebook }} </a>
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/instagram.svg" v-show="atividade.instagram">
							<p class="infoSobreConteudoDiv-text"  v-show="atividade.instagram">
								{{ atividade.instagram }}
							</p>
						</div>
					</div>
				</div>
				<div class="atividadeContainer-local" v-else="mostarAbaLocal">
					<div class="atividadeContainerLocal-conteudo">
						<iframe class="containerLocalConteudo-mapa" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d14705.747493678937!2d-43.2834086092895!3d-22.860314632117355!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x997c7352b8f01f%3A0xdc43e9597c8e45ad!2sComplexo+do+Alem%C3%A3o%2C+Rio+de+Janeiro+-+RJ!5e0!3m2!1spt-BR!2sbr!4v1513266764891"  frameborder="0" style="border:0" allowfullscreen></iframe>
						<p class="containerLocalConteudo-endereco">{{ atividade.endereço }}</p>
					</div>
				</div>
			</section>
		</main>
	</div>
</template>
<script>

import CasaBrota from '../../static/imagens/CasaBrota/Casa Brota Coworking de Favela.jpg'
import ClasseD from '../../static/imagens/Classe D/D - classed2.jpg'
import ClasseDM from '../../static/imagens/Classe D/M - classed.jpg'
import RaizesMovimento from '../../static/imagens/Raízes em Movimentos/raizesemmovimento1.jpg'
import NoixQFaz from '../../static/imagens/Noix Q Faz/noixqfaz1.jpg'
import ViDancar from '../../static/imagens/VIdançar/vidancar.jpg'
import SlamLaje from '../../static/imagens/SlamLaje/slamlaje1.jpg'
import AfroLaje from '../../static/imagens/Afro Laje/D - afrolaje1.jpg'
import AfroLajeM from '../../static/imagens/Afro Laje/M - afrolaje.jpg'
import CriancasFelizes from '../../static/imagens/projeto-criancas-felizes/criancasfelizes1.jpg'
import GatoMidia from '../../static/imagens/Gato Mídia/D - 23379978_1864848067161628_7307016498340374063_n.jpg'
import MovimentoeVida from '../../static/imagens/instituto movimento e vida/movimentoevida1.jpg'
import CRJ from '../../static/imagens/crj/D - crj.jpg'
import NovosLideres from '../../static/imagens/Novos Líderes/novoslideres1.jpg'
import FavelaFashion from '../../static/imagens/favela é fashion/fashion.jpg'
import BrigadeiroLiterario from '../../static/imagens/Brigadeiros Literários/Brigadeiros Literários.jpg'
import ClubeLuta from '../../static/imagens/Clube de lutas do complexo/clubedelutas4.jpg'
import NaveConhecimento from '../../static/imagens/Nave do Conhecimento/navedoconhecimento1.jpg'
import SambaFavela from '../../static/imagens/Samba Favela/sambadefavela2.jpg'
import CasaPrimas from '../../static/imagens/Casa das Primas Doceria/Logo Casa das Primas Doceria.png'

	export default{
		name: 'Atividade',
		props:{
			selectAtividade: String
		},
		data(){
			return{
				mostarAbaSobre:true,
				mostarAbaLocal:false,
				bgColorSobre: '#fff',
				bgColorLocal:  '#f46424',
				atividades: [
					{
						nome: 'Casa Brota',
						imagem: CasaBrota,
						imagemMobile: CasaBrota,
						sobre: [
							'Coworking de Favela, um espaço de conexão com foco na promoção cultural da favela e no desenvolvimento econômico das micro empresas.',
							'Empreender a partir das criações e subjetividade de cada indivíduo, visando expandir e fortalecer as redes destes espaços populares para além da favela.',
							'Prestação de serviços: Assessoria de imprensa, consultoria para empreendimentos da favela, redes, audiovisual, artes e tecnologia.'
						],
						site: '',
						email: 'falecom@casabrota.com.br',
						telefone: '(21) 97264-7819',
						facebook: '/.comcasabrota',
						facebookLink: '',
						instagram: '@casabrota',
						twitter: null,
						endereço: 'Rua 24, Nº 10 - CPX Alemão, Rio de Janeiro '
					},
					{
						nome: 'Classe D – Ateliê de Ideias',
						imagem: ClasseD,
						imagemMobile: ClasseDM,
						sobre: [
							'O Coletivo Classe-D é formado por um grupo de amigos que se conheceram pelas ruas do Rio de Janeiro fazendo graffiti por volta do início dos anos 2000.',
							'Mas só em 2012 que parte deste coletivo começou a pensar profissionalmente em suas habilidades com produções de arte e comunicação visual. A partir de então tem se desenvolvido gradativamente seus aprendizados, trabalhando para oferecer um serviço de qualidade e com características ousadas, com'
						],
						site: '',
						email: 'produto.classed@gmail.com',
						telefone: '(21) 99311-9672',
						facebook: '/classed',
						facebookLink: '',
						instagram: '',
						twitter: null,
						endereço: 'Rua 24, no 10 - CPX Alemão, Rio de Janeiro'
					},
					{
						nome: 'Instituto Raízes Em Movimento',
						imagem: RaizesMovimento,
						imagemMobile: RaizesMovimento,
						sobre: [
							'O INSTITUTO RAÍZES EM MOVIMENTO tem como missão promover o desenvolvimento humano, social e cultural do Complexo do Alemão e demais comunidades por meio da participação de atores locais como protagonistas desses processos, tendo como foco o fortalecimento e ampliação do capital social dessas comunidades'
						],
						site: 'raizesemmovimento.org.br',
						email: 'contato@raizesememovimento.org.br',
						telefone: '21 2260-3998',
						facebook: '/Instituto Raízes Em Movimento ',
						facebookLink: '',
						instagram: null,
						twitter: null,
						endereço: 'Avenida Central, n° 68 - Ramos - Complexo do Alemão '
					},
					{
						nome: 'Noix Q Faz',
						imagem: NoixQFaz,
						imagemMobile: NoixQFaz,
						sobre: [
							'Somos um grupo de grafiteiros moradores do Complexo do Alemão, sendo cada um de uma localidade da favela. Resolvemos nos reunir para revitalizar espaços que precisam de reparos, o coletivo, batizado de "Noix Q Faz #Cpx", escolheu a quadra da comunidade do Reservatório para começar seu trabalho, todo custeado pelos próprios moradores. Uma das missões do coletivo é levar ação a todos os lugares que estejam precisando de uma transformação e permitir que o grafite se multiplique pela favela.'
						],
						site: null,
						email: 'vivianyribeiroart@gmail.com',
						telefone: '21 99958-2597',
						facebook: '/Coletivo Noix Q Faz #Cpx',
						facebookLink: '',
						instagram: '@annyvii',
						twitter: null,
						endereço: 'Complexo do Alemão'
					},
					{
						nome: 'Vidançar',
						imagem: ViDancar,
						imagemMobile: ViDancar,
						sobre: [
							'Atuam com aulas de dança, teatro, apoio escolar e atendimento jurídico às famílias. O projeto iniciou as atividades no ano de 2009 com 14 crianças. Atualmente são 145 assistidos diretamente e 300 assistidos indiretamente.',
							'O Vidançar conseguiu inserir 2 alunos no balé Bolshoi e 4 no Theatro Municipal. Além da aprovação de todos os alunos durante 3 anos consecutivos.'
						],
						site: null,
						email: null,
						telefone: '(21) 987394551',
						facebook: '/projetovidançar',
						facebookLink: '',
						instagram: null,
						twitter: null,
						endereço: 'Crj Alemão- Estrada do Itararé N: 690 Ref.: Atrás do Colégio Tim Lopes, na Antiga Faetec'
					},
					{
						nome: 'Slam Laje',
						imagem: SlamLaje,
						imagemMobile: SlamLaje,
						sobre: [
							'Fundado por moradores da região, o Slam Laje é a primeira batalha de poesia do Complexo do Alemão.',
							'O objetivo é incentivar a poesia e a literatura marginal, fortalecendo o movimento cultural dentro da favela com muito passinho, batalhas de rimas, de uma forma sagaz e resistente.',
							'A favela tá passando a mensagem: Slam laje!'
						],
						site: null,
						email: 'slamlaje@gmail.com',
						telefone: null,
						facebook: '/slamlaje',
						facebookLink: null,
						instagram: null,
						twitter: null,
						endereço: 'Casa Brota - Rua Ari Barroso, s/n - Ref.: Ao lado da estação Teleférico Alemão.'
					},
					{
						nome: 'Afro Laje',
						imagem: AfroLaje,
						imagemMobile: AfroLajeM,
						sobre: [
							' A Associação Cultural Afrolaje  é um grupo cultural que atua fazendo a disseminação do jongo com quem tem o interesse em aprender esta cultura popular que é oriunda do Rio de Janeiro.',
 							'O grupo tem sede no Engenho de dentro e faz uma grande atuação pela Zona Norte.',
							'Consolidou uma grande parceria no Centro Cultural Oca dos Curumins, promovendo a primeira roda de jongo do Complexo do Alemão.'
						],
						site: null,
						email: 'rosaneanalise@yahoo.com.br',
						telefone: '21984626467 ',
						facebook: '/afrolaje',
						facebookLink: null,
						instagram: '@negraro19',
						twitter: null,
						endereço: 'Alvorada. Travessa São José,  n. 13 - Ramos'
					},
					{
						nome: 'Crianças Felizes',
						imagem: CriancasFelizes,
						imagemMobile: CriancasFelizes,
						sobre: [
							'Fundada no dia 4 de Maio de 2013 pelo jovem Luciano Daniel que na época tinha 13 anos de idade. O projeto  conta com a participação de 15 voluntários para ajudar na arrecadação e na distribuição nos dias de evento. Nesses seus 4 anos de existência o projeto tem as redes sociais como uma de suas melhores ferramentas de trabalho para a arrecadação das doações, e já são mais de 20 ações que beneficiaram mais de 7 mil crianças, inclusive em 2015 o Projeto expandiu suas festas para o bairro de Santa Cruz, zona oeste do Rio.',
							'O Projeto Crianças Felizes foi selecionado para participar do reality show de mobilização social "Click Esperança" da TV Globo, sendo ele finalista e vencedor do reality.',
							'Nosso público alvo são as crianças, mas envolvemos toda a comunidade para que juntos possamos sonhar com um futuro melhor, todos são moradores e merecem um dia de alegria, já que a violência nos persegue em todos os dias.'
						],
						site: null,
						email: 'lucianoodaniell@gmail.com',
						telefone: '(21) 997143427',
						facebook: '/Projetocriancasfelizes',
						facebookLink: null,
						instagram: null,
						twitter: null,
						endereço: 'Complexo do Alemão'
					},
					{
						nome: 'GatoMÍDIA',
						imagem: GatoMidia,
						imagemMobile: GatoMidia,
						sobre: [
							'Espaço de aprendizado em mídia e tecnologia para jovens negros e moradores de espaços populares. Criado em 2014 no Complexo do Alemão estimula nesses jovens a produção da sua própria comunicação, rede e conexões.',
							'Possibilitando diferentes narrativas, visibilidade, oportunidades e ideias criativas e coletivas que construam um mundo mais justo, igualitário e afetivo.'
						],
						site: '',
						email: 'projetogatomidia@gmail.com',
						telefone: null,
						facebook: '/gatomidia',
						facebookLink: '',
						instagram: '@gatomidia',
						twitter: null,
						endereço: 'Casa Brota - Rua Ari Barroso, s/n - Ref.: Ao lado da estação Teleférico Alemão.'
					},
					{
						nome: 'Instituto Movimento & Vida',
						imagem: MovimentoeVida,
						imagemMobile: MovimentoeVida,
						sobre: [
							'O Instituto Movimento & Vida é uma organização sem fins lucrativos que realiza atendimento de fisioterapia gratuito aos moradores do conjunto de favelas do Complexo do Alemão.',
							'A melhoria da qualidade de vida e reabilitação dos pacientes é o objetivo principal do trabalho desenvolvido pela instituição que atua 2007, promovendo informações de hábitos saudáveis e de proteção à saúde.',
							'Sua missão é atender com qualidade, dedicação e amor moradores de uma região do Rio de Janeiro que segue marcada com violência, dificuldade, miséria e falta de atenção.'
						],
						site: null,
						email: 'monicacirnea@gmail.com',
						telefone: '21 964648101',
						facebookLink: '',
						facebook: '/movimentoevida',
						instagram: null,
						twitter: null,
						endereço: 'Rua das Andorinhas, 98'
					},
					{
						nome: 'CRJ Alemão',
						imagem: CRJ,
						imagemMobile: CRJ,
						sobre: [
							' O Centro de Referência para Juventude oferece cursos e atividades GRATUITAS.',
							'Além disso, disponibiliza seus espaços para que projetos e pessoas que não tenha um local para estudar, ensaiar ou acessar a internet utilize-o totalmente em seu horário de funcionamento.',
							'Está aberto de segunda a sexta 09h às 21h e aos sábados de 09h às 13h.'
						],
						site: null,
						email: 'alemaocrj@gmail.com',
						telefone: '(21) 23347971',
						facebook: '/crjalemão',
						facebookLink: '',
						instagram: null,
						twitter: null,
						endereço: 'Crj Alemão- Estrada do Itararé N: 690 Ref.: Atrás do Colégio Tim Lopes, na Antiga Faetec'
					},
					{
						nome: 'Novos Líderes',
						imagem: NovosLideres,
						imagemMobile: NovosLideres,
						sobre: [
							'Atuando há 3 anos, desde 2014, a ONG usa a educação empreendedora para desenvolver e empoderar jovens e adultos das comunidades cariocas em prol de modificar e melhorar suas comunidades de origem.'
						],
						site: 'Educatethefavela.org',
						email: 'Lohransantos009@gmail.com',
						telefone: '(21) 995008681',
						facebook: null,
						facebookLink: '',
						instagram: '@EducatetheFavela',
						twitter: null,
						endereço: 'Complexo do Alemão'
					},
					{
						nome: 'Favela é Fashion',
						imagem: FavelaFashion,
						imagemMobile: FavelaFashion,
						sobre: [
							'Favela é fashion é um projeto criado para selecionar jovens de comunidades que não tem chances de pagar um curso de moda.',
							'“ Ajudo esses jovens a encarar o sonho deles... Realizo meus sonhos conquistando os deles!!!”',
							'Ele existe desde 2011 e atualmente sonha em ter seu próprio espaço fixo.'
						],
						site: '',
						email: 'juhenrik26@gmail.com',
						telefone: '(21) 986683701',
						facebook: '/favelaéfashiow',
						facebookLink: '',
						instagram: null,
						twitter: null,
						endereço: 'Complexo do Alemão'
					},
					{
						nome: 'Brigadeiros Literários',
						imagem: BrigadeiroLiterario,
						imagemMobile: BrigadeiroLiterario,
						sobre: [
							'Os Brigadeiros Literários não é só um empreendimento, é um convite para uma experiência gustativa.',
							'Um veículo de divulgação da palavra escrita, uma possibilidade de comunicação, de reflexão, de carinho, trocas que estão em sintonia com o jeito de ser de quem está envolvido neste projeto.'
						],
						site: null,
						email: 'brigadeirosliterarios@gmail.com',
						telefone: '(21) 983040842',
						facebook: '/brigadeiros literários',
						facebookLink: '',
						instagram: '@brigadeirosliterarios',
						twitter: null,
						endereço: 'Espaços públicos com venda ambulante, eventos culturais, instituições públicas e privadas e através do uso da tecnologia.'
					},
					{
						nome: 'Clube de Luta do Complexo',
						imagem: ClubeLuta,
						imagemMobile: ClubeLuta,
						sobre: [
							'O Clube de Luta atua há 15 anos e oferece atividades esportivas com ênfase nas artes marciais, além de reforço escolar e atividades de lazer e cultura para crianças, jovens e adultos.',
							'Também se destacam no cenário de competições oficiais com dezenas de títulos estaduais e nacionais, inclusive em modalidades olímpicas como o Taekwondo.'
						],
						site: null,
						email: 'Taekwondo.@gmail.com',
						telefone: '(21) 980486486',
						facebook: '/clubedelutadocomplexo',
						facebookLink: '',
						instagram: null,
						twitter: null,
						endereço: 'Estrada do Itararé '
					},
					{
						nome: 'Nave do Conhecimento Nova Brasília',
						imagem: NaveConhecimento,
						imagemMobile: NaveConhecimento,
						sobre: [
							'Espaço público onde oferecemos cursos nas área de tecnologia, educação e internet grátis a toda população do conjunto de favelas do Complexo do Alemão.Aberto de Seg a Sábado de 09h às 19h.'
						],
						site: null,
						email: 'luciana.rodrigues@idaco.org.br',
						telefone: '4101-1510 ',
						facebook: '/navedoconhecimento.rio ',
						facebookLink: '',
						instagram: null,
						twitter: null,
						endereço: 'Complexo do Alemão'
					},
					{
						nome: 'Samba Favela',
						imagem: SambaFavela,
						imagemMobile: SambaFavela,
						sobre: [
							'O Projeto Samba Favela teve início quando integrantes e amigos do antigo Grupo Brincadeira Tem Hora (BTH) se reencontraram pela internet e decidiram se reunir novamente para relembrar os velhos e bons tempos na música.',
							'O (BTH)  foi fundado nos anos 90 e teve várias formações ao longo do tempo e hoje visa trazer para o Alemão a conexão entre o morro e o asfalto através do gênero musical e patrimônio cultural da cidade do Rio de Janeiro.',
							'O evento tem entrada gratuita e promove a campanha de doações de alimentos não perecíveis para serem destinado à moradores da comunidade. '
						],
						site: null,
						email: 'projetosambafavela@gmail.com',
						telefone: '(21) 987500896',
						facebook: '/sambafavela',
						facebookLink: null,
						instagram: ' @sambafavela',
						twitter: null,
						endereço: 'Complexo do Alemão'
					},
					{
						nome: 'Casa das Primas Doceria',
						imagem: CasaPrimas,
						imagemMobile: CasaPrimas,
						sobre: [
							'Loja de doces e salgados que tem como especialidades brownies, tortas, sorvetes e milk shake',
							'"Aqui você pode se sentir o último brownie do pacote."'
						],
						site: null,
						email: null,
						telefone: '21 97344-1959',
						facebook: '/Casa das Primas Doceria',
						facebookLink: '',
						instagram: '@casadasprimasdoceria',
						twitter: null,
						endereço: 'Estrada do Itararé, 341 - Loja 20 - Complexo do Alemão - Rio de Janeiro'
					},
					// {
					// 	nome: '',
					// 	imagem: '',
					// 	imagemMobile: '',
					// 	sobre: [
					// 	],
					// 	site: '',
					// 	email: '',
					// 	telefone: '',
					// 	facebook: '',
					// 	facebookLink: '',
					// 	instagram: '',
					// 	twitter: '',
					// 	endereço: ''
					// }
				]
			}
		},
		computed:{
			subcategoriaFiltradas(){
				const subSegmento = this.subcategorias
					.filter(subcategoria => subcategoria.categoria === this.categoria)	

					if(subSegmento){
						return this.subcategoria.subcategoria
					}
			},
			atividadesSelecionadas(){
				const atividade = this.atividades.filter(atividade => atividade.nome === this.selectAtividade) 

				return atividade
			},

		},
		methods:{
			// alterarAba(){
			// 	if(this.zIndexSobre === 2){
			// 		this.zIndexSobre = 1
			// 		this.zIndexLocal = 2
			// 		this.bgColorSobre = '#f46424'
			// 		this.bgColorLocal = '#fff'
			// 	} else {
			// 		this.zIndexSobre = 2
			// 		this.zIndexLocal = 1
			// 		this.bgColorSobre = '#fff'
			// 		this.bgColorLocal = '#f46424'
			// 	}

			// },
			selecionarAbaSobre(){
				this.mostarAbaSobre = true
				this.bgColorSobre = '#fff'
				this.mostarAbaLocal = false
				this.bgColorLocal = '#f46424'
			},
			selecionarAbaLocal(){
				this.mostarAbaLocal = true
				this.bgColorLocal = '#fff'
				this.mostarAbaSobre = false
				this.bgColorSobre = '#f46424'
			},
			resetAtividade(){
				this.$emit('alterar', true)
			}
		}
	}
</script>

<style scoped>
#atividade{
	width: 40%;
	min-height: 100vh;
	margin-right: auto;
	position: relative;
	top:0;
	display: flex;
	flex-flow: row wrap;
	align-content: flex-start;
	justify-content: flex-start;
	align-items: flex-start;
}
@media(max-width: 640px){
	#atividade{
		width: 100%;
	}
}
.atividade-container{
	width:100%;
    min-height: 100vh;
	display: flex;
	flex-flow: row wrap;
	align-content: flex-start;
	justify-content: flex-start;
}
.atividadeContainer-foto{
	width: 100%;
	min-height: 10px;
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
	align-items: flex-start;
}
.atividadeContainerFoto-titulo{
	width: 100%;
	margin: 0; 
	padding: 5px 15px;
	/*padding-left: 15px;*/
	position: relative;
	background-color: rgb(244, 100, 36);
	font-family: ministry, sans-serif;
	font-style: normal;
    font-weight: 700;
	font-size: 2em;
	color: #ffffff;
	text-align: left;
}
.atividadeContainerFoto-btnClose{
	width: 25px;
	height: 25px;
	margin: 0;
	border-radius: 50%;
	background-color: #fff;
	cursor:pointer;
	position: absolute;
	right: 10px;
	top:20%;
	font-family: ministry, sans-serif;
	font-weight: 900;
	font-size: 0.5em;
	color: rgb(244, 100, 36);
	display: flex;
	align-items: center;
	justify-content: center;
}
.atividadeContainerFoto-format{
	width: 100%;
	min-height: 5vh;
	max-height: 50vh;
	overflow: hidden;
	display: flex;
	justify-content: center;
	align-items: center;
	align-content: center;
}
.formatMobile{
	display: none;
	max-height: 50vh;

	background-color: red;
}
@media(max-width: 640px){
	.formatDesktop{
		display: none;
	}
	.formatMobile{
		display: flex;
	}	
}
.atividadeContainerFoto-imagemDesktop{
	min-width: 100%;
	max-width: 130%;
	min-height: 35vh;
}
.atividadeContainerFoto-imagemMobile{
	max-width: 130%;
	min-height: 50vh;
}
.atividadeContainer-info{
	width: 100%;
	min-height: 40vh;
	margin: 0 auto;
	margin-top: 10px;
	display: flex;
	flex-flow: row wrap;
	justify-content: flex-start;
	align-content: flex-start;
	align-items: flex-start;
}
@media(max-width: 640px){
	.atividadeContainer-info{
		width: 95%;
	}
}
.atividadeContainerInfo-sobre{
	width: 100%;
	display: flex;
	flex-direction: column;
	align-items: center;
}
.atividadeContainerInfo-aba{
	width: 33.3%;
	height: 48px;
	margin: 0;
	cursor:pointer;
	border:none;
	border-radius: 20px 20px 0 0;
	display: flex;
	justify-content: center;
	align-items: center;
}
.atividadeContainerInfoSobre-conteudo{
	width: 100%;
	min-height: 40vh;
	padding: 5px;
	background-color: #fff;
	border-radius: 0px 20px 20px 20px;
	display: flex;
	flex-flow: row wrap;
	/*justify-content: center;*/
}
@media(max-width: 640px){
	.cabecalhoContainer-filtros{

	}
}
.infoSobreConteudo-div{
	min-width: 200px;
	max-width: 50%;
}
@media(max-width: 1140px){
	.infoSobreConteudo-div{
		max-width: 100%;
	}	
}
.atividadesobre-texto{
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 400;
	font-size: 14px;
	color: #2e3192;
	text-align: left;
	margin: 15px;
	margin-top: 8px;
}
.sobreConteudo-divIcon{
	padding-left: 10px;
	display: flex;
	flex-flow: row wrap;
	align-items: center;
	justify-content: flex-start;
	align-content: flex-start;
}
.infoSobreConteudoDiv-icon{
	width: 30px;
	margin: 15px 0;
}
.infoSobreConteudoDiv-text{
	width: 95%;
	margin-left: 8px;
	margin-right: auto;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 400;
	font-size: 13px;
}
@media (max-width: 1140px){
	.infoSobreConteudoDiv-text{
		width: 80%;
	}
}
.atividadeContainer-local{
	width: 100%;
	min-height: 60vh;
}

.atividadeContainerLocal-conteudo{
	width: 100%;
	min-height: 40vh;
	background-color: #fff;
	border-radius: 0 20px 20px 20px;
	display: flex;
	flex-flow: row wrap;
	align-items: center;
	align-content: center;
	justify-content: center;
}
.containerLocalConteudo-mapa{
	width: 80%;
	height: 220px;
	margin: 20px 0;
}
.containerLocalConteudo-endereco{

}
</style>