<template>
  <router-link :to="'/users/userId=' + user.id">
    <div
      class="user"
    >
      <div class="user-item">
        <div class="avatar">
          <img :src="getAvatar()" :alt="user.name" />
        </div>
        <div class="user-info">
          <div class="user-head">{{ user.name }}</div>
          <div class="user-desc">{{ user.address.city }}</div>
        </div>
      </div>
      <div class="user-item">
        <div class="user-info">
          <div class="user-head">{{ user.company.name }}</div>
          <div class="user-desc">{{ user.company.bs }}</div>
        </div>
      </div>
      <div class="user-item">
        <div class="user-info">
          <div class="user-head">{{ user.email }}</div>
          <div class="user-desc">{{ user.website }}</div>
        </div>
      </div>
      <div class="user-item">
        <div
          v-if="
            Number(user.address.geo.lat) < 20 &&
            Number(user.address.geo.lat) > -20
          "
          class="pill"
          :style="{ backgroundColor: distance[0].color }"
        >
          {{ distance[0].value }}
        </div>
        <div
          v-else-if="
            (Number(user.address.geo.lat) > 20 &&
            Number(user.address.geo.lat) < 30) ||
            (Number(this.user.address.geo.lat) < -20 &&
            Number(this.user.address.geo.lat) > -30)
          "
          class="pill"
          :style="{ backgroundColor: distance[1].color }"
        >
          {{ distance[1].value }}
        </div>
        <div
          v-else-if="
            (Number(user.address.geo.lat) > 30 &&
            Number(user.address.geo.lat) < 80) ||
            (Number(this.user.address.geo.lat) < -30 &&
            Number(this.user.address.geo.lat) > -80)
          "
          class="pill"
          :style="{ backgroundColor: distance[2].color }"
        >
          {{ distance[2].value }}
        </div>
      </div>
      <div class="user-item">
        <svg
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M12 8C13.1 8 14 7.1 14 6C14 4.9 13.1 4 12 4C10.9 4 10 4.9 10 6C10 7.1 10.9 8 12 8ZM12 10C10.9 10 10 10.9 10 12C10 13.1 10.9 14 12 14C13.1 14 14 13.1 14 12C14 10.9 13.1 10 12 10ZM12 16C10.9 16 10 16.9 10 18C10 19.1 10.9 20 12 20C13.1 20 14 19.1 14 18C14 16.9 13.1 16 12 16Z"
            fill="#C5C7CD"
          />
        </svg>
      </div>
    </div>
  </router-link>
</template>

<script>
export default {
  data() {
    return {
      distance: [
        {
          value: "low",
          color: "#FEC400",
        },
        {
          value: "normal",
          color: "#29CC97",
        },
        {
          value: "high",
          color: "#F12B2C",
        },
      ],
    };
  },
  props: ["user", "index", "borderNone"],
  methods: {
    getAvatar() {
      let avatars = require.context("../assets/avatars/", false, /\.png$/);
      return avatars("./" + this.index + ".png");
    },
  },
};
</script>

<style lang="scss" scoped>
.user {
  display: flex;
  align-items: center;
  padding: 19px 0 20.7px 31px;
  border-top: 1px solid #dfe0eb;
  // border-bottom: 1px solid #dfe0eb;
  &:hover {
    background-color: #f7f8ff;
  }
  .user-item {
    display: flex;
    justify-content: flex-start;
    align-items: center;
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
      justify-content: center;
      margin-right: 3px;
      margin-left: -3px;
      margin-top: 1px;
      width: 80px;
    }
    .avatar {
      margin-top: 4px;
    }
    .user-info {
      margin-top: 2px;
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      
      &:nth-child(2) {
        margin-left: 24px;
        min-width: 190px;
      }
      &:not(:nth-child(2)) {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
      }
      .user-head {
        max-width: 90%;
        font-weight: 600;
        font-size: 14px;
        line-height: 20px;
        letter-spacing: 0.2px;
        color: #252733;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
      }
      .user-desc {
        font-weight: 400;
        font-size: 12px;
        line-height: 16px;
        letter-spacing: 0.1px;
        color: #c5c7cd;
        margin-top: 5px;
      }
    }
    .pill {
      height: 24px;
      border-radius: 12px;
      padding: 0 12px;
      margin-top: 1px;
      font-weight: 700;
      font-size: 11px;
      line-height: 14px;
      display: flex;
      align-items: center;
      text-align: center;
      letter-spacing: 0.5px;
      text-transform: uppercase;
      color: #ffffff;
    }
  }
}
</style>