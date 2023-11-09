<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();

function dismiss() {
  router.push({ name: "login" });
}
</script>
<template>
  <main class="app">
    <div
      class="flex justify-center items-center h-screen sm:bg-darkSlateGrey bg-white"
    >
      <div class="max-w-lg sm:w-full bg-white p-12 sm:rounded-3xl">
        <img class="mb-5" src="/assets/images/icon-success.svg" alt="" />
        <h1 class="text-6xl font-bold mb-4 text-darkSlateGrey">
          Thanks for subscribing!
        </h1>
        <p class="text-darkSlateGrey mb-4">
          A confirmation email has been sent to <b>ash@lormcompany.com</b>.
          Please open it and click the button inside to confirm your
          subscription
        </p>
        <div class="sm:mt-5 mt-2">
          <button
            class="text-center sm:text-md text-sm text-white bg-darkSlateGrey hover:shadow-lg hover:bg-tomato w-full rounded-lg p-4"
            type="submit"
            @click="dismiss()"
          >
            Dismiss message
          </button>
        </div>
      </div>
    </div>
  </main>
</template>
