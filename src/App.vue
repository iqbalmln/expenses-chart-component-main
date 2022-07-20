<script setup lang="ts">
import TheStats from "@/components/TheStats.vue";

import gsap from "gsap";
import { onMounted } from "vue";

onMounted(() => {
  document.body.classList.remove("loading");
  gsap.from(document.body, {
    opacity: 0,
    duration: 1,
    delay: 0.2,
    ease: "Powe3.easeOut",
  });
});
</script>

<template>
  <div class="container">
    <div class="card">
      <header>
        <div class="header-col left">
          <span>My balance</span>
          <h3>$921.48</h3>
        </div>
        <div class="header-col right">
          <img src="./assets/images/logo.svg" />
        </div>
      </header>
      <main>
        <h3>Spending - Last 7 days</h3>
        <TheStats />
        <footer>
          <div class="footer-col left">
            <span>Total this month</span>
            <p>$478.33</p>
          </div>
          <div class="footer-col right">
            <span>+2.4%</span>
            <p>from last month</p>
          </div>
        </footer>
      </main>
    </div>
  </div>
</template>

<style scoped lang="scss">
// ### Primary
$soft-red: hsl(10, 79%, 65%);
$cyan: hsl(186, 34%, 60%);

// ### Neutral
$dark-brown: hsl(25, 47%, 15%);
$medium-brown: hsl(28, 10%, 53%);
$cream: hsl(27, 66%, 92%);
$very-pale-orange: hsl(33, 100%, 98%);
.container {
  background: $cream;
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  .card {
    @media (min-width: 768px) {
      width: 25%;
      margin: 0;
    }
    width: 100%;
    margin: 0 24px;
    height: 400px;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    header {
      background: $soft-red;
      padding: 0.75rem 1rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-radius: 12px;
      color: #fff;
      .header-col {
        &.left {
          display: flex;
          flex-direction: column;
          gap: 0.5rem;
          span {
            font-size: 12px;
          }
          h3 {
            font-weight: 500;
            font-size: 24px;
          }
        }
        &.right {
          img {
            width: 48px;
            height: 48px;
          }
        }
      }
    }
    main {
      display: flex;
      background: #fff;
      flex-direction: column;
      gap: 2rem;
      border-radius: 12px;
      padding: 1.5rem;

      h3 {
        color: $dark-brown;
      }

      footer {
        display: flex;
        justify-content: space-between;
        align-items: center;
        .footer-col {
          &.left {
            span {
              font-size: 12px;
              // font-weight: 500;
              color: $medium-brown;
            }
            p {
              font-size: 2rem;
              color: $dark-brown;
              font-weight: 900;
            }
          }
          &.right {
            text-align: right;
            span {
              font-size: 14px;
              color: $dark-brown;
              font-weight: bolder;
            }
            p {
              font-size: 14px;
              color: $medium-brown;
            }
          }
        }
      }
    }
  }
}
</style>
