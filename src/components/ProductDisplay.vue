<template>
  <div :class="productCategory">

    <!-- Loader -->
    <div v-if="loading" class="loader"></div>
    
    <div
      class="container"
      v-if="productCategory === 'men-section' || productCategory === 'women-section'"
    >
      
      <div class="left-section">
        <img :src="product.image" alt="Product Image" />
      </div>

      
      <div class="right-section">
        <h1 id="title-product">{{ product.title }}</h1>
        <div class="type-section">
          <p id="type-product">{{ product.category }}</p>
          <p>{{ product.rating?.rate }} ⭐</p>
        </div>
        <div class="divider"></div>
        <p id="desc-product">{{ product.description }}</p>
        <div class="divider"></div>
        <h1>${{ product.price }}</h1>
        <div class="button">
          <div id="button-1">Buy Now</div>
          <div id="button-2" @click="getNextProduct">Next Product</div>
        </div>
      </div>
    </div>

    <div v-else class="unavailable-product">
      <p>This product is unavailable to show</p>
      <button @click="getNextProduct">Next Product</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      index: 1,
      product: {},
      productCategory: "men-section",
      loading: false
    };
  },
  methods: {
    async fetchProduct() {
      try {
        this.loading = true;
        const response = await fetch(
          `https://fakestoreapi.com/products/${this.index}`
        );
        const data = await response.json();
        if (
          data.category === "men's clothing" ||
          data.category === "women's clothing"
        ) {
          this.product = data;
          this.productCategory =
            data.category === "men's clothing"
              ? "men-section"
              : "women-section";
        } else {
          this.product = {};
          this.productCategory = "unavailable-product";
        }
      } catch (error) {
        console.error("Error fetching product:", error);
      } finally {
        this.loading = false;
      }
    },
    getNextProduct() {
      this.index = this.index >= 20 ? 1 : this.index + 1;
      this.fetchProduct();
    },
  },
  mounted() {
    this.fetchProduct();
  },
};
</script>

<style>
.container {
  padding: 10px;
  display: flex;
  align-items: center;
}

.left-section,
.right-section {
  width: 100%;
  display: flex;
  flex: 1;
  flex-direction: column;
  padding: 0 30px;
}

.left-section {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-basis: 33.33%;
}

.left-section img {
  max-width: 100%;
  max-height: 100%;
}

.right-section {
  flex-basis: 66.66%;
}

.type-section {
  display: flex;
  justify-content: space-between;
}

.left-section h1,
.right-section h1,
.right-section p {
  margin: 0;
  padding: 0;
}

.divider {
  width: 100%;
  height: 1px;
  background-color: var(--light-brown);
  margin-top: 10px;
  margin-bottom: 15px;
}

.button {
  margin-top: 15px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  gap: 20px;
}

.unavailable-product {
  background-image: url('../assets/sad_face.png');
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 400px;
  width: 100%;
}

.unavailable-product p {
  color: var(--dark-brown);
  font-size: 30px;
  text-align: center;
}

.unavailable-product button {
  margin-top: 5px;
  background: transparent;
  border: 2px solid var(--dark-brown);
  text-align: center;
  padding: 10px 30px;
  border-radius: 5px;
  color: var(--dark-brown);
  font-size: 20px;
  cursor: pointer;
}

.loader {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border: 8px solid #f3f3f3;
  border-top: 8px solid var(--dark-pink); /* Blue */
  border-radius: 50%;
  width: 50px;
  height: 50px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

h1 {
  color: var(--dark-pink);
  font-size: 28px;
}

p {
  color: var(--dark-brown);
  font-size: 18px;
}

#title-product {
  padding-bottom: 10px;
}

#desc-product {
  margin-bottom: 100px;
}

#button-1 {
  width: 100%;
  background: var(--dark-pink);
  text-align: center;
  padding: 10px 0;
  border-radius: 5px;
  color: var(--white);
  font-size: 20px;
  cursor: pointer;
}

#button-2 {
  width: 100%;
  border: 2px solid var(--dark-pink);
  text-align: center;
  padding: 10px 0;
  border-radius: 5px;
  color: var(--dark-pink);
  font-size: 20px;
  cursor: pointer;
}
</style>
