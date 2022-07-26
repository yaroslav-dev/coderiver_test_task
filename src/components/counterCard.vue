<template>
  <div class="counter-card">
    <div class="card-title">
      {{ card.title }}
    </div>
    <div class="card-value">
      {{ card.value }}
    </div>
  </div>
</template>

<script>
export default {
  props: ["card"],
};
</script>

<style lang="scss">
.counter-card {
  border: 1px solid #dfe0eb;
  outline: 2px solid transparent;
  border-radius: 8px;
  background-color: #fff;
  flex: 1;
  display: flex;
  flex-direction: column;
  padding: 23px 32px;
  margin: 24px 15px;
  cursor: pointer;
  transition: all .1s ease-in;
  &:hover {
    outline: 2px solid #dfe0eb;
    border-color: #3751FF;
    .card-title,
    .card-value {
      color: #3751FF;
    }
  }
  &:first-child {
    margin-left: 0;
  }
  &:last-child {
    margin-right: 0;
  }
  .card-title {
    font-weight: 700;
    font-size: 19px;
    line-height: 24px;
    text-align: center;
    letter-spacing: 0.4px;
    color: #9fa2b4;
    margin-bottom: 12px;
    margin-left: 1px;
    transition: all .1s ease-in;
  }
  .card-value {
    margin-left: 2px;
    font-weight: 700;
    font-size: 40px;
    line-height: 50px;
    text-align: center;
    letter-spacing: 1px;
    color: #252733;
    transition: all .1s ease-in;
  }
}
</style>