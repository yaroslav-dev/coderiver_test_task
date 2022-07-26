<template>
  <div class="container">
    <div class="page">
      <Header />
      <div class="cards">
        <template v-for="(idx, i) in cards">
          <CounterCard :key="i" :card="idx" />
        </template>
      </div>
      <div class="users">
        <div class="users-header">
          <h3 class="users-title">All users</h3>
          <div class="users-sort-block">
            <svg
              class="users-sort-icon"
              width="14"
              height="12"
              viewBox="0 0 14 12"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M0.128568 2.26839L2.31563 0.125478C2.48647 -0.0418526 2.7636 -0.0417991 2.93434 0.125478L5.12132 2.26839C5.39667 2.53812 5.20059 3.00001 4.81195 3.00001H3.5V11.5714C3.5 11.8081 3.30414 12 3.0625 12H2.1875C1.94586 12 1.75 11.8081 1.75 11.5714V3.00001H0.437935C0.0485329 3.00001 -0.146209 2.53758 0.128568 2.26839ZM6.5625 1.7143H13.5625C13.8041 1.7143 14 1.52243 14 1.28573V0.428584C14 0.191879 13.8041 1.34454e-05 13.5625 1.34454e-05H6.5625C6.32086 1.34454e-05 6.125 0.191879 6.125 0.428584V1.28573C6.125 1.52243 6.32086 1.7143 6.5625 1.7143ZM6.125 4.71429V3.85715C6.125 3.62045 6.32086 3.42858 6.5625 3.42858H11.8125C12.0541 3.42858 12.25 3.62045 12.25 3.85715V4.71429C12.25 4.951 12.0541 5.14287 11.8125 5.14287H6.5625C6.32086 5.14287 6.125 4.951 6.125 4.71429ZM6.125 11.5714V10.7143C6.125 10.4776 6.32086 10.2857 6.5625 10.2857H8.3125C8.55414 10.2857 8.75 10.4776 8.75 10.7143V11.5714C8.75 11.8081 8.55414 12 8.3125 12H6.5625C6.32086 12 6.125 11.8081 6.125 11.5714ZM6.125 8.14286V7.28572C6.125 7.04901 6.32086 6.85715 6.5625 6.85715H10.0625C10.3041 6.85715 10.5 7.04901 10.5 7.28572V8.14286C10.5 8.37957 10.3041 8.57143 10.0625 8.57143H6.5625C6.32086 8.57143 6.125 8.37957 6.125 8.14286Z"
                fill="#C5C7CD"
              />
            </svg>
            Sort
          </div>
        </div>
        <TableHeader />
        <template v-for="(user, i) in usersData">
          <User
            :key="i"
            :user="user"
            :index="i"
            :borderNone="i == usersData.length - 1"
          />
        </template>
      </div>
      <div class="task-cards">
        <tasks-card
          :title="'Unresolved tickets'"
          :subTitle="'Group'"
          :group="group"
          :btnTitle="'View details'"
        >
          <template v-for="(ticket, i) in tickets">
            <div :key="i" class="unresolved">
              <span class="ticket">{{ ticket.title }}</span>
              <span class="count">{{ ticket.count }}</span>
            </div>
          </template>
        </tasks-card>
        <tasks-card :title="'Tasks'" :subTitle="'Today'" :btnTitle="'View all'">
          <div class="input-block">
            <input class="input" type="text" placeholder="Create new task" />
            <button class="plus-btn">
              <svg
                width="12"
                height="12"
                viewBox="0 0 12 12"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M6 1V11"
                  stroke="#9FA2B4"
                  stroke-width="2"
                  stroke-linecap="round"
                />
                <path
                  d="M11 6L1 6"
                  stroke="#9FA2B4"
                  stroke-width="2"
                  stroke-linecap="round"
                />
              </svg>
            </button>
          </div>
          <div class="tasks">
            <div class="task" v-for="(task, i) in tasks" :key="i">
              <label class="task-checkbox">
                <input class="checkbox" type="checkbox" name="" id="" />
                <span class="checkmark"></span>
              </label>
              <div class="task-title">{{ task.title }}</div>
              <div class="task-pill-block">
                <div
                  class="task-pill"
                  :style="{ backgroundColor: task.pill.color, color: task.pill.value == 'default' ? '#9FA2B4' : '#FFF' }"
                >
                  {{ task.pill.value }}
                </div>
              </div>
            </div>
          </div>
        </tasks-card>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/header.vue";
import CounterCard from "@/components/counterCard.vue";
import TableHeader from "@/components/tableHeader.vue";
import User from "@/components/userItem.vue";
import tasksCard from "@/components/tasksCard.vue";

export default {
  data() {
    return {
      tasks: [
        {
          title: "Finish ticket update",
          pill: {
            value: "urgent",
            color: "#FEC400",
          },
        },
        {
          title: "Create new ticket example",
          pill: {
            value: "new",
            color: "#29CC97",
          },
        },
        {
          title: "Update ticket report",
          pill: {
            value: "default",
            color: "#F0F1F7",
          },
        },
      ],
      tickets: [
        {
          title: "Waiting on Feature Request",
          count: 4238,
        },
        {
          title: "Awaiting Customer Response",
          count: 1005,
        },
        {
          title: "Awaiting Developer Fix",
          count: 914,
        },
        {
          title: "Pending",
          count: 281,
        },
      ],
      group: "Support",
      usersData: [],
      cards: {
        active: {
          title: "Active",
          value: 60,
        },
        online: {
          title: "Online",
          value: 16,
        },
        filtered: {
          title: "Filtered",
          value: 43,
        },
        banned: {
          title: "Banned",
          value: 64,
        },
      },
    };
  },
  components: {
    Header,
    CounterCard,
    TableHeader,
    User,
    tasksCard,
  },
  created() {
    this.getUsers();
  },
  methods: {
    async getUsers() {
      let response = await fetch(
        "https://jsonplaceholder.typicode.com/users?_limit=8"
      );
      if (response.status == 200) {
        this.usersData = await response.json();
      } else {
        this.usersData = null;
        console.warn(response.status);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  display: flex;
  flex-direction: column;
  // justify-content: center;
  align-items: center;
  .page {
    flex: 1;
    width: 1099px;
    .cards {
      display: flex;
      justify-content: stretch;
      margin: 0 2px 14px -1px;
    }
    .users {
      border: 1px solid #dfe0eb;
      outline: 2px solid transparent;
      border-radius: 8px;
      background-color: #fff;
      flex: 1;
      margin: 0 4px 0 -2px;
      .users-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 14px 31.5px 14px 31px;
        .users-title {
          font-weight: 700;
          font-size: 19px;
          line-height: 24px;
          letter-spacing: 0.4px;
          color: #252733;
          margin-top: 17px;
        }
        .users-sort-block {
          font-weight: 600;
          font-size: 14px;
          line-height: 20px;
          letter-spacing: 0.2px;
          color: #4b506d;
          margin-top: 2px;
          cursor: pointer;
          .users-sort-icon {
            margin-right: 5px;
          }
        }
      }
    }
    .task-cards {
      display: flex;
      margin-left: -2px;
      .unresolved {
        display: flex;
        justify-content: space-between;
        padding: 19px 26px 18px 31.5px;
        border-bottom: 1px solid #dfe0eb;
        &:last-child {
          border: none;
        }
        .ticket {
          font-weight: 600;
          font-size: 14px;
          line-height: 20px;
          letter-spacing: 0.2px;
          color: #252733;
        }
        .count {
          padding-right: 4px;
          font-weight: 600;
          font-size: 14px;
          line-height: 20px;
          text-align: right;
          letter-spacing: 0.2px;
          color: #9fa2b4;
        }
      }
      .input-block {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: -3px;
        padding: 19px 30px 14.3px 31.5px;
        border-bottom: 1px solid #dfe0eb;
        .input {
          padding: 0;
          margin-left: -1px;
          height: 20px;
          font-weight: 600;
          font-size: 14px;
          line-height: 20px;
          letter-spacing: 0.2px;
          color: #252733;
          border: none;
          outline: none;
          &::placeholder {
            font-weight: 600;
            font-size: 14px;
            line-height: 20px;
            letter-spacing: 0.2px;
            color: #c5c7cd;
          }
        }
        .plus-btn {
          height: 24px;
          margin-bottom: 2px;
          margin-right: 1px;
          border: none;
          outline: none;
          border-radius: 8px;
        }
      }
      .tasks {
        .task {
          display: flex;
          text-align: left;
          padding: 20px 30.5px 11px 31.5px;
          border-bottom: 1px solid #dfe0eb;
          &:last-child {
            border-bottom: none;
          }
          &:hover .task-checkbox ~ .checkmark {
            background-color: #ccc;
          }
          .task-checkbox {
            position: relative;
            margin-top: -1px;
            flex: 0.6;
            .checkbox {
              position: absolute;
              opacity: 0;
              cursor: pointer;
              height: 0;
              width: 0;
            }
            .checkbox:checked ~ .checkmark {
              background-color: #3751ff;
            }
            .checkmark {
              position: absolute;
              // top: 0;
              // left: 0;
              height: 16px;
              width: 16px;
              border-radius: 50%;
              border: 2px solid #c5c7cd;
              background-color: #fff;
              &:after {
                content: "";
                position: absolute;
                display: none;
              }
            }
            .checkbox:checked ~ .checkmark {
              border: none;
              height: 20px;
              width: 20px;
            }
            .checkbox:checked ~ .checkmark:after {
              display: block;
            }
            .checkmark:after {
              left: 7px;
              top: 3px;
              width: 4px;
              height: 10px;
              border: solid white;
              border-width: 0 2px 2px 0;
              -webkit-transform: rotate(45deg);
              -ms-transform: rotate(45deg);
              transform: rotate(45deg);
            }
          }
          .task-title {
            text-align: left;
            flex: 6;
            font-weight: 600;
            font-size: 14px;
            line-height: 20px;
            letter-spacing: 0.2px;
            color: #252733;
          }
          .task-pill-block {
            flex: 1.2;
            display: flex;
            justify-content: flex-end;
            align-items: center;
            .task-pill {
              height: 24px;
              border-radius: 8px;
              padding: 0 13px;
              margin-top: -3px;
              margin-bottom: 5px;
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
      }
    }
  }
}
</style>