<template>
        <div class="grid__calc">
          <article class="calc" >
            <h3 class="calc__title">Baker's Calculator</h3>

            <!-- an input field for the calculator; contains two inputs (grams, and percent, with the symbols for each as a span element after) -->
            <div class="calc__outer-wrap" v-for="quantity in quantities" v-bind:key="quantity.id" >
              <div class="wrap-two" v-show="quantity.show">
              <h6 class="calc__subtitle"> {{ quantity.name }}</h6>
              <div class="calc__wrap">
                <div class="calc__inner-wrap">
                  <input class="calc__input" type="text" :name="quantity.id"  :value="quantity.grams" :id="quantity.id">
                  <span class="calc__grams">g</span>
                </div>

                <div class="calc__inner-wrap calc__percent">
                  <input class="calc__input" type="text" :name="quantity.pId" :value="quantity.percent" :id="quantity.pId">
                  <span class="calc__grams">%</span>
                </div>
              </div>
            </div>
            </div>
            
            <div class="calc__button-container">
              <button type="button" name="button" class="calc__button">Add Ingredient</button>
            </div>
          </article>
        </div>
</template>

<script>
export default {
    data () {
        return {
            // the calculator's default data, including a "show" quality for the "add ingredient" element I'll add later
        quantities: [
          {
            name: "Flour",
            id: "flour",
            pId: "p-flour",
            grams: 500,
            percent: 100,
            show: true
          },
          {
            name: "Water",
            id: "water",
            pId: "p-water",
            grams: 375,
            percent: 75,
            show: true
          },
          {
            name: "Salt",
            id: "salt",
            pId: "p-salt",
            grams: 10,
            percent: 2.5,
            show: true
          },
          {
            name: "Yeast",
            id: "yeast",
            pId: "p-yeast",
            grams: 2.5,
            percent: .5,
            show: true
          },
          {
            name: "Leaven",
            id: "leaven",
            pId: "p-leaven",
            grams: 75,
            percent: 15,
            show: false
          }
        ]
        }
    }
}
</script>