<template>
  <header class="main-header">
    <router-link class="link" to="/users">
      <h2 class="header-title">Users</h2>
    </router-link>

    <div class="header-actions">
      <div class="actions-block">
        <div class="search-block">
          <svg
            width="16"
            height="16"
            viewBox="0 0 16 16"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <circle
              cx="6.5"
              cy="6.5"
              r="5.75"
              stroke="#C5C7CD"
              stroke-width="1.5"
            />
            <path
              d="M11 11L15 15"
              stroke="#C5C7CD"
              stroke-width="1.5"
              stroke-linecap="round"
            />
          </svg>
        </div>
        <div class="notification-block">
          <svg
            width="18"
            height="19"
            viewBox="0 0 18 19"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M7.99999 19C9.10374 19 9.99905 18.1047 9.99905 17H6.00093C6.00093 18.1047 6.89624 19 7.99999 19ZM14.7309 14.3216C14.1272 13.6728 12.9975 12.6969 12.9975 9.5C12.9975 7.07188 11.295 5.12812 8.99937 4.65125V4C8.99937 3.44781 8.55187 3 7.99999 3C7.44812 3 7.00062 3.44781 7.00062 4V4.65125C4.70499 5.12812 3.00249 7.07188 3.00249 9.5C3.00249 12.6969 1.8728 13.6728 1.26905 14.3216C1.08155 14.5231 0.998429 14.7641 0.999991 15C1.00343 15.5125 1.40562 16 2.00312 16H13.9969C14.5944 16 14.9969 15.5125 15 15C15.0016 14.7641 14.9184 14.5228 14.7309 14.3216Z"
              fill="#C5C7CD"
            />
            <circle
              cx="13"
              cy="5"
              r="3.75"
              fill="#3751FF"
              stroke="#F7F8FC"
              stroke-width="1.5"
            />
          </svg>
        </div>
      </div>
      <div class="vertical-line"></div>
      <span class="name-block">{{user.name}}</span>
      <div class="avatar-block"></div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: 'Jones Ferdinand'
      }
    }
  },
};
</script>

<style lang="scss" scoped>
.main-header {
  height: 44px;
  margin: 30px 1.5px 30px -1.5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .link {
      margin-bottom: 2px;
    }
  .header-title {
    font-weight: 700;
    font-size: 24px;
    line-height: 30px;
    letter-spacing: 0.3px;
    color: #252733;
  }
  .header-actions {
    display: flex;
    align-items: center;
    .actions-block {
      display: flex;
      align-items: center;
      .search-block {
        margin: 3px 9px 0 10px;
      }
      .notification-block {
        margin: 0 15px;
      }
    }
    .vertical-line {
      height: 32px;
      border-left: 1px solid #DFE0EB;
      margin: 5px 15px 0 15px;
    }
    .name-block {
      margin: 2px 14px 0 16px;
      font-weight: 600;
      font-size: 14px;
      line-height: 20px;
      letter-spacing: 0.2px;
      color: #252733;
    }
    .avatar-block {
      height: 40px;
      width: 40px;
      outline: 2px solid #dfe0eb;
      border: 2px solid #f7f8fc;
      border-radius: 50%;
      background-image: url(../assets/head_avatar.png);
      background-position: 50% 50%;
    }
  }
}
</style>