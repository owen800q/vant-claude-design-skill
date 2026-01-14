---
name: vant-page-templates
description: Ready-to-use Vue.js page templates and component compositions for Vant mobile apps. Use when building complete mobile app pages like login, home, product list, product detail, shopping cart, profile, or checkout pages using Vue.js and Vant components.
---

# Vant Page Templates & Component Examples

This skill provides ready-to-use Vue.js page templates and component compositions for building mobile apps with Vant.

## Available Templates

1. **Login Page** - User authentication with social login
2. **Home Page** - Tab bar, search, banners, product grid
3. **Product List** - Filters, pull-refresh, infinite scroll
4. **Product Detail** - Image gallery, SKU selector, action bar
5. **Shopping Cart** - Swipe delete, quantity stepper, checkout bar
6. **Profile Page** - User info, order stats, settings menu

---

## 1. Login Page

```vue
<template>
  <div class="login-page">
    <van-nav-bar title="Login" />

    <div class="login-header">
      <van-image round width="80" height="80" src="/logo.png" />
      <h1>Welcome Back</h1>
      <p>Sign in to continue</p>
    </div>

    <van-form @submit="onSubmit" class="login-form">
      <van-cell-group inset>
        <van-field
          v-model="form.phone"
          name="phone"
          label="Phone"
          placeholder="Enter phone number"
          type="tel"
          :rules="[{ required: true, message: 'Phone is required' }]"
        >
          <template #left-icon>
            <van-icon name="phone-o" />
          </template>
        </van-field>

        <van-field
          v-model="form.password"
          name="password"
          label="Password"
          placeholder="Enter password"
          :type="showPassword ? 'text' : 'password'"
          :rules="[{ required: true, message: 'Password is required' }]"
        >
          <template #left-icon>
            <van-icon name="lock" />
          </template>
          <template #right-icon>
            <van-icon
              :name="showPassword ? 'eye-o' : 'closed-eye'"
              @click="showPassword = !showPassword"
            />
          </template>
        </van-field>
      </van-cell-group>

      <div class="login-actions">
        <van-button round block type="primary" native-type="submit" :loading="loading">
          Sign In
        </van-button>
        <van-button round block plain type="primary" @click="goToRegister">
          Create Account
        </van-button>
      </div>

      <div class="login-footer">
        <van-divider>Or continue with</van-divider>
        <van-row gutter="16" justify="center">
          <van-col><van-button icon="wechat" round /></van-col>
          <van-col><van-button icon="alipay" round /></van-col>
          <van-col><van-button icon="qq" round /></van-col>
        </van-row>
      </div>
    </van-form>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';

const form = reactive({ phone: '', password: '' });
const showPassword = ref(false);
const loading = ref(false);

const onSubmit = async () => {
  loading.value = true;
  // API call here
  loading.value = false;
};
</script>

<style scoped>
.login-page { min-height: 100vh; background: var(--van-background); }
.login-header { text-align: center; padding: 48px 24px 24px; }
.login-header h1 { margin: 16px 0 8px; font-size: 24px; }
.login-header p { color: var(--van-text-color-2); font-size: 14px; }
.login-form { padding: 16px; }
.login-actions { margin-top: 24px; display: flex; flex-direction: column; gap: 12px; }
.login-footer { margin-top: 32px; }
</style>
```

---

## 2. Home Page with Tab Bar

```vue
<template>
  <div class="home-page">
    <!-- Header with Search -->
    <div class="home-header">
      <van-search v-model="searchValue" placeholder="Search..." shape="round" background="transparent" />
    </div>

    <!-- Banner Swiper -->
    <van-swipe :autoplay="3000" indicator-color="white" class="home-banner">
      <van-swipe-item v-for="banner in banners" :key="banner.id">
        <van-image :src="banner.image" fit="cover" height="180" />
      </van-swipe-item>
    </van-swipe>

    <!-- Quick Actions Grid -->
    <van-grid :column-num="5" :border="false" class="home-grid">
      <van-grid-item v-for="item in quickActions" :key="item.id" :icon="item.icon" :text="item.text" />
    </van-grid>

    <!-- Notice Bar -->
    <van-notice-bar left-icon="volume-o" text="Welcome! New users get 20% off." />

    <!-- Products Section -->
    <div class="home-section">
      <div class="section-header">
        <h3>Hot Deals</h3>
        <van-button size="small" plain>View All</van-button>
      </div>
      <van-row gutter="12">
        <van-col span="12" v-for="product in products" :key="product.id">
          <van-card :price="product.price" :title="product.title" :thumb="product.image">
            <template #tags><van-tag type="danger">Hot</van-tag></template>
          </van-card>
        </van-col>
      </van-row>
    </div>

    <!-- Tab Bar -->
    <van-tabbar v-model="activeTab" fixed safe-area-inset-bottom>
      <van-tabbar-item icon="home-o" name="home">Home</van-tabbar-item>
      <van-tabbar-item icon="apps-o" name="category">Category</van-tabbar-item>
      <van-tabbar-item icon="cart-o" name="cart" :badge="cartCount">Cart</van-tabbar-item>
      <van-tabbar-item icon="user-o" name="profile">Profile</van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const searchValue = ref('');
const activeTab = ref('home');
const cartCount = ref(3);
const banners = ref([{ id: 1, image: '/banner1.jpg' }]);
const quickActions = ref([
  { id: 1, icon: 'fire-o', text: 'Hot' },
  { id: 2, icon: 'gift-o', text: 'New' },
  { id: 3, icon: 'coupon-o', text: 'Coupons' },
  { id: 4, icon: 'gem-o', text: 'VIP' },
  { id: 5, icon: 'more-o', text: 'More' },
]);
const products = ref([
  { id: 1, title: 'Product 1', price: '99.00', image: '/p1.jpg' },
]);
</script>

<style scoped>
.home-page { padding-bottom: 60px; background: var(--van-background); }
.home-header { position: sticky; top: 0; z-index: 100; background: var(--van-primary-color); padding: 8px 16px; }
.home-banner { margin: 12px; border-radius: var(--van-radius-lg); overflow: hidden; }
.home-grid { margin: 12px; background: #fff; border-radius: var(--van-radius-lg); }
.home-section { margin: 12px; padding: 16px; background: #fff; border-radius: var(--van-radius-lg); }
.section-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; }
.section-header h3 { font-size: 16px; margin: 0; }
</style>
```

---

## 3. Product List Page

```vue
<template>
  <div class="product-list-page">
    <van-nav-bar title="Products" left-arrow @click-left="goBack" fixed placeholder />

    <!-- Filter Tabs -->
    <van-tabs v-model:active="activeFilter" sticky offset-top="46">
      <van-tab title="All" name="all" />
      <van-tab title="Hot" name="hot" />
      <van-tab title="New" name="new" />
      <van-tab title="Price ↑" name="price_asc" />
    </van-tabs>

    <!-- Product Grid with Pull Refresh -->
    <van-pull-refresh v-model="refreshing" @refresh="onRefresh">
      <van-list v-model:loading="loading" :finished="finished" finished-text="No more" @load="loadMore">
        <van-row gutter="8" class="product-grid">
          <van-col span="12" v-for="product in products" :key="product.id">
            <div class="product-card">
              <van-image :src="product.image" fit="cover" width="100%" height="180" lazy-load />
              <div class="product-info">
                <p class="product-title van-multi-ellipsis--l2">{{ product.title }}</p>
                <div class="product-price">
                  <span class="current-price">¥{{ product.price }}</span>
                  <span class="original-price">¥{{ product.originalPrice }}</span>
                </div>
              </div>
            </div>
          </van-col>
        </van-row>
      </van-list>
    </van-pull-refresh>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const activeFilter = ref('all');
const refreshing = ref(false);
const loading = ref(false);
const finished = ref(false);
const products = ref([]);

const loadMore = async () => { loading.value = false; };
const onRefresh = async () => { refreshing.value = false; };
</script>

<style scoped>
.product-list-page { min-height: 100vh; background: var(--van-background); }
.product-grid { padding: 8px; }
.product-card { background: #fff; border-radius: 8px; overflow: hidden; margin-bottom: 8px; }
.product-info { padding: 8px 12px 12px; }
.product-title { font-size: 13px; margin: 0 0 8px; height: 36px; }
.current-price { font-size: 16px; font-weight: 600; color: var(--van-danger-color); }
.original-price { font-size: 12px; color: var(--van-text-color-3); text-decoration: line-through; margin-left: 4px; }
</style>
```

---

## 4. Shopping Cart

```vue
<template>
  <div class="cart-page">
    <van-nav-bar title="Shopping Cart" />

    <van-empty v-if="cartItems.length === 0" description="Your cart is empty">
      <van-button round type="primary">Go Shopping</van-button>
    </van-empty>

    <div v-else class="cart-content">
      <van-checkbox-group v-model="selectedItems">
        <van-swipe-cell v-for="item in cartItems" :key="item.id">
          <div class="cart-item">
            <van-checkbox :name="item.id" />
            <van-image width="90" height="90" :src="item.image" radius="8" />
            <div class="item-info">
              <p class="item-title van-multi-ellipsis--l2">{{ item.title }}</p>
              <p class="item-sku">{{ item.skuName }}</p>
              <div class="item-bottom">
                <span class="item-price">¥{{ item.price }}</span>
                <van-stepper v-model="item.quantity" :min="1" theme="round" />
              </div>
            </div>
          </div>
          <template #right>
            <van-button square type="danger" text="Delete" @click="removeItem(item.id)" />
          </template>
        </van-swipe-cell>
      </van-checkbox-group>
    </div>

    <van-submit-bar v-if="cartItems.length > 0" :price="totalPrice" button-text="Checkout" @submit="onCheckout">
      <van-checkbox v-model="allSelected" @change="toggleAll">All</van-checkbox>
    </van-submit-bar>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const cartItems = ref([
  { id: 1, title: 'Wireless Headphones', skuName: 'Black', price: '299.00', quantity: 1, image: '/p1.jpg' },
]);
const selectedItems = ref([]);
const allSelected = ref(false);

const totalPrice = computed(() => {
  return selectedItems.value.reduce((sum, id) => {
    const item = cartItems.value.find(i => i.id === id);
    return sum + (parseFloat(item.price) * item.quantity * 100);
  }, 0);
});

const toggleAll = (checked) => {
  selectedItems.value = checked ? cartItems.value.map(i => i.id) : [];
};

const removeItem = (id) => {
  cartItems.value = cartItems.value.filter(i => i.id !== id);
};
</script>

<style scoped>
.cart-page { min-height: 100vh; background: var(--van-background); padding-bottom: 60px; }
.cart-item { display: flex; align-items: flex-start; gap: 12px; padding: 16px; background: #fff; }
.item-info { flex: 1; min-width: 0; }
.item-title { font-size: 14px; margin: 0 0 4px; height: 40px; }
.item-sku { font-size: 12px; color: var(--van-text-color-3); margin: 0 0 8px; }
.item-bottom { display: flex; justify-content: space-between; align-items: center; }
.item-price { font-size: 16px; font-weight: 600; color: var(--van-danger-color); }
</style>
```

---

## 5. Profile Page

```vue
<template>
  <div class="profile-page">
    <!-- User Header -->
    <div class="profile-header">
      <van-image round width="64" height="64" :src="user.avatar" />
      <div class="user-info">
        <h2>{{ user.name }}</h2>
        <p>{{ user.phone }}</p>
      </div>
      <van-icon name="setting-o" size="24" />
    </div>

    <!-- Stats Card -->
    <van-grid :column-num="4" :border="false" class="stats-grid">
      <van-grid-item icon="orders-o" text="Orders" :badge="orderCounts.all" />
      <van-grid-item icon="pending-payment" text="Pending" :badge="orderCounts.pending" />
      <van-grid-item icon="logistics" text="Shipping" :badge="orderCounts.shipping" />
      <van-grid-item icon="comment-o" text="Review" :badge="orderCounts.review" />
    </van-grid>

    <!-- Menu Sections -->
    <van-cell-group inset class="menu-section">
      <van-cell title="My Favorites" icon="star-o" is-link />
      <van-cell title="Coupons" icon="coupon-o" is-link>
        <template #value><van-tag type="danger" round>{{ couponCount }}</van-tag></template>
      </van-cell>
    </van-cell-group>

    <van-cell-group inset class="menu-section">
      <van-cell title="Shipping Address" icon="location-o" is-link />
      <van-cell title="Help Center" icon="question-o" is-link />
    </van-cell-group>

    <!-- Dark Mode Toggle -->
    <van-cell-group inset class="menu-section">
      <van-cell title="Dark Mode" icon="eye-o">
        <template #right-icon>
          <van-switch v-model="isDarkMode" size="24" @change="toggleDarkMode" />
        </template>
      </van-cell>
    </van-cell-group>

    <div class="logout-section">
      <van-button plain block type="danger">Log Out</van-button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const user = ref({ name: 'John Doe', phone: '+1 234 567 8900', avatar: '/avatar.jpg' });
const orderCounts = ref({ all: 12, pending: 2, shipping: 1, review: 3 });
const couponCount = ref(5);
const isDarkMode = ref(false);

const toggleDarkMode = (checked) => {
  document.documentElement.classList.toggle('van-theme-dark', checked);
};
</script>

<style scoped>
.profile-page { min-height: 100vh; background: var(--van-background); padding-bottom: 24px; }
.profile-header { background: linear-gradient(135deg, var(--van-primary-color), #4facfe); padding: 32px 20px 48px; display: flex; align-items: center; gap: 16px; color: #fff; }
.user-info { flex: 1; }
.user-info h2 { font-size: 20px; margin: 0 0 4px; }
.user-info p { font-size: 14px; opacity: 0.8; margin: 0; }
.stats-grid { margin: -24px 12px 12px; background: #fff; border-radius: 8px; box-shadow: 0 2px 12px rgba(0,0,0,0.08); }
.menu-section { margin: 12px; }
.logout-section { padding: 24px 16px; }
</style>
```

---

## Component Compositions

### Address Selector
```vue
<van-address-list v-model="chosenAddressId" :list="addressList" @add="onAdd" @edit="onEdit" />
```

### Coupon Selector
```vue
<van-coupon-cell :coupons="coupons" :chosen-coupon="chosenCoupon" @click="showCoupons = true" />
<van-popup v-model:show="showCoupons" position="bottom" round style="height: 90%">
  <van-coupon-list :coupons="coupons" :chosen-coupon="chosenCoupon" @change="onCouponChange" />
</van-popup>
```

### Date Picker
```vue
<van-field v-model="dateText" is-link readonly label="Date" @click="showPicker = true" />
<van-popup v-model:show="showPicker" position="bottom" round>
  <van-date-picker v-model="selectedDate" title="Select Date" @confirm="onConfirm" @cancel="showPicker = false" />
</van-popup>
```

### Image Uploader
```vue
<van-uploader v-model="fileList" :max-count="9" :after-read="afterRead" multiple />
```
