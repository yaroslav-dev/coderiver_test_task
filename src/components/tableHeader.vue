<template>
  <div class="header">
    <div class="header-item">User details</div>
    <div class="header-item">Company name</div>
    <div class="header-item">Email</div>
    <div class="header-item">Distance</div>
    <div class="header-item"></div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  align-items: center;
  padding: 15px 0 10px 31px;
  border-bottom: 1.5px solid #dfe0eb;
  .header-item {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    font-weight: 700;
    font-size: 14px;
    line-height: 18px;
    letter-spacing: 0.2px;
    color: #9fa2b4;
    &:nth-child(1) {
      flex: 1;
    }
    &:nth-child(2) {
      width: 248px;
    }
    &:nth-child(3) {
      width: 180px;
    }
    &:nth-child(4) {
      width: 101px;
    }
    &:nth-child(5) {
      width: 80px;
    }
  }
}
</style>