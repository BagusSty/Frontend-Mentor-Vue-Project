<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();

const email = ref("");
const validEmail = ref(true);
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

const lists = [
  {
    img: "/assets/images/icon-list.svg",
    text: "Product discovery and building what matters",
  },
  {
    img: "/assets/images/icon-list.svg",
    text: "measuring to ensure updates are a success",
  },
  {
    img: "/assets/images/icon-list.svg",
    text: "And much more!",
  },
];

function subscribe() {
  if (email.value === "" || !emailRegex.test(email.value)) {
    validEmail.value = false;
  } else {
    validEmail.value = true;
    router.push({ name: "success" });
  }
}
</script>

<template>
  <main class="app">
    <div
      class="flex justify-center items-center h-screen sm:bg-darkSlateGrey bg-white"
    >
      <div class="max-w-3xl sm:w-full bg-white p-5 sm:rounded-3xl">
        <div class="sm:flex">
          <div class="sm:hidden block w-full">
            <img src="/assets/images/illustration-sign-up-mobile.svg" alt="" />
          </div>
          <div class="sm:w-1/2 sm:p-6 mt-2 sm:my-4 sm:mr-4">
            <h1
              class="sm:text-4xl text-2xl font-bold sm:text-center text-left text-darkSlateGrey"
            >
              Stay Updated!
            </h1>
            <p class="text-darkSlateGrey text-sm text-justify font-thin my-3">
              Join 60,000+ product managers receiving monthly updates on:
            </p>
            <ul class="sm:my-5">
              <li
                class="flex sm:my-4 mt-2"
                :key="index"
                v-for="(list, index) in lists"
              >
                <img class="mr-4" src="/assets/images/icon-list.svg" alt="" />
                <p class="text-sm text-darkSlateGrey">{{ list.text }}</p>
              </li>
            </ul>
            <div class="sm:mt-10 mt-2">
              <div class="flex justify-between">
                <label
                  class="block text-xs text-left font-bold mb-2 text-darkSlateGrey"
                  for="email"
                  >Email Address</label
                >
                <span
                  class="text-tomato text-xs text-left font-bold mb-2"
                  v-if="!validEmail"
                  >Valid email required</span
                >
              </div>
              <input
                class="text-semibold placeholder:text-lightGrey sm:p-3 p-2 w-full border-lightGrey border cursor-pointer rounded-lg hover:border-darkSlateGrey"
                :class="{
                  ' placeholder:text-tomato bg-red-100 border-tomato':
                    !validEmail,
                }"
                placeholder="email@company.com"
                v-model="email"
                type="email"
                name="email"
                id="email"
              />
            </div>
            <div class="sm:mt-5 mt-2">
              <button
                class="text-center sm:text-md text-sm text-white hover:shadow-lg bg-darkSlateGrey hover:bg-tomato w-full rounded-lg p-3"
                type="submit"
                @click="subscribe()"
              >
                Subscribe to monthly newsletter
              </button>
            </div>
          </div>
          <div class="w-1/2 hidden sm:block">
            <img
              class="w-full h-auto"
              src="/assets/images/illustration-sign-up-desktop.svg"
              alt="logo"
            />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
