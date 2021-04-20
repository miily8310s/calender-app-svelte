<script lang="ts">
  import Navbar from './components/Navbar.svelte';
  import Month from './components/Month.svelte';
  let current = new Date();
  let currentYear = current.getFullYear();
  let currentMonth = current.getMonth() + 1;
  let dayOfWeek = ['Su', 'Mo', 'Tu', 'We', 'Th', 'Fr', 'Sa'];

  function incrementMonth(direction) {
    current.setMonth(currentMonth + direction);
    currentYear = current.getFullYear();
    currentMonth = current.getMonth();
  }
</script>

<main>
  <Navbar
    year={currentYear}
    month={currentMonth}
    on:incrementMonth={(e) => incrementMonth(e.detail)}
  />
  <div class="weekdays">
    {#each dayOfWeek as day}
      <span>{day}</span>
    {/each}
  </div>
  <Month year={currentYear} month={currentMonth} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  .weekdays {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    text-transform: uppercase;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
