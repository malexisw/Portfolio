<template>
    <div class="home">
        <div :class="viewH">
            <div class="title">
                Alexis Martel
            </div>

            <div class="nav-bar">
                <a href="#accueil">
                    <div :class="headAccueil" @click="setViewH()">
                        Accueil
                    </div>
                </a>
                <a href="#portfolio">
                    <div :class="headPortfolio" @click="setViewH()">
                        Portfolio
                    </div>
                </a>
                <a href="#about">
                    <div :class="headAbout" @click="setViewH()">
                        A propos
                    </div>
                </a>
                <a href="#contact">
                    <div :class="headContact" @click="setViewH()">
                        Contact
                    </div>
                </a>

                <div class="link">
                    <div class="square ink">
                        <a href="https://www.linkedin.com/in/alexis-martel-3054571b3/" target="_blank"> <i class="fab fa-linkedin"></i></a>
                    </div>
                    <div class="square git">
                        <a href="https://github.com/malexisw" target="_blank"><i class="fab fa-github"></i></a>
                    </div>
                </div>
            </div>

            <div class="info">
                <div class="profil">
                    <img src="../assets/profil.jpg">
                </div>
            </div>
            
        </div>

        <div class="body">
            <div class="btn-head" v-if="!head" @click="setViewH()">
                <i class="fas fa-bars"></i>
            </div>
            <div class="accueil" id="accueil">
                <div class="content">
                    <p class="name">Alexis Martel</p>
                    <p class="sub">Développeur Front-End</p>

                    <a class="link-resume" href="/files/AlexisMartelResumeENG.pdf" download>
                        Télécharger CV
                    </a>
                </div>
            </div>
            <div class="portfolio" id="portfolio">
                <div class="section">
                    <div class="section-title">
                        Portfolio
                    </div>
                    <div class="works">
                        <div class="workGrid" v-for="(work,index) in portfolio" :key="index" @click="sendWork(work)">
                            <img :src="require('@/assets/icon/' + work.illustration)">
                            <p class="w-name">{{ work.name }}</p>
                            <p class="w-frame">{{ work.framework }}</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="about" id="about">
                <div class="section">
                    <div class="section-title">
                        A propos
                    </div>

                    <div class="presentation">
                        <div class="paragraphe">
                            <div class="pres-title">
                                Alexis Martel, Développeur Front-End
                            </div>
                            <div class="pres-content">
                                Je suis un jeune diplômé d'une <span style="color: cyan"> licence informatique </span>. <br />
                                J'ai étudié a l'université de Picardie Jules Verne à Amiens.<br />
                                Je recherche une position de <span style="color: cyan"> développeur front-end Angular ou VueJs </span> pour gagner en expérience et en compétences.<br /><br />

                                Depuis l'obtention de mon diplôme j'ai créé quelques <span style="color: cyan"> projets personnels </span> pour apprendre les frameworks Angular et VueJS. <br />
                                Je veut être un développeur front-end parceque j'aime l'idée de transformer une page blanche en quelque chose <span style="color: cyan"> d'utile et d'interréssant </span> pour quelqu'un.
                            </div>
                        </div>
                        <div class="pres-info">
                            <p class="age">
                                <span class="underline">Age</span> 23 ans
                            </p>
                            <p class="mail">
                                <span class="underline">E-mail</span> <a class="mail-link" href="mailto:alexis.martel.w@hotmail.com"> alexis.martel.w@hotmail.com </a>
                            </p>
                            <p class="phone">
                                <span class="underline">Téléphone</span> 06 02 28 18 30
                            </p>
                            <p class="adresse">
                                <span class="underline">Adresse</span> 6ter rue des avesnes, 60130 Fournival
                            </p>
                        </div>
                    </div>

                    <a class="link-resume" href="/files/AlexisMartelResumeENG.pdf" download>
                        Télécharger CV
                    </a>
                </div>
            </div>
            <div class="contact" id="contact">
                <div class="section">
                    <div class="section-title">
                        Contact
                    </div>

                    <div class="section-contact">
                        <div class="inSC contact-phone">
                           <i class="fas fa-phone-alt"></i> <p>06.02.28.18.30</p> 
                        </div>

                        <div class="inSC contact-mail">
                            <i class="fas fa-envelope"></i> <a href="mailto:alexis.martel.w@hotmail.com">alexis.martel.w@hotmail.com</a> 
                        </div>
                        
                        <div class="inSC contact-adresse">
                            <i class="fas fa-map-marker-alt"></i> <p> 6ter rue des avesnes, 60130 fournival</p>
                        </div>
                    </div>

                </div>
            </div>
        </div>

        <transition name="appearWork">
            <Work v-if="viewWork" :work="work" @clicked="viewWork = $event"/>
        </transition>

    </div>
</template>

<script>
import Work from './Work.vue';

export default {
    name: "Home",
    components: { Work },
    data(){
        return{
            portfolio: {
                quizgame: {
                    image: 'quizgame.jpg',
                    illustration:'quizgame.jpg',
                    name: 'Quizgame',
                    site: 'https://cocky-cori-51d3c2.netlify.app/#/',
                    date:'01/10/2020',
                    techno:['Vue.JS', 'Javascript', 'Html5', 'CSS', 'Bootstrap'],
                    outils:['Visual Studio Code','OpenTriviaDB API'],
                    description: `Ce projet est une application simulant un jeu de quiz. L'utilisateur choisit une catégorie puis une difficulté et ensuite répond aux questions prises par l'API OpenTriviaDB.`,
                    framework: 'VueJS'
                },
                rps: {
                    image: 'RPS.jpg',
                    illustration:'RPS.jpg',
                    name: 'RPS',
                    site: 'https://zealous-yalow-0dc5e5.netlify.app/#/home',
                    date:'16/09/2020',
                    techno:['Vue.JS', 'Javascript', 'Html5', 'CSS'],
                    outils:['Visual Studio Code'],
                    description: `Cette application web simule le jeu populaire du pierre/feuille/ciseaux. Pour jouer, il suffit de choisir l'un des trois choix en espérant gagner contre le choix de l'adversaire qui n'est d'autre que l'ordinateur.`,
                    framework: 'VueJS'
                },
                simon: {
                    image: 'simon.jpg',
                    illustration:'simon.png',
                    name: 'Simon',
                    site: 'https://eager-lamarr-2bf430.netlify.app/',
                    date:'29/12/2020',
                    techno:['Vue.JS', 'Javascript', 'Html5', 'CSS','SCSS'],
                    outils:['Visual Studio Code'],
                    description: `Ce site mime le Simon qui est un jeu de plateau très connu. Pour jouer, il suffit de cliquer sur le bouton 'start', de mémoriser la séquence et de la reproduire en cliquant.`,
                    framework: 'VueJS'
                } ,
                noisemix: {
                    image: 'noisemix.jpg',
                    illustration:'noisemix.jpg',
                    name: 'Noisemix',
                    site: 'https://serene-clarke-0bc81c.netlify.app/',
                    date:'16/09/2020',
                    techno:['AngularJS', 'Javascript', 'Html5', 'CSS','Sass','Typescript','SCSS'],
                    outils:['Visual Studio Code','Font Awesome'],
                    description: `Noisemix est une application de relaxation où il suffit de choisir le ou les sons que l'utilisateur veut écouter et les écouter.`,
                    framework: 'Angular'
                },
                copycat: {
                    image: 'copycat.jpg',
                    illustration:'copycat.jpg',
                    name: 'Copycat',
                    site: 'https://compassionate-kowalevski-879f8d.netlify.app/',
                    date:'01/11/2020',
                    techno:['AngularJS', 'Javascript', 'Html5', 'CSS','Sass','Typescript','SCSS'],
                    outils:['Visual Studio Code'],
                    description: `Copycat est un site qui imite les pages d'accueil de 4 différents sites très connus. J'e l'est crée pour m'améliorer en HTML/CSS mais aussi pour voir si j'étais capable de les intégrer correctement.`,
                    framework: 'Angular'
                },
                shopcart: {
                    image: 'shopcart.jpg',
                    illustration:'shopcart.jpg',
                    name: 'Shopcart',
                    site: 'https://gallant-archimedes-c140b8.netlify.app/',
                    date:'16/09/2020',
                    techno:['AngularJS', 'Javascript', 'Html5', 'CSS','Sass','Typescript','SCSS'],
                    outils:['Visual Studio Code','Font Awesome'],
                    description: `Cette application est un exemple d'un site de commerce qui a l'option du panier. Il suffit de cliquer sur 'ajouter au panier' sur n'importe quel article.`,
                    framework: 'Angular'
                },
                album: {
                    image: 'album.jpg',
                    illustration:'album.jpg',
                    name: 'Album',
                    site: 'https://my-second-project-eae54.web.app/home',
                    date:'23/07/2020',
                    techno:['AngularJS', 'Javascript', 'Html5', 'CSS','Sass','Typescript'],
                    outils:['Visual Studio Code','Firebase','Font Awesome'],
                    description: `Album est une application, un réseau social et un service de partage de photos inspiré d'instagram.`,
                    framework: 'Angular'
                }
            },
            headAccueil: 'nav highlight',
            headPortfolio: 'nav',
            headAbout: 'nav',
            headContact: 'nav',
            head: null,
            viewH: '',
            viewWork: false,
            work: null
        }
    },
    mounted(){
        this.head = window.innerWidth > 1300 ? true : false;
        this.viewH = window.innerWidth > 1300 ? 'header visible' : 'header hidden';
    },
    created () {
        window.addEventListener('scroll', this.setHead);
        window.addEventListener('resize', this.handleHead);
    },
    destroyed () {
        window.removeEventListener('scroll', this.setHead);
        window.removeEventListener('resize', this.handleHead);
    },
    methods:{
        setHead(){
            this.headAccueil = window.scrollY >= 0 && window.scrollY < 800 ? "nav highlight" : "nav";
            this.headPortfolio = window.scrollY >= 800 && window.scrollY < 1200 ? "nav highlight" : "nav";
            this.headAbout = window.scrollY >= 1200 && window.scrollY < 1750 ? "nav highlight" : "nav";
            this.headContact = window.scrollY >= 1750 ? "nav highlight" : "nav";
        },
        handleHead(){
            this.head = window.innerWidth > 1300 ? true : false;
            this.viewH = window.innerWidth > 1300 ? 'header visible' : 'header hidden';
        },
        setViewH(){
            this.viewH = this.viewH == 'header visible' && window.innerWidth < 1300 ? 'header hidden' : 'header visible';
        },
        sendWork(data){
            this.work = null;
            this.work = data;
            this.viewWork = true;
        }
    }
}
</script>

<style scoped>

.header{
    position: fixed;
    width: 160px;
    height: 100vh;

    left: -160px;

    z-index: 2;

    background: #2b2828;

    animation: slide-in 1.5s 3s forwards;
}

@keyframes slide-in {
    100%{
        left: 0px;
    }
}

.hidden{
    visibility: hidden;
}

.visible{
    visibility: visible;
}

.nav-bar{
    position: relative;
    top: 35%;
    transform: translateY(-35%);
}

.nav{
    width: 100%;
    text-align: center;
    background:  #2b2828;
    border-bottom: solid 1px #221f1f;
    border-top: solid 1px #221f1f;

    padding: 5px 0;
    cursor: pointer;
}

.highlight{
    background: #443f3f;
    border-right: solid 2px cyan;
}

.nav:hover{
    background: #443f3f;
    border-right: solid 2px cyan;
}

span{
    min-width: fit-content;
}

.info{
    position: absolute;
    bottom: 5%;
}

.link{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 25px;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
    height: 25px;
}

.about,.portfolio,.cv,.contact{
    background: #2b2828;
    margin-top: 15px;
}

.square{
    text-align: center;
    width: 25px;
    height: 25px;

    background: #443f3f;

    cursor: pointer;
}

.square:hover{
    background: cyan;
}

.profil{
    width: 50%;
    margin-left: auto;
    margin-right: auto;
    margin-top: 25px;
}

.accueil{
    background: center / cover no-repeat url("../assets/landscape.jpg");

    min-height: 100vh;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.content{
    width: 100%;
    text-align: center;
}

.name{
    font-weight: 600;
    font-size: 4em;
    letter-spacing: 2px;
    text-transform: uppercase;
    line-height: 1.5em;

    opacity: 0;

    animation: fade-in 2s 3s forwards;
}

@keyframes fade-in {
    100%{opacity: 1;}
}

.link-resume{
    text-align: center;
    width: 170px;

    border: solid 2px cyan;
    padding: .8em 2em;

    transition: .3s;
}

.link-resume:hover{
    background: cyan;
}

.sub{
    font-size: 1.8em;
    margin-bottom: 80px;
    opacity: 0;
    transform: translateY(-50px);

    animation: slide-down .5s 4.5s forwards;
}

@keyframes slide-down {
    100%{
        opacity: 1;
        transform: translateY(0px);
    }
}

.title{
    width: 90%;
    font-weight: 600;
    font-size: 1.1em;
    text-align: center;

    margin-top: 50px;
    background: linear-gradient(to right, #fff 20%, cyan 40%, cyan 60%, #fff 80%);
    background-size: 200% auto;
    color: #000;

    background-clip: text;
    text-fill-color: transparent;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;

    animation: shine 5s 3s linear infinite;
}

@keyframes shine {
    to{
        background-position: 200% center;
    }
}

img{
    max-width: 100%;
    max-height: 100%;
    width: auto;
    height: auto;
}

a{
    text-decoration: none;
    color: #fff;
}

.about{
    width: 100%;
}

.paragraphe{
    margin-bottom: 50px;
    margin-top: 15px;
    margin-right: 5%;
}

.pres-title{
    font-weight: 600;
    font-size: 1.4em;
    margin-bottom: 20px;
}

.pres-content{
    font-size: 1.1em;
    line-height: 2em;
}

.age,.mail,.phone,.adresse{
    display: flex;
    margin: 10px 0;
}

.mail-link{
    color: cyan;
}

.underline{
    color: #fff;
    font-weight: 600;
    margin-right: 10px;
}

.underline::after{
    display: block;
    content: '';
    min-width: 95%;
    height: 2px;
    background: cyan;
}

.section-title{
    font-size: 2.5em;
    font-weight: 600;
}

.section-title:after{
    display: block;
    content: '';
    width: 100%;
    height: 2px;
    margin-top: 5px;
    background: #4d4848;
}


.works{
    display: flex;
    flex-wrap: wrap;

    margin-top: 50px;
}

.workGrid:hover{
    transform: scale(1.05);
}

.workGrid:hover .w-name,.workGrid:hover .w-frame{
    opacity: 1;
}

.w-name,.w-frame{
    position: absolute;

    padding: 0 5px;

    font-weight: 600;
    color: black;
    background: #fff;

    opacity: 0;

    transition: .3s;
}

.w-name{
    top: 5px;
    left: 10px;

    font-size: .9em;
}

.w-frame{
    bottom: 5px;
    right: 10px;

    font-size: .8em;
}


.inSC{
    display: flex;
    justify-content: center;
    align-items: center;

    height: 100px;
    margin: 20px;

    background: #443f3f;

    font-weight: 600;
}

.inSC p,.inSC a{
    margin-left: 10px;
}

.btn-head{
    position: fixed;
    top: 10%;
    left: 90%;
    cursor: pointer;

    font-size: 2em;
}

.workGrid{
    position: relative;
    width: auto;
    height: auto;

    margin-right: 5px;
    margin-bottom: 5px;

    cursor: pointer;

    background:#eee;

    transition: .3s;
}

.presentation{
    margin-top: 20px;
    max-width: 100%;
}

.section{
    height: auto;
    width: 85%;
    min-height: 100%;
    min-width: 85%;
}

.appearWork-enter-active,
.appearWork-leave-active{
    transition: .5s ease-in;
}

.appearWork-enter{
    transform: translate(100%, 0);
}

.appearWork-leave-active{
    transform: translate(100%, 0);
}

@media only screen and (min-width: 1300px) {

    .body{
        width: calc(100%-175px);
        margin-left: 175px;

        background: #0f0f0f;
    }

    .section-contact{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
    }

    .inSC{
        font-size: 1.4em;
    }

    .workGrid{
        max-height: 225px;
        max-width: 225px;
    }

    .presentation{
        display: flex;
    }

    .paragraphe{
        width: 55%;
        max-width: 55%;
    }

    .pres-info{
        max-width: 40%;
        width: 40%;
    }

    .section{
        padding: 50px 70px 70px;
    }
}

@media only screen and (max-width: 1300px) {

    .body{
        width: 100%;

        background: #0f0f0f;
    }

    .section-contact{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
    }

    .inSC{
        font-size: 1.1em;
    }

    .workGrid{
        max-height: 225px;
        max-width: 225px;
    }

    .presentation{
        display: flex;
    }

    .paragraphe{
        width: 55%;
        max-width: 55%;
    }

    .pres-info{
        max-width: 40%;
        width: 40%;
    }

    .section{
        padding: 50px 70px 70px;
    }
}

@media only screen and (max-width: 900px) {
    .section-contact{
        display: grid;
        grid-template-columns: repeat(1, 1fr);
    }

    .workGrid{
        max-height: 150px;
        max-width: 150px;
    }

    .presentation{
        display: block;
    }

    .paragraphe{
        width: 95%;
        max-width: 95%;
    }

    .pres-info{
        max-width: 90%;
        width: 90%;

        margin-bottom: 40px;
    }

    .section{
        padding: 50px 30px 30px;
    }
}

</style>