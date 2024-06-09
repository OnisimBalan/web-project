<template>
  <div>
    <div class="container">
      <div class="row">
        <!-- Post Product Section -->
        <div class="col-md-6">
          <!-- Post Product Card -->
          <div class="card mb-3">
            <div class="card-header">Post Product</div>
            <div class="card-body">
              <!-- Product Form -->
              <div class="form-group">
                <label>Product Name</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="productName"
                  placeholder="Name"
                />
              </div>
              <div class="form-group">
                <label>Price</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="Price"
                  placeholder="Price"
                />
              </div>
              <div class="form-group">
                <label>Desription</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="Desription"
                  placeholder="Desription"
                />
              </div>
              <div class="form-group">
                <label>Quantity</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="Quantity"
                  placeholder="Quantity"
                />
              </div>
              <div class="form-group">
                <label>Category ID</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="categoryId"
                  placeholder="categoryId"
                />
              </div>
              <button @click="postProduct" class="btn btn-primary">
                Post product
              </button>
            </div>
          </div>
        </div>

        <!-- Delete Product Section -->
        <div class="col-md-6">
          <!-- Delete Product Card -->
          <div class="card mb-3">
            <div class="card-header">Delete Product</div>
            <div class="card-body">
              <!-- Product Deletion Form -->
              <div class="form-group">
                <label>Product Name</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="deleteProductName"
                  placeholder="Product Name"
                />
              </div>
              <button @click="deleteProduct" class="btn btn-danger">
                Delete product
              </button>
            </div>
          </div>

          <div class="card mb-3">
            <div class="card-header">Delete user</div>
            <div class="card-body">
              <div class="form-group">
                <label>User Name</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="deleteUserName"
                  placeholder="User Name"
                />
              </div>
              <button @click="deleteUser" class="btn btn-danger">
                Delete user
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Get Product Section -->
      <div class="row">
        <div class="col-md-6">
          <div class="card mb-3">
            <div class="card-header">Get Product</div>
            <div class="card-body">
              <div class="form-group">
                <label>Product Name</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="product"
                  placeholder="Product Name"
                />
              </div>
              <button @click="getProduct" class="btn btn-primary">
                Get product
              </button>
            </div>
          </div>
        </div>

        <!-- Get Categories Section -->
        <div class="col-md-6">
          <div class="card mb-3">
            <div class="card-header">Get Categories</div>
            <div class="card-body">
              <button @click="getCategories" class="btn btn-primary">
                Get Categories
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Get Users and Orders Section -->
      <div class="row">
        <div class="col-md-6">
          <div class="card mb-3">
            <div class="card-header">Get Users</div>
            <div class="card-body">
              <button @click="getUsers" class="btn btn-primary">
                Get Users
              </button>
              <div class="form-group mt-3">
                <label>User Name</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="user"
                  placeholder="User Name"
                />
              </div>
              <button @click="getUser" class="btn btn-primary">Get User</button>
            </div>
          </div>
        </div>

        <div class="col-md-6">
          <div class="card mb-3">
            <div class="card-header">Get Orders</div>
            <div class="card-body">
              <div class="form-group">
                <input
                  type="text"
                  class="form-control"
                  v-model="order"
                  placeholder="Order Name"
                />
              </div>
              <button @click="getOrder" class="btn btn-primary">
                Get Order
              </button>
              <button @click="getAllProductsAndOrders" class="btn btn-primary">
                Get all orders
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6">
          <div class="card mb-3">
            <div class="card-header">All results</div>
            <div class="card-body">
              <!-- Product Deletion Form -->
              <div class="form-group">
                <input
                  type="text"
                  class="form-control"
                  v-model="deleteProductName"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import axios from 'axios';
import { Vue } from 'vue-class-component';

const BASE_URL = 'https://127.0.0.1:8000';

interface Category {
  id: number;
  desription: string;
}

interface Order {
  id: number;
  productId: number;
  quantity: string;
  price: number;
}

interface Product {
  name: string;
  price: number;
  desription: string;
  available_quantity: string;
  category_id: number;
}

interface User {
  id: number;
  username: string;
  email: string;
  role: string;
  password: string;
}

export default class Start extends Vue {
  product = '';
  productName = '';
  Price = 0;
  Desription = '';
  Quantity = '';
  categoryId = 0;
  order = '';
  productForOrder = '';
  deleteProductName = '';
  deleteUserName = '';
  user = '';

  async deleteProduct() {
    try {
      await axios.delete(
        `${BASE_URL}/products/delete/${this.deleteProductName}`,
      );
      alert('Product ' + this.deleteProductName + ' was deleted!');

      console.log('Product deleted');
    } catch (error) {
      console.error('Error deleting product:', error);
    }
  }

  async deleteUser() {
    try {
      await axios.delete(`${BASE_URL}/users/delete/${this.deleteUserName}`);
      alert('User ' + this.deleteUserName + ' was deleted!');
      console.log('User deleted');
    } catch (error) {
      console.error('Error deleting User:', error);
    }
  }

  async postProduct() {
    const product: Product = {
      name: this.productName,
      desription: this.Desription,
      price: 0,
      available_quantity: '0',
      category_id: 0,
    };

    try {
      const response = await axios.post(`${BASE_URL}/products,${product}`);
      console.log('Product posted:', response.data);
    } catch (error) {
      console.error('Error posting product:', error);
    }
  }

  async getProduct() {
    try {
      const response = await axios.get(`${BASE_URL}/products/${this.product}`);
      alert('Product: ' + this.product);

      console.log('Product:', response.data);
    } catch (error) {
      console.error('Error getting product:', error);
    }
  }

  async getCategories() {
    try {
      const response = await axios.get<Category[]>(`${BASE_URL}/categories`);
      alert('Product: ' + response.data);

      console.log('Categories:', response.data);
    } catch (error) {
      console.error('Error getting categories:', error);
    }
  }

  async getUsers() {
    try {
      const response = await axios.get<User[]>(`${BASE_URL}/users`);
      alert('Users: ' + response.data);

      console.log('Users:', response.data);
    } catch (error) {
      console.error('Error getting users:', error);
    }
  }

  async getUser() {
    try {
      const response = await axios.get<User>(`${BASE_URL}/users/${this.user}`);
      alert('User: ' + response.data);
      console.log('User:', response.data);
    } catch (error) {
      console.error('Error getting user:', error);
    }
  }

  async getOrder() {
    try {
      const response = await axios.get<Order>(
        `${BASE_URL}/orders/${this.order}`,
      );
      alert('Order: ' + response.data);
      console.log('Order:', response.data);
    } catch (error) {
      console.error('Error getting order:', error);
    }
  }

  async getAllProductsAndOrders() {
    try {
      const response = await axios.get(`${BASE_URL}/products-and-orders`);
      alert('Orders: ' + response.data);
      console.log('All Products and Orders:', response.data);
    } catch (error) {
      console.error('Error getting all products and orders:', error);
    }
  }
}
</script>

<style scoped>
.d-flex {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 1rem;
}

.form-control {
  margin-bottom: 0.5rem;
}

.btn {
  margin-right: 0.5rem;
}
</style>
