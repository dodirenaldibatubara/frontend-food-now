<script setup>
import { ref, computed, defineEmits, watch } from "vue";
const props = defineProps(["topping", "selectedPizza", "checkSelectedTopping"]);
const emit = defineEmits(["selectTopping"]);

let selectedTopping = ref(null);

function selectTopping() {
  if (isAvailable.value) {
    emit("selectTopping", {
      topping: props.topping,
      selected: selectedTopping.value,
    });
  }
  emit("selectTopping", selectedTopping.value);
}

const isAvailable = computed(() => {
  if (props.selectedPizza) {
    return props.selectedPizza.toppings.includes(props.topping.id);
  }
});

// Reset checkbox
watch(
  () => props.checkSelectedTopping,
  () => {
    //   reset (uncheck all topping)
    if (!props.checkSelectedTopping.length) {
      selectedTopping.value = false;
    }
  }
);
</script>

<template>
  <div class="w-full flex justify-center items-center group">
    <input
      type="checkbox"
      :id="`topping${topping.id}`"
      :disabled="!isAvailable"
      v-model="selectedTopping"
      :value="props.topping"
      @change="selectTopping"
      class="hidden"
    />
    <label
      :for="`topping${topping.id}`"
      class="w-full font-bold xl:text-[16px] lg:text-[14px] md:text-[12px] text-[10px] group-hover:text-primary transition-all duration-200 text-center xl:py-[12px] lg:py-[8px] md:py-[8px] py-[5px] border border-black border-opacity-50 rounded-full cursor-pointer"
      :class="{
        'text-[#919191]': !isAvailable,
        'bg-[#E3E3E3]': !isAvailable,
        'border-none': !isAvailable,
        'cursor-default': !isAvailable,
        'group-hover:text-[#919191]': !isAvailable,
        'bg-primary': selectedTopping,
        'text-primary': selectedTopping,
        'border-primary': selectedTopping,
        'bg-opacity-30': selectedTopping,
      }"
      >{{ topping.name }}</label
    >
  </div>
</template>

