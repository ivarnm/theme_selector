<h1>Theme selector</h1>

<div class="box-container">
  <div class="box neutral-0">--neutral-0</div>
  <div class="box neutral-10">--neutral-10</div>
  <div class="box neutral-30">--neutral-30</div>
  <div class="box neutral-40">--neutral-40</div>
  <div class="box neutral-60">--neutral-60</div>
  <div class="box neutral-70">--neutral-70</div>
  <div class="box neutral-100">--neutral-100</div>
  <div class="box primary-60">--primary-60</div>
  <div class="box primary-70">--primary-70</div>
  <div class="box primary-80">--primary-80</div>
  <div class="box secondary-70">--secondary-70</div>
  <div class="box secondary-80">--secondary-80</div>
</div>

<style>
  .box-container {
    display: flex;
    gap: 30px;
    flex-wrap: wrap;
  }

  .box {
    width: 150px;
    height: 150px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .neutral-0 {
    background-color: var(--neutral-0);
    color: var(--neutral-100);
  }

  .neutral-10 {
    background-color: var(--neutral-10);
    color: var(--neutral-100);
    border: 5px solid var(--neutral-30);
    box-sizing: border-box;
  }

  .neutral-30 {
    background-color: var(--neutral-30);
    color: var(--neutral-100);
  }

  .neutral-40 {
    background-color: var(--neutral-40);
    color: var(--neutral-100);
  }

  .neutral-60 {
    background-color: var(--neutral-60);
    color: var(--neutral-0);
  }

  .neutral-70 {
    background-color: var(--neutral-70);
    color: var(--neutral-0);
  }

  .neutral-100 {
    background-color: var(--neutral-100);
    color: var(--neutral-0);
  }

  .primary-60 {
    background-color: var(--primary-60);
    color: var(--neutral-0);
  }

  .primary-70 {
    background-color: var(--primary-70);
    color: var(--neutral-0);
  }

  .primary-80 {
    background-color: var(--primary-80);
    color: var(--neutral-0);
  }

  .secondary-70 {
    background-color: var(--secondary-70);
    color: var(--neutral-0);
  }

  .secondary-80 {
    background-color: var(--secondary-80);
    color: var(--neutral-0);
  }
</style>
