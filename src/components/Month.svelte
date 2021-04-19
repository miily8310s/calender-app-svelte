<script lang="ts">
  // Props
  export let year: number;
  export let month: number;

  let days = [];

  // Day
  $: firstDayOfMonth = new Date(year, month + 1, 1);
  $: lastDay = new Date(year, month + 1, 0).getDate();
  $: prevLastDay = new Date(year, month, 0).getDate();

  // Index
  $: firstDayIndex = firstDayOfMonth.getDay();
  $: lastDayIndex = new Date(year, month + 1, 0).getDay();

  $: {
    days = [];
    for (let x = firstDayIndex; x > 0; x--) {
      days.push(prevLastDay - x + 1);
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
  .day {
    margin-right: 2px;
  }
</style>
