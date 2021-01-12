<template>
    <div class="work">
        <div class="back" @click="onBack()">
            x
        </div>

        <div class="content">
            <h1 class="pres-title">
                {{ work.name }}
            </h1>
            <div class="desc">
                <div class="left">
                    <p class="pres">
                        {{ work.description }}
                    </p>
                    <div class="cadre">
                        <img :src="require('@/assets/image/' + work.image)">
                    </div>
                </div>
                <div class="right">
                    <h1 class="info-title">
                        Description
                    </h1>
                    <div class="info">
                        <p class="text-info">
                            <span class="underline"><i class="fas fa-calendar-alt"></i> Date</span>  {{ work.date }}
                        </p>
                        <div class="text-info">
                            <span class="underline"><i class="fas fa-globe"></i> Site</span> <a :href="work.site" target="_blank">{{ work.site }}</a> 
                        </div>
                    </div>
                    <div class="technos">
                        <h2 class="title-technos underline">
                            <i class="fas fa-cog"></i> Technologies
                        </h2>
                        <div class="text-technos" >
                            <p class="techno" v-for="(techno,index) in work.techno" :key="index">
                                {{ techno }}
                            </p>
                        </div>
                    </div>
                    <div class="outils">
                        <h2 class="title-outils underline">
                            <i class="fas fa-tools"></i> Outils
                        </h2>
                        <div class="text-outils" >
                            <p class="outil" v-for="(outil,index) in work.outils" :key="index">
                                {{ outil }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
   name: 'Work',
   props:{
       work: {}
   },
   methods:{
       onBack(){
           this.$emit('clicked',false)
       }
   }
}
</script>

<style scoped>
.work{
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;

    height: 100vh;
    width: 100%;

    background: #2b2828;

    z-index: 99;
}


.back{
    position: absolute;
    right: 18%;
    top: 5%;

    width: 30px;
    height: 30px;

    background: #000;

    text-align: center;
    font-size: 2em;
    cursor: pointer;

    transition: .5s;
}

.back:hover{
    color: cyan;

    transform: rotate(360deg);
}

img{
    max-width: 100%;
    max-height: 100%;
    width: auto;
    height: auto;
}

.cadre{
    width: 100%;
    height: auto;
}

.desc{
    display: flex;

    width: 80%;

    margin: auto
}

.pres-title{
    width: 80%;
    margin: auto;

    letter-spacing: 1.5px;
    font-weight: 600;

    text-transform: uppercase;
}

.right{
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    background: #443f3f;
}

.text-technos,.text-outils{
    display: flex;
    flex-wrap: wrap;
}

.techno,.outil{
    margin: 5px;
    padding: 0 5px;

    background:  #2b2828;
}

.underline{
    color: #fff;
    font-weight: 600;
    margin-right: 10px;

    min-width: fit-content;
}

p,h1,h2,span{
    cursor: default;
}

.title-technos,.title-outils{
    font-weight: 600;
    font-size: 1.2em;
    margin: 15px 0;
}

.text-info{
    display: flex;
    margin: 20px 0;
}

.info-title{
    font-size: 1.5em;
    font-weight: 600;
}

.outils,.technos{
    margin-bottom: 20px;
}

.info-title:after{
    display: block;
    content: '';
    width: 100%;
    height: 2px;
    margin-top: 5px;
    background: #4d4848;
}

a{
    text-decoration: none;
    color: cyan;
}


@media only screen and (min-width: 1300px) {
    .desc{
        display: flex;
    }

    .left{
        width: 65%;
        margin-right: 20px;

        padding: 10px 0px 50px;
    }

    .right{
        width: 35%;
        padding: 20px;
    }

    .pres-title{
        font-size: 1.8em; 
        margin-bottom: 85px;
    }

    .pres{
        font-size: 1.1em;
        margin-bottom: 50px;
    }

    .content{
        width: 80%;
        margin: auto;
        padding: 50px 70px 70px;
    }
}

@media only screen and (max-width: 1300px) {
    .desc{
        display: block;
    }

    .left{
        width: 100%;
    }

    .right{
        width: calc(100%-40px);
        padding: 20px;
    }

    .pres-title{
        font-size: 1.8em; 
        margin-bottom: 35px;
    }

    .pres{
        font-size: 1.1em;
        margin-bottom: 20px;
    }

    .content{
        width: 95%;
        margin: auto;
        padding: 50px 20px 20px;
    }
}
</style>