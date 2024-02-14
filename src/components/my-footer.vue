<script setup>
import { ref, computed, defineEmits } from "vue";
</script>

<template>
  <footer class="container lg:mt-[40px] md:mt-[30px] mt-[20px]">
    <div class="grid lg:grid-cols-4 md:grid-cols-4 grid-cols-2">
      <div class="">
        <div class="lg:w-[180px] md:w-[140px] w-[80px]">
          <img :src="'/image/logo-alt.svg'" alt="logo" />
        </div>

        <div
          class="lg:gap-[20px] md:gap-[15px] gap-[10px] lg:mt-[50px] md:mt-[30px] mt-[20px]"
        >
          <h5
            class="font-bold text-primary lg:text-[20px] md:text-[18px] text-[16px]"
          >
            Find Us :
          </h5>

          <div
            class="flex lg:gap-[20px] md:gap-[15px] gap-[10px] lg:mt-[20px] md:mt-[15px] mt-[10px]"
          >
            <a
              href="https://www.facebook.com/"
              class="flex justify-center items-center md:w-[40px] w-[30px] aspect-square lg:p-[2px] md:p-[2px] p-[2px] border border-primary rounded-full hover:bg-primary hover:bg-opacity-30"
            >
              <img
                :src="'/image/icons/facebook.svg'"
                alt="ic-facebook"
                class=""
              />
            </a>

            <a
              href="https://www.instagram.com/accounts/login/?hl=en"
              class="flex justify-center items-center md:w-[40px] w-[30px] aspect-square lg:p-[2px] md:p-[2px] border border-primary rounded-full hover:bg-primary hover:bg-opacity-30"
            >
              <img
                :src="'/image/icons/instagram.svg'"
                alt="ic-instagram"
                class=""
              />
            </a>

            <a
              href="https://www.youtube.com/"
              class="flex justify-center items-center md:w-[40px] w-[30px] aspect-square lg:p-[2px] md:p-[2px] border border-primary rounded-full hover:bg-primary hover:bg-opacity-30"
            >
              <img
                :src="'/image/icons/youtube.svg'"
                alt="ic-youtube"
                class=""
              />
            </a>
          </div>
        </div>
      </div>

      <div class="">
        <h5
          class="font-bold text-primary lg:text-[20px] md:text-[18px] text-[16px]"
        >
          Navigation
        </h5>

        <div
          class="grid lg:grid-cols-2 md:grid-cols-2 grid-cols-2 lg:gap-y-[12px] lg:mt-[20px] md:mt-[15px] mt-[10px]"
        >
          <a
            href=""
            class="text-[#4D4D4D] lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer hover:text-primary"
            >Home</a
          >
          <a
            href=""
            class="text-[#4D4D4D] lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer hover:text-primary"
            >Contact</a
          >
          <a
            href=""
            class="text-[#4D4D4D] lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer hover:text-primary"
            >Order</a
          >
          <a
            href=""
            class="text-[#4D4D4D] lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer hover:text-primary"
            >Login</a
          >
          <a
            href=""
            class="text-[#4D4D4D] lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer hover:text-primary"
            >About</a
          >
          <a
            href=""
            class="text-[#4D4D4D] lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer hover:text-primary"
            >Register</a
          >
          <a
            href=""
            class="text-[#4D4D4D] lg:text-[16px] md:text-[14px] text-[12px] cursor-pointer hover:text-primary"
            >Blog</a
          >
        </div>
      </div>

      <div class="md:mt-[0px] mt-[20px]">
        <h5
          class="font-bold text-primary lg:text-[20px] md:text-[18px] text-[16px]"
        >
          Contact
        </h5>

        <div
          class="lg:mt-[20px] md:mt-[15px] mt-[10px] flex flex-col lg:gap-[16px] md:gap-[14px] gap-[12px]"
        >
          <div class="flex items-center lg:gap-[5px] md:gap-[5px] gap-[5px]">
            <img :src="'/image/icons/mail.svg'" alt="ic-mail" />
            <a
              href="mailto:Food.now@mail.com"
              class="text-[#333333] lg:text-[16px] md:text-[14px] text-[12px]"
            >
              Food.now@mail.com
            </a>
          </div>
          <div class="flex items-center lg:gap-[5px] md:gap-[5px] gap-[5px]">
            <img :src="'/image/icons/phone.svg'" alt="ic-phone" />
            <h6
              class="text-[#333333] lg:text-[16px] md:text-[14px] text-[12px]"
            >
              +62848477102943
            </h6>
          </div>
          <div class="flex items-center lg:gap-[5px] md:gap-[5px] gap-[5px]">
            <img :src="'/image/icons/whatsapp.svg'" alt="ic-whatsapp" />
            <a
              a
              href="https://api.whatsapp.com/send?phone=08184938494"
              class="text-[#333333] lg:text-[16px] md:text-[14px] text-[12px]"
            >
              +628184938494
            </a>
          </div>
        </div>
      </div>

      <div class="md:mt-[0px] mt-[20px]">
        <h5
          class="font-bold text-primary lg:text-[20px] md:text-[18px] text-[16px]"
        >
          Location
        </h5>

        <div
          class="flex items-start lg:gap-[5px] md:gap-[5px] gap-[5px] lg:mt-[20px] md:mt-[15px] mt-[10px]"
        >
          <img :src="'/image/icons/location.svg'" alt="location-ic" />

          <h6 class="text-[#333333] lg:text-[16px] md:text-[14px] text-[12px]">
            Jl. Raya Kerobokan Br Taman, Kuta No.98, Kerobokan Kelod, Kec. Kuta
            Utara, Kabupaten Badung, Bali 80361
          </h6>
        </div>
      </div>
    </div>

    <hr class="lg:mt-[50px] md:mt-[40px] mt-[30px]" />

    <div class="flex justify-center">
      <p
        class="lg:w-7/12 md:w-8/12 w-10/12 text-center text-[#333333] lg:text-[14px] md:text-[12px] text-[10px] lg:my-[20px] md:my-[15px] my-[10px]"
      >
        Copyright © 2022 Foodnow. All Rights Reserved. Powered by PT. Timedoor
        Indonesia. | Privacy Policy This site is protected by reCAPTCHA and the
        Google Privacy Policy and Terms of Service apply.
      </p>
    </div>
  </footer>
</template>

