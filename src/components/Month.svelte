<script lang="ts">
  // Props
  export let year: number;
  export let month: number;

  let days = [];

  // Day
  let firstDayOfMonth = new Date(year, month + 1, 1);
  let lastDay = new Date(year, month + 1, 0).getDate();
  let prevLastDay = new Date(year, month, 0).getDate();

  // Index
  let firstDayIndex = firstDayOfMonth.getDay();
  let lastDayIndex = new Date(year, month + 1, 0).getDay();

  for (let x = firstDayIndex; x > 0; x--) {
    days.push(prevLastDay - x + 1);
  }
  for (let i = 1; i <= lastDay; i++) {
    days.push(i);
  }
</script>

<div class="monthdays">
  {#each days as day}
    <div>{day}</div>
  {/each}
</div>
