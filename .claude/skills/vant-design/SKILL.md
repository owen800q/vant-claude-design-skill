---
name: vant-design
description: Design and build mobile apps, PWAs, and WeChat Mini Programs using Vant UI and WeChat/WeUI design guidelines. Use for mobile-first web apps, Vue.js mobile interfaces, HTML prototypes, Vant components, WeChat Mini Program design compliance, responsive layouts, dark mode, theming, tab bars, navigation, forms, lists, e-commerce pages, and mobile UI patterns. Supports Vue.js development, pure HTML/CSS prototyping, and WeChat ecosystem design standards.
---

# Vant Mobile App Design System

You are an expert in designing and building mobile applications using **Vant** - a lightweight Vue.js mobile UI library with 80+ components. This skill covers Vue.js development, pure HTML/CSS prototyping, and **WeChat Mini Program design guidelines** compliance. When designing for the WeChat ecosystem, always follow the WeChat Mini Program design principles and WeUI specifications documented below.

## Quick Start

### For HTML Prototypes (No Build Tools)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
  <title>Mobile App</title>
  <link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/vant@4/lib/index.css">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', sans-serif;
      background: var(--van-background);
      color: var(--van-text-color);
    }
    .mobile-container { max-width: 414px; margin: 0 auto; min-height: 100vh; }
  </style>
</head>
<body>
  <div class="mobile-container">
    <!-- Content here -->
  </div>
</body>
</html>
```

### For Vue.js Projects

```bash
npm install vant
```

```js
// main.js
import 'vant/lib/index.css';
```

---

## WeChat Mini Program Design Guidelines (微信小程序设计规范)

Reference: https://developers.weixin.qq.com/miniprogram/design/

When building apps for the WeChat ecosystem or following WeChat-style design patterns, apply these official design principles and specifications. The Vant component library is built to align with these standards.

### Core Design Principles

#### 1. Friendly & Polite (友好礼貌)
- **Clear page focus**: Each page must have one clear focal point to help users understand content immediately
- **Reduce visual noise**: Remove decorative elements unrelated to user decisions or tasks
- **Uninterrupted flows**: Do not inject unrelated content into task flows; keep processes smooth

#### 2. Clear & Explicit (清晰明确)
- **Navigation clarity**: Users must always know where they are, where they can go, and how to go back
- **Back navigation**: Secondary pages must include a back button (top-left corner)
- **WeChat official menu**: Reserve space for the top-right system menu (cannot be customized); it offers light/dark color variants
- **Tab navigation**: 2–5 tabs maximum, **4 recommended**; can be positioned top or bottom; only one tab group per page

#### 3. Convenient & Elegant (便捷优雅)
- **Minimize input**: Use device APIs (camera, location, etc.) instead of manual entry; prefer selection controls over keyboard input; show search history
- **Touch targets**: Clickable areas must be **7–9mm** in physical size (≈44px at standard density) to prevent mistaps
- **Avoid crowded tap areas**: Do not place multiple small interactive elements too close together

#### 4. Unified & Stable (统一稳定)
- **Consistency**: Use the same controls and interaction patterns across all pages
- **Reduce learning cost**: Familiar patterns minimize cognitive load; avoid inventing new interaction paradigms

### WeChat Visual Specifications

#### Design Canvas
- Standard design at **iPhone 6 size: 750×1334px**
- Use **rpx** units for responsive sizing (screen width = 750rpx, so 1px = 1rpx on iPhone 6)

#### Typography (字体规范)

**Font Family:**
```css
font-family: system-ui, -apple-system, 'Helvetica Neue', sans-serif;
/* WeChat defaults to PingFang SC on iOS */
```

**Font Size Scale (based on 750px design / rpx):**

| Usage | pt | rpx | px (375 screen) |
|-------|-----|------|------------------|
| Large title | 20–22 | 40–44 | 20–22 |
| Page title / Nav title | 18 | 36 | 18 |
| Body text / Nav bar title | 17 | 34 | 17 |
| List item text | 16 | 32 | 16 |
| Secondary / auxiliary text | 14 | 28 | 14 |
| Caption / description | 13 | 26 | 13 |
| Minimum / labels / tags | 11–12 | 22–24 | 11–12 |

**Line height:** 1.6 (WeUI default)

#### Color System (颜色规范)

**Text Colors (无彩色):**

| Role | Color Value | Usage |
|------|-------------|-------|
| Primary text (Black) | `rgba(0,0,0,0.9)` / `#000` | Main content, titles |
| Semi-dark text | `rgba(0,0,0,0.7)` | Long-form body content |
| Secondary text (Grey) | `rgba(0,0,0,0.5)` | Subtitles, descriptions |
| Placeholder/timestamp (Light) | `rgba(0,0,0,0.3)` | Timestamps, form defaults |
| Divider lines | `rgba(0,0,0,0.1)` | Separators, borders |

**Functional Colors (有彩色):**

| Role | Color Value | Usage |
|------|-------------|-------|
| Link / Blue | `#10AEFF` | Links, interactive text |
| WeChat brand link | `#576B95` | Article links in WeChat style |
| Success / Green | `#09BB07` | Completion, success states |
| Error / Red | `#F43530` | Errors, destructive actions |
| Warning / Orange | `#F76260` | Warnings |

**States:** Press state = default color at 20% opacity; Disabled state = default color at 10% opacity

**WeUI Background Colors (Light Theme):**
```css
--weui-BG-0: #ededed;   /* Page background */
--weui-BG-1: #f7f7f7;   /* Section background */
--weui-BG-2: #fff;       /* Card / cell background */
--weui-BG-3: #f7f7f7;   /* Secondary section */
--weui-BG-4: #4c4c4c;   /* Dark overlay */
--weui-BG-5: #fff;       /* Surface */
```

**WeUI Brand Colors:**
```css
--weui-BLUE-100: #10aeff;   /* Primary blue */
--weui-BLUE-120: #3fbeff;   /* Blue hover */
--weui-BLUE-170: #b7e6ff;   /* Blue light */
--weui-BLUE-80: #0c8bcc;    /* Blue pressed */
--weui-BLUE-90: #0e9ce6;    /* Blue active */
```

#### Spacing System (间距规范)
- **Base unit: 8px** — all spacing should be multiples of 8
- Module vertical gap: **32rpx** (16px)
- Module horizontal margin: **32rpx** (16px)
- Common spacing values: **8px, 12px, 16px, 24px, 32px**
- Icon-to-text gap: **8px**

#### Navigation Dimensions

| Element | Height (rpx) | Height (px) |
|---------|--------------|-------------|
| Top navigation bar | 128rpx | 64px |
| Tab bar (top/bottom) | 98rpx | 49px |
| Status bar (iOS) | 40rpx | 20px |

#### Icon Specifications
- Standard icon sizes: **24, 32, 48, 56, 64, 72, 80** (all multiples of 8)
- Default in-app icon: **100×100px** (50×50pt)
- Icons should maintain clear visual meaning at all sizes

#### Button Specifications (WeUI)
```css
--weui-BTN-HEIGHT: 48px;         /* Large button */
--weui-BTN-HEIGHT-MEDIUM: 40px;  /* Medium button */
--weui-BTN-HEIGHT-SMALL: 32px;   /* Small button */
```

### WeChat Loading & Feedback Patterns

| Pattern | When to Use | Implementation |
|---------|-------------|----------------|
| Launch screen | App startup | Brand logo (controlled by WeChat) |
| Pull-to-refresh | List/feed refresh | Standard WeChat pull-down style |
| Page loading | Full page load | Simplified skeleton / spinner animation |
| Modal loading | Global blocking operation | Use sparingly — `showLoadingToast()` |
| Partial loading | Section content load | **Preferred** — localized spinner within affected area |
| Toast feedback | Action confirmation | Brief toast: `showSuccessToast()` / `showToast()` |
| Result page | Critical operation result | Full-page success/failure state |
| Progress bar | Long operations (upload/download) | Show percentage progress |

**Key rule:** Avoid modal loading overlays for non-global operations. Always prefer localized loading indicators.

### WeChat Error Handling
- Form errors must **clearly identify the problematic field** with inline error messages
- Provide **specific correction guidance** (not just "error occurred")
- Show error summary at top of form when multiple errors exist
- Network errors should offer **retry options**

### WeChat Dark Mode (WeUI)
```html
<!-- Enable dark mode -->
<body data-weui-theme="dark">
```
```css
/* Dark mode automatically switches all --weui-* variables */
/* Key dark mode overrides: */
--weui-BG-0: #111;
--weui-BG-1: #1e1e1e;
--weui-BG-2: #191919;
--weui-BTN-DEFAULT-ACTIVE-BG: hsla(0,0%,100%,.126);
--weui-DIALOG-LINE-COLOR: hsla(0,0%,100%,.1);
```

### Accessibility (适老化设计)
- In elderly-accessible mode, enlarge fonts, icons, and buttons proportionally
- Maintain **minimum contrast ratio of 4.5:1** for text and icon elements
- Ensure touch targets meet or exceed the 7–9mm physical size requirement

### Mapping WeChat Design to Vant Components

| WeChat Pattern | Vant Component | Notes |
|----------------|----------------|-------|
| Top navigation bar | `van-nav-bar` | Set `left-arrow` for back button |
| Bottom tab navigation | `van-tabbar` | 2–5 items, recommend 4 |
| Tab switching (top) | `van-tabs` | Swipeable, scrollable |
| Cell / list item | `van-cell` | Standard list rows |
| Form with validation | `van-form` + `van-field` | Inline error messages |
| Action feedback (toast) | `showToast` / `showSuccessToast` | Brief, non-blocking |
| Modal dialog | `van-dialog` | For critical confirmations |
| Action sheet | `van-action-sheet` | Bottom slide-up options |
| Pull-to-refresh | `van-pull-refresh` | Standard pull-down gesture |
| Loading indicator | `van-loading` | Localized spinner |
| Skeleton screen | `van-skeleton` | Page loading placeholder |
| Search bar | `van-search` | With history suggestions |
| Swipe cell actions | `van-swipe-cell` | Slide to reveal actions |
| Empty state | `van-empty` | When no data available |
| Progress | `van-progress` | Upload/download progress |

---

## Design Tokens (CSS Variables)

### Colors

```css
/* Primary Colors */
--van-primary-color: #1989fa;    /* Blue - main actions */
--van-success-color: #07c160;    /* Green - positive */
--van-danger-color: #ee0a24;     /* Red - destructive */
--van-warning-color: #ff976a;    /* Orange - warning */

/* Text Colors */
--van-text-color: #323233;       /* Primary text */
--van-text-color-2: #969799;     /* Secondary text */
--van-text-color-3: #c8c9cc;     /* Placeholder */

/* Background Colors */
--van-background: #f7f8fa;       /* Page background */
--van-background-2: #fff;        /* Card background */

/* Grayscale */
--van-gray-1: #f7f8fa;  --van-gray-2: #f2f3f5;  --van-gray-3: #ebedf0;
--van-gray-4: #dcdee0;  --van-gray-5: #c8c9cc;  --van-gray-6: #969799;
--van-gray-7: #646566;  --van-gray-8: #323233;

/* Gradients */
--van-gradient-red: linear-gradient(to right, #ff6034, #ee0a24);
--van-gradient-orange: linear-gradient(to right, #ffd01e, #ff8917);
```

### Spacing

```css
--van-padding-base: 4px;   --van-padding-xs: 8px;   --van-padding-sm: 12px;
--van-padding-md: 16px;    --van-padding-lg: 24px;  --van-padding-xl: 32px;
```

### Border Radius

```css
--van-radius-sm: 2px;   --van-radius-md: 4px;
--van-radius-lg: 8px;   --van-radius-max: 999px;
```

### Typography

```css
--van-font-size-xs: 10px;  --van-font-size-sm: 12px;
--van-font-size-md: 14px;  --van-font-size-lg: 16px;
--van-font-bold: 600;
```

### Animation

```css
--van-duration-base: 0.3s;  --van-duration-fast: 0.2s;
--van-active-opacity: 0.6;  --van-disabled-opacity: 0.5;
```

---

## Component Size Standards

| Size | Height | Use Case |
|------|--------|----------|
| mini | 24px | Inline actions, tags |
| small | 32px | Secondary actions |
| normal | 44px | Default touch target |
| large | 50px | Primary CTA, full-width |

**Touch Target**: Always maintain **44px minimum** for accessibility.

---

## Dark Mode

### HTML
```html
<body class="van-theme-dark">
```

### Vue.js
```vue
<van-config-provider :theme="isDark ? 'dark' : 'light'">
  <App />
</van-config-provider>
```

### Dark Mode Colors
```css
.van-theme-dark {
  --van-text-color: #f5f5f5;
  --van-text-color-2: #707070;
  --van-background: #000;
  --van-background-2: #1c1c1e;
}
```

---

## HTML Component Patterns

### Navigation Bar

```html
<div style="height: 46px; background: #fff; display: flex; align-items: center; padding: 0 16px; border-bottom: 1px solid #ebedf0;">
  <i class="van-icon van-icon-arrow-left" style="font-size: 18px; color: #1989fa;"></i>
  <span style="flex: 1; text-align: center; font-size: 16px; font-weight: 600;">Page Title</span>
  <i class="van-icon van-icon-search" style="font-size: 18px;"></i>
</div>
```

### Tab Bar (Bottom Navigation)

```html
<div style="position: fixed; bottom: 0; left: 0; right: 0; height: 50px; background: #fff; display: flex; border-top: 1px solid #ebedf0;">
  <div style="flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; color: #1989fa; font-size: 10px;">
    <i class="van-icon van-icon-home-o" style="font-size: 22px;"></i>
    <span>Home</span>
  </div>
  <div style="flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; color: #646566; font-size: 10px;">
    <i class="van-icon van-icon-apps-o" style="font-size: 22px;"></i>
    <span>Category</span>
  </div>
  <div style="flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; color: #646566; font-size: 10px;">
    <i class="van-icon van-icon-cart-o" style="font-size: 22px;"></i>
    <span>Cart</span>
  </div>
  <div style="flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; color: #646566; font-size: 10px;">
    <i class="van-icon van-icon-user-o" style="font-size: 22px;"></i>
    <span>Profile</span>
  </div>
</div>
```

### Button Styles

```html
<!-- Primary -->
<button style="height: 44px; padding: 0 15px; background: #1989fa; color: #fff; border: none; border-radius: 2px; font-size: 14px;">Primary</button>

<!-- Round -->
<button style="height: 44px; padding: 0 15px; background: #1989fa; color: #fff; border: none; border-radius: 999px; font-size: 14px;">Round</button>

<!-- Plain -->
<button style="height: 44px; padding: 0 15px; background: transparent; color: #1989fa; border: 1px solid #1989fa; border-radius: 2px; font-size: 14px;">Plain</button>

<!-- Block -->
<button style="width: 100%; height: 44px; background: #1989fa; color: #fff; border: none; border-radius: 2px; font-size: 14px;">Block Button</button>
```

### Cell / List Item

```html
<div style="display: flex; align-items: center; padding: 10px 16px; background: #fff; border-bottom: 1px solid #ebedf0;">
  <i class="van-icon van-icon-location-o" style="font-size: 18px; color: #969799; margin-right: 8px;"></i>
  <span style="flex: 1; font-size: 14px;">Title</span>
  <span style="color: #969799; font-size: 14px;">Value</span>
  <i class="van-icon van-icon-arrow" style="font-size: 16px; color: #969799; margin-left: 4px;"></i>
</div>
```

### Card

```html
<div style="display: flex; padding: 12px; background: #fff;">
  <img src="image.jpg" style="width: 88px; height: 88px; border-radius: 8px; object-fit: cover;">
  <div style="flex: 1; margin-left: 12px; display: flex; flex-direction: column;">
    <p style="font-size: 14px; margin: 0;">Product Title</p>
    <p style="font-size: 12px; color: #969799; margin: 4px 0;">Description</p>
    <div style="margin-top: auto; display: flex; justify-content: space-between; align-items: flex-end;">
      <span style="color: #ee0a24; font-weight: 600;">¥99.00</span>
      <span style="font-size: 12px; color: #969799;">x1</span>
    </div>
  </div>
</div>
```

### Search Bar

```html
<div style="display: flex; align-items: center; padding: 10px 12px; background: #fff;">
  <div style="flex: 1; display: flex; align-items: center; padding: 0 12px; height: 34px; background: #f7f8fa; border-radius: 999px;">
    <i class="van-icon van-icon-search" style="color: #969799; font-size: 18px; margin-right: 8px;"></i>
    <input type="text" placeholder="Search..." style="flex: 1; border: none; background: transparent; outline: none; font-size: 14px;">
  </div>
  <span style="padding-left: 12px; color: #1989fa; font-size: 14px;">Cancel</span>
</div>
```

### Tags

```html
<span style="display: inline-flex; padding: 0 4px; font-size: 12px; line-height: 16px; border-radius: 2px; color: #fff; background: #1989fa;">Primary</span>
<span style="display: inline-flex; padding: 0 4px; font-size: 12px; line-height: 16px; border-radius: 2px; color: #fff; background: #07c160;">Success</span>
<span style="display: inline-flex; padding: 0 4px; font-size: 12px; line-height: 16px; border-radius: 2px; color: #fff; background: #ee0a24;">Danger</span>
```

### Grid

```html
<div style="display: flex; flex-wrap: wrap; background: #fff;">
  <div style="flex: 0 0 25%; display: flex; flex-direction: column; align-items: center; padding: 16px 8px;">
    <i class="van-icon van-icon-photo-o" style="font-size: 28px;"></i>
    <span style="margin-top: 8px; font-size: 12px; color: #969799;">Gallery</span>
  </div>
  <!-- Repeat for more items -->
</div>
```

---

## Vue.js Component Patterns

### Tab Bar
```vue
<van-tabbar v-model="active" fixed safe-area-inset-bottom>
  <van-tabbar-item icon="home-o">Home</van-tabbar-item>
  <van-tabbar-item icon="search">Search</van-tabbar-item>
  <van-tabbar-item icon="cart-o" badge="3">Cart</van-tabbar-item>
  <van-tabbar-item icon="user-o">Profile</van-tabbar-item>
</van-tabbar>
```

### NavBar
```vue
<van-nav-bar title="Title" left-arrow @click-left="goBack">
  <template #right>
    <van-icon name="search" size="18" />
  </template>
</van-nav-bar>
```

### Form
```vue
<van-form @submit="onSubmit">
  <van-cell-group inset>
    <van-field v-model="username" label="Username" placeholder="Enter username"
      :rules="[{ required: true, message: 'Required' }]" />
    <van-field v-model="password" type="password" label="Password" placeholder="Enter password"
      :rules="[{ required: true, message: 'Required' }]" />
  </van-cell-group>
  <div style="margin: 16px;">
    <van-button round block type="primary" native-type="submit">Submit</van-button>
  </div>
</van-form>
```

### Pull Refresh + List
```vue
<van-pull-refresh v-model="refreshing" @refresh="onRefresh">
  <van-list v-model:loading="loading" :finished="finished" @load="onLoad">
    <van-cell v-for="item in list" :key="item.id" :title="item.title" />
  </van-list>
</van-pull-refresh>
```

### Swipe Cell
```vue
<van-swipe-cell>
  <van-cell title="Item" value="Content" />
  <template #right>
    <van-button square type="danger" text="Delete" />
  </template>
</van-swipe-cell>
```

### Product Card
```vue
<van-card price="99.00" title="Product" thumb="image.jpg">
  <template #tags><van-tag type="danger">Hot</van-tag></template>
  <template #footer><van-button size="mini">Add to Cart</van-button></template>
</van-card>
```

### Submit Bar
```vue
<van-submit-bar :price="3050" button-text="Checkout" @submit="onSubmit">
  <van-checkbox v-model="checked">Select All</van-checkbox>
</van-submit-bar>
```

### Action Sheet
```vue
<van-action-sheet v-model:show="show" :actions="actions" cancel-text="Cancel" @select="onSelect" />
```

### Dialog
```vue
<van-dialog v-model:show="show" title="Confirm" message="Are you sure?" show-cancel-button @confirm="onConfirm" />
```

### Toast
```js
import { showToast, showSuccessToast, showLoadingToast } from 'vant';
showToast('Message');
showSuccessToast('Success');
showLoadingToast({ message: 'Loading...', forbidClick: true });
```

---

## Page Templates

### Login Page (HTML)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Login</title>
  <link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/vant@4/lib/index.css">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: -apple-system, BlinkMacSystemFont, sans-serif; background: #f7f8fa; min-height: 100vh; }
    .page { max-width: 414px; margin: 0 auto; padding: 20px; }
    .header { text-align: center; padding: 48px 0 32px; }
    .logo { width: 80px; height: 80px; border-radius: 50%; background: #1989fa; margin: 0 auto 16px; display: flex; align-items: center; justify-content: center; }
    .logo i { font-size: 40px; color: #fff; }
    .header h1 { font-size: 24px; color: #323233; margin-bottom: 8px; }
    .header p { font-size: 14px; color: #969799; }
    .form-group { background: #fff; border-radius: 8px; overflow: hidden; margin-bottom: 24px; }
    .field { display: flex; align-items: center; padding: 12px 16px; border-bottom: 1px solid #ebedf0; }
    .field:last-child { border-bottom: none; }
    .field i { font-size: 20px; color: #969799; margin-right: 12px; }
    .field input { flex: 1; border: none; outline: none; font-size: 14px; }
    .btn { width: 100%; height: 44px; border: none; border-radius: 22px; font-size: 16px; cursor: pointer; margin-bottom: 12px; }
    .btn-primary { background: #1989fa; color: #fff; }
    .btn-outline { background: transparent; color: #1989fa; border: 1px solid #1989fa; }
  </style>
</head>
<body>
  <div class="page">
    <div class="header">
      <div class="logo"><i class="van-icon van-icon-user-o"></i></div>
      <h1>Welcome Back</h1>
      <p>Sign in to continue</p>
    </div>
    <div class="form-group">
      <div class="field">
        <i class="van-icon van-icon-phone-o"></i>
        <input type="tel" placeholder="Phone number">
      </div>
      <div class="field">
        <i class="van-icon van-icon-lock"></i>
        <input type="password" placeholder="Password">
      </div>
    </div>
    <button class="btn btn-primary">Sign In</button>
    <button class="btn btn-outline">Create Account</button>
  </div>
</body>
</html>
```

### Home Page (HTML)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Home</title>
  <link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/vant@4/lib/index.css">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: -apple-system, BlinkMacSystemFont, sans-serif; background: #f7f8fa; }
    .container { max-width: 414px; margin: 0 auto; padding-bottom: 60px; }
    .header { background: #1989fa; padding: 12px 16px; position: sticky; top: 0; z-index: 100; }
    .search { display: flex; align-items: center; background: rgba(255,255,255,0.9); border-radius: 20px; padding: 8px 16px; }
    .search i { color: #969799; margin-right: 8px; }
    .search input { flex: 1; border: none; background: transparent; outline: none; }
    .banner { margin: 12px; border-radius: 8px; height: 150px; background: linear-gradient(135deg, #667eea, #764ba2); display: flex; align-items: center; justify-content: center; color: #fff; font-size: 20px; }
    .grid { display: flex; background: #fff; margin: 12px; border-radius: 8px; padding: 12px 0; }
    .grid-item { flex: 1; display: flex; flex-direction: column; align-items: center; }
    .grid-item i { font-size: 28px; color: #1989fa; margin-bottom: 8px; }
    .grid-item span { font-size: 12px; color: #969799; }
    .section { margin: 12px; background: #fff; border-radius: 8px; padding: 16px; }
    .section-header { display: flex; justify-content: space-between; margin-bottom: 12px; }
    .section-header h3 { font-size: 16px; margin: 0; }
    .section-header a { font-size: 12px; color: #969799; text-decoration: none; }
    .products { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; }
    .product { background: #f7f8fa; border-radius: 8px; overflow: hidden; }
    .product img { width: 100%; height: 140px; object-fit: cover; background: #ddd; }
    .product-info { padding: 8px; }
    .product-title { font-size: 13px; margin: 0 0 4px; height: 36px; overflow: hidden; }
    .product-price { color: #ee0a24; font-weight: 600; }
    .tabbar { position: fixed; bottom: 0; left: 0; right: 0; height: 50px; background: #fff; display: flex; border-top: 1px solid #ebedf0; max-width: 414px; margin: 0 auto; }
    .tab { flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; color: #646566; font-size: 10px; }
    .tab.active { color: #1989fa; }
    .tab i { font-size: 22px; margin-bottom: 2px; }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <div class="search">
        <i class="van-icon van-icon-search"></i>
        <input type="text" placeholder="Search products...">
      </div>
    </div>
    <div class="banner">Promotional Banner</div>
    <div class="grid">
      <div class="grid-item"><i class="van-icon van-icon-fire-o"></i><span>Hot</span></div>
      <div class="grid-item"><i class="van-icon van-icon-gift-o"></i><span>New</span></div>
      <div class="grid-item"><i class="van-icon van-icon-coupon-o"></i><span>Coupons</span></div>
      <div class="grid-item"><i class="van-icon van-icon-gem-o"></i><span>VIP</span></div>
      <div class="grid-item"><i class="van-icon van-icon-more-o"></i><span>More</span></div>
    </div>
    <div class="section">
      <div class="section-header"><h3>Hot Deals</h3><a href="#">View All ></a></div>
      <div class="products">
        <div class="product">
          <img src="https://via.placeholder.com/180x140/ddd/999?text=Product">
          <div class="product-info">
            <p class="product-title">Wireless Headphones</p>
            <span class="product-price">¥99</span>
          </div>
        </div>
        <div class="product">
          <img src="https://via.placeholder.com/180x140/ddd/999?text=Product">
          <div class="product-info">
            <p class="product-title">Smart Watch</p>
            <span class="product-price">¥299</span>
          </div>
        </div>
      </div>
    </div>
    <div class="tabbar">
      <div class="tab active"><i class="van-icon van-icon-home-o"></i><span>Home</span></div>
      <div class="tab"><i class="van-icon van-icon-apps-o"></i><span>Category</span></div>
      <div class="tab"><i class="van-icon van-icon-cart-o"></i><span>Cart</span></div>
      <div class="tab"><i class="van-icon van-icon-user-o"></i><span>Profile</span></div>
    </div>
  </div>
</body>
</html>
```

### Profile Page (HTML)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Profile</title>
  <link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/vant@4/lib/index.css">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: -apple-system, BlinkMacSystemFont, sans-serif; background: #f7f8fa; }
    .container { max-width: 414px; margin: 0 auto; padding-bottom: 60px; }
    .header { background: linear-gradient(135deg, #1989fa, #4facfe); padding: 32px 20px 48px; display: flex; align-items: center; gap: 16px; }
    .avatar { width: 64px; height: 64px; border-radius: 50%; background: #fff; display: flex; align-items: center; justify-content: center; }
    .avatar i { font-size: 32px; color: #c8c9cc; }
    .user-info { flex: 1; color: #fff; }
    .user-info h2 { font-size: 20px; margin: 0 0 4px; }
    .user-info p { font-size: 14px; opacity: 0.8; margin: 0; }
    .stats { background: #fff; margin: -24px 12px 12px; border-radius: 8px; padding: 16px; display: flex; box-shadow: 0 2px 8px rgba(0,0,0,0.08); }
    .stat { flex: 1; text-align: center; position: relative; }
    .stat i { font-size: 24px; margin-bottom: 4px; }
    .stat span { font-size: 12px; color: #969799; }
    .stat .badge { position: absolute; top: -4px; right: 20%; min-width: 16px; height: 16px; padding: 0 4px; font-size: 10px; line-height: 16px; color: #fff; background: #ee0a24; border-radius: 8px; }
    .menu { background: #fff; margin: 12px; border-radius: 8px; overflow: hidden; }
    .menu-item { display: flex; align-items: center; padding: 14px 16px; border-bottom: 1px solid #f2f3f5; }
    .menu-item:last-child { border-bottom: none; }
    .menu-item i.icon { font-size: 20px; color: #969799; margin-right: 12px; }
    .menu-item span { flex: 1; font-size: 14px; }
    .menu-item i.arrow { font-size: 16px; color: #c8c9cc; }
    .logout { margin: 24px 12px; }
    .logout button { width: 100%; height: 44px; background: #fff; color: #ee0a24; border: 1px solid #ee0a24; border-radius: 22px; font-size: 16px; }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <div class="avatar"><i class="van-icon van-icon-manager-o"></i></div>
      <div class="user-info"><h2>John Doe</h2><p>+1 234 567 8900</p></div>
      <i class="van-icon van-icon-setting-o" style="color: #fff; font-size: 22px;"></i>
    </div>
    <div class="stats">
      <div class="stat"><i class="van-icon van-icon-orders-o"></i><span>Orders</span><span class="badge">12</span></div>
      <div class="stat"><i class="van-icon van-icon-pending-payment"></i><span>Pending</span><span class="badge">2</span></div>
      <div class="stat"><i class="van-icon van-icon-logistics"></i><span>Shipping</span><span class="badge">1</span></div>
      <div class="stat"><i class="van-icon van-icon-comment-o"></i><span>Review</span><span class="badge">3</span></div>
    </div>
    <div class="menu">
      <div class="menu-item"><i class="van-icon van-icon-star-o icon"></i><span>My Favorites</span><i class="van-icon van-icon-arrow arrow"></i></div>
      <div class="menu-item"><i class="van-icon van-icon-coupon-o icon"></i><span>Coupons</span><i class="van-icon van-icon-arrow arrow"></i></div>
    </div>
    <div class="menu">
      <div class="menu-item"><i class="van-icon van-icon-location-o icon"></i><span>Shipping Address</span><i class="van-icon van-icon-arrow arrow"></i></div>
      <div class="menu-item"><i class="van-icon van-icon-question-o icon"></i><span>Help Center</span><i class="van-icon van-icon-arrow arrow"></i></div>
    </div>
    <div class="logout"><button>Log Out</button></div>
  </div>
</body>
</html>
```

---

## Utility Classes

```html
<!-- Text truncation -->
<p class="van-ellipsis">Single line...</p>
<p class="van-multi-ellipsis--l2">Two lines...</p>

<!-- Hairline borders -->
<div class="van-hairline--top">Top border</div>
<div class="van-hairline--bottom">Bottom border</div>
<div class="van-hairline--surround">All borders</div>

<!-- Touch feedback -->
<div class="van-haptics-feedback">Clickable</div>

<!-- Safe areas -->
<div class="van-safe-area-top">Notch padding</div>
<div class="van-safe-area-bottom">Home indicator padding</div>
```

---

## Icon Reference

Use pattern: `van-icon van-icon-{name}`

| Category | Icons |
|----------|-------|
| Navigation | `arrow`, `arrow-left`, `cross`, `search`, `plus`, `minus` |
| Actions | `edit`, `delete`, `share`, `scan`, `qr`, `filter-o` |
| Status | `success`, `fail`, `warning-o`, `info-o`, `question-o` |
| Objects | `cart-o`, `home-o`, `user-o`, `setting-o`, `phone-o`, `location-o` |
| Social | `like-o`, `star-o`, `comment-o`, `chat-o`, `friends-o` |
| E-commerce | `coupon-o`, `gift-o`, `gem-o`, `gold-coin-o`, `orders-o` |

---

## PWA Configuration

### Manifest
```json
{
  "name": "My App",
  "short_name": "App",
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#1989fa",
  "background_color": "#ffffff"
}
```

### Viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
<meta name="theme-color" content="#1989fa">
<meta name="apple-mobile-web-app-capable" content="yes">
```

### Safe Area CSS
```css
.app {
  padding-top: env(safe-area-inset-top);
  padding-bottom: env(safe-area-inset-bottom);
}
```

---

## Theme Customization

### CSS Override
```css
:root {
  --van-primary-color: #7232dd;
  --van-button-primary-background: #7232dd;
}
```

### Vue ConfigProvider
```vue
<van-config-provider :theme-vars="{ primaryColor: '#7232dd' }">
  <App />
</van-config-provider>
```
