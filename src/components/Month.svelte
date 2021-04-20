<script lang="ts">
  // Props
  export let year: number;
  export let month: number;

  let days = [];

  // Day
  $: firstDayOfMonth = new Date(year, month - 1, 1);
  $: lastDay = new Date(year, month, 0).getDate();

  // Index
  $: firstDayIndex = firstDayOfMonth.getDay();

  $: {
    days = [];
    for (let x = firstDayIndex; x > 0; x--) {
      days.push('');
    }
    for (let i = 1; i <= lastDay; i++) {
      days.push(i);
    }
  }
</script>

<div class="monthdays">
  {#each days as day}
    <div class="day">{day}</div>
  {/each}
</div>

<style>
  .monthdays {
    display: flex;
    justify-content: center;
  }

  .monthdays {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
  }
  .day {
    margin-right: 2px;
  }
</style>
