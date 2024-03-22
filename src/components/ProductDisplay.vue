<template>
  <!-- This is value of container  -->
  <div class="container">
    <!-- This is left secion of container -->
    <div class="left-section">
      <h1>ini gambar</h1>
    </div>

    <!-- This is right secion of container -->
    <div class="right-section">
      <h1 id="title-product">Title</h1>
      <div class="type-section">
        <p id="type-product">men's clothing</p>
        <p>2.9/5</p>
      </div>
      <div class="divider" />
      <p id="desc-product">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non, sequi
        dolor enim iusto tempora cumque mollitia obcaecati ducimus eum numquam
        voluptate totam quos in. Deleniti explicabo quos aut quis eaque.
      </p>
      <div class="divider" />
      <h1>$ini harga</h1>
      <div class="button">
        <div id="button-1">Buy Now</div>
        <div id="button-2">Next Product</div>
      </div>
    </div>
  </div>
</template>

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
}

.left-section {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-basis: 33.33%;
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

<script></script>
