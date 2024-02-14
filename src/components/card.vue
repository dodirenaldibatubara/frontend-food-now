<script setup>
import { ref, computed, defineEmits } from "vue";

const props = defineProps(["pizza"]);
const emit = defineEmits(["selectPizza"]);

function selectPizza(pizza) {
  // console.log(pizza);
  emit("selectPizza", pizza);
}
const getImageName = computed(() => {
  if (props.pizza.id == 1) {
    return "Cheese Pizza.png";
  } else if (props.pizza.id == 2) {
    return "Veggie Pizza.png";
  } else if (props.pizza.id == 3) {
    return "Classical Pizza.png";
  }
});
</script>

<template>
  <div class="relative radio">
    <input
      @input="selectPizza(pizza)"
      type="radio"
      name="pizza"
      :id="pizza.id"
      class="hidden"
    />
    <label
      :for="pizza.id"
      class="group flex justify-center items-center xl:gap-[25px] lg:gap-[10px] md:gap-[5px] gap-[5px] xl:px-[20px] xl:py-[20px] lg:px-[10px] lg:py-[15px] md:px-[5px] md:py-[15px] px-[5px] py-[5px] border border-black border-opacity-10 rounded-2xl hover:bg-primary hover:bg-opacity-30 cursor-pointer bg-white"
    >
      <div>
        <img
          class="xl:w-[120px] lg:w-[70px] md:w-[50px] w-[50px] group-hover:rotate-[15deg] transition-all duration-300"
          :src="`/src/assets/image/pizza/${getImageName}`"
          alt="Cheese pizza image"
        />
      </div>

      <div class="lg:text-[16px] md:text-[14px] text-[12px]">
        <h4
          class="font-bold xl:text-[16px] lg:text-[14px] md:text-[12px] text-[10px]"
        >
          {{ pizza.name }}
        </h4>
        <div class="flex lg:gap-[5px] md:gap-[5px] gap-[3px]">
          <h5>${{ pizza.discount.final_price }}</h5>
          <h5
            v-if="pizza.discount.is_active"
            :class="{
              'line-through': pizza.discount.is_active,
              'opacity-50': pizza.discount.is_active,
            }"
          >
            ${{ pizza.price }}
          </h5>
        </div>
      </div>
    </label>

    <!-- ribbon -->
    <img
      v-if="pizza.discount.is_active"
      :src="'/src/assets/image/ribbon.svg'"
      alt="img-ribbon"
      class="xl:w-[100px] lg:w-[70px] md:w-[50px] w-[35px] absolute top-0 right-0"
    />
  </div>
</template>

<style>
/* .radio input ~ label {
  background-color: greenyellow;
  color: rgb(158, 146, 146);
} */
.radio input:checked ~ label {
  background-color: #e77e23;
  color: white;
}
</style>