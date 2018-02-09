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
						<div class="sobreConteudo-divIcon">
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/email.svg" v-show="atividade.email">
							<p class="infoSobreConteudoDiv-text" v-show="atividade.email">
								{{ atividade.email }}
							</p>
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/telefone.svg" v-show="atividade.telefone">
							<p class="infoSobreConteudoDiv-text" v-show="atividade.telefone">
								{{ atividade.telefone }}
							</p>
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/facebook.svg" v-show="atividade.facebook">
							<a :href="facebookLink"
								target="_blank"
								class="infoSobreConteudoDiv-text"
								v-show="atividade.facebook">
								 {{ atividade.facebook }}
							</a>
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/instagram.svg" v-show="atividade.instagram">
							<a :href="instagramLink" 
								target="_blank" 
								class="infoSobreConteudoDiv-text"
								v-show="atividade.instagram">
								{{ atividade.instagram }}
							</a>
							<img class="infoSobreConteudoDiv-icon" src="../../static/assets/instagram.svg" v-show="atividade.twitter">
							<a :href="twitterLink"
								target="_blank"
								class="infoSobreConteudoDiv-text"
								v-show="atividade.instagram">
								{{ atividade.twitter }}
							</a>
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
// As imagens precisa ser revisada. Não são estas!
// Import imagens
import AbracoCampeao_Logo from '../../static/imagens/AbracoCampeao-Logo.jpg'
import AfroLaje from '../../static/imagens/AfroLaje-M.jpg'
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
import DocesMomentos from '../../static/imagens/DocesMomentos.jpg'
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
					nome: 'Brigadeiros Literários',
					imagem: BrigadeirosLiterarios,
					imagemMobile:BrigadeirosLiterarios,
					sobre: [
						'Os Brigadeiros Literários não é só um empreendimento, é um convite para uma experiência gustativa. Um veículo de divulgação da palavra escrita, uma possibilidade de comunicação, de reflexão, de carinho, trocas que estão em sintonia com o jeito de ser de quem está envolvido neste projeto.'
					],
					telefone: '21 96686-2218',
					site: null,
					email: 'brigadeiroslisterarios@gmail.com',
					facebook: '/brigadeirosliterarios',
					facebookLink: 'https://www.facebook.com/brigadeirosliterarios',
					instagram: '@brigadeirosliterarios',
					instagramLink:'https://www.instagram.com/brigadeirosliterarios/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Casa das Primas Doceria',
					imagem:CasaPrimas_Logo,
					imagemMobile:CasaPrimas_Logo,
					sobre: [
						'm recente point aberto no Complexo do Alemão, onde tem como especialidades brownies, tortas, sorvetes e milk sheik.',
						'" Aqui você pode se sentir o último brownie do pacote."'
					],
					telefone: '21 97344-1959',
					site: null,
					email: null,
					facebook: 'casadasprimasdoceria',
					facebookLink: 'https://www.facebook.com/casadasprimasdoceria/',
					instagram: '@casadasprimasdoceria',
					instagramLink:'https://www.instagram.com/casadasprimasdoceria/',
					twitter: null,
					twitterLink:null,
					endereço: 'Estrada do Itararé, 341 - Loja 20'
				},
				,
				{
					nome: 'Doces e Momentos',
					imagem:DocesMomentos,
					imagemMobile:DocesMomentos,
					sobre: [
						'A confeitaria Doces e Momentos, é da empreendedoa Joana, cuja qual realiza verdadeiras obras de artes em seus bolos, trabalhando há mais de um ano com doces, sonhos, planos e momentos marcantes na vida de nossos clientes.',
						'“Expresse e demonstre seus sentimentos com nossos Doces e Momentos!”'
					],
					telefone: '21 98062-1818',
					site: null,
					email: null,
					facebook: '/docesemomentosjoana',
					facebookLink: 'https://www.facebook.com/docesemomentosjoana',
					instagram: '@docesemomentosjoana',
					instagramLink:'https://www.instagram.com/docesemomentosjoana/',
					twitter: null,
					twitterLink:null,
					endereço: 'Rua da Assembléia - Próximo a Estação do teleférico itararé - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Afro Laje',
					imagem:AfroLaje,
					imagemMobile:AfroLaje,
					sobre: [
						'A Associação Cultural Afrolaje  é um grupo cultural que atua fazendo a disseminação do jongo com quem tem o interesse em aprender esta cultura popular que é oriunda do Rio de Janeiro.',
						'O grupo tem sede no Engenho de dentro e faz uma grande atuação pela Zona Norte.',
						'Consolidou uma grande parceria no Centro Cultural Oca dos Curumins, promovendo a primeira roda de jongo do Complexo do Alemão.'
					],
					telefone: '21 98403-4178',
					site: null,
					email: null,
					facebook: '/afrolaje',
					facebookLink: 'https://www.facebook.com/afrolaje',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Travessa São José, n°13 - Oca dos Curumins - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Coletivo de Grafite NoixQFaz',
					imagem:NoixQFaz,
					imagemMobile:NoixQFaz,
					sobre: [
						'É um grupo de grafiteiros, moradores do Complexo do Alemão cujo os quais resolveram se reunir para revitalizar espaços que precisam de reparos. Batizado de "Noix Q Faz #Cpx", escolheram a quadra da comunidade do Reservatório para começar o trabalho, tendo todo material de tintas, jets, pincéis custeado pelos próprios moradores.',
						'Uma das missões do coletivo é levar ação à  lugares que estejam precisando de uma transformação e permitir que o grafite se multiplique pela favela. Realizam oficinas em ações sociais de revitalização de espaços e ambientes usando a arte do graffiti como ferramenta fundamental. Desenvolvem projetos coletivos como o Arte e Transformação para crianças a partir de 06 anos, adolescentes, jovens e, quem quiser interagir e aprender, nas oficinas, workshop de artistas convidados, e bate papo de conhecimento sobre culturas urbanas e os elementos do hip hop.'
					],
					telefone: '21 99958-2597',
					site: null,
					email: 'vivianyribeiroart@gmail.com',
					facebook: '/noixqfazcpx',
					facebookLink: 'https://www.facebook.com/noixqfazcpx',
					instagram: '@annyvii',
					instagramLink:'https://www.instagram.com/annyvii/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Contra Bando de Teatro',
					imagem:ContraBandoTeatro_Logo,
					imagemMobile:ContraBandoTeatro_Logo,
					sobre: [
						'O Contra Bando de teatro é um grupo formado em 2013 por jovens moradores com alma artística do Complexo do Alemão.',
						'Com sua arte amplia olhares e o mais importante, faz o público refletir sobre diversos assuntos. Gera questionamento sobre como vivemos e até que ponto as coisas são justas.'
					],
					telefone: '21 99265-1517',
					site: 'http://contra-bando.wixsite.com/',
					email: 'contrabandodeteatro@gmail.com',
					facebook: '/Contra-Bando-de-Teatro',
					facebookLink: 'https://www.facebook.com/Contra-Bando-de-Teatro-1438195543130396',
					instagram: '@contrabandodeteatro',
					instagramLink:'https://www.instagram.com/contrabandodeteatro/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'CRJ - Alemão',
					imagem:CRJ_Logo,
					imagemMobile:CRJ_Logo,
					sobre: [
						'O Centro de Referência para Juventude oferece cursos e atividades GRATUITAS. Além disso, disponibiliza seus espaços para que projetos e pessoas que não tenha um local para estudar, ensaiar ou acessar a internet utilize-o totalmente em seu horário de funcionamento. Está aberto de segunda a sexta 09h às 21h e aos sábados de 09h às 13h.'
					],
					telefone: '21 2334-7971',
					site: null,
					email: 'alemaocrj@gmail.com',
					facebook: '/crj.alemao',
					facebookLink: 'https://www.facebook.com/crj.alemao.50',
					instagram: '@crjalemao',
					instagramLink:'https://www.instagram.com/crjalemao/',
					twitter: null,
					twitterLink:null,
					endereço: 'Estrada do Itararé, 690 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Futuro em Movimento',
					imagem:FuturoMovimento,
					imagemMobile:FuturoMovimento,
					sobre: [
						'Preocupados com o alto índice de adolescentes grávidas, surgiu a iniciativa de oferecer oficinas de dança para ajudar mais os jovens em situação de vulnerabilidade social.',
						'Além das aulas, também realizam debates com temas sobre: Drogas, violência. Oficinas de artesanatos foi uma maneira encontrada de tornar uma das das suas fonte renda.'
					],
					telefone: '21 98811-0220',
					site: null,
					email: 'amamulheresdeatitude@gmailcom',
					facebook: '/FuturoMovimento',
					facebookLink: 'https://www.facebook.com/groups/1740561566261151/about/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Rua Sebastião de Carvalho, 33 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Projeto Crianças Felizes',
					imagem:ProjetoCriancasFelizes_Logo,
					imagemMobile:ProjetoCriancasFelizes_Logo,
					sobre: [
						'Fundada no dia 4 de Maio de 2013 pelo jovem Luciano Daniel que na época tinha 13 anos de idade, o projeto conta com a participação de 15 voluntários para ajudar na arrecadação e na distribuição nos dias de evento.',
						'Nesses 4 anos de existência, utiliza as redes sociais como uma de suas melhores ferramentas de trabalho para a arrecadação das doações, e já são mais de 20 ações que beneficiaram mais de 7 mil crianças, inclusive em 2015 o Projeto expandiu suas festas para o bairro de Santa Cruz, Zona Oeste do Rio. O Projeto Crianças Felizes foi selecionado para participar do reality show de mobilização social "Click Esperança" da TV Globo, sendo ele finalista e vencedor do reality.',
						'Seu público alvo são as crianças, porém, evolvem toda a comunidade para que juntos possam sonhar com um futuro melhor.'
					],
					telefone: '21 99714-3427',
					site: null,
					email: 'lucianoodaniell@gmail.com',
					facebook: '/Projetocriancasfelizes',
					facebookLink: 'https://www.facebook.com/Projetocriancasfelizes/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Avenida Central, n° 120 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Projeto Samba Favela',
					imagem:SambaFavela_Logo,
					imagemMobile:SambaFavela_Logo,
					sobre: [
						'O Projeto Samba Favela teve início quando integrantes e amigos do antigo Grupo Brincadeira Tem Hora (BTH) se reencontraram pela internet e decidiram se reunir novamente para relembrar os velhos e bons tempos na música.',
						'O (BTH)  foi fundado nos anos 90 e teve várias formações ao longo do tempo e hoje visa trazer para o Alemão a conexão entre o morro e o asfalto através do gênero musical e patrimônio cultural da cidade do Rio de Janeiro.',
						'O evento tem entrada gratuita e promove a campanha de doações de alimentos não perecíveis para serem destinado à moradores da comunidade.'
					],
					telefone: '21 98750-0896',
					site: null,
					email: 'lipebth@gmail.com',
					facebook: '/projetosambafavela',
					facebookLink: 'https://www.facebook.com/projetosambafavela',
					instagram: '@projetosambafavela',
					instagramLink:'https://www.instagram.com/projetosambafavela',
					twitter: null,
					twitterLink:null,
					endereço: 'Espaço Cultural Maria Madalena (Madá) - Estrada do Iatararé, 320 - Complexo do Alemão - Ramos - Rio de janeiro'
				},
				{
					nome: 'Projeto Vidançar',
					imagem:ViDancar,
					imagemMobile:ViDancar,
					sobre: [
						'Atuam com aulas de dança, teatro, apoio escolar e atendimento jurídico às famílias. O projeto iniciou as atividades no ano de 2009 com 14 crianças. Atualmente são 145 assistidos diretamente e 300 assistidos indiretamente.',
						'O Vidançar conseguiu inserir 2 alunos no balé Bolshoi e 4 no Theatro Municipal. Além da aprovação de todos os alunos durante 3 anos consecutivos.'
					],
					telefone: '21 98739-4551',
					site: 'http://projetovidancar.com.br/',
					email: 'projetovidacar@gmail.com',
					facebook: '/projetovidancar',
					facebookLink: 'https://www.facebook.com/projetovidancar/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'CRJ Alemão - Estrada do Itararé, n°690 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Slam Laje',
					imagem:SlamLaje_Logo,
					imagemMobile:SlamLaje_Logo,
					sobre: [
						'Fundado por moradores da região, o Slam Laje é a primeira batalha de poesia do Complexo do Alemão. O objetivo é incentivar a poesia e a literatura marginal, fortalecendo o movimento cultural dentro da favela com muito passinho, batalhas de rimas, de uma forma sagaz e resistente.',
						'A favela tá passando a mensagem: Slam laje!'
					],
					telefone: '21 98622-1392',
					site: null,
					email: 'slamlaje@gmail.com',
					facebook: '/batalhadepoesia',
					facebookLink: 'https://www.facebook.com/batalhadepoesia',
					instagram: '@slamlaje',
					instagramLink:'https://www.instagram.com/slamlaje/',
					twitter: null,
					twitterLink:null,
					endereço: 'Laje da Casa Brota - Rua Ari Barroso, s/n° - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Debora Amorim - Makeup',
					imagem:DeboraAmorim_Logo,
					imagemMobile:DeboraAmorim_Logo,
					sobre: [
						'Débora Amorim, formada em maquiagem, trabalha a cerca de 2 anos na área.'
					],
					telefone: '21 97145-0779',
					site: null,
					email: 'contato.demoraamorim@gmail.com',
					facebook: '/debamorimmakeup',
					facebookLink: 'https://www.facebook.com/debamorimmakeup',
					instagram: '@debamorimm',
					instagramLink:'https://www.instagram.com/debamorimm/',
					twitter: null,
					twitterLink:null,
					endereço: 'Estrada do Itararé, 480 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Favela é Fashion',
					imagem:FavelaFashion_Logo,
					imagemMobile:FavelaFashion_Logo,
					sobre: [
						'Favela é fashion é um projeto criado para selecionar jovens de comunidades que não tem chances de pagar um curso de moda.',
						'“Ajudo esses jovens a encarar o sonho deles... Realizo meus sonhos conquistando os deles !!!!!.”',
						'Ele existe desde 2011 e atualmente sonha em ter seu próprio espaço fixo.'
					],
					telefone: '21 98668-3701',
					site: null,
					email: 'juhenrik26@gmail.com',
					facebook: '/FavelaeFashion',
					facebookLink: 'https://www.facebook.com/FavelaeFashion',
					instagram: '@favelaefashion',
					instagramLink:'https://www.instagram.com/favelaefashion/',
					twitter: '@favelaefashion',
					twitterLink:'https://twitter.com/Favelaefashion',
					endereço: 'Espaço do CRJ Alemão - Estrada do Itararé, 690 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Favelagrafia',
					imagem:FavelaGrafia_Logo,
					imagemMobile:FavelaGrafia_Logo,
					sobre: [
						'O Favelagrafia é um coletivo de 9 fotógrafos, sendo os 9 moradores de favelas do Rio de Janeiro, inclusive o Complexo do Alemão. O projeto tem um pouco mais de um ano de existência e foi idealizado pela a agência de publicidade NBS - a melhor da América Latina.',
						'O objetivo é desconstruir a visão estereotipada e preconceituosa que as pessoas têm das favelas e nada melhor do que os próprios moradores para fazer isso através da fotografia.'
					],
					telefone: '21 97323-7174',
					site: null,
					email: 'josianefotografia@gmail.com',
					facebook: '/favelagrafia',
					facebookLink: 'https://www.facebook.com/favelagrafia',
					instagram: '@favelagrafia',
					instagramLink:'https://www.instagram.com/favelagrafia/',
					twitter: '@favelagrafia',
					twitterLink:'https://twitter.com/favelagrafia',
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Foto Clube Alemão',
					imagem:FotoClubeAlemao_Logo,
					imagemMobile:FotoClubeAlemao_Logo,
					sobre: [
						'O Foto Clube Alemão nasceu do desejo de promover o intercâmbio entre fotógrafos do Alemão e fora do Alemão, quebrar os paradigmas e preconceitos que existem sobre a fotografia dentro da favela e junto aos próprios moradores, disseminando e fomentando essa cultura de fotografia através de saídas fotográficas, palestras, oficinas e exposiçōes fotográficas, visando também mostrar que a boa fotografia não depende somente de equipamentos profissionais.'
					],
					telefone: '21 98021-8721',
					site: null,
					email: 'brunoitan@gmail.com',
					facebook: '/Foto-Clube-Alemão',
					facebookLink: 'https://www.facebook.com/Foto-Clube-Alemão-142926802508619',
					instagram: '@fotoclubealemao',
					instagramLink:'https://www.instagram.com/fotoclubealemao/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'GAS - Grupo Alemão Solidário ',
					imagem:GAS_Logo,
					imagemMobile:GAS_Logo,
					sobre: [
						'GAS (Grupo Alemão Solidário) é coordenado por 3 mulheres, conta com o apoio de 15 voluntários, parceria do Conselho Tutelar com o cadastro de crianças em situações vulneráveis, entre outros de diversos bairros da cidade e de fora do país.',
						'São 57 famílias atendidas totalizando 282 crianças beneficiadas direta e indiretamente pelas ações realizadas, sendo procurados também por famílias que necessitam de ajuda e estão fora da comunidade. Direciona sua principal campanha no Natal, realizando cadastrados para beneficiar crianças  de 0 à 14 anos de idade, das comunidades da Pedra do Sapo, Nova Brasília, Fazendinha, Capão, Adeus, Baiana, Lagoinha, Inferno Verde, Palmeiras, Favela da Skol, Favela da Galinha…'
					],
					telefone: '21 98888-1452',
					site: null,
					email: 'maysefm@gmail.com',
					facebook: '/gasgrupoalemaosolidario',
					facebookLink: 'https://www.facebook.com/gasgrupoalemaosolidario',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Rua Sebastião de Carvalho - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Poetas Favelados',
					imagem:PoetasFavelados_Logo,
					imagemMobile:PoetasFavelados_Logo,
					sobre: [
						'O coletivo Poetas Favelados, sente o quanto a poesia inspira, grita e aquece os corações.',
						'Pensando nisso, realizamo saraus itinerantes em transportes e espaços públicos pela cidade com Ataques Poéticos.'
					],
					telefone: '21 98622-1392',
					site: null,
					email: 'poetasfavelados@gmail.com',
					facebook: '/PoetasFavelados',
					facebookLink: 'https://www.facebook.com/PoetasFavelados',
					instagram: '@poetasfavelados',
					instagramLink:'https://www.instagram.com/poetasfavelados/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Gato Mídia',
					imagem:GatoMidia_Logo,
					imagemMobile:GatoMidia_Logo,
					sobre: [
						'Espaço de aprendizado em mídia e tecnologia para jovens negros e moradores de espaços populares. Criado em 2014 no Complexo do Alemão estimula nesses jovens a produção da sua própria comunicação, rede e conexões.',
						'Possibilitando diferentes narrativas, visibilidade, oportunidades e ideias criativas e coletivas que construam um mundo mais justo, igualitário e afetivo.'
					],
					telefone: null,
					site: 'https://gatomidia.wordpress.com/',
					email: 'projetogatomidia@gmail.com',
					facebook: '/gatomidia',
					facebookLink: 'https://www.facebook.com/gatomidia',
					instagram: '@gatomidia',
					instagramLink:'https://www.instagram.com/gatomidia/',
					twitter: '@gato_midia',
					twitterLink:'https://twitter.com/Gato_MIDIA',
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Joga Cria',
					imagem:JogaCria_Logo,
					imagemMobile:JogaCria_Logo,
					sobre: [
						'Criação de jogos como forma de incentivar o aprendizado projetual e tecnológico. Os encontros têm ocorrido no Complexo do Lins e Alemão.'
					],
					telefone: '21 97660-3854',
					site: null,
					email: 'joonasjss@gmail.com',
					facebook: '/JogaCria',
					facebookLink: 'https://www.facebook.com/JogaCria',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Nave do Conhecimento de Nova Brasília',
					imagem:NaveConhecimento_Logo,
					imagemMobile:NaveConhecimento_Logo,
					sobre: [
						'Espaço público onde oferecemos cursos nas área de tecnologia, educação e internet grátis a toda população do conjunto de favelas do Complexo do Alemão. Aberto de Seg a Sábado de 09h às 19h.'
					],
					telefone: '21 4101-1510',
					site: 'https://navedoconhecimento.rio',
					email: 'luciana.rodrigues@idaco.org.br',
					facebook: '/navedoconhecimentonovabrasilia',
					facebookLink: 'https://www.facebook.com/navedoconhecimentonovabrasilia',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Rua Nova Brasília, s/n° - Praça do Terço - Nova Brasília - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Recreação Infantil Estrelinha',
					imagem:RecreacaoInfantilEstrelinha,
					imagemMobile:RecreacaoInfantilEstrelinha,
					sobre: [
						''
					],
					telefone: '21 7985-9026',
					site: null,
					email: 'jornalista.cmarinho@gmail.com',
					facebook: null,
					facebookLink: null,
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Fazendinha, Área 5 e Nova Brasília - Comlexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Vai na web',
					imagem:VaiNaWeb_Logo,
					imagemMobile:VaiNaWeb_Logo,
					sobre: [
						'O Vai Na Web é um programa de educação em tecnologias digitais avançadas que busca democratizar o ensino e aprendizado de tecnologia e ajudar na emancipação dos nossos jovens nos desafios da nova era digital.'
					],
					telefone: '21 96850-2828',
					site: 'http://www.vainaweb.com.br/',
					email: null,
					facebook: '/vainaweb',
					facebookLink: 'https://www.facebook.com/vainaweb/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Clube de Luta do Complexo',
					imagem:ClubeLuta_Logo,
					imagemMobile:ClubeLuta_Logo,
					sobre: [
						'O Clube de Luta atua há 15 anos e oferece atividades esportivas com ênfase nas artes marciais, além de reforço escolar e atividades de lazer e cultura para crianças, jovens e adultos.',
						'Também se destacam no cenário de competições oficiais com dezenas de títulos estaduais e nacionais, inclusive em modalidades olímpicas como o Taekwondo. '
					],
					telefone: '21 98048-6486',
					site: null,
					email: 'dr.andreluiz1981@gmail.com',
					facebook: '/clubedelutadocomplexo',
					facebookLink: 'https://www.facebook.com/groups/clubedelutadocomplexo/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Estrada do Itararé - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Família Perninha Kickboxing',
					imagem:FamiliaPerninha,
					imagemMobile:FamiliaPerninha,
					sobre: [
						'Competidor e invicto há 3 anos, Mestre Perninha dá aulas de kickboxing há mais de 15 anos, já participou de projetos sociais e no momento continua oferecendo aulas gratuitas para crianças e adolescentes.'
					],
					telefone: '21 96820-5972',
					site: null,
					email: 'profperninhakick@gmail.com',
					facebook: '/FamíliaPerninha',
					facebookLink:'https://www.facebook.com/groups/582405115123151/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Associação Abraço Campeão',
					imagem:AbracoCampeao_Logo,
					imagemMobile:AbracoCampeao_Logo,
					sobre: [
						'A associação Abraço Campeão foi fundada pelo então professor/atleta Alan Duarte que iniciou suas atividades no ano de 2014, atuando na comunidade Morro do Adeus levando uma nova perspectiva para os jovens e adultos através do esporte, despertando novas potencialidades com disciplina através do boxe.'
					],
					telefone: '21 96892-9016',
					site: 'http://thegoodfightmovie.com/abraco-campeao/',
					email: null,
					facebook: '/alan.duarte.3386',
					facebookLink: 'https://www.facebook.com/alan.duarte.3386',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Morro do Adeus - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Centro Cultural Oca dos Curumins',
					imagem: OcaCurumins_Logo,
					imagemMobile: OcaCurumins_Logo,
					sobre: [
						'Conhecida como Escolinha da Tia Bete, tendo seu início no mês de Abril de 1977 com alfabetização, o Centro Cultural Ocas dos Curumins atualmente proporciona atividades na área social, cultural, esportivas, ambiental e prepara jovens para o mercado de trabalho.',
						'É um ponto de cultura reconhecido pela secretaria estadual e um ponto de leitura reconhecido também pela prefeitura do Rio. Realizam intercâmbio em parceria com a ONG Comunidade em Ação com parceiros voluntários de outros países.',
						'Na Oca dos Curumins são oferecidas oficinas de teatro, brincadeiras antigas, exibição de filmes, artesanatos, inclusive o Grupo Sempre Juntos do AA, cujo qual presta atendimento há 15 anos, além de estar desenvolvendo o resgate da cultura afro brasileira, entre outras atividades.',
						'A Oca dos Curumins é uma das instituições mais ativas do Complexo do Alemão com 40 anos de atividades na comunidade da Alvorada.'
					],
					telefone: '21 3071-6750',
					site: null,
					email: 'ccocadoscurumins@hotmail.com',
					facebook: '/CentroCulturalOcadosCurumins',
					facebookLink: 'https://www.facebook.com/CentroCulturalOcadosCurumins/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Estrada do Itararé, n°480 - Travessa São José, n° 13 - Alvorada - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'EDUCAP - Espaço Democrático de União, Convivência e Aprendizagem',
					imagem:'',
					imagemMobile:'',
					sobre: [
						''
					],
					telefone: '21 98832-3246',
					site: null,
					email: 'luciaeducap@gmail.com',
					facebook: '/educap.org',
					facebookLink: 'https://www.facebook.com/educap.org/',
					instagram: '@luciaeducap1716',
					instagramLink:'https://www.instagram.com/luciaeducap1716/',
					twitter: null,
					twitterLink:null,
					endereço: 'Rua Canitar - Campo do Sargento, s/n° - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Instituto Raízes Em Movimento ',
					imagem: RaizesMovimento_Logo,
					imagemMobile: RaizesMovimento_Logo,
					sobre: [
						'O INSTITUTO RAÍZES EM MOVIMENTO tem como missão promover o desenvolvimento humano, social e cultural do Complexo do Alemão e demais comunidades por meio da participação de atores locais como protagonistas desses processos, tendo como foco o fortalecimento e ampliação do capital social dessas comunidades'
					],
					telefone: '21 2260-3998',
					site: 'http://www.raizesemmovimento.org.br/',
					email: 'contato@raizesememovimento.org.br',
					facebook: '/raizesemmovimento',
					facebookLink: 'https://www.facebook.com/raizesemmovimento/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Avenida Central, n° 68 - Ramos - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Novos Líderes Empreendedores',
					imagem:'',
					imagemMobile:'',
					sobre: [
						'Atuando há 3 anos, desde 2014, a ONG usa a educação empreendedora para desenvolver e empoderar jovens e adultos das comunidades cariocas em prol de modificar e melhorar suas comunidades de origem.'
					],
					telefone: '21 99500-8681',
					site: 'http://novoslideresempreendedores.com/',
					email: 'lohransanto009@gmail.com',
					facebook: '/novoslideresempreendedores',
					facebookLink: 'https://www.facebook.com/novoslideresempreendedores',
					instagram: '@educatethefavela',
					instagramLink:'https://www.instagram.com/educatethefavela/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Instituto Movimento & Vida',
					imagem: MovimentoVida,
					imagemMobile: MovimentoVida,
					sobre: [
						'O Instituto Movimento & Vida é uma organização sem fins lucrativos que realiza atendimento de fisioterapia gratuito aos moradores do conjunto de favelas do Complexo do Alemão.  A melhoria da qualidade de vida e reabilitação dos pacientes é o objetivo principal do trabalho desenvolvido pela instituição que atua 2007, promovendo informações de hábitos saudáveis e de proteção à saúde.',
						'Sua missão é atender com qualidade, dedicação e amor moradores de uma região do Rio de Janeiro que segue marcada com violência, dificuldade, miséria e falta de atenção.',
						'Atualmente precisa de recursos para manter o funcionamento diário e ampliar o número de pessoas atendidas, reduzindo a fila de espera de pacientes.'
					],
					telefone: '21 96464-8101',
					site: null,
					email: 'monicacirnea@gmail.com',
					facebook: '/projetopaloma',
					facebookLink: 'https://www.facebook.com/projetopaloma/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Rua das Andorinhas, n° 98, Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Alexandre Silva Fotografia',
					imagem: AlexandreFotografia_Logo,
					imagemMobile: AlexandreFotografia_Logo,
					sobre: [
						''
					],
					telefone: '21 99744-5063',
					site: null,
					email: 'monicacirnea@gmail.com',
					facebook: '/projetopaloma',
					facebookLink: 'https://www.facebook.com/projetopaloma/',
					instagram: null,
					instagramLink:null,
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Casa Brota - Coworking de favela',
					imagem: CasaBrota_Logo,
					imagemMobile: CasaBrota_Logo,
					sobre: [
						'Casa Brota: Coworking de Favela, um espaço de conexão com foco na promoção cultural da favela e no desenvolvimento econômico das micro empresas.  Empreender a partir das criações e subjetividade de cada indivíduo, visando expandir e fortalecer as redes destes espaços populares para além da favela.  Prestação de serviços: Assessoria de imprensa, consultoria para empreendimentos da favela, redes, audiovisual, artes e tecnologia.'
					],
					telefone: '21 97264-7819',
					site: null,
					email: 'falecom@casabrota.com.br',
					facebook: '/casabrota',
					facebookLink: 'https://www.facebook.com/casabrota',
					instagram: '@casabrota',
					instagramLink:'https://www.instagram.com/casabrota/',
					twitter: null,
					twitterLink:null,
					endereço: 'Rua Ari Barroso, s/n° - ao lado da Estação do teleférico do Alemão - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Classe D - Ateliê de Ideias',
					imagem: ClasseD_Logo,
					imagemMobile: ClasseD_Logo,
					sobre: [
						'O Coletivo Classe-D é formado por um grupo de amigos que se conheceram pelas ruas do Rio de Janeiro fazendo graffiti por volta do início dos anos 2000.',
						'Mas só em 2012 que parte deste coletivo começou a pensar profissionalmente em suas habilidades com produções de arte e comunicação visual.',
						'A partir de então tem se desenvolvido gradativamente seus aprendizados, trabalhando para oferecer um serviço de qualidade e com características ousadas, com criatividade, segurança e compromisso. '
					],
					telefone: '21 99311-9672',
					site: null,
					email: 'produto.classed@gmail.com',
					facebook: '/Classe-D-Ateliê-de-Ideias',
					facebookLink: 'https://www.facebook.com/Classe-D-Ateliê-de-Ideias-950892308279847',
					instagram: '@classe_d22',
					instagramLink:'https://www.instagram.com/classe_d22/',
					twitter: null,
					twitterLink:null,
					endereço: 'Avenida Central, n°55 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Dança e Cia Art',
					imagem: DancaCiaArt_Logo,
					imagemMobile: DancaCiaArt_Logo,
					sobre: [
						'Tendo hoje 20 anos de idade, Pedro iniciou sua história com a dança no ano de 2010 com o grupo AfroReggae que com 1 ano se dedicando conseguiu uma bolsa e se aprofundar no que gosta. A coisa deu tão certo que perto de completar 2 anos ele foi promovido a monitor das aulas, o que o fez ganhar um pouco mais que só uma bolsa. Com o fechamento do AfroReggae em 2013, Pedro passou a dançar e a ensinar por conta própria, estando hoje à disposição daqueles que queiram aprender a arte da dança criando então a Dança e Cia Art.'
					],
					telefone: '21 99417-8279',
					site: null,
					email: 'pedro.grh@gmail.com',
					facebook: '/dancaeciaart',
					facebookLink: 'https://www.facebook.com/dancaeciaart',
					instagram: '@dancaeciaart',
					instagramLink:'https://www.instagram.com/dancaeciaart/',
					twitter: null,
					twitterLink:null,
					endereço: 'Estrada Adhemar Bebiano, 1185 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Erica Martin Fotografia',
					imagem: ErikaMartin,
					imagemMobile: ErikaMartin,
					sobre: [
						'Iniciou na fotografia há três anos na Nave do Conhecimento (Nova Brasília) e de lá foi encaminhada para cursar fotografia no SENAI. Foi integrante de um curso audiovisual e um webdoc também dentro do Alemão. Atualmente é integrante do coletivo Cá Entre Clicks e Fotógrafas Brasileiras.'
					],
					telefone: '21 99645-4187',
					site: null,
					email: 'ericamar_irgm@hotmail.com',
					facebook: '/photosnpictures',
					facebookLink: 'https://www.facebook.com/photosnpictures',
					instagram: '@ericamfotos',
					instagramLink:'https://www.instagram.com/ericamfotos/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Estúdio Abaeté',
					imagem: EstudioAbaete_Logo,
					imagemMobile: EstudioAbaete_Logo,
					sobre: [
						'O Estúdio Abaeté é uma produtora de desenvolvimento, criação e produção audiovisual. Todos os profissionais atuantes na empresa são moradores do Alemão, com formação através de projetos e cursos locais, colocando a juventude recém formada numa atuação direta com o mercado.'
					],
					telefone: '21 98336-9348',
					site: null,
					email: 'estudioabaete@gmail.com',
					facebook: '/estudioabaete',
					facebookLink: 'https://www.facebook.com/estudioabaete',
					instagram: '@estudioabaete',
					instagramLink:'https://www.instagram.com/estudioabaete/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Agência Carol Muniz ',
					imagem: CarolMuniz,
					imagemMobile: CarolMuniz,
					sobre: [
						''
					],
					telefone: '21 97012-0816',
					site: null,
					email: 'contatoagenciamuniz@yahoo.com',
					facebook: '/contatoagenciamuniz',
					facebookLink: 'https://www.facebook.com/contatoagenciamuniz',
					instagram: '@contatoagenciamuniz',
					instagramLink:'https://www.instagram.com/contatoagenciamuniz/',
					twitter: null,
					twitterLink:null,
					endereço: 'Estrada do Itararé, 480 - Rua Nova, n°1 - Alvorada - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Marcos Carolino Art',
					imagem: MarcosCarolinno_Logo,
					imagemMobile: MarcosCarolinno_Logo,
					sobre: [
						'Dançarino há 9 anos, Marcos Carolinno, sentiu a necessidade de dividir esse dom com outras pessoas que também amam dançar. Atua como coreógrafo para festas de 15 anos desde 2013 e quer divulgar seu trabalho para além do Complexo do Alemão.'
					],
					telefone: '21 98027-4304',
					site: null,
					email: 'mcarolino20@gmail.com',
					facebook: '/marcos.carolinoart',
					facebookLink: 'https://www.facebook.com/marcos.carolinoart',
					instagram: '@carolinnocoreografo',
					instagramLink:'https://www.instagram.com/carolinnocoreografo/',
					twitter: null,
					twitterLink:null,
					endereço: 'Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Toca do Lobo Produções',
					imagem: TocaLobo_Logo,
					imagemMobile: TocaLobo_Logo,
					sobre: [
						'Há 6 anos a Toca do Lobo Produções oferece serviços de decorações de festas em Malhas Tensionadas, produção cultural, além de aluguel de equipamentos de som, iluminação e DJ.',
						'Seu proprietário, Helcimar Lopes, também atua e presta seus serviços com produção cultural e drinkeiro. É reconhecido por promover os eventos mais badalados no Complexo do Alemão.'
					],
					telefone: '21 97045-3227',
					site: null,
					email: 'helcimar@gmail.com',
					facebook: '/tdlproducoes',
					facebookLink: 'https://www.facebook.com/tdlproducoes',
					instagram: '@malhastensionadashelcimarlopes',
					instagramLink:'https://www.instagram.com/malhastensionadashelcimarlopes/',
					twitter: null,
					twitterLink:null,
					endereço: 'Rua Sebastião de Carvalho, n°193 Fundos - Casa 01 - Complexo do Alemão - Rio de janeiro'
				},
				{
					nome: 'Tiaguinho Silva',
					imagem: TiaguinhoSilva,
					imagemMobile:TiaguinhoSilva,
					sobre: [
						'Tiago é um dos inúmeros mototaxista que resolveu se incorporar nesta opção de transporte alternativo oriundo da favela. O Moto Táxi é o transporte de passageiros que possibilita comodidade e agiliza a viagem por conta da flexibilidade sobre duas rodas.'
					],
					telefone: '21 97361-7113',
					site: null,
					email: 'tspurificacao@gmail.com',
					facebook: '/TiaguinhoSilva',
					facebookLink: 'https://www.facebook.com/profile.php?id=100013204902709',
					instagram: '@tiaguinhoalvorada',
					instagramLink:'https://www.instagram.com/tiaguinhoalvorada/',
					twitter: null,
					twitterLink:null,
					endereço: ','
				}
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
	width: 50%;
	max-width: 670px;
	min-height: 100vh;
	margin-right: auto;
	background: url(../../static/assets/background.svg) center bottom no-repeat;
	background-size: 100%;
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
	object-fit: contain;
	object-position: center;
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
}
.infoSobreConteudo-div{
	min-width: 240px;
	width: 40%;
}
@media(max-width: 1290px){
	.infoSobreConteudo-div{
		max-width: 100%;
	}
	.sobreConteudo-divIcon{
		max-width: 50%;
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
	min-width: 300px;
	max-width: 60%;
	padding-left: 10px;
	display: flex;
	flex-flow: row wrap;
	align-items: center;
	justify-content: flex-start;
	align-content: flex-start;
}
.infoSobreConteudoDiv-icon{
	width: 25px;
	margin: 15px 0;
}
.sobreConteudo-divIcon a{
	cursor: pointer;
}
.infoSobreConteudoDiv-text{
	width: 85%;
	margin-left: 8px;
	margin-right: auto;
	font-family: ministry, sans-serif;
	font-style: normal;
	font-weight: 400;
	font-size: 14px;
	color: #2e3192;
}
.infoSobreConteudoDiv-text:hover{
	text-decoration: none;
}
@media (max-width: 1350px){
	.infoSobreConteudoDiv-text{
		width: 85%;
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