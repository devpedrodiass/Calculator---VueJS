<template>
  <div
    class="
      calculator
      w-screen
      h-screen
      flex flex-col
      justify-around
      text-center text-2xl
    "
  >
    <div class="calculator-header self-start ml-5 text-white text-2xl">
      <button
        class="calculator-header-btn w-52 h-16 rounded-full"
        @click="backToHome"
      >
        back to home
      </button>
    </div>
    <div class="flex flex-col items-center justify-center">
      <div class="calculator-display">
        <input
          type="text"
          class="
            text-center
            bg-gray-500
            border-2 border-gray-700
            rounded-full
            p-4
            w-80
            h-16
            text-white
          "
          disabled
          v-model="numberDisplay"
        />
        <input
          type="text"
          class="
            text-center
            bg-gray-500
            border-2 border-gray-700
            rounded-full
            p-4
            w-16
            h-16
            text-white
          "
          disabled
          v-model="clickedOperation"
        />
      </div>

      <div class="calculator-numbers">
        <div class="flex flex-row">
          <div>
            <div>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="deleteNumber('all')"
              >
                C
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="deleteNumber('one')"
              >
                CE
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="submit"
              >
                =
              </button>
            </div>
            <div>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number1)"
              >
                1
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number2)"
              >
                2
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number3)"
              >
                3
              </button>
            </div>
            <div>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number4)"
              >
                4
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number5)"
              >
                5
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number6)"
              >
                6
              </button>
            </div>
            <div>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number7)"
              >
                7
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number8)"
              >
                8
              </button>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number9)"
              >
                9
              </button>
            </div>
            <div>
              <button
                class="
                  text-white
                  rounded-full
                  border-2 border-purple-900
                  bg-purple-700
                  w-16
                  h-16
                  m-2
                "
                @click="addNumber(number0)"
              >
                0
              </button>
            </div>
          </div>

          <div class="flex flex-col">
            <button
              class="
                text-white
                rounded-full
                border-2 border-purple-900
                bg-purple-700
                w-16
                h-16
                m-2
              "
              @click="addOperation(operation1)"
            >
              +
            </button>
            <button
              class="
                text-white
                rounded-full
                border-2 border-purple-900
                bg-purple-700
                w-16
                h-16
                m-2
              "
              @click="addOperation(operation2)"
            >
              -
            </button>
            <button
              class="
                text-white
                rounded-full
                border-2 border-purple-900
                bg-purple-700
                w-16
                h-16
                m-2
              "
              @click="addOperation(operation3)"
            >
              /
            </button>
            <button
              class="
                text-white
                rounded-full
                border-2 border-purple-900
                bg-purple-700
                w-16
                h-16
                m-2
              "
              @click="addOperation(operation4)"
            >
              x
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "calculator",
  data() {
    return {
      firstClickedNumber: "",
      secondClickedNumber: "",
      clickedOperation: "",
      numberDisplay: "Select a number",
      number1: 1,
      number2: 2,
      number3: 3,
      number4: 4,
      number5: 5,
      number6: 6,
      number7: 7,
      number8: 8,
      number9: 9,
      number0: 0,
      operation1: "+",
      operation2: "-",
      operation3: "/",
      operation4: "x",
      submitted: false,
    };
  },
  methods: {
    backToHome() {
      this.$router.push({
        path: "/",
      });
    },
    addNumber(number) {
      if (this.numberDisplay == "Select a number") {
        this.numberDisplay = "";
        if (this.clickedOperation == "") {
          this.numberDisplay = this.numberDisplay.concat(number);
          this.firstClickedNumber = this.numberDisplay;
          console.log("entrou");
        } else {
          this.numberDisplay = this.numberDisplay.concat(number);
          this.secondClickedNumber = this.numberDisplay;
        }
      } else {
        if (this.clickedOperation == "") {
          this.numberDisplay = this.numberDisplay.concat(number);
          this.firstClickedNumber = this.numberDisplay;
          console.log("entrou");
        } else {
          this.numberDisplay = this.numberDisplay.concat(number);
          this.secondClickedNumber = this.numberDisplay;
        }
      }
    },
    addOperation(operation) {
      this.numberDisplay = "";
      this.clickedOperation = operation;
    },
    deleteNumber(quantity) {
      if (this.numberDisplay !== "Select a number") {
        if (quantity == "one") {
          let numberDisplay = String(this.numberDisplay);
          this.numberDisplay = numberDisplay.substring(
            0,
            numberDisplay.length - 1
          );
          this.clickedOperation = "";
          this.submitted = false;
        } else {
          this.numberDisplay = "";
          this.clickedOperation = "";
          this.submitted = false;
        }
      }
    },
    submit() {
      console.log("entrou");
      let number1 = Number(this.firstClickedNumber);
      let number2 = Number(this.secondClickedNumber);
      let operation = this.clickedOperation;

      console.log(number1);
      console.log(number2);

      if (this.submitted !== true) {
        switch (operation) {
          case "+":
            this.numberDisplay = number1 + number2;
            this.submitted = true;
            break;
          case "-":
            this.numberDisplay = number1 - number2;
            this.submitted = true;
            break;
          case "/":
            this.numberDisplay = number1 / number2;
            this.submitted = true;
            break;
          case "x":
            this.numberDisplay = number1 * number2;
            this.submitted = true;
            break;

          default:
            break;
        }
      } else {
        switch (operation) {
          case "+":
            this.numberDisplay = this.numberDisplay + number2;
            this.submitted = true;
            break;
          case "-":
            this.numberDisplay = this.numberDisplay - number2;
            this.submitted = true;
            break;
          case "/":
            this.numberDisplay = this.numberDisplay / number2;
            this.submitted = true;
            break;
          case "x":
            this.numberDisplay = this.numberDisplay * number2;
            this.submitted = true;
            break;

          default:
            break;
        }
      }
    },
  },
};
</script>

<style>
.calculator-header-btn:hover {
  --tw-bg-opacity: 1;
  background-color: rgba(75, 85, 99, var(--tw-bg-opacity));
  transition: background-color 1s;
}
.calculator-numbers button:hover {
  --tw-border-opacity: 1;
  background-color: rgba(76, 29, 149, var(--tw-border-opacity)) !important;
  transition: background-color 0.2s;
}
</style>
