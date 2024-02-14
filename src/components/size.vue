<script setup>
import { ref, computed, defineEmits } from "vue";
const props = defineProps(["size"]);
const emit = defineEmits(["selectSize"]);

function selectSize(size) {
  //   console.log(size);
  emit("selectSize", size);
}
</script>

<template>
  <div class="flex items-center lg:gap-[5px] md:gap-[5px] gap-[5px]">
    <input
      @input="selectSize(size)"
      :id="`size${size.id}`"
      :checked="size.id === 1"
      type="radio"
      name="size"
      class="lg:w-[14px] lg:h-[14px] cursor-pointer checked:cursor-default accent-primary"
    />
    <label
      :for="`size${size.id}`"
      class="lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer checked:cursor-default"
      >{{ size.name }}
      <span v-if="size.name == 'Medium'" class="text-[#333333] opacity-50"
        >(+5$)</span
      >
      <span v-if="size.name == 'Large'" class="text-[#333333] opacity-50"
        >(+7$)</span
      >
    </label>
  </div>
</template>

