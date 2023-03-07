<template>
  <div id="app">
    <main class="main__recipes">

      <!-- recipe of the day card (same as index) -->
      <div class="container">
        <div class="row">
          <div class="col-12 p-5">
            <TodayRecipe></TodayRecipe>
          </div>
        </div>

        <!-- a bottom row with more recipes -->
        <div class="row">
          <div class="col-lg-8 col-12 p-3">
            <article class="recipes">
              <h3 class="recipes__title">Base Recipes</h3>
              <ul>
                <li class="recipes__item" v-for="(recipe, id) in baseRecipes" :key="id">
                  <a :href="recipe.link" class="recipes__link"> >> {{ recipe.name }}</a>
                </li>
              </ul>

            </article>
          </div>

          <!-- extra recipes card opens when button is clicked -->
          <div class="col-lg-8 col-12 p-3">
            <article class="recipes" v-if="!show">
              <h3 class="recipes__title">More Recipes</h3>
              <ul>
                <li class="recipes__item" v-for="(recipe, id) in xRecipes" :key="id">
                  <a :href="recipe.link" class="recipes__link"> >> {{recipe.name}}</a>
                </li>
              </ul>
            </article>

            <!-- button that hides or shows more recipes -->
            <div class="recipes__button-wrap">
              <button class="recipe__button" @click="buttonText('See More Recipes', 'Hide Recipes')" ref="buttonToggle">See More Recipes</button>
            </div>
          </div>
        </div>
      </div>

    </main>
  </div>
</template>

<script>
import buttonText from '@/components/mixins.vue';
import TodayRecipe from '@/components/TodayRecipe.vue'

export default {
    name: 'app',
    components: {
      TodayRecipe
    },
    mixins: [buttonText],
    data () {
      return {

        // data for base and extra recipes
        baseRecipes: [
          {
            name: "Base Sourdough",
            link: "#"
          },
          {
            name: "Base White Bread",
            link: "#"
          },
          {
            name: "Base Focaccia",
            link: "#"
          }
        ],
        xRecipes: [
          {
            name: "Spiced Rye",
            link: "#"
          },
          {
            name: "Poolish White Bread",
            link: "#"
          },
          {
            name: "Naan",
            link: "#"
          },
          {
            name: "Pita",
            link: "#"
          }
        ]
      }
    },
    head () {
      return {
        titleTemplate: 'Recipes — %s',
        meta: [
          {
            hid: 'description', 
            name: 'description',
            content: "A library of bread recipes."
        }

        ]
      }
    }
  }
</script>