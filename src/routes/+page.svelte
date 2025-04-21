<script lang="ts">
  import "../app.scss";

  let num_input: String = "";
  let first_input: String = "";

  function display(num: string): void {
    if (
      num_input === "Please enter number" ||
      num_input === "Please close the bracket" ||
      num_input === "Please close the bracket"
    )
      num_input = "";
    num_input += num;
  }

  function clear_display(): void {
    num_input = "";
  }

  function fn_btn(btn: string): void {
    first_input = `${num_input}${btn}`;
    num_input = "";
  }

  function fn_summation(): void {
    try {
      num_input = eval(String(first_input) + String(num_input));
    } catch (error) {
      if (num_input.at(0) === "(" && num_input.at(-1) === ")")
        num_input = "Please enter number";
      else if (num_input.at(0) === "(") num_input = "Please close the bracket";
      else if (num_input.at(-1) === ")") num_input = "Please close the bracket";
    }
  }
</script>

<main>
  <div class="calculator">
    <div class="display">
      <input type="text" value={num_input} placeholder="0" disabled />
    </div>
    <div class="button">
      <div class="btn-number">
        <button onclick={() => display("(")}>(</button>
        <button onclick={() => display(")")}>)</button>
        <button class="secondary" onclick={() => clear_display()}>C</button>
        <button onclick={() => display("7")}>7</button>
        <button onclick={() => display("8")}>8</button>
        <button onclick={() => display("9")}>9</button>
        <button onclick={() => display("4")}>4</button>
        <button onclick={() => display("5")}>5</button>
        <button onclick={() => display("6")}>6</button>
        <button onclick={() => display("3")}>3</button>
        <button onclick={() => display("2")}>2</button>
        <button onclick={() => display("1")}>1</button>
        <button onclick={() => display("0")}>0</button>
        <button onclick={() => display("00")}>00</button>
        <button onclick={() => display(".")}>.</button>
      </div>
      <div class="btn-fn">
        <button class="secondary" onclick={() => fn_btn("/")}>/</button>
        <button class="secondary" onclick={() => fn_btn("*")}>x</button>
        <button class="secondary" onclick={() => fn_btn("-")}>-</button>
        <button class="secondary" onclick={() => fn_btn("+")}>+</button>
        <button class="contrast" onclick={() => fn_summation()}>=</button>
      </div>
    </div>
  </div>
</main>

<style>
  main {
    display: flex;
    justify-content: center;
    padding: 1rem;
  }

  .display {
    input {
      text-align: right;
    }
  }

  .calculator {
    display: grid;
    border: 2px solid gray;
    border-radius: 10px;
    padding: 1rem;

    .button {
      display: flex;
      justify-content: center;
      .btn-number {
        display: grid;
        gap: 0.5rem;
        grid-template-columns: repeat(3, 1fr);
        margin-right: 0.5rem;
      }
      .btn-fn {
        display: grid;
        gap: 0.5rem;
      }
    }
  }
</style>
