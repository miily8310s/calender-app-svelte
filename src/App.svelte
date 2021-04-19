<script lang="ts">
  import Navbar from './components/Navbar.svelte';
  import Month from './components/Month.svelte';
  export let name: string;
  let current = new Date();
  let currentYear = current.getFullYear();
  let currentMonth = current.getMonth();
  let dayOfWeek = [
    'Sunday',
    'Monday',
    'Tuesday',
    'Wednesday',
    'Thursday',
    'Friday',
    'Saturday',
  ];

  function incrementMonth(direction) {
    current.setMonth(current.getMonth() + direction);
    currentYear = current.getFullYear();
    currentMonth = current.getMonth();
  }
</script>

<main>
  <h1>Hello {name}!</h1>
  <Navbar
    year={currentYear}
    month={currentMonth + 1}
    on:incrementMonth={(e) => incrementMonth(e.detail)}
  />
  <div class="weekdays">
    {#each dayOfWeek as day}
      <span>{day}</span>
    {/each}
  </div>
  <Month year={currentYear} month={currentMonth + 1} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
