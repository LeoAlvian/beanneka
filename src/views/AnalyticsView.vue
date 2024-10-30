<template>
  <h2>Analytics</h2>
  <div class="cards">
    <div class="card" v-for="bean in beans" :key="bean">
      <div class="img-container">
        <img class="product-img" :src="require(`../assets/${bean.imgUrl}.jpg`)" :alt="`${bean.flavor}`">
        <div class="modal">{{ bean.package }}gr</div>
      </div>
      <div class="card-header">
        <h3>{{ bean.flavor }}</h3>
        <p class="id">{{ bean.id }}</p>
      </div>
      <p class="price">Rp.{{ bean.price }}<span class="kilo">K</span></p>
      <p class="bean-type">{{ bean.beanType }}</p>
      <p class="bean-type marg">{{ bean.coffeeCategory }}</p>
      <hr>
      <div class="detail-product">
        <div class="detail-product-left">
          <p>Roasting</p>
          <p>Stock</p>
          <p>Lokasi</p>
          <p>Tanggal Masuk</p>
        </div>
        <div class="detail-product-right">
          <p>: {{ bean.roast }}</p>
          <p>: {{ bean.weight }} gr</p>
          <p>: {{ bean.loc }}</p>
          <p>: {{ bean.inDate }}</p>
        </div>
      </div>
      <hr>
      <div class="action-btn">
        <div class="add-quantity">
          <button class="btn quantity"><i class="fa-solid fa-minus"></i></button>
          <p>100</p>
          <button class="btn quantity"><i class="fa-solid fa-plus"></i></button>
        </div>
        <button class="btn buy">Buy</button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {

    const beans = ref([
      {
        id: 'PMH1024',
        loc: 'Palasari',
        weight: 1000,
        roast: 'Medium',
        flavor: 'Honey',
        inDate: '22-10-2024',
        // price: Intl.NumberFormat('id-ID',{style: 'currency', currency: 'IDR'}).format(40000),
        price: 40,
        imgUrl: 'Honey100gr',
        beanType: 'Arabica',
        coffeeCategory: 'Single Origin',
        package: 100,
        type: 'Sigaruntang'
      },
      {
        id: 'PMW1024',
        loc: 'Palasari',
        weight: 1000,
        roast: 'Medium',
        flavor: 'Wine',
        inDate: '22-10-2024',
        price: 50,
        imgUrl: 'Wine100gr',
        beanType: 'Arabica',
        coffeeCategory: 'Single Origin',
        package: 100,
        type: 'Sigaruntang'
      },
      {
        id: 'PMN1024',
        loc: 'Palasari',
        weight: 1000,
        roast: 'Medium',
        flavor: 'Natural',
        inDate: '22-10-2024',
        price: 45,
        imgUrl: 'Natural100gr',
        beanType: 'Arabica',
        coffeeCategory: 'Single Origin',
        package: 100,
        type: 'Sigaruntang'
      },
  ])

    return { beans }
  }
}
</script>

<style scoped>
.cards {
  display: flex;
  padding: 1rem 2rem;
  gap: 1rem;
}

.card {
  background-color: var(--latte);
  padding: 1rem;
  border-radius: 10px;
  color: var(--blue2);
  text-align: left;
}

.img-container {
  position: relative;
}

.product-img {
  height: 13rem;
  width: 13rem;
  border-radius: 5px;
  margin-bottom: 1rem;
  object-fit: cover;
}

.modal {
  position: absolute;
  top: 7px;
  right: 7px;
  background: var(--blue2);
  color: var(--latte);
  padding: 5px 10px;
  border-radius: 5px;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: .3rem;
}

.id {
  font-size: 11px;
  color: #646464;
  font-weight: 700;
  
}

.price {
  font-size: 16px;
  font-weight: 700;
  
}

.kilo {
  font-size: 14px;
}

.bean-type {
  font-size: 11px;
  text-align: right;
}

.marg {
  color: #646464;
  margin-bottom: 1rem;
}

.detail-product {
  display: flex;
  font-size: 12px;
  margin: 1rem 0;
}

.detail-product-left {
  margin: 0.5rem 0;
  margin-right: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.detail-product-right {
  margin: 0.5rem 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.action-btn {
  display: flex;
  justify-content: space-between;
  margin: 1rem 0;
}

.add-quantity {
  display: flex;
  gap: .5rem;
}

.btn {
  border: 1px solid var(--latte);
  color: var(--blue2);
  cursor: pointer;
  border-radius: 5px;
}

.quantity:hover {
  background-color: var(--blue2);
  color: var(--latte);
}

.quantity {
  padding: .4rem;
}

.add-quantity p {
  padding: .4rem 0;
}

.buy {
  padding: .4rem 2rem;
  background-color: var(--blue2);
  color: var(--latte);
}

.buy:hover {
  color: var(--blue2);
  background-color: var(--latte);
  border: 1px solid var(--blue2);
}

</style>