<script setup>
import { ref, computed, defineEmits } from "vue";

const emit = defineEmits(["closePopupSuccess"]);

function closePopupSuccess() {
  emit("closePopupSuccess");
}
</script>

<template>
  <div>
    <div
      class="fixed left-0 top-0 z-40 w-full h-[100vh] flex justify-center items-center bg-black bg-opacity-30"
    >
      <div
        class="relative xl:w-3/12 lg:w-4/12 md:w-5/12 w-8/12 xl:p-[28px] lg:p-[20px] md:p-[20px] p-[15px] rounded-lg bg-[#FFFFFF] shadow-sm"
      >
        <div class="flex justify-center">
          <img
            class="lg:w-[100px] md:w-[80px] w-[60px]"
            :src="'/image/icons/ic-success.svg'"
            alt="ic-success"
          />
        </div>

        <div class="text-center lg:mt-[15px] md:mt-[12px] mt-[10px]">
          <h4 class="font-semibold lg:text-[20px] md:text-[18px] text-[16px]">
            Order Success
          </h4>

          <p class="text-[#333333] lg:text-[18px] md:text-[16px] text-[14px]">
            Thank you, we have received your order successfully.
          </p>
        </div>

        <div class="lg:mt-[20px] md:mt-[15px] mt-[10px]">
          <button
            @click="closePopupSuccess"
            class="w-full font-bold lg:px-[12px] lg:py-[10px] md:py-[6px] py-[4px] text-center text-white rounded-full hover:bg-[#C16515] transition-all duration-200 bg-primary"
          >
            close
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

