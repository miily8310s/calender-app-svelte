<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let year: number;
  export let month: number;
</script>

<div class="heading">
  <div class="control" on:click={() => dispatch('incrementMonth', -1)}>
    <i class="arrow left" />
  </div>
  <div class="label">{year}年 {month + 1}月</div>
  <div class="control" on:click={() => dispatch('incrementMonth', 1)}>
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
