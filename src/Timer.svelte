<script>
  import Progress from './Progress.svelte';
  const totalSeconds = 20;
  let secondsLeft = totalSeconds;
  let isRunning = false;

  $:progress = ((totalSeconds - secondsLeft) / totalSeconds) * 100;

  function startTimer(){
    const timer = setInterval(() => {
      isRunning = true;
      secondsLeft -=1;
      if (secondsLeft == 0){
        clearInterval(timer);
        isRunning = false;
        secondsLeft = totalSeconts;
      };
    }, 1000);
  };

</script>

<style>
  h2{
    margin: 0;
  }
  button{
    background-color: #0078d4;
    width: 100%;
    margin: 10px 0;
  }
  button[disabled]{
    background-color: #f2f2f2;
    color: #333;
    cursor: not-allowed;
  }
</style>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">
    Seconds left: {secondsLeft}
  </h2>
  <Progress {progress} />
  <button disabled={isRunning} class="start" on:click={startTimer}>
    Start
  </button>
</div>





