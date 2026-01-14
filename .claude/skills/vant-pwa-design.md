# Vant PWA & Mobile App Design Skill

You are an expert in designing and building Progressive Web Apps (PWA) and mobile applications using **Vant** - a lightweight, customizable Vue.js mobile UI library with 80+ high-quality components.

## When to Use This Skill

Use this skill when the user wants to:
- Design or build a mobile-first web application
- Create a Progressive Web App (PWA)
- Build Vue.js mobile interfaces
- Implement mobile UI components and patterns
- Work with Vant component library
- Create responsive mobile layouts
- Implement dark mode or theming

---

## Vant Design System Reference

### Design Tokens (CSS Variables)

All Vant design tokens use CSS custom properties with `--van-` prefix for easy customization.

#### Color Palette

```css
/* Base Colors */
--van-black: #000;
--van-white: #fff;

/* Grayscale (8 steps) */
--van-gray-1: #f7f8fa;  /* Lightest - backgrounds */
--van-gray-2: #f2f3f5;  /* Active states */
--van-gray-3: #ebedf0;  /* Borders */
--van-gray-4: #dcdee0;
--van-gray-5: #c8c9cc;  /* Placeholder text */
--van-gray-6: #969799;  /* Secondary text */
--van-gray-7: #646566;
--van-gray-8: #323233;  /* Primary text */

/* Semantic Colors */
--van-primary-color: #1989fa;   /* Blue - main actions */
--van-success-color: #07c160;   /* Green - positive */
--van-danger-color: #ee0a24;    /* Red - destructive */
--van-warning-color: #ff976a;   /* Orange - caution */

/* Gradient Colors */
--van-gradient-red: linear-gradient(to right, #ff6034, #ee0a24);
--van-gradient-orange: linear-gradient(to right, #ffd01e, #ff8917);

/* Text Colors */
--van-text-color: #323233;      /* Primary text */
--van-text-color-2: #969799;    /* Secondary text */
--van-text-color-3: #c8c9cc;    /* Tertiary/placeholder */

/* Background Colors */
--van-background: #f7f8fa;      /* Page background */
--van-background-2: #fff;       /* Card background */
--van-background-3: #fff;       /* Elevated background */
```

#### Typography

```css
/* Font Family */
--van-base-font: -apple-system, BlinkMacSystemFont, 'Helvetica Neue',
                 Helvetica, Segoe UI, Arial, Roboto, 'PingFang SC',
                 'miui', 'Hiragino Sans GB', 'Microsoft Yahei', sans-serif;

/* Price Font (for e-commerce) */
--van-price-font: avenir-heavy, 'PingFang SC', helvetica neue, arial, sans-serif;

/* Font Sizes */
--van-font-size-xs: 10px;
--van-font-size-sm: 12px;
--van-font-size-md: 14px;  /* Default body text */
--van-font-size-lg: 16px;

/* Font Weight */
--van-font-bold: 600;

/* Line Heights */
--van-line-height-xs: 14px;
--van-line-height-sm: 18px;
--van-line-height-md: 20px;
--van-line-height-lg: 22px;
```

#### Spacing Scale

```css
/* Padding Scale */
--van-padding-base: 4px;   /* Smallest unit */
--van-padding-xs: 8px;
--van-padding-sm: 12px;
--van-padding-md: 16px;    /* Default */
--van-padding-lg: 24px;
--van-padding-xl: 32px;
```

#### Border & Radius

```css
/* Border */
--van-border-width: 1px;
--van-border-color: #ebedf0;

/* Border Radius */
--van-radius-sm: 2px;
--van-radius-md: 4px;
--van-radius-lg: 8px;
--van-radius-max: 999px;  /* Fully rounded (pills) */
```

#### Animation

```css
/* Duration */
--van-duration-base: 0.3s;
--van-duration-fast: 0.2s;

/* Easing */
--van-ease-out: ease-out;
--van-ease-in: ease-in;
```

#### Opacity States

```css
--van-active-opacity: 0.6;    /* Pressed state */
--van-disabled-opacity: 0.5;  /* Disabled state */
```

---

### Dark Mode Support

Vant supports dark mode through the ConfigProvider component:

```vue
<template>
  <van-config-provider :theme="isDark ? 'dark' : 'light'">
    <App />
  </van-config-provider>
</template>
```

**Dark Mode Color Overrides:**
```css
.van-theme-dark {
  --van-text-color: #f5f5f5;
  --van-text-color-2: #707070;
  --van-text-color-3: #4d4d4d;
  --van-border-color: #3a3a3c;
  --van-active-color: #3a3a3c;
  --van-background: #000;
  --van-background-2: #1c1c1e;
  --van-background-3: #37363b;
}
```

---

### Component Size Standards

#### Button Sizes
| Size | Height | Use Case |
|------|--------|----------|
| mini | 24px | Inline actions, tags |
| small | 32px | Secondary actions |
| normal | 44px | Default touch target |
| large | 50px | Primary CTA, full-width |

#### Touch Target Minimum
Always maintain **44px minimum** touch target for accessibility on mobile.

---

### Layout Patterns

#### 1. Grid Layout (Icon Grids, Product Grids)
```vue
<van-grid :column-num="4" :gutter="10">
  <van-grid-item v-for="item in items" :key="item.id" :icon="item.icon" :text="item.text" />
</van-grid>
```

#### 2. Row/Col Flex Layout (24-Column System)
```vue
<van-row :gutter="[12, 12]">
  <van-col span="12">Half width</van-col>
  <van-col span="12">Half width</van-col>
  <van-col span="8">One third</van-col>
  <van-col span="16">Two thirds</van-col>
</van-row>
```

#### 3. Cell Lists (Settings, Menus)
```vue
<van-cell-group inset>
  <van-cell title="Profile" is-link to="/profile" />
  <van-cell title="Settings" is-link to="/settings" />
  <van-cell title="Help" is-link to="/help" />
</van-cell-group>
```

#### 4. Safe Area Handling
```vue
<!-- For notch and home indicator -->
<div class="van-safe-area-top"></div>
<div class="van-safe-area-bottom"></div>
```

---

### Common Mobile UI Patterns

#### Navigation Patterns

**1. Tab Bar (Bottom Navigation)**
```vue
<van-tabbar v-model="active" fixed safe-area-inset-bottom>
  <van-tabbar-item icon="home-o">Home</van-tabbar-item>
  <van-tabbar-item icon="search">Discover</van-tabbar-item>
  <van-tabbar-item icon="friends-o">Messages</van-tabbar-item>
  <van-tabbar-item icon="setting-o">Profile</van-tabbar-item>
</van-tabbar>
```

**2. NavBar (Top Navigation)**
```vue
<van-nav-bar
  title="Page Title"
  left-arrow
  @click-left="onBack"
  safe-area-inset-top
>
  <template #right>
    <van-icon name="search" size="18" />
  </template>
</van-nav-bar>
```

**3. Tabs (Content Switching)**
```vue
<van-tabs v-model:active="activeTab" sticky>
  <van-tab title="All">Content 1</van-tab>
  <van-tab title="Popular">Content 2</van-tab>
  <van-tab title="New">Content 3</van-tab>
</van-tabs>
```

#### Action Patterns

**1. Action Sheet**
```vue
<van-action-sheet
  v-model:show="showActions"
  :actions="actions"
  cancel-text="Cancel"
  close-on-click-action
  @select="onSelect"
/>
```

**2. Dialog**
```vue
<van-dialog
  v-model:show="showDialog"
  title="Confirm"
  message="Are you sure?"
  show-cancel-button
  @confirm="onConfirm"
/>
```

**3. Toast**
```vue
<script setup>
import { showToast, showSuccessToast, showFailToast, showLoadingToast } from 'vant';

showToast('Message');
showSuccessToast('Success');
showFailToast('Failed');
showLoadingToast({ message: 'Loading...', forbidClick: true });
</script>
```

#### Form Patterns

**1. Form with Validation**
```vue
<van-form @submit="onSubmit">
  <van-cell-group inset>
    <van-field
      v-model="username"
      name="username"
      label="Username"
      placeholder="Enter username"
      :rules="[{ required: true, message: 'Required' }]"
    />
    <van-field
      v-model="password"
      type="password"
      name="password"
      label="Password"
      placeholder="Enter password"
      :rules="[{ required: true, message: 'Required' }]"
    />
  </van-cell-group>
  <div style="margin: 16px;">
    <van-button round block type="primary" native-type="submit">
      Submit
    </van-button>
  </div>
</van-form>
```

**2. Search Bar**
```vue
<van-search
  v-model="searchValue"
  show-action
  placeholder="Search..."
  @search="onSearch"
  @cancel="onCancel"
/>
```

#### List Patterns

**1. Pull Refresh + Infinite Scroll**
```vue
<van-pull-refresh v-model="refreshing" @refresh="onRefresh">
  <van-list
    v-model:loading="loading"
    :finished="finished"
    finished-text="No more data"
    @load="onLoad"
  >
    <van-cell v-for="item in list" :key="item.id" :title="item.title" />
  </van-list>
</van-pull-refresh>
```

**2. Swipe Cell (Swipe Actions)**
```vue
<van-swipe-cell>
  <van-cell title="Item" value="Content" />
  <template #right>
    <van-button square type="danger" text="Delete" />
    <van-button square type="primary" text="Edit" />
  </template>
</van-swipe-cell>
```

#### E-commerce Patterns

**1. Product Card**
```vue
<van-card
  num="2"
  price="2.00"
  origin-price="10.00"
  title="Product Title"
  thumb="https://example.com/image.jpg"
>
  <template #tags>
    <van-tag plain type="primary">Tag</van-tag>
  </template>
  <template #footer>
    <van-button size="mini">Add to Cart</van-button>
  </template>
</van-card>
```

**2. Submit Bar (Checkout)**
```vue
<van-submit-bar
  :price="3050"
  button-text="Checkout"
  @submit="onSubmit"
>
  <van-checkbox v-model="checked">Select All</van-checkbox>
</van-submit-bar>
```

**3. Sku Selector**
```vue
<van-sku
  v-model:show="showSku"
  :sku="sku"
  :goods="goods"
  @buy-clicked="onBuyClicked"
  @add-cart="onAddCart"
/>
```

---

### PWA Best Practices

#### 1. Manifest Configuration
```json
{
  "name": "My Vant App",
  "short_name": "VantApp",
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#1989fa",
  "background_color": "#ffffff",
  "icons": [
    {
      "src": "/icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "/icons/icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
```

#### 2. Viewport Configuration
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
<meta name="theme-color" content="#1989fa">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
```

#### 3. Safe Area CSS
```css
/* For iPhone X+ notch handling */
.app-container {
  padding-top: constant(safe-area-inset-top);
  padding-top: env(safe-area-inset-top);
  padding-bottom: constant(safe-area-inset-bottom);
  padding-bottom: env(safe-area-inset-bottom);
}
```

---

### Customizing Theme

#### Method 1: CSS Variable Override
```css
:root {
  --van-primary-color: #7232dd;
  --van-success-color: #00b578;
  --van-button-primary-background: #7232dd;
}
```

#### Method 2: ConfigProvider (Runtime)
```vue
<van-config-provider :theme-vars="themeVars">
  <App />
</van-config-provider>

<script setup>
const themeVars = {
  primaryColor: '#7232dd',
  buttonPrimaryBackground: '#7232dd',
  buttonPrimaryBorderColor: '#7232dd',
};
</script>
```

#### Method 3: Less Variables (Build Time)
```less
// vant.theme.less
@primary-color: #7232dd;
@success-color: #00b578;
```

---

### Utility Classes

#### Text Truncation
```html
<!-- Single line ellipsis -->
<div class="van-ellipsis">Long text that will be truncated...</div>

<!-- Multi-line ellipsis (2 lines) -->
<div class="van-multi-ellipsis--l2">Long text that spans multiple lines...</div>

<!-- Multi-line ellipsis (3 lines) -->
<div class="van-multi-ellipsis--l3">Even longer text...</div>
```

#### Hairline Borders
```html
<!-- 0.5px borders for Retina displays -->
<div class="van-hairline--top">Top border</div>
<div class="van-hairline--bottom">Bottom border</div>
<div class="van-hairline--surround">All borders</div>
<div class="van-hairline--top-bottom">Top and bottom</div>
```

#### Touch Feedback
```html
<!-- Adds opacity feedback on press -->
<div class="van-haptics-feedback">Clickable element</div>
```

---

### Animation Classes

Vant provides built-in Vue transitions:

```vue
<!-- Fade -->
<transition name="van-fade">
  <div v-if="show">Fades in/out</div>
</transition>

<!-- Slide Up -->
<transition name="van-slide-up">
  <div v-if="show">Slides up from bottom</div>
</transition>

<!-- Slide Down -->
<transition name="van-slide-down">
  <div v-if="show">Slides down from top</div>
</transition>

<!-- Slide Left/Right -->
<transition name="van-slide-left">
  <div v-if="show">Slides from right</div>
</transition>
```

---

### Icon Usage

Vant includes 100+ icons via icon font:

```vue
<!-- Basic icon -->
<van-icon name="chat-o" />

<!-- Sized and colored -->
<van-icon name="like" size="24" color="#ee0a24" />

<!-- With badge -->
<van-icon name="cart-o" badge="5" />

<!-- With dot indicator -->
<van-icon name="bell" dot />

<!-- Custom image as icon -->
<van-icon name="https://example.com/icon.png" />
```

**Common Icons:**
- Navigation: `arrow`, `arrow-left`, `cross`, `search`
- Actions: `plus`, `minus`, `edit`, `delete`, `share`
- Status: `success`, `fail`, `warning-o`, `info-o`
- Objects: `cart-o`, `home-o`, `user-o`, `setting-o`
- Communication: `chat-o`, `phone-o`, `envelop-o`

---

### Best Practices Summary

1. **Touch Targets**: Minimum 44px for all interactive elements
2. **Safe Areas**: Always handle notch/home indicator with safe-area classes
3. **Loading States**: Show loading indicators for async operations
4. **Error Handling**: Use Toast for transient feedback, Dialog for confirmations
5. **Scrolling**: Use native scroll with `-webkit-overflow-scrolling: touch`
6. **Images**: Use lazy loading (`<van-image lazy-load />`)
7. **Lists**: Implement virtual scrolling for long lists
8. **Forms**: Provide clear validation feedback
9. **Gestures**: Support swipe actions where appropriate
10. **Performance**: Use on-demand import to reduce bundle size

---

### Project Setup

#### Vue 3 + Vite
```bash
npm create vue@latest my-vant-app
cd my-vant-app
npm install vant
npm install -D @vant/auto-import-resolver unplugin-vue-components unplugin-auto-import
```

**vite.config.js:**
```js
import { defineConfig } from 'vite';
import vue from '@vitejs/plugin-vue';
import Components from 'unplugin-vue-components/vite';
import { VantResolver } from '@vant/auto-import-resolver';

export default defineConfig({
  plugins: [
    vue(),
    Components({
      resolvers: [VantResolver()],
    }),
  ],
});
```

**main.js:**
```js
import { createApp } from 'vue';
import App from './App.vue';

// Import base styles (required)
import 'vant/lib/index.css';

createApp(App).mount('#app');
```
