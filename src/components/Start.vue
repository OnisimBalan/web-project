<template>
  <div>
    <div class="d-flex">
      <div class="form-group p-1">
        <label>Post product</label>
        <div class="d-flex">
          <div class="">
            <input
              type="text"
              class="form-control"
              id="products"
              placeholder="name"
            />
            <input
              type="text"
              class="form-control"
              id="products"
              placeholder="s"
            />
            <input
              type="text"
              class="form-control"
              id="products"
              placeholder="s"
            />
          </div>
        </div>
        <button class="btn btn-primary ml-2 mr-2">Post</button>
      </div>
      <div class="form-group p-1">
        <label>Get product</label>
        <div class="d-flex">
          <input
            type="text"
            class="form-control"
            id="products"
            placeholder="product name"
            v-model="product"
          />
          <button @click="getProdcut()" class="btn btn-primary ml-2 mr-2">
            Get
          </button>
        </div>
      </div>

      <div class="form-group p-1">
        <label>Get Categories</label>
        <div class="d-flex">
          <input
            type="text"
            class="form-control"
            id="products"
            placeholder="category name"
          />
          <button class="btn btn-primary ml-2 mr-2">Get</button>
        </div>
      </div>

      <div class="form-group p-1">
        <label>Get Users</label>
        <div class="d-flex">
          <input
            type="text"
            class="form-control"
            id="products"
            placeholder="user name"
          />
        </div>

        <button class="btn btn-primary ml-2 mr-2">Get</button>
        <button class="btn btn-primary ml-2 mr-2">Get all users</button>
      </div>

      <div class="form-group p-1">
        <label>Get orders and products</label>
        <div class="d-flex">
          <input
            type="text"
            class="form-control"
            id="products"
            placeholder="order name"
          />
          <input
            type="text"
            class="form-control"
            id="products"
            placeholder="product name"
          />
        </div>
        <button class="btn btn-primary ml-2 mr-2">Get order</button>
        <button class="btn btn-primary ml-2 mr-2">Get product</button>
        <button class="btn btn-primary ml-2 mr-2">Get all</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class Start extends Vue {
  product = "";

  postProdcuts() {
    return;
  }

  getProdcut() {
    if (this.product == "") {
      return;
    }
    console.log(this.product);
    return this.product;
  }

  getCategories() {
    return;
  }

  getUsers() {
    return;
  }

  getUser() {
    return;
  }

  postUsers() {
    return;
  }

  getOrder() {
    return;
  }

  getAllProdcutsAdnOrders() {
    return;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
