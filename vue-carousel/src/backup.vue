<!--representa uma resolucao que contem 4 slides e os slides tem conter os seguintes:
1- Neste slide, escreva/mostre uma pergunta de sua escolha. Fora do carrossel, queremos que você exiba a resposta à pergunta.
2- Este slide deve conter uma data (em dd/mm/aaaa ou em formato estúpido). Você exibirá mais uma vez a data que foi inserida fora do carrossel.
3- Este slide segue a estrutura do challenge2.png , você pode adicionar qualquer texto (seja criativo), não sendo necessário ser o da imagem. Para fazer isso, você deve usar o flexbox.
4- Por último, exiba uma imagem: challenge.png .-->
<template>
    <Carousel>
        <Slide v-for="slide in 10" :key="slide">
            <div class="carousel__item">{{ slide }}</div>
        </Slide>

        <Slide>
            <div class="carousel__item">
                <h1>Onde fica o IST?</h1>
            </div>
        </Slide>
        
        <Slide>
            <div class="carousel__item">
                <h1>{{ date }}</h1>
            </div>
        </Slide>

        <Slide>
            <div class="carousel__item challenge2">
                <div class="flex-item">Texto</div>
            </div>
        </Slide>

        <Slide>
            <div class="carousel__item">
                <img :src="image">
            </div>
        </Slide>

        <template #addons>
            <Navigation />
            <Pagination />
        </template>
    </Carousel>
        <div class="answers">
        <p>Resposta: Alameda</p>
        <p>Resposta: {{ Date }}</p>
        </div>
</template>
  
  <script>
  import { defineComponent } from 'vue'
  import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel'
  
  import 'vue3-carousel/dist/carousel.css'
  
  export default defineComponent({
    name: 'Basic',
    components: {
      Carousel,
      Slide,
      Pagination,
      Navigation,
    },
    data(){
        return {
            date: ''
        }
    },
    mounted(){
        this.getCurrentDate()
    },
    methods: {
        getCurrentDate() {
            const now = new Date();
            const day = String(now.getDate()).padStart(2, '0');
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const year = now.getFullYear();
            this.currentDate = `${day}/${month}/${year}`;
        }
    }
  })
  </script>
  
  <style scoped>
  .challenge2 {
    display: flex;
    justify-content: space-around;
  }

  .flex-item {
    flex: 1;
    padding: 20px;
    border: 1px solid #ccc;
}
  .carousel__item {
    width: 100px;
    height: 100px;
    background-color: blue;
    color: black;
    font-size: 20px;
    border-radius: 8px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .carousel__slide {
    padding: 10px;
  }
  
  .carousel__prev,
  .carousel__next {
    box-sizing: content-box;
    border: 5px solid white;
  }
  </style>
  