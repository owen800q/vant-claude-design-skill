# Vant Page Templates & Component Examples

This is a companion reference for the Vant PWA Design Skill with ready-to-use page templates and component compositions.

---

## Complete Page Templates

### 1. Login Page

```vue
<template>
  <div class="login-page">
    <van-nav-bar title="Login" />

    <div class="login-header">
      <van-image
        round
        width="80"
        height="80"
        src="/logo.png"
      />
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
          <van-col>
            <van-button icon="wechat" round />
          </van-col>
          <van-col>
            <van-button icon="alipay" round />
          </van-col>
          <van-col>
            <van-button icon="qq" round />
          </van-col>
        </van-row>
      </div>
    </van-form>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import { showToast } from 'vant';

const form = reactive({
  phone: '',
  password: '',
});
const showPassword = ref(false);
const loading = ref(false);

const onSubmit = async () => {
  loading.value = true;
  // API call here
  loading.value = false;
};
</script>

<style scoped>
.login-page {
  min-height: 100vh;
  background: var(--van-background);
}

.login-header {
  text-align: center;
  padding: 48px 24px 24px;
}

.login-header h1 {
  margin: 16px 0 8px;
  font-size: 24px;
  color: var(--van-text-color);
}

.login-header p {
  color: var(--van-text-color-2);
  font-size: 14px;
}

.login-form {
  padding: 16px;
}

.login-actions {
  margin-top: 24px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.login-footer {
  margin-top: 32px;
}
</style>
```

---

### 2. Home Page with Tab Bar

```vue
<template>
  <div class="home-page">
    <!-- Header with Search -->
    <div class="home-header">
      <van-search
        v-model="searchValue"
        placeholder="Search products..."
        shape="round"
        background="transparent"
      />
    </div>

    <!-- Banner Swiper -->
    <van-swipe :autoplay="3000" indicator-color="white" class="home-banner">
      <van-swipe-item v-for="banner in banners" :key="banner.id">
        <van-image :src="banner.image" fit="cover" height="180" />
      </van-swipe-item>
    </van-swipe>

    <!-- Quick Actions Grid -->
    <van-grid :column-num="5" :border="false" class="home-grid">
      <van-grid-item
        v-for="item in quickActions"
        :key="item.id"
        :icon="item.icon"
        :text="item.text"
        @click="navigateTo(item.path)"
      />
    </van-grid>

    <!-- Notice Bar -->
    <van-notice-bar
      left-icon="volume-o"
      :scrollable="true"
      text="Welcome! New users get 20% off on first order."
    />

    <!-- Product Sections -->
    <div class="home-section">
      <div class="section-header">
        <h3>Hot Deals</h3>
        <van-button size="small" plain @click="viewAll('deals')">
          View All <van-icon name="arrow" />
        </van-button>
      </div>

      <van-row gutter="12">
        <van-col span="12" v-for="product in hotDeals" :key="product.id">
          <van-card
            :price="product.price"
            :origin-price="product.originalPrice"
            :title="product.title"
            :thumb="product.image"
            @click="viewProduct(product.id)"
          >
            <template #tags>
              <van-tag type="danger">Hot</van-tag>
            </template>
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

const banners = ref([
  { id: 1, image: '/banner1.jpg' },
  { id: 2, image: '/banner2.jpg' },
]);

const quickActions = ref([
  { id: 1, icon: 'fire-o', text: 'Hot', path: '/hot' },
  { id: 2, icon: 'gift-o', text: 'New', path: '/new' },
  { id: 3, icon: 'coupon-o', text: 'Coupons', path: '/coupons' },
  { id: 4, icon: 'gem-o', text: 'VIP', path: '/vip' },
  { id: 5, icon: 'more-o', text: 'More', path: '/more' },
]);

const hotDeals = ref([
  { id: 1, title: 'Product 1', price: '99.00', originalPrice: '199.00', image: '/p1.jpg' },
  { id: 2, title: 'Product 2', price: '149.00', originalPrice: '299.00', image: '/p2.jpg' },
]);
</script>

<style scoped>
.home-page {
  padding-bottom: 60px;
  background: var(--van-background);
}

.home-header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--van-primary-color);
  padding: 8px 16px;
}

.home-banner {
  margin: 12px;
  border-radius: var(--van-radius-lg);
  overflow: hidden;
}

.home-grid {
  margin: 12px;
  background: var(--van-background-2);
  border-radius: var(--van-radius-lg);
  padding: 12px 0;
}

.home-section {
  margin: 12px;
  padding: 16px;
  background: var(--van-background-2);
  border-radius: var(--van-radius-lg);
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

.section-header h3 {
  font-size: 16px;
  font-weight: var(--van-font-bold);
  margin: 0;
}
</style>
```

---

### 3. Product List Page

```vue
<template>
  <div class="product-list-page">
    <van-nav-bar
      title="Products"
      left-arrow
      @click-left="goBack"
      fixed
      placeholder
    />

    <!-- Filter Tabs -->
    <van-tabs v-model:active="activeFilter" sticky offset-top="46">
      <van-tab title="All" name="all" />
      <van-tab title="Hot" name="hot" />
      <van-tab title="New" name="new" />
      <van-tab title="Price ↑" name="price_asc" />
      <van-tab title="Price ↓" name="price_desc" />
    </van-tabs>

    <!-- Product Grid with Pull Refresh -->
    <van-pull-refresh v-model="refreshing" @refresh="onRefresh">
      <van-list
        v-model:loading="loading"
        :finished="finished"
        finished-text="No more products"
        @load="loadMore"
      >
        <van-row gutter="8" class="product-grid">
          <van-col span="12" v-for="product in products" :key="product.id">
            <div class="product-card" @click="viewProduct(product.id)">
              <van-image
                :src="product.image"
                fit="cover"
                width="100%"
                height="180"
                lazy-load
              >
                <template #loading>
                  <van-loading type="spinner" size="24" />
                </template>
              </van-image>

              <div class="product-info">
                <p class="product-title van-multi-ellipsis--l2">{{ product.title }}</p>
                <div class="product-price">
                  <span class="current-price">¥{{ product.price }}</span>
                  <span class="original-price" v-if="product.originalPrice">
                    ¥{{ product.originalPrice }}
                  </span>
                </div>
                <div class="product-meta">
                  <van-tag plain size="small">Free Shipping</van-tag>
                  <span class="sales">{{ product.sales }} sold</span>
                </div>
              </div>
            </div>
          </van-col>
        </van-row>
      </van-list>
    </van-pull-refresh>

    <!-- Filter Action Sheet -->
    <van-action-sheet
      v-model:show="showFilter"
      title="Filter"
    >
      <div class="filter-content">
        <van-cell-group>
          <van-cell title="Price Range">
            <van-slider v-model="priceRange" range :max="1000" />
          </van-cell>
          <van-cell title="Brand">
            <van-checkbox-group v-model="selectedBrands" direction="horizontal">
              <van-checkbox name="a">Brand A</van-checkbox>
              <van-checkbox name="b">Brand B</van-checkbox>
            </van-checkbox-group>
          </van-cell>
        </van-cell-group>
        <van-button type="primary" block @click="applyFilter">Apply</van-button>
      </div>
    </van-action-sheet>

    <!-- Floating Filter Button -->
    <van-floating-bubble icon="filter-o" @click="showFilter = true" />
  </div>
</template>

<script setup>
import { ref } from 'vue';

const activeFilter = ref('all');
const refreshing = ref(false);
const loading = ref(false);
const finished = ref(false);
const showFilter = ref(false);
const priceRange = ref([0, 500]);
const selectedBrands = ref([]);

const products = ref([]);

const loadMore = async () => {
  // Load more products
  loading.value = false;
};

const onRefresh = async () => {
  products.value = [];
  finished.value = false;
  await loadMore();
  refreshing.value = false;
};
</script>

<style scoped>
.product-list-page {
  min-height: 100vh;
  background: var(--van-background);
}

.product-grid {
  padding: 8px;
}

.product-card {
  background: var(--van-background-2);
  border-radius: var(--van-radius-lg);
  overflow: hidden;
  margin-bottom: 8px;
}

.product-info {
  padding: 8px 12px 12px;
}

.product-title {
  font-size: 13px;
  color: var(--van-text-color);
  margin: 0 0 8px;
  height: 36px;
}

.product-price {
  margin-bottom: 6px;
}

.current-price {
  font-size: 16px;
  font-weight: var(--van-font-bold);
  color: var(--van-danger-color);
}

.original-price {
  font-size: 12px;
  color: var(--van-text-color-3);
  text-decoration: line-through;
  margin-left: 4px;
}

.product-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.sales {
  font-size: 11px;
  color: var(--van-text-color-3);
}

.filter-content {
  padding: 16px;
}
</style>
```

---

### 4. Product Detail Page

```vue
<template>
  <div class="product-detail-page">
    <!-- Image Gallery -->
    <van-swipe :autoplay="0" indicator-color="white">
      <van-swipe-item v-for="(img, index) in product.images" :key="index">
        <van-image :src="img" fit="cover" height="375" @click="previewImages(index)" />
      </van-swipe-item>
    </van-swipe>

    <!-- Product Info -->
    <div class="product-info-card">
      <div class="price-row">
        <span class="current-price">¥{{ product.price }}</span>
        <span class="original-price">¥{{ product.originalPrice }}</span>
        <van-tag type="danger" round>{{ product.discount }}% OFF</van-tag>
      </div>

      <h1 class="product-title">{{ product.title }}</h1>
      <p class="product-subtitle">{{ product.subtitle }}</p>

      <van-row class="stats-row">
        <van-col span="8">
          <span class="stat-value">{{ product.sales }}</span>
          <span class="stat-label">Sold</span>
        </van-col>
        <van-col span="8">
          <span class="stat-value">{{ product.favorites }}</span>
          <span class="stat-label">Favorites</span>
        </van-col>
        <van-col span="8">
          <span class="stat-value">{{ product.rating }}</span>
          <span class="stat-label">Rating</span>
        </van-col>
      </van-row>
    </div>

    <!-- Options -->
    <van-cell-group inset class="options-card">
      <van-cell title="Specification" is-link @click="showSku = true">
        <template #value>
          <span v-if="selectedSku">{{ selectedSku.name }}</span>
          <span v-else class="placeholder">Select</span>
        </template>
      </van-cell>
      <van-cell title="Delivery" is-link>
        <template #value>
          <span>Free shipping to {{ address }}</span>
        </template>
      </van-cell>
      <van-cell title="Service" is-link>
        <template #value>
          <van-tag plain size="small" style="margin-right: 4px">7-day return</van-tag>
          <van-tag plain size="small">Authentic</van-tag>
        </template>
      </van-cell>
    </van-cell-group>

    <!-- Reviews Preview -->
    <div class="reviews-card">
      <van-cell title="Reviews" :value="`${product.reviewCount} reviews`" is-link />
      <div class="review-item" v-for="review in reviews" :key="review.id">
        <div class="review-header">
          <van-image round width="32" height="32" :src="review.avatar" />
          <span class="reviewer-name">{{ review.name }}</span>
          <van-rate v-model="review.rating" readonly size="12" />
        </div>
        <p class="review-content van-multi-ellipsis--l2">{{ review.content }}</p>
      </div>
    </div>

    <!-- Product Description -->
    <div class="description-card">
      <van-cell title="Product Details" />
      <div class="description-content" v-html="product.description"></div>
    </div>

    <!-- Bottom Action Bar -->
    <van-action-bar safe-area-inset-bottom>
      <van-action-bar-icon icon="chat-o" text="Chat" @click="openChat" />
      <van-action-bar-icon icon="cart-o" text="Cart" :badge="cartCount" @click="goToCart" />
      <van-action-bar-icon :icon="isFavorite ? 'star' : 'star-o'" text="Save" @click="toggleFavorite" />
      <van-action-bar-button type="warning" text="Add to Cart" @click="showSku = true" />
      <van-action-bar-button type="danger" text="Buy Now" @click="buyNow" />
    </van-action-bar>

    <!-- SKU Selector -->
    <van-sku
      v-model:show="showSku"
      :sku="sku"
      :goods="goods"
      :goods-id="product.id"
      :hide-stock="false"
      :quota="0"
      :quota-used="0"
      @buy-clicked="onBuyClicked"
      @add-cart="onAddCart"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { showImagePreview, showToast } from 'vant';

const product = ref({
  id: 1,
  title: 'Premium Wireless Headphones',
  subtitle: 'Active noise cancellation, 30h battery',
  price: '299.00',
  originalPrice: '599.00',
  discount: 50,
  sales: '10k+',
  favorites: '5.2k',
  rating: '4.9',
  reviewCount: 2345,
  images: ['/p1.jpg', '/p2.jpg', '/p3.jpg'],
  description: '<p>Product description HTML...</p>',
});

const showSku = ref(false);
const isFavorite = ref(false);
const cartCount = ref(2);

const previewImages = (index) => {
  showImagePreview({
    images: product.value.images,
    startPosition: index,
  });
};

const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value;
  showToast(isFavorite.value ? 'Added to favorites' : 'Removed');
};
</script>

<style scoped>
.product-detail-page {
  padding-bottom: 60px;
  background: var(--van-background);
}

.product-info-card,
.options-card,
.reviews-card,
.description-card {
  margin: 12px;
  background: var(--van-background-2);
  border-radius: var(--van-radius-lg);
  overflow: hidden;
}

.product-info-card {
  padding: 16px;
}

.price-row {
  display: flex;
  align-items: baseline;
  gap: 8px;
  margin-bottom: 12px;
}

.current-price {
  font-size: 28px;
  font-weight: var(--van-font-bold);
  color: var(--van-danger-color);
}

.original-price {
  font-size: 14px;
  color: var(--van-text-color-3);
  text-decoration: line-through;
}

.product-title {
  font-size: 16px;
  font-weight: var(--van-font-bold);
  margin: 0 0 8px;
}

.product-subtitle {
  font-size: 13px;
  color: var(--van-text-color-2);
  margin: 0;
}

.stats-row {
  margin-top: 16px;
  text-align: center;
}

.stat-value {
  display: block;
  font-size: 16px;
  font-weight: var(--van-font-bold);
}

.stat-label {
  font-size: 12px;
  color: var(--van-text-color-3);
}

.review-item {
  padding: 12px 16px;
  border-top: 1px solid var(--van-border-color);
}

.review-header {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
}

.reviewer-name {
  flex: 1;
  font-size: 13px;
}

.review-content {
  font-size: 13px;
  color: var(--van-text-color-2);
  margin: 0;
}

.description-content {
  padding: 16px;
}

.placeholder {
  color: var(--van-text-color-3);
}
</style>
```

---

### 5. Cart Page

```vue
<template>
  <div class="cart-page">
    <van-nav-bar title="Shopping Cart" />

    <!-- Empty State -->
    <van-empty
      v-if="cartItems.length === 0"
      description="Your cart is empty"
      image="https://img.yzcdn.cn/vant/empty-image-default.png"
    >
      <van-button round type="primary" @click="goShopping">Go Shopping</van-button>
    </van-empty>

    <!-- Cart Items -->
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
                <van-stepper v-model="item.quantity" :min="1" :max="99" theme="round" />
              </div>
            </div>
          </div>

          <template #right>
            <van-button square type="danger" text="Delete" @click="removeItem(item.id)" />
          </template>
        </van-swipe-cell>
      </van-checkbox-group>

      <!-- Recommended Products -->
      <div class="recommend-section">
        <van-divider>You May Also Like</van-divider>
        <van-row gutter="8">
          <van-col span="12" v-for="product in recommended" :key="product.id">
            <van-card
              :price="product.price"
              :title="product.title"
              :thumb="product.image"
              @click="viewProduct(product.id)"
            />
          </van-col>
        </van-row>
      </div>
    </div>

    <!-- Submit Bar -->
    <van-submit-bar
      v-if="cartItems.length > 0"
      :price="totalPrice"
      button-text="Checkout"
      :disabled="selectedItems.length === 0"
      @submit="onCheckout"
      safe-area-inset-bottom
    >
      <van-checkbox v-model="allSelected" @change="toggleAll">All</van-checkbox>
    </van-submit-bar>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';
import { showConfirmDialog, showToast } from 'vant';

const cartItems = ref([
  {
    id: 1,
    title: 'Wireless Headphones with Noise Cancellation',
    skuName: 'Black, Standard',
    price: '299.00',
    quantity: 1,
    image: '/p1.jpg',
  },
  {
    id: 2,
    title: 'Smart Watch Series 5',
    skuName: 'Silver, 44mm',
    price: '1299.00',
    quantity: 2,
    image: '/p2.jpg',
  },
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

watch(selectedItems, (val) => {
  allSelected.value = val.length === cartItems.value.length && cartItems.value.length > 0;
});

const removeItem = async (id) => {
  try {
    await showConfirmDialog({ title: 'Remove item?', message: 'This item will be removed from cart' });
    cartItems.value = cartItems.value.filter(i => i.id !== id);
    selectedItems.value = selectedItems.value.filter(i => i !== id);
    showToast('Removed');
  } catch {}
};

const onCheckout = () => {
  // Navigate to checkout
};
</script>

<style scoped>
.cart-page {
  min-height: 100vh;
  background: var(--van-background);
  padding-bottom: 60px;
}

.cart-item {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  padding: 16px;
  background: var(--van-background-2);
}

.item-info {
  flex: 1;
  min-width: 0;
}

.item-title {
  font-size: 14px;
  margin: 0 0 4px;
  height: 40px;
}

.item-sku {
  font-size: 12px;
  color: var(--van-text-color-3);
  margin: 0 0 8px;
}

.item-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.item-price {
  font-size: 16px;
  font-weight: var(--van-font-bold);
  color: var(--van-danger-color);
}

.recommend-section {
  padding: 0 12px;
}
</style>
```

---

### 6. Profile/Settings Page

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
      <van-icon name="setting-o" size="24" @click="goToSettings" />
    </div>

    <!-- Stats Cards -->
    <van-grid :column-num="4" :border="false" class="stats-grid">
      <van-grid-item @click="goToOrders('all')">
        <template #icon>
          <van-badge :content="orderCounts.all || ''">
            <van-icon name="orders-o" size="24" />
          </van-badge>
        </template>
        <template #text>Orders</template>
      </van-grid-item>
      <van-grid-item @click="goToOrders('pending')">
        <template #icon>
          <van-badge :content="orderCounts.pending || ''">
            <van-icon name="pending-payment" size="24" />
          </van-badge>
        </template>
        <template #text>Pending</template>
      </van-grid-item>
      <van-grid-item @click="goToOrders('shipping')">
        <template #icon>
          <van-badge :content="orderCounts.shipping || ''">
            <van-icon name="logistics" size="24" />
          </van-badge>
        </template>
        <template #text>Shipping</template>
      </van-grid-item>
      <van-grid-item @click="goToOrders('review')">
        <template #icon>
          <van-badge :content="orderCounts.review || ''">
            <van-icon name="comment-o" size="24" />
          </van-badge>
        </template>
        <template #text>Review</template>
      </van-grid-item>
    </van-grid>

    <!-- Menu Sections -->
    <van-cell-group inset class="menu-section">
      <van-cell title="My Favorites" icon="star-o" is-link to="/favorites" />
      <van-cell title="Browsing History" icon="browsing-history-o" is-link to="/history" />
      <van-cell title="Coupons" icon="coupon-o" is-link to="/coupons">
        <template #value>
          <van-tag type="danger" round v-if="couponCount">{{ couponCount }}</van-tag>
        </template>
      </van-cell>
      <van-cell title="My Reviews" icon="comment-o" is-link to="/my-reviews" />
    </van-cell-group>

    <van-cell-group inset class="menu-section">
      <van-cell title="Shipping Address" icon="location-o" is-link to="/addresses" />
      <van-cell title="Payment Methods" icon="credit-pay" is-link to="/payment" />
      <van-cell title="Account Security" icon="shield-o" is-link to="/security" />
    </van-cell-group>

    <van-cell-group inset class="menu-section">
      <van-cell title="Help Center" icon="question-o" is-link to="/help" />
      <van-cell title="About" icon="info-o" is-link to="/about" />
      <van-cell title="Feedback" icon="smile-comment-o" is-link @click="showFeedback" />
    </van-cell-group>

    <!-- Logout Button -->
    <div class="logout-section">
      <van-button plain block type="danger" @click="logout">Log Out</van-button>
    </div>

    <!-- Dark Mode Toggle -->
    <van-cell-group inset class="menu-section">
      <van-cell title="Dark Mode" icon="eye-o">
        <template #right-icon>
          <van-switch v-model="isDarkMode" size="24" @change="toggleDarkMode" />
        </template>
      </van-cell>
    </van-cell-group>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { showConfirmDialog } from 'vant';

const user = ref({
  name: 'John Doe',
  phone: '+1 234 567 8900',
  avatar: '/avatar.jpg',
});

const orderCounts = ref({
  all: 12,
  pending: 2,
  shipping: 1,
  review: 3,
});

const couponCount = ref(5);
const isDarkMode = ref(false);

const toggleDarkMode = (checked) => {
  document.documentElement.classList.toggle('van-theme-dark', checked);
};

const logout = async () => {
  try {
    await showConfirmDialog({ title: 'Log Out', message: 'Are you sure?' });
    // Handle logout
  } catch {}
};
</script>

<style scoped>
.profile-page {
  min-height: 100vh;
  background: var(--van-background);
  padding-bottom: 24px;
}

.profile-header {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 24px 16px;
  background: linear-gradient(135deg, var(--van-primary-color), #4facfe);
  color: white;
}

.user-info {
  flex: 1;
}

.user-info h2 {
  margin: 0 0 4px;
  font-size: 20px;
}

.user-info p {
  margin: 0;
  opacity: 0.8;
  font-size: 14px;
}

.stats-grid {
  margin: -20px 12px 12px;
  background: var(--van-background-2);
  border-radius: var(--van-radius-lg);
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.08);
}

.menu-section {
  margin: 12px;
}

.logout-section {
  padding: 24px 16px;
}
</style>
```

---

## Component Compositions

### Address Selector

```vue
<template>
  <van-address-list
    v-model="chosenAddressId"
    :list="addressList"
    default-tag-text="Default"
    @add="onAddAddress"
    @edit="onEditAddress"
  />
</template>
```

### Coupon Selector

```vue
<template>
  <van-coupon-cell :coupons="coupons" :chosen-coupon="chosenCoupon" @click="showCoupons = true" />

  <van-popup v-model:show="showCoupons" position="bottom" round style="height: 90%">
    <van-coupon-list
      :coupons="coupons"
      :chosen-coupon="chosenCoupon"
      @change="onCouponChange"
      @exchange="onExchange"
    />
  </van-popup>
</template>
```

### Cascader (Area Picker)

```vue
<template>
  <van-field
    v-model="areaText"
    is-link
    readonly
    label="Area"
    placeholder="Select area"
    @click="showArea = true"
  />

  <van-popup v-model:show="showArea" position="bottom" round>
    <van-cascader
      v-model="areaCode"
      title="Select Area"
      :options="areaOptions"
      @close="showArea = false"
      @finish="onAreaFinish"
    />
  </van-popup>
</template>
```

### Image Uploader

```vue
<template>
  <van-uploader
    v-model="fileList"
    :max-count="9"
    :after-read="afterRead"
    :before-delete="beforeDelete"
    multiple
  />
</template>
```

### Date Time Picker

```vue
<template>
  <van-field
    v-model="dateText"
    is-link
    readonly
    label="Date"
    @click="showPicker = true"
  />

  <van-popup v-model:show="showPicker" position="bottom" round>
    <van-date-picker
      v-model="selectedDate"
      title="Select Date"
      :min-date="minDate"
      :max-date="maxDate"
      @confirm="onConfirm"
      @cancel="showPicker = false"
    />
  </van-popup>
</template>
```

---

## PWA Service Worker Setup

```js
// sw.js - Basic service worker for PWA
const CACHE_NAME = 'vant-pwa-v1';
const urlsToCache = [
  '/',
  '/index.html',
  '/css/app.css',
  '/js/app.js',
];

self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME)
      .then((cache) => cache.addAll(urlsToCache))
  );
});

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request)
      .then((response) => response || fetch(event.request))
  );
});
```

---

## Recommended Folder Structure

```
src/
├── assets/
│   ├── images/
│   └── styles/
│       ├── variables.css      # Theme overrides
│       └── global.css
├── components/
│   ├── common/               # Shared components
│   ├── layout/               # Layout components
│   └── business/             # Business components
├── composables/              # Vue composables
├── pages/
│   ├── home/
│   ├── product/
│   ├── cart/
│   ├── order/
│   └── profile/
├── router/
├── stores/                   # Pinia stores
├── utils/
├── App.vue
└── main.js
```
