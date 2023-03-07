
<template>
  <div id="app">
    <main class="main">
      <!-- image carousel with three images and controls -->
      <h3>Community Bread Gallery</h3>
        <b-carousel
          id="carousel-1"
          v-model="slide"
          :interval="6000"
          controls
          indicators
          background="$background-beige"
          img-width="1024"
          img-height="480"
          style="text-shadow: 1px 1px 2px #333;"
          @sliding-start="onSlideStart"
          @sliding-end="onSlideEnd"
        >
          <!-- picture component, looping through array of images -->
          <Picture 
            v-for="(pic, index) in pics" 
            :key="index" 
            :picture="pic.image" 
            :alt-text="pic.text"
            :img-title="pic.title"
            :class="{ active: index === 0}"
          >
          </Picture>
        </b-carousel>
    </main>
  </div>
</template>

<script>
    import Picture from "../components/PicView.vue";

    export default {
    name: 'app',
    components: {
      Picture
    },
    data () {
      return {
        // pictures with alt text
        pics: [
          {
            image: "bread-2.jpeg",
            text: "a loaf of bread from above",
            title: "Seeded Rye Boule"
          },
          {
            image: "bread-3.jpeg",
            text: "the interior of a loaf of bread",
            title: "Caraway & Coriander Sourdough"
          },
          {
            image: "bread-4.jpeg",
            text: "a seeded loaf of bread",
            title: "Seeded Buckwheat Loaf"
          }
        ],
        slide: 0,
        sliding: null
      }
    },
    methods: {
        onSlideStart(slide) {
        this.sliding = true
      },
      onSlideEnd(slide) {
        this.sliding = false
      }
    },
    head () {
      return {
        titleTemplate: 'Community Images — %s',
        meta: [
          {
            hid: 'description', 
            name: 'description',
            content: "Users post photographs of bread."
        }

        ]
      }
    }
  }
</script>

