<script setup>
import { ref, computed, defineEmits } from "vue";

let mobileMenu = ref(false);

function showMobileMenu() {
  mobileMenu.value = !mobileMenu.value;
  //   console.log(mobileMenu.value);
}
</script>

<template>
  <nav
    class="container fixed w-full flex justify-between items-center top-0 xl:min-h-[100px] lg:min-h-[100px] md:min-h-[80px] min-h-[50px]"
  >
    <div class="lg:w-[180px] md:w-[140px] w-[80px]">
      <img :src="'/src/assets/image/logo.svg'" alt="logo" />
    </div>

    <div class="text-white">
      <ul
        class="lg:flex hidden lg:gap-[20px] md:gap-[15px] gap-[10px] font-bold lg:text-[14px] md:text-[16px] text-[14px]"
      >
        <li class="hover:text-primary cursor-pointer">Home</li>
        <li class="hover:text-primary cursor-pointer text-primary">Order</li>
        <li class="hover:text-primary cursor-pointer">About</li>
        <li class="hover:text-primary cursor-pointer">Blog</li>
        <li class="hover:text-primary cursor-pointer">Contact us</li>
      </ul>
    </div>

    <div
      class="lg:flex hidden items-center lg:gap-[20px] md:gap-[15px] gap-[10px]"
    >
      <button
        class="font-bold text-white lg:text-[14px] md:text-[16px] text-[14px]"
      >
        Login
      </button>
      <button
        class="font-bold text-white lg:text-[14px] md:text-[16px] text-[14px] lg:px-[24px] lg:py-[8px] rounded-full bg-primary hover:bg-[#C16515]"
      >
        Register
      </button>
    </div>

    <!-- toggle button -->
    <button @click="showMobileMenu" class="lg:hidden">
      <img
        :src="'/src/assets/image/hamburger-menu-white.svg'"
        alt="hamburger-menu"
        class="w-7 nav-mobile"
      />
      <!-- <img
          :src="require(`assets/image/close-button.png`)"
          alt="hamburger-menu"
          class="w-7 nav-mobile"
        /> -->
    </button>

    <!-- End toggle button -->
  </nav>

  <!-- Mobile Navbar -->
  <div
    v-if="mobileMenu == true"
    class="container lg:hidden fixed w-full md:top-[80px] top-[50px]"
  >
    <div class="bg-white rounded-sm">
      <ul
        class="flex flex-col md:gap-[10px] gap-[10px] font-bold lg:text-[14px] md:text-[16px] text-[14px]"
      >
        <li
          class="hover:text-primary hover:bg-slate-200 transition-all duration-300 cursor-pointer text-center"
        >
          <a href="">Home</a>
        </li>
        <li
          class="hover:text-primary hover:bg-slate-200 transition-all duration-300 cursor-pointer text-center"
        >
          <a href="">Order</a>
        </li>
        <li
          class="hover:text-primary hover:bg-slate-200 transition-all duration-300 cursor-pointer text-center"
        >
          <a href="">About</a>
        </li>
        <li
          class="hover:text-primary hover:bg-slate-200 transition-all duration-300 cursor-pointer text-center"
        >
          <a href="">Blog</a>
        </li>
        <li
          class="hover:text-primary hover:bg-slate-200 transition-all duration-300 cursor-pointer text-center"
        >
          <a href="">Contact us</a>
        </li>
      </ul>
    </div>
  </div>
  <!-- End mobile navbar -->
</template>

