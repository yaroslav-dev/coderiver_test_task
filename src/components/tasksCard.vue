<template>
  <div class="card">
    <div class="header">
      <h3 class="title">{{ title }}</h3>
      <button class="btn">{{ btnTitle }}</button>
    </div>
    <div class="sub-header">
      <span v-if="group"
        >{{ subTitle }}:
        <span class="group">{{ group }}</span>
      </span>
      <span v-else>{{ subTitle }}</span>
    </div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: ["title", "subTitle", "btnTitle", "group"],
};
</script>

<style lang="scss" scoped>
.card {
  border: 1px solid #dfe0eb;
  outline: 2px solid transparent;
  border-radius: 8px;
  background-color: #fff;
  flex: 1;
  padding-bottom: 7px;
  margin-top: 29px;
  margin-bottom: 300px;
  &:first-child {
    margin-right: 31px;
    // padding-right: 2px;
    .header {
      padding-right: 25.5px;
    }
    .btn {
      margin-right: -2px;
    }
  }
  &:last-child {
    margin-right: 4px;
    // padding-right: 24px;
    .header {
      padding-right: 24.5px;
    }
  }
  .header {
    display: flex;
    justify-content: space-between;
    padding: 31px 25px 0px 31px;
    .title {
      margin: 0;
      font-weight: 700;
      font-size: 19px;
      line-height: 24px;
      letter-spacing: 0.4px;
      color: #252733;
    }
    .btn {
      background: none;
      outline: none;
      border: none;
      margin-top: 3px;
      font-weight: 600;
      font-size: 14px;
      line-height: 20px;
      text-align: right;
      letter-spacing: 0.2px;
      color: #3751ff;
      cursor: pointer;
    }
  }
  .sub-header {
    display: flex;
    padding: 8px 25px 8px 31px;
    margin-bottom: 8px;
    font-weight: 400;
    font-size: 12px;
    line-height: 16px;
    letter-spacing: 0.1px;
    color: #9fa2b4;
    .group {
      font-weight: 600;
      font-size: 12px;
      line-height: 15px;
      letter-spacing: 0.1px;
      color: #4b506d;
    }
  }
}
</style>