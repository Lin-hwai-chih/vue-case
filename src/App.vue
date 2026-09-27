<script setup>
//產品資料串接網址：https://cwpeng.github.io/live-records-samples/data/products.json
//評論資料串接網址：https://cwpeng.github.io/live-records-samples/data/reviews.json
//建立一個標籤選單做內容切換
import ProductPage from "./product/ProductPage.vue";
import ReviewPage from "./review/ReviewPage.vue";
import { ref } from "vue";
let page = ref("product"); //記錄一個page的響應式，用來決定現在要看的是哪一個內容product或是review，預設為product

let change = function (clickedPage) {
  page.value = clickedPage;
};
</script>

<template>
  <nav>
    <span
      :class="page === 'product' ? 'current' : ''"
      @click="change('product')"
      >產品資料</span
    >
    <span :class="page === 'review' ? 'current' : ''" @click="change('review')"
      >評論訊息</span
    >
  </nav>
  <main>
    <ProductPage v-if="page === 'product'"></ProductPage>
    <ReviewPage v-if="page === 'review'"></ReviewPage>
  </main>
</template>
 
<style scoped>
nav {
  font-size: 20px;
}
nav span {
  margin-right: 10px;
}
nav span.current {
  font-weight: bold;
}
</style>
