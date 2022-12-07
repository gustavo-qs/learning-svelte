<script>
// @ts-nocheck
let equation = '';

  function select(number){
    let screen = document.getElementById('calcScreen');
    if (number === 'D') {
      screen.value = screen.value.slice(0, -1);
    } else if(number == 'C') {
      screen.value = '';
      equation = ''; 
    } else if(number == '=') {
      screen.value = eval(equation);
      equation = screen.value;
    } else if(number == 'X') {
      equation = equation && equation + ' * ';
      screen.value = '';
    } else if(number == '+') {
      equation = equation && equation + ' + ';
      screen.value = '';
    } else if(number == '-') {
      equation = equation && equation + ' - ';
      screen.value = '';
    } else if(number == '/') {
      equation = equation && equation + ' / ';
      screen.value = '';
    } else {
      equation ? screen.value += number : screen.value = number;
      equation += number;
    }
  }
</script>

<main class="sc" style="flex-direction: column;">
  <div class="screen-bg">
    <input id="calcScreen" readonly dir="rtl"  class="screen" type="text">
  </div>

  <div>
    { #each [[7, 8, 9, 'D', 'C' ], [4, 5, 6, 'X', '/'], [1, 2, 3, '+', '-'], [0, '.', '=']] as row }
      <div class="sc">
        {#each row as number}
          {#if number === 'D' || number === 'C'}
            <button on:click={() => select(number)} class="delBtn" title={`${number == 'D' ? 'Deletar' : 'Limpar'}`}>{number}</button>
          {:else}
            <button on:click={() => select(number)}>{number}</button>
          {/if}
        {/each}
      </div>
    {/each}
  </div>

</main>

<style>
@import url('https://fonts.cdnfonts.com/css/digital-7-mono');
  .screen {
    background-color: #d6e1e3;
    color: #0b1313;
    border-radius: 5px;
    font-size: 45pt;
    margin: 1rem;
    width: 90%;
    font-family: 'Digital-7 Mono', sans-serif;
    font-family: 'Digital-7', sans-serif;
    font-family: 'Digital-7 Italic', sans-serif;  
}
  .screen-bg {
    background-color: #000000;
    margin-top: 1.5rem;
    border-radius: 5px;
    width: 520px
  }
  .sc {
    justify-content: center;
    align-items: center;
    display: flex;
  }
  button {
    border-radius: 5px;
    font-size: 20pt;
    margin: 1rem;
    width: 100%;
    font-family: 'Digital-7 Mono', sans-serif;
    font-family: 'Digital-7', sans-serif;
    font-family: 'Digital-7 Italic', sans-serif;  
  }
  button:hover {
    background-color: #282b2b;
    color: #949bae;
  }

  .delBtn {
    background-color: #e74c3c;
    color: #ffffff;
  }
  .delBtn:hover {
    background-color: #c0392b;
    color: #ffffff;
  }
</style>