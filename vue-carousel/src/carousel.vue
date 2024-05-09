<template>
    <Carousel class="carousel-section"  @slide-end="SlideEnd">
        <Slide :key="slide">
            <div class="carousel__item">
                <div class="question">
                    <h1>Qual a cor clássica do Técnico?</h1>
                </div>
            </div>  
        </Slide>
        
        <Slide :key="slide">
            <div class="carousel__item">
                <div class="date">
                    <form @submit.prevent="newDate">
                        <input type="date" v-model="date">
                        <button>Enter</button>
                    </form>
                </div>
            </div>
        </Slide>

        <Slide :key="slide">
            <div class="carousel__item">
                <div class="flex-box">
                    <div class="flex-item1">
                        <p class="text1">Interation of Wind Farms into Electrity Grids</p>
                    </div>
                    <div class="flex-item2">
                        <p class="text2">Workshops by Vestas</p>
                    </div>
                    <div class="flex-item3">
                        <p class="text3">This workshops will cover the representation of wind farms in simulation software, with an empasis on wind turbine design and electrical performance for compliance with grid requirements.</p>
                    </div>
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
    <div class="answer1">
        <p v-if=" currentSlide === 1">Azul</p>
        <p v-else-if="currentSlide === 2">{{ new_date }}</p>
        <p v-else>{{ '' }}</p>
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
            date: '',
            new_date: '',
            image: './src/challenge.png',
            currentSlide : 1
        }
    },
    methods: {
        SlideEnd(data) {
            console.log('slide-end', data)
            if(data.currentSlideIndex == 0){
                this.currentSlide = 1
            }
            else if(data.currentSlideIndex == 1){
                this.currentSlide = 2
            }
            else{
                this.currentSlide =0
            }
        },
        newDate() {
            this.new_date = this.date
        }
    }
  })
  </script>
  
  <style scoped>
  .question {
    width: 50%;
  }
  .answer1 {
    display: flex;
    justify-content: center;
    font-size: xx-large
  }
  

  .date input {
    font-size: larger
  }
  
  .date button {
    font-size: larger;
  }

    .flex-box {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        row-gap: 20px;
        align-content: flex-start;
        margin: auto 5%;
    }
    .flex-item1{
        order: 1;
        text-align: start;
    }

    .flex-item2 {
        order: 2;
        text-align: start;
    }

    .flex-item3 {
        order:3;
        text-align: start;
    }

    .text1 {
        font-size: 50px;
        margin-block: 0%;
    }

    .text2 {
        font-size: 40px;
        margin-block: 0%;
    }

    .text3 {
        font-size: 30px;
        margin-block: 0%;
    }
    .image_style{
        width: 100%;
    }

    .carousel-section {
    max-width: 50%;
    margin: auto auto;
    margin-top: 10%;
    
    }

  .carousel__item {
    /*min-width: 200px;
    min-height: 500px;*/
    width: 100%;
    height: 100%;

    background-color: rgb(75, 179, 227);
    color: white;
    font-size: 20px;
    border-radius: 8px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .carousel__slide {
    padding: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 500px;
    border: 1px #ccc;
  }
  
  .carousel__prev,
  .carousel__next {
    box-sizing: content-box;
    border: 5px solid white;
  }
  </style>
  