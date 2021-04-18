<script lang="ts">
  let year = 2021;
  let monthesOfYear = [
    '1',
    '2',
    '3',
    '4',
    '5',
    '6',
    '7',
    '8',
    '9',
    '10',
    '11',
    '12',
  ];
  let month = 1;
  function incrementMonth(direction) {
    const current = new Date(year, month, 1);
    current.setMonth(current.getMonth() + direction);
    month = current.getMonth();
    year = current.getFullYear();
  }
</script>

<div class="heading">
  <div class="control" onclick={() => incrementMonth(-1)}>
    <i class="arrow left" />
  </div>
  <div class="label">{year}年 {month}月</div>
  <div class="control" onclick={() => incrementMonth(1)}>
    <i class="arrow right" />
  </div>
</div>

<style>
  .heading {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .arrow {
    display: inline-block;
    width: 15px;
    height: 15px;
    border-style: solid;
    border-color: #a9a9;
    border-width: 0;
    border-bottom-width: 1.5px;
    border-right-width: 1.5px;
  }
  .arrow.left {
    transform: rotate(135deg);
  }
  .arrow.right {
    transform: rotate(315deg);
  }
</style>
