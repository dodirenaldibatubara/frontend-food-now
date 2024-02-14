<script setup>
import { ref, defineEmits, computed } from "vue";
import pizzaList from "/src/pizza-list.json";
import sizeList from "/src/size-list.json";
import toppingList from "/src/topping-list.json";
import Card from "/src/components/card.vue";
import MyFooter from "/src/components/my-footer.vue";
import Size from "/src/components/size.vue";
import Topping from "/src/components/topping.vue";
import PopupSuccess from "/src/components/popup-success.vue";
import Navbar from "/src/components/navbar.vue";

defineProps({
  // msg: String,
});

const dataPizzaList = ref(pizzaList.data);
let selectedPizza = ref(null);

const dataSizeList = ref(sizeList.data);
let selectedSize = ref(sizeList.data[0]);

const dataToppingList = ref(toppingList.data);
let selectedTopping = ref([]);

let popupSuccess = ref(false);

function selectPizza(pizza) {
  selectedPizza.value = pizza;
  selectedTopping.value = [];
}
function selectSize(size) {
  selectedSize.value = size;
  // console.log(selectedSize.value);
}
function showPopupSuccess() {
  popupSuccess.value = popupSuccess.value = true;
}
function closePopupSuccess() {
  popupSuccess.value = popupSuccess.value = false;
}

const updateSelectedToppings = (data) => {
  const { topping, selected } = data;
  if (selected) {
    selectedTopping.value.push(topping);
  } else {
    selectedTopping.value = selectedTopping.value.filter(
      (selected) => selected !== topping
    );
  }
};

const totalTopping = computed(() => {
  return selectedTopping.value.reduce((obj, item) => {
    return obj + parseInt(item.price);
  }, 0);
});

const totalPrice = computed(() => {
  const pizzaPrice = selectedPizza.value
    ? selectedPizza.value.discount.final_price
    : 0;
  const sizeExtraPrice = selectedSize.value
    ? selectedSize.value.extra_price
    : 0;

  return (
    parseFloat(totalTopping.value) +
    parseFloat(sizeExtraPrice) +
    parseFloat(pizzaPrice)
  );
});
</script>

<template>
  <div class="">
    <header
      class="w-full flex justify-center items-center xl:h-[540px] lg:h-[500px] md:h-[300px] h-[250px] bg-[url('/image/hero.png')] bg-cover"
    >
      <h1
        class="font-bold text-primary xl:text-[80px] lg:text-[72px] md:text-[46px] text-[26px]"
      >
        Pizza order
      </h1>

      <navbar></navbar>
    </header>

    <div
      class="container md:flex lg:gap-[20px] md:gap-[15px] gap-[10px] lg:mt-[80px] md:mt-[60px] mt-[40px]"
    >
      <div class="lg:w-9/12 md:w-9/12 w-full">
        <h2
          class="font-bold text-primary xl:text-[40px] lg:text-[36px] md:text-[32px] text-[26px]"
        >
          Choose your pizza
        </h2>

        <div
          class="grid lg:grid-cols-3 md:grid-cols-3 grid-cols-3 lg:gap-[20px] md:gap-[15px] gap-[5px] lg:mt-[30px] md:mt-[20px] mt-[10px]"
        >
          <card
            v-for="(pizza, index) in dataPizzaList"
            :key="index"
            :pizza="pizza"
            v-on:selectPizza="selectPizza"
          ></card>
        </div>

        <h2
          class="font-bold text-primary xl:text-[40px] lg:text-[36px] md:text-[32px] text-[26px] lg:mt-[120px] md:mt-[20px] mt-[10px]"
        >
          Custom Pizza
        </h2>

        <h4
          class="font-bold lg:text-[20px] md:text-[18px] text-[16px] lg:mt-[20px] md:mt-[20px] mt-[10px]"
        >
          Size
        </h4>

        <div
          class="flex lg:gap-[20px] md:gap-[15px] gap-[10px] lg:mt-[20px] md:mt-[15px] mt-[10px]"
        >
          <size
            v-for="(size, index) in dataSizeList"
            :key="index"
            :size="size"
            v-on:selectSize="selectSize"
          ></size>
        </div>

        <!-- {{ selectedTopping }} -->
        <!-- toppings -->
        <div class="lg:mt-[30px] md:mt-[20px] mt-[10px]">
          <h4 class="font-bold lg:text-[20px] md:text-[18px] text-[16px]">
            Toppings
          </h4>

          <div
            class="grid lg:grid-cols-6 md:grid-cols-4 grid-cols-3 xl:gap-[16px] lg:gap-[10px] md:gap-[10px] gap-[5px] lg:mt-[20px] md:mt-[20px] mt-[10px]"
          >
            <topping
              v-for="(topping, index) in dataToppingList"
              :key="index"
              :topping="topping"
              :selectedPizza="selectedPizza"
              :checkSelectedTopping="selectedTopping"
              v-on:selectTopping="updateSelectedToppings"
            ></topping>
          </div>
        </div>

        <!-- End toppings -->
      </div>

      <div
        class="lg:w-3/12 md:w-3/12 w-10/12 md:mt-0 mt-[20px] md:mx-0 mx-auto"
      >
        <div
          class="shadow-md rounded-2xl lg:p-[20px] md:p-[15px] p-[10px] bg-white"
        >
          <h2
            class="font-bold xl:text-[24px] lg:text-[20px] md:text-[15px] text-[14px] text-primary"
          >
            Payment summary
          </h2>

          <div
            class="flex flex-col lg:gap-[14px] lg:mt-[20px] md:mt-[20px] mt-[20px]"
          >
            <div
              class="flex justify-between lg:mt-[15px] md:mt-[10px] mt-[10px]"
            >
              <h4 v-if="selectedPizza" class="text-[#626F79]">
                {{ selectedPizza.name }}
              </h4>
              <h4 v-if="selectedPizza" class="text-[#333333]">
                {{ selectedPizza.discount.final_price }}$
              </h4>
            </div>
            <div class="flex justify-between items-center">
              <div class="flex text-[#626F79]">
                <h4 class="">Size -</h4>
                <h4 class="">{{ selectedSize.name }}</h4>
              </div>

              <h4 class="text-[#333333]">{{ selectedSize.extra_price }}$</h4>
            </div>
            <!-- toppings -->
            <div v-for="(topping, index) in selectedTopping" :key="index">
              <div class="flex justify-between items-center">
                <div class="flex text-[#626F79]">
                  <h4 class="">{{ topping.name }}</h4>
                </div>

                <h4 class="text-[#333333]">{{ topping.price }}$</h4>
              </div>
            </div>
            <!-- End toppings -->
          </div>

          <hr class="lg:my-[20px] md:my-[15px] my-[10px]" />

          <div
            class="flex justify-between lg:text-[22px] md:text-[18px] text-[18px] lg:mt-[10px] md:mt-[10px] mt-[10px]"
          >
            <h4 class="text-[#333333]">Total Price</h4>
            <h4 class="font-bold text-primary">${{ totalPrice }}</h4>
          </div>

          <div>
            <button
              @click="showPopupSuccess"
              class="w-full font-bold text-white lg:text-[14px] md:text-[16px] text-[14px] lg:px-[24px] lg:py-[8px] md:px-[0px] md:py-[6px] px-[24px] py-[8px] lg:mt-[20px] md:mt-[10px] mt-[10px] rounded-full bg-primary hover:bg-[#C16515] transition-all duration-100"
            >
              Order now
            </button>
          </div>
        </div>
      </div>
    </div>

    <div class="container xl:mt-[130px] lg:mt-[100px] md:mt-[80px] mt-[30px]">
      <hr class="" />
    </div>

    <popup-success
      v-if="popupSuccess"
      v-on:closePopupSuccess="closePopupSuccess"
    ></popup-success>

    <my-footer></my-footer>
  </div>
</template>


