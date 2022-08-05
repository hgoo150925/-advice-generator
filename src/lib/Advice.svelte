<script>
  let id;
  let quote;
  let src = '../assets/images/pattern-divider-desktop.svg';

  const handleClick = async () => {
    const response = await fetch('https://api.adviceslip.com/advice');
    const data = await response.json();
    id = data.slip.id;
    quote = data.slip.advice;
  };
</script>

<main>
  <div class="container">
    <div class="container__adivice">
      {#if id}
        <h1>Advice #{id}</h1>
        <p>"{quote}"</p>
      {:else}
        <h1>Advice #{117}</h1>
        <p>
          {`"It is easy to sit up and take notice, what's difficult is getting up and
            taking actions."`}
        </p>
      {/if}
    </div>
  </div>
  <div>
    <button class="container__btn btn" on:click={handleClick}>btn</button>
  </div>
</main>

<style>
  .container {
    background-color: var(--dark-grayish-blue);
    border-radius: 1.2rem;
    max-width: 54rem;
    height: 34rem;
    margin: 22.4rem auto;
  }
  .container__adivice h1 {
    color: var(--neon-green);
    letter-spacing: 0.5rem;
    text-transform: uppercase;
  }
  .container__adivice p {
    color: var(--light-cyan);
    font-size: 2.5rem;
    margin: 3.2rem 0 0 0;
  }
  .container__adivice {
    padding: 4.6rem;
    text-align: center;
    background-image: url('../assets/images/pattern-divider-desktop.svg');
    background-repeat: no-repeat;
    background-position: bottom;
    background-size: 85%;
  }
  .container__btn {
    background-color: var(--neon-green);
    background-image: url('../assets/images/icon-dice.svg');
    background-repeat: no-repeat;
    background-position: center;
    background-size: 40%;
  }

  .btn {
    border-radius: 50%;
    border: none;
    cursor: pointer;
    width: 5.5rem;
    height: 5.5rem;
  }
</style>
