<template>
    <Carousel>
        <Slide :key="slide">
            <div class="carousel__item">
                <div class="question">
                    <h1>你瞅啥?</h1>
                    <p>{{ answer }}</p>
                </div>
            </div>  
        </Slide>
        
        <Slide :key="slide">
            <div class="carousel__item">
                <div class="date">
                    <h1>{{ date }}</h1>
                </div>
            </div>
        </Slide>

        <Slide :key="slide">
            <div class="carousel__item">
                <div class="flex-item1">
                    <h1>Interation of Wind Farms into Electrity Grids</h1>
                </div>
                <div class="flex-item2">
                    <h2>Workshops</h2>
                    <h2>by Vestas</h2>
                </div>
                <div class="flex-item3">
                    <p>This workshops will cover the representation of wind farms in simulation software, with an empasis on wind turbine design and electrical performance for compliance with grid requirements.</p>
                </div>
            </div>
        </Slide>

        <Slide :key="slide">
            <div class="carousel__item">
                <img class="image_style" :src="image">
            </div>
        </Slide>
  
        <template #addons>
            <Navigation />
            <Pagination />
        </template>
    </Carousel>

    <div>
        <form @submit.prevent="responder_pergunta">
            <input v-model="text" required placeholder="Type answer">
            <button>Enter</button>
        </form>
        <form @submit.prevent="responder_data">
            <input v-model="new_date" required placeholder="Type new date">
            <button>Enter</button>
        </form>
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
            text: '',
            answer: '',
            date: '08/05/2024',
            new_date: '',
            image: './src/challenge.png'
        }
    },
    methods: {
        responder_pergunta() {
            this.answer = ''
            this.answer = this.text 
            this.text = ''
        },
        responder_data () {
            this.date = this.new_date
            this.new_date= ''
        }
    }
  })
  </script>
  
  <style scoped>
  .question {
    width: 50%;
  }
  .answer {
    width: 50%;
  }

  /*.challenge2 {
    display: flex;
    justify-content: space-around;
    align-items: center;
  }*/

    .flex-item1{
        order: 1;
        align-items: flex-start;
        text-align: start;
    }

    .flex-item2 {
        order: 2;
        text-align: start;
    }

    .flex-item3 {
        order:3;
        align-items: flex-end;
        text-align: start;
    }
    .image_style{
        width: 100%;
    }

  .carousel__item {
    /*min-width: 200px;
    min-height: 500px;*/
    width: 100%;
    height: 100%;
    max-width: 700px;

    background-color: rgb(41, 154, 207);
    color: white;
    font-size: 20px;
    border-radius: 8px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .carousel__slide {
    max-width: 700px;
    padding: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 300px;
    border: 1px #ccc;
  }
  
  .carousel__prev,
  .carousel__next {
    box-sizing: content-box;
    border: 5px solid white;
  }
  </style>
  