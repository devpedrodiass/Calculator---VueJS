<template>
  <div class="w-screen h-screen begin bg-gray-700 flex flex-col justify-center">
    <p class="begin-title text-6xl ml-24 text-white">
      Press the button <br />
      to start the calculator
    </p>

    <div class="flex justify-center items-center mt-20 h-60">
      <button
        class="
          begin-btn
          rounded-lg
          p-5
          border-2 border-gray-800
          bg-purple-700
          text-5xl
          text-white
          
        "
        @click="openCalculatorPage"
      >
        Get Started
      </button>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "Begin",
  methods: {
    openCalculatorPage() {
      this.$router.push({
        path: "/calculator"
      })
    }
  },
};
</script>

<style>
.begin-btn {
  width: 650px;
  height: 150px;
  filter: drop-shadow(0 0 0.5rem black);
}
.begin-btn:hover {
  margin-bottom: 35px;
  transition-property: margin;
  transition-duration: 1s;
  transition-timing-function: ease;
}
</style>
