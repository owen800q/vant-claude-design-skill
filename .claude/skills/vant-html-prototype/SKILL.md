---
name: vant-html-prototype
description: Create HTML prototypes and static mockups for mobile apps using Vant design system. Use when building HTML mockups, static mobile pages, UI demos without build tools, clickable prototypes, or mobile web pages with Vant CSS styling. Provides CDN setup, pure HTML/CSS components, and complete page templates.
---

# Vant HTML Prototype Design Skill

You are an expert in creating **HTML prototypes** and **static mockups** for mobile apps using the Vant design system. This skill focuses on pure HTML/CSS prototyping WITHOUT requiring Vue.js or build tools.

## When to Use This Skill

Use this skill when the user wants to:
- Create HTML mockups or prototypes for mobile apps
- Design static HTML pages with Vant styling
- Build quick UI demos without a build system
- Create clickable prototypes for presentations
- Design mobile web pages with Vant CSS

---

## Quick Start: CDN Setup

### Basic HTML Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
  <meta name="theme-color" content="#1989fa">
  <title>Mobile App Prototype</title>

  <!-- Vant CSS -->
  <link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/vant@4/lib/index.css">

  <!-- Custom Styles -->
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', Helvetica,
                   Segoe UI, Arial, Roboto, 'PingFang SC', sans-serif;
      background: var(--van-background);
      color: var(--van-text-color);
      font-size: 14px;
      line-height: 1.5;
      -webkit-font-smoothing: antialiased;
    }

    /* Mobile container - simulates phone screen */
    .mobile-container {
      max-width: 414px;
      margin: 0 auto;
      min-height: 100vh;
      background: var(--van-background);
      position: relative;
    }

    /* Page wrapper with safe areas */
    .page {
      padding-bottom: 50px; /* Space for tab bar */
      padding-bottom: calc(50px + env(safe-area-inset-bottom));
    }
  </style>
</head>
<body>
  <div class="mobile-container">
    <!-- Your prototype content here -->
  </div>
</body>
</html>
```

---

## Design Tokens (CSS Variables)

Use these CSS variables directly in your HTML prototypes:

### Colors

```css
/* Primary Colors */
--van-primary-color: #1989fa;      /* Main action blue */
--van-success-color: #07c160;      /* Green - positive */
--van-danger-color: #ee0a24;       /* Red - destructive */
--van-warning-color: #ff976a;      /* Orange - warning */

/* Text Colors */
--van-text-color: #323233;         /* Primary text */
--van-text-color-2: #969799;       /* Secondary text */
--van-text-color-3: #c8c9cc;       /* Placeholder/disabled */

/* Background Colors */
--van-background: #f7f8fa;         /* Page background */
--van-background-2: #fff;          /* Card background */
--van-background-3: #fff;          /* Elevated surfaces */

/* Gray Scale */
--van-gray-1: #f7f8fa;
--van-gray-2: #f2f3f5;
--van-gray-3: #ebedf0;
--van-gray-4: #dcdee0;
--van-gray-5: #c8c9cc;
--van-gray-6: #969799;
--van-gray-7: #646566;
--van-gray-8: #323233;

/* Gradients */
--van-gradient-red: linear-gradient(to right, #ff6034, #ee0a24);
--van-gradient-orange: linear-gradient(to right, #ffd01e, #ff8917);
```

### Spacing

```css
--van-padding-base: 4px;
--van-padding-xs: 8px;
--van-padding-sm: 12px;
--van-padding-md: 16px;
--van-padding-lg: 24px;
--van-padding-xl: 32px;
```

### Border Radius

```css
--van-radius-sm: 2px;
--van-radius-md: 4px;
--van-radius-lg: 8px;
--van-radius-max: 999px;  /* Pill shape */
```

### Typography

```css
--van-font-size-xs: 10px;
--van-font-size-sm: 12px;
--van-font-size-md: 14px;
--van-font-size-lg: 16px;
--van-font-bold: 600;
```

---

## Utility CSS Classes

Vant provides these utility classes you can use directly:

```html
<!-- Text truncation -->
<p class="van-ellipsis">Single line truncation with ellipsis...</p>
<p class="van-multi-ellipsis--l2">Two line truncation...</p>
<p class="van-multi-ellipsis--l3">Three line truncation...</p>

<!-- Hairline borders (0.5px on retina) -->
<div class="van-hairline--top">Top border</div>
<div class="van-hairline--bottom">Bottom border</div>
<div class="van-hairline--left">Left border</div>
<div class="van-hairline--right">Right border</div>
<div class="van-hairline--surround">All borders</div>
<div class="van-hairline--top-bottom">Top and bottom borders</div>

<!-- Touch feedback -->
<div class="van-haptics-feedback">Clickable with opacity feedback</div>

<!-- Safe areas -->
<div class="van-safe-area-top">Notch padding</div>
<div class="van-safe-area-bottom">Home indicator padding</div>
```

---

## HTML Component Patterns

### Navigation Bar

```html
<div class="van-nav-bar van-hairline--bottom">
  <div class="van-nav-bar__content">
    <div class="van-nav-bar__left">
      <i class="van-icon van-icon-arrow-left van-nav-bar__arrow"></i>
    </div>
    <div class="van-nav-bar__title van-ellipsis">Page Title</div>
    <div class="van-nav-bar__right">
      <i class="van-icon van-icon-search"></i>
    </div>
  </div>
</div>

<style>
.van-nav-bar {
  position: relative;
  height: 46px;
  background: #fff;
}
.van-nav-bar__content {
  display: flex;
  align-items: center;
  height: 100%;
  padding: 0 16px;
}
.van-nav-bar__left,
.van-nav-bar__right {
  display: flex;
  align-items: center;
  font-size: 14px;
  color: var(--van-primary-color);
}
.van-nav-bar__title {
  flex: 1;
  text-align: center;
  font-size: 16px;
  font-weight: 600;
  color: var(--van-text-color);
}
.van-nav-bar__arrow {
  font-size: 18px;
}
</style>
```

### Tab Bar (Bottom Navigation)

```html
<div class="van-tabbar van-tabbar--fixed van-hairline--top-bottom">
  <div class="van-tabbar-item van-tabbar-item--active">
    <div class="van-tabbar-item__icon">
      <i class="van-icon van-icon-home-o"></i>
    </div>
    <div class="van-tabbar-item__text">Home</div>
  </div>
  <div class="van-tabbar-item">
    <div class="van-tabbar-item__icon">
      <i class="van-icon van-icon-search"></i>
    </div>
    <div class="van-tabbar-item__text">Search</div>
  </div>
  <div class="van-tabbar-item">
    <div class="van-tabbar-item__icon">
      <i class="van-icon van-icon-friends-o"></i>
    </div>
    <div class="van-tabbar-item__text">Messages</div>
  </div>
  <div class="van-tabbar-item">
    <div class="van-tabbar-item__icon">
      <i class="van-icon van-icon-setting-o"></i>
    </div>
    <div class="van-tabbar-item__text">Profile</div>
  </div>
</div>

<style>
.van-tabbar {
  display: flex;
  width: 100%;
  height: 50px;
  background: #fff;
}
.van-tabbar--fixed {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding-bottom: env(safe-area-inset-bottom);
}
.van-tabbar-item {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: var(--van-gray-7);
  font-size: 12px;
  cursor: pointer;
}
.van-tabbar-item--active {
  color: var(--van-primary-color);
}
.van-tabbar-item__icon {
  font-size: 22px;
  margin-bottom: 2px;
}
</style>
```

### Button Styles

```html
<!-- Primary Button -->
<button class="van-button van-button--primary van-button--normal">
  <span class="van-button__text">Primary Button</span>
</button>

<!-- Success Button -->
<button class="van-button van-button--success van-button--normal">
  <span class="van-button__text">Success</span>
</button>

<!-- Danger Button -->
<button class="van-button van-button--danger van-button--normal">
  <span class="van-button__text">Danger</span>
</button>

<!-- Plain/Outline Button -->
<button class="van-button van-button--primary van-button--plain van-button--normal">
  <span class="van-button__text">Plain Button</span>
</button>

<!-- Round Button -->
<button class="van-button van-button--primary van-button--round van-button--normal">
  <span class="van-button__text">Round Button</span>
</button>

<!-- Block Button (Full Width) -->
<button class="van-button van-button--primary van-button--normal van-button--block">
  <span class="van-button__text">Block Button</span>
</button>

<!-- Button Sizes -->
<button class="van-button van-button--primary van-button--large">Large</button>
<button class="van-button van-button--primary van-button--normal">Normal</button>
<button class="van-button van-button--primary van-button--small">Small</button>
<button class="van-button van-button--primary van-button--mini">Mini</button>

<style>
.van-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border: 1px solid transparent;
  border-radius: 2px;
  font-size: 14px;
  cursor: pointer;
  transition: opacity 0.2s;
}
.van-button:active { opacity: 0.6; }
.van-button--primary {
  color: #fff;
  background: var(--van-primary-color);
  border-color: var(--van-primary-color);
}
.van-button--success {
  color: #fff;
  background: var(--van-success-color);
  border-color: var(--van-success-color);
}
.van-button--danger {
  color: #fff;
  background: var(--van-danger-color);
  border-color: var(--van-danger-color);
}
.van-button--warning {
  color: #fff;
  background: var(--van-warning-color);
  border-color: var(--van-warning-color);
}
.van-button--default {
  color: var(--van-text-color);
  background: #fff;
  border-color: var(--van-gray-4);
}
.van-button--plain {
  background: transparent;
}
.van-button--plain.van-button--primary { color: var(--van-primary-color); }
.van-button--plain.van-button--success { color: var(--van-success-color); }
.van-button--plain.van-button--danger { color: var(--van-danger-color); }
.van-button--round { border-radius: 999px; }
.van-button--block { display: flex; width: 100%; }
.van-button--large { height: 50px; padding: 0 24px; font-size: 16px; }
.van-button--normal { height: 44px; padding: 0 15px; }
.van-button--small { height: 32px; padding: 0 8px; font-size: 12px; }
.van-button--mini { height: 24px; padding: 0 4px; font-size: 10px; }
</style>
```

### Cell / List Item

```html
<div class="van-cell-group van-cell-group--inset">
  <!-- Basic Cell -->
  <div class="van-cell van-hairline--bottom">
    <div class="van-cell__title">Title</div>
    <div class="van-cell__value">Value</div>
  </div>

  <!-- Cell with Icon -->
  <div class="van-cell van-hairline--bottom">
    <i class="van-icon van-icon-location-o van-cell__left-icon"></i>
    <div class="van-cell__title">Location</div>
    <div class="van-cell__value">Beijing</div>
  </div>

  <!-- Cell with Arrow (Link) -->
  <div class="van-cell van-cell--clickable van-hairline--bottom">
    <div class="van-cell__title">Settings</div>
    <div class="van-cell__value"></div>
    <i class="van-icon van-icon-arrow van-cell__right-icon"></i>
  </div>

  <!-- Cell with Label -->
  <div class="van-cell van-hairline--bottom">
    <div class="van-cell__title">
      <span>Title</span>
      <div class="van-cell__label">Description text</div>
    </div>
    <div class="van-cell__value">Value</div>
  </div>
</div>

<style>
.van-cell-group--inset {
  margin: 12px;
  border-radius: 8px;
  overflow: hidden;
}
.van-cell {
  display: flex;
  align-items: center;
  padding: 10px 16px;
  background: #fff;
  min-height: 48px;
}
.van-cell--clickable {
  cursor: pointer;
}
.van-cell--clickable:active {
  background: var(--van-gray-2);
}
.van-cell__left-icon {
  margin-right: 8px;
  font-size: 18px;
  color: var(--van-gray-6);
}
.van-cell__title {
  flex: 1;
  color: var(--van-text-color);
}
.van-cell__label {
  margin-top: 4px;
  font-size: 12px;
  color: var(--van-text-color-2);
}
.van-cell__value {
  color: var(--van-text-color-2);
  font-size: 14px;
}
.van-cell__right-icon {
  margin-left: 4px;
  font-size: 16px;
  color: var(--van-gray-6);
}
</style>
```

### Card Component

```html
<div class="van-card">
  <div class="van-card__thumb">
    <img src="https://via.placeholder.com/100x100" alt="Product">
  </div>
  <div class="van-card__content">
    <div class="van-card__title van-multi-ellipsis--l2">Product Title Goes Here</div>
    <div class="van-card__desc">Product description or SKU</div>
    <div class="van-card__bottom">
      <div class="van-card__price">
        <span class="van-card__price-currency">¥</span>
        <span class="van-card__price-integer">99</span>
        <span class="van-card__price-decimal">.00</span>
      </div>
      <div class="van-card__num">x1</div>
    </div>
  </div>
</div>

<style>
.van-card {
  display: flex;
  padding: 12px;
  background: #fff;
}
.van-card__thumb {
  width: 88px;
  height: 88px;
  margin-right: 12px;
  border-radius: 8px;
  overflow: hidden;
  flex-shrink: 0;
}
.van-card__thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.van-card__content {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
}
.van-card__title {
  font-size: 14px;
  color: var(--van-text-color);
  line-height: 1.4;
}
.van-card__desc {
  font-size: 12px;
  color: var(--van-text-color-2);
  margin-top: 4px;
}
.van-card__bottom {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-top: auto;
  padding-top: 8px;
}
.van-card__price {
  color: var(--van-danger-color);
  font-weight: 600;
}
.van-card__price-currency {
  font-size: 12px;
}
.van-card__price-integer {
  font-size: 18px;
}
.van-card__price-decimal {
  font-size: 12px;
}
.van-card__num {
  font-size: 12px;
  color: var(--van-text-color-2);
}
</style>
```

### Search Bar

```html
<div class="van-search">
  <div class="van-search__content van-search__content--round">
    <i class="van-icon van-icon-search van-search__icon"></i>
    <input type="text" class="van-search__input" placeholder="Search...">
  </div>
  <div class="van-search__action">Cancel</div>
</div>

<style>
.van-search {
  display: flex;
  align-items: center;
  padding: 10px 12px;
  background: #fff;
}
.van-search__content {
  flex: 1;
  display: flex;
  align-items: center;
  padding: 0 12px;
  height: 34px;
  background: var(--van-gray-1);
  border-radius: 2px;
}
.van-search__content--round {
  border-radius: 999px;
}
.van-search__icon {
  color: var(--van-gray-6);
  font-size: 18px;
  margin-right: 8px;
}
.van-search__input {
  flex: 1;
  border: none;
  background: transparent;
  outline: none;
  font-size: 14px;
  color: var(--van-text-color);
}
.van-search__input::placeholder {
  color: var(--van-text-color-3);
}
.van-search__action {
  padding-left: 12px;
  color: var(--van-primary-color);
  font-size: 14px;
  cursor: pointer;
}
</style>
```

### Tag / Badge

```html
<!-- Tags -->
<span class="van-tag van-tag--primary">Primary</span>
<span class="van-tag van-tag--success">Success</span>
<span class="van-tag van-tag--danger">Danger</span>
<span class="van-tag van-tag--warning">Warning</span>

<!-- Plain Tags -->
<span class="van-tag van-tag--primary van-tag--plain">Plain</span>

<!-- Round Tags -->
<span class="van-tag van-tag--primary van-tag--round">Round</span>

<!-- Badge -->
<div class="badge-wrapper">
  <i class="van-icon van-icon-chat-o" style="font-size: 24px;"></i>
  <div class="van-badge">5</div>
</div>

<!-- Dot Badge -->
<div class="badge-wrapper">
  <i class="van-icon van-icon-chat-o" style="font-size: 24px;"></i>
  <div class="van-badge van-badge--dot"></div>
</div>

<style>
.van-tag {
  display: inline-flex;
  align-items: center;
  padding: 0 4px;
  font-size: 12px;
  line-height: 16px;
  border-radius: 2px;
  color: #fff;
}
.van-tag--primary { background: var(--van-primary-color); }
.van-tag--success { background: var(--van-success-color); }
.van-tag--danger { background: var(--van-danger-color); }
.van-tag--warning { background: var(--van-warning-color); }
.van-tag--plain {
  background: transparent;
  border: 1px solid currentColor;
}
.van-tag--plain.van-tag--primary { color: var(--van-primary-color); }
.van-tag--plain.van-tag--success { color: var(--van-success-color); }
.van-tag--plain.van-tag--danger { color: var(--van-danger-color); }
.van-tag--round { border-radius: 999px; padding: 0 8px; }

.badge-wrapper {
  display: inline-block;
  position: relative;
}
.van-badge {
  position: absolute;
  top: 0;
  right: 0;
  transform: translate(50%, -50%);
  min-width: 16px;
  padding: 0 3px;
  font-size: 12px;
  line-height: 14px;
  text-align: center;
  color: #fff;
  background: var(--van-danger-color);
  border: 1px solid #fff;
  border-radius: 999px;
}
.van-badge--dot {
  width: 8px;
  height: 8px;
  min-width: auto;
  padding: 0;
  border-radius: 50%;
}
</style>
```

### Form Field

```html
<div class="van-cell-group van-cell-group--inset">
  <!-- Text Input -->
  <div class="van-field van-hairline--bottom">
    <label class="van-field__label">Username</label>
    <div class="van-field__body">
      <input type="text" class="van-field__control" placeholder="Enter username">
    </div>
  </div>

  <!-- Password Input -->
  <div class="van-field van-hairline--bottom">
    <label class="van-field__label">Password</label>
    <div class="van-field__body">
      <input type="password" class="van-field__control" placeholder="Enter password">
      <i class="van-icon van-icon-eye-o van-field__right-icon"></i>
    </div>
  </div>

  <!-- Textarea -->
  <div class="van-field">
    <label class="van-field__label">Message</label>
    <div class="van-field__body">
      <textarea class="van-field__control" rows="3" placeholder="Enter message"></textarea>
    </div>
  </div>
</div>

<style>
.van-field {
  display: flex;
  padding: 10px 16px;
  background: #fff;
}
.van-field__label {
  width: 6.2em;
  color: var(--van-text-color);
  font-size: 14px;
  flex-shrink: 0;
}
.van-field__body {
  flex: 1;
  display: flex;
  align-items: center;
}
.van-field__control {
  flex: 1;
  border: none;
  background: transparent;
  outline: none;
  font-size: 14px;
  color: var(--van-text-color);
  resize: none;
}
.van-field__control::placeholder {
  color: var(--van-text-color-3);
}
.van-field__right-icon {
  padding-left: 8px;
  font-size: 18px;
  color: var(--van-gray-6);
  cursor: pointer;
}
</style>
```

### Grid Layout

```html
<div class="van-grid">
  <div class="van-grid-item">
    <i class="van-icon van-icon-photo-o van-grid-item__icon"></i>
    <span class="van-grid-item__text">Gallery</span>
  </div>
  <div class="van-grid-item">
    <i class="van-icon van-icon-gift-o van-grid-item__icon"></i>
    <span class="van-grid-item__text">Gifts</span>
  </div>
  <div class="van-grid-item">
    <i class="van-icon van-icon-cart-o van-grid-item__icon"></i>
    <span class="van-grid-item__text">Cart</span>
  </div>
  <div class="van-grid-item">
    <i class="van-icon van-icon-setting-o van-grid-item__icon"></i>
    <span class="van-grid-item__text">Settings</span>
  </div>
</div>

<style>
.van-grid {
  display: flex;
  flex-wrap: wrap;
  background: #fff;
}
.van-grid-item {
  flex: 0 0 25%; /* 4 columns */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 16px 8px;
  cursor: pointer;
}
.van-grid-item:active {
  background: var(--van-gray-2);
}
.van-grid-item__icon {
  font-size: 28px;
  color: var(--van-text-color);
}
.van-grid-item__text {
  margin-top: 8px;
  font-size: 12px;
  color: var(--van-text-color-2);
}
</style>
```

---

## Complete Page Templates (HTML)

### Login Page

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
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', sans-serif;
      background: var(--van-background);
      min-height: 100vh;
    }
    .login-page { max-width: 414px; margin: 0 auto; padding: 20px; }
    .login-header {
      text-align: center;
      padding: 48px 0 32px;
    }
    .login-logo {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      background: var(--van-primary-color);
      margin: 0 auto 16px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .login-logo i { font-size: 40px; color: #fff; }
    .login-header h1 {
      font-size: 24px;
      color: var(--van-text-color);
      margin-bottom: 8px;
    }
    .login-header p {
      font-size: 14px;
      color: var(--van-text-color-2);
    }
    .form-group {
      background: #fff;
      border-radius: 8px;
      overflow: hidden;
      margin-bottom: 24px;
    }
    .form-field {
      display: flex;
      align-items: center;
      padding: 12px 16px;
      border-bottom: 1px solid var(--van-gray-3);
    }
    .form-field:last-child { border-bottom: none; }
    .form-field i {
      font-size: 20px;
      color: var(--van-gray-6);
      margin-right: 12px;
    }
    .form-field input {
      flex: 1;
      border: none;
      outline: none;
      font-size: 14px;
    }
    .form-field input::placeholder { color: var(--van-text-color-3); }
    .btn-primary {
      width: 100%;
      height: 44px;
      background: var(--van-primary-color);
      color: #fff;
      border: none;
      border-radius: 22px;
      font-size: 16px;
      cursor: pointer;
      margin-bottom: 12px;
    }
    .btn-primary:active { opacity: 0.8; }
    .btn-outline {
      width: 100%;
      height: 44px;
      background: transparent;
      color: var(--van-primary-color);
      border: 1px solid var(--van-primary-color);
      border-radius: 22px;
      font-size: 16px;
      cursor: pointer;
    }
    .divider {
      display: flex;
      align-items: center;
      margin: 32px 0;
      color: var(--van-text-color-3);
      font-size: 12px;
    }
    .divider::before, .divider::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--van-gray-3);
    }
    .divider span { padding: 0 16px; }
    .social-login {
      display: flex;
      justify-content: center;
      gap: 24px;
    }
    .social-btn {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      border: 1px solid var(--van-gray-4);
      background: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
    }
    .social-btn i { font-size: 24px; }
    .social-btn.wechat i { color: #07c160; }
    .social-btn.qq i { color: #1989fa; }
    .social-btn.weibo i { color: #ee0a24; }
  </style>
</head>
<body>
  <div class="login-page">
    <div class="login-header">
      <div class="login-logo">
        <i class="van-icon van-icon-user-o"></i>
      </div>
      <h1>Welcome Back</h1>
      <p>Sign in to continue</p>
    </div>

    <div class="form-group">
      <div class="form-field">
        <i class="van-icon van-icon-phone-o"></i>
        <input type="tel" placeholder="Phone number">
      </div>
      <div class="form-field">
        <i class="van-icon van-icon-lock"></i>
        <input type="password" placeholder="Password">
        <i class="van-icon van-icon-eye-o" style="color: var(--van-gray-5);"></i>
      </div>
    </div>

    <button class="btn-primary">Sign In</button>
    <button class="btn-outline">Create Account</button>

    <div class="divider"><span>Or continue with</span></div>

    <div class="social-login">
      <button class="social-btn wechat"><i class="van-icon van-icon-wechat"></i></button>
      <button class="social-btn qq"><i class="van-icon van-icon-qq"></i></button>
      <button class="social-btn weibo"><i class="van-icon van-icon-weibo"></i></button>
    </div>
  </div>
</body>
</html>
```

### Home Page with Tab Bar

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
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', sans-serif;
      background: var(--van-background);
    }
    .mobile-container {
      max-width: 414px;
      margin: 0 auto;
      min-height: 100vh;
      background: var(--van-background);
      padding-bottom: 60px;
    }

    /* Header */
    .home-header {
      background: var(--van-primary-color);
      padding: 12px 16px;
      position: sticky;
      top: 0;
      z-index: 100;
    }
    .search-bar {
      display: flex;
      align-items: center;
      background: rgba(255,255,255,0.9);
      border-radius: 20px;
      padding: 8px 16px;
    }
    .search-bar i { color: var(--van-gray-6); margin-right: 8px; }
    .search-bar input {
      flex: 1;
      border: none;
      background: transparent;
      outline: none;
      font-size: 14px;
    }

    /* Banner */
    .banner {
      margin: 12px;
      border-radius: 8px;
      overflow: hidden;
      height: 150px;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      color: #fff;
      font-size: 20px;
    }

    /* Quick Actions */
    .quick-grid {
      display: flex;
      background: #fff;
      margin: 12px;
      border-radius: 8px;
      padding: 12px 0;
    }
    .grid-item {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      cursor: pointer;
    }
    .grid-item i {
      font-size: 28px;
      color: var(--van-primary-color);
      margin-bottom: 8px;
    }
    .grid-item span {
      font-size: 12px;
      color: var(--van-text-color-2);
    }

    /* Notice */
    .notice {
      display: flex;
      align-items: center;
      background: #fffbe8;
      padding: 10px 16px;
      margin: 0 12px;
      border-radius: 4px;
      font-size: 13px;
      color: #ed6a0c;
    }
    .notice i { margin-right: 8px; }

    /* Section */
    .section {
      margin: 12px;
      background: #fff;
      border-radius: 8px;
      padding: 16px;
    }
    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
    }
    .section-header h3 {
      font-size: 16px;
      color: var(--van-text-color);
    }
    .section-header a {
      font-size: 12px;
      color: var(--van-text-color-2);
      text-decoration: none;
    }

    /* Product Grid */
    .product-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 12px;
    }
    .product-card {
      background: var(--van-gray-1);
      border-radius: 8px;
      overflow: hidden;
    }
    .product-card img {
      width: 100%;
      height: 140px;
      object-fit: cover;
      background: var(--van-gray-3);
    }
    .product-info {
      padding: 8px;
    }
    .product-title {
      font-size: 13px;
      color: var(--van-text-color);
      margin-bottom: 4px;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      overflow: hidden;
      height: 36px;
    }
    .product-price {
      color: var(--van-danger-color);
      font-weight: 600;
    }
    .product-price-old {
      color: var(--van-text-color-3);
      font-size: 12px;
      text-decoration: line-through;
      margin-left: 4px;
    }

    /* Tab Bar */
    .tabbar {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      height: 50px;
      background: #fff;
      display: flex;
      border-top: 1px solid var(--van-gray-3);
      max-width: 414px;
      margin: 0 auto;
    }
    .tab-item {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: var(--van-gray-7);
      font-size: 10px;
      cursor: pointer;
    }
    .tab-item.active { color: var(--van-primary-color); }
    .tab-item i { font-size: 22px; margin-bottom: 2px; }
  </style>
</head>
<body>
  <div class="mobile-container">
    <!-- Header -->
    <div class="home-header">
      <div class="search-bar">
        <i class="van-icon van-icon-search"></i>
        <input type="text" placeholder="Search products...">
      </div>
    </div>

    <!-- Banner -->
    <div class="banner">
      <span>Promotional Banner</span>
    </div>

    <!-- Quick Actions -->
    <div class="quick-grid">
      <div class="grid-item">
        <i class="van-icon van-icon-fire-o"></i>
        <span>Hot</span>
      </div>
      <div class="grid-item">
        <i class="van-icon van-icon-gift-o"></i>
        <span>New</span>
      </div>
      <div class="grid-item">
        <i class="van-icon van-icon-coupon-o"></i>
        <span>Coupons</span>
      </div>
      <div class="grid-item">
        <i class="van-icon van-icon-gem-o"></i>
        <span>VIP</span>
      </div>
      <div class="grid-item">
        <i class="van-icon van-icon-more-o"></i>
        <span>More</span>
      </div>
    </div>

    <!-- Notice -->
    <div class="notice">
      <i class="van-icon van-icon-volume-o"></i>
      <span>New users get 20% off on first order!</span>
    </div>

    <!-- Products Section -->
    <div class="section">
      <div class="section-header">
        <h3>Hot Deals</h3>
        <a href="#">View All ></a>
      </div>
      <div class="product-grid">
        <div class="product-card">
          <img src="https://via.placeholder.com/180x140/ddd/999?text=Product" alt="">
          <div class="product-info">
            <p class="product-title">Wireless Bluetooth Headphones</p>
            <div>
              <span class="product-price">¥99</span>
              <span class="product-price-old">¥199</span>
            </div>
          </div>
        </div>
        <div class="product-card">
          <img src="https://via.placeholder.com/180x140/ddd/999?text=Product" alt="">
          <div class="product-info">
            <p class="product-title">Smart Watch Series 5</p>
            <div>
              <span class="product-price">¥299</span>
              <span class="product-price-old">¥599</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Tab Bar -->
    <div class="tabbar">
      <div class="tab-item active">
        <i class="van-icon van-icon-home-o"></i>
        <span>Home</span>
      </div>
      <div class="tab-item">
        <i class="van-icon van-icon-apps-o"></i>
        <span>Category</span>
      </div>
      <div class="tab-item">
        <i class="van-icon van-icon-cart-o"></i>
        <span>Cart</span>
      </div>
      <div class="tab-item">
        <i class="van-icon van-icon-user-o"></i>
        <span>Profile</span>
      </div>
    </div>
  </div>
</body>
</html>
```

### Profile Page

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
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', sans-serif;
      background: var(--van-background);
    }
    .mobile-container {
      max-width: 414px;
      margin: 0 auto;
      min-height: 100vh;
      padding-bottom: 60px;
    }

    /* Profile Header */
    .profile-header {
      background: linear-gradient(135deg, var(--van-primary-color), #4facfe);
      padding: 32px 20px 48px;
      display: flex;
      align-items: center;
      gap: 16px;
    }
    .avatar {
      width: 64px;
      height: 64px;
      border-radius: 50%;
      background: #fff;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .avatar i { font-size: 32px; color: var(--van-gray-5); }
    .user-info { flex: 1; color: #fff; }
    .user-info h2 { font-size: 20px; margin-bottom: 4px; }
    .user-info p { font-size: 14px; opacity: 0.8; }
    .settings-btn { color: #fff; font-size: 22px; }

    /* Stats Card */
    .stats-card {
      background: #fff;
      margin: -24px 12px 12px;
      border-radius: 8px;
      padding: 16px;
      display: flex;
      box-shadow: 0 2px 8px rgba(0,0,0,0.08);
    }
    .stat-item {
      flex: 1;
      text-align: center;
      cursor: pointer;
      position: relative;
    }
    .stat-icon {
      font-size: 24px;
      color: var(--van-text-color);
      margin-bottom: 4px;
    }
    .stat-text {
      font-size: 12px;
      color: var(--van-text-color-2);
    }
    .stat-badge {
      position: absolute;
      top: -4px;
      right: 20%;
      min-width: 16px;
      height: 16px;
      padding: 0 4px;
      font-size: 10px;
      line-height: 16px;
      color: #fff;
      background: var(--van-danger-color);
      border-radius: 8px;
    }

    /* Menu */
    .menu-group {
      background: #fff;
      margin: 12px;
      border-radius: 8px;
      overflow: hidden;
    }
    .menu-item {
      display: flex;
      align-items: center;
      padding: 14px 16px;
      border-bottom: 1px solid var(--van-gray-2);
      cursor: pointer;
    }
    .menu-item:last-child { border-bottom: none; }
    .menu-item:active { background: var(--van-gray-1); }
    .menu-item i.icon {
      font-size: 20px;
      color: var(--van-gray-6);
      margin-right: 12px;
    }
    .menu-item span {
      flex: 1;
      font-size: 14px;
      color: var(--van-text-color);
    }
    .menu-item i.arrow {
      font-size: 16px;
      color: var(--van-gray-5);
    }
    .menu-item .badge {
      background: var(--van-danger-color);
      color: #fff;
      font-size: 10px;
      padding: 2px 6px;
      border-radius: 10px;
      margin-right: 8px;
    }

    /* Logout */
    .logout-btn {
      margin: 24px 12px;
      height: 44px;
      background: #fff;
      color: var(--van-danger-color);
      border: 1px solid var(--van-danger-color);
      border-radius: 22px;
      font-size: 16px;
      cursor: pointer;
      width: calc(100% - 24px);
    }

    /* Tab Bar */
    .tabbar {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      height: 50px;
      background: #fff;
      display: flex;
      border-top: 1px solid var(--van-gray-3);
      max-width: 414px;
      margin: 0 auto;
    }
    .tab-item {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: var(--van-gray-7);
      font-size: 10px;
    }
    .tab-item.active { color: var(--van-primary-color); }
    .tab-item i { font-size: 22px; margin-bottom: 2px; }
  </style>
</head>
<body>
  <div class="mobile-container">
    <!-- Header -->
    <div class="profile-header">
      <div class="avatar">
        <i class="van-icon van-icon-manager-o"></i>
      </div>
      <div class="user-info">
        <h2>John Doe</h2>
        <p>+1 234 567 8900</p>
      </div>
      <i class="van-icon van-icon-setting-o settings-btn"></i>
    </div>

    <!-- Stats Card -->
    <div class="stats-card">
      <div class="stat-item">
        <i class="van-icon van-icon-orders-o stat-icon"></i>
        <div class="stat-text">Orders</div>
        <span class="stat-badge">12</span>
      </div>
      <div class="stat-item">
        <i class="van-icon van-icon-pending-payment stat-icon"></i>
        <div class="stat-text">Pending</div>
        <span class="stat-badge">2</span>
      </div>
      <div class="stat-item">
        <i class="van-icon van-icon-logistics stat-icon"></i>
        <div class="stat-text">Shipping</div>
        <span class="stat-badge">1</span>
      </div>
      <div class="stat-item">
        <i class="van-icon van-icon-comment-o stat-icon"></i>
        <div class="stat-text">Review</div>
        <span class="stat-badge">3</span>
      </div>
    </div>

    <!-- Menu -->
    <div class="menu-group">
      <div class="menu-item">
        <i class="van-icon van-icon-star-o icon"></i>
        <span>My Favorites</span>
        <i class="van-icon van-icon-arrow arrow"></i>
      </div>
      <div class="menu-item">
        <i class="van-icon van-icon-coupon-o icon"></i>
        <span>Coupons</span>
        <span class="badge">5</span>
        <i class="van-icon van-icon-arrow arrow"></i>
      </div>
    </div>

    <div class="menu-group">
      <div class="menu-item">
        <i class="van-icon van-icon-location-o icon"></i>
        <span>Shipping Address</span>
        <i class="van-icon van-icon-arrow arrow"></i>
      </div>
      <div class="menu-item">
        <i class="van-icon van-icon-question-o icon"></i>
        <span>Help Center</span>
        <i class="van-icon van-icon-arrow arrow"></i>
      </div>
    </div>

    <button class="logout-btn">Log Out</button>

    <!-- Tab Bar -->
    <div class="tabbar">
      <div class="tab-item">
        <i class="van-icon van-icon-home-o"></i>
        <span>Home</span>
      </div>
      <div class="tab-item">
        <i class="van-icon van-icon-apps-o"></i>
        <span>Category</span>
      </div>
      <div class="tab-item">
        <i class="van-icon van-icon-cart-o"></i>
        <span>Cart</span>
      </div>
      <div class="tab-item active">
        <i class="van-icon van-icon-user-o"></i>
        <span>Profile</span>
      </div>
    </div>
  </div>
</body>
</html>
```

---

## Icon Reference

Vant icons can be used with the class pattern: `van-icon van-icon-{name}`

### Common Icons

| Category | Icons |
|----------|-------|
| Navigation | `arrow`, `arrow-left`, `arrow-up`, `arrow-down`, `cross`, `plus`, `minus` |
| Actions | `search`, `share`, `edit`, `delete`, `scan`, `qr`, `filter-o` |
| Status | `success`, `fail`, `warning-o`, `info-o`, `question-o` |
| Objects | `cart-o`, `home-o`, `user-o`, `setting-o`, `phone-o`, `location-o` |
| Media | `photo-o`, `photograph`, `video-o`, `music-o`, `play-circle-o` |
| Social | `like-o`, `star-o`, `comment-o`, `chat-o`, `friends-o` |
| E-commerce | `coupon-o`, `gift-o`, `gem-o`, `gold-coin-o`, `shopping-cart-o` |

---

## Dark Mode Support

Add the `van-theme-dark` class to the body or container:

```html
<body class="van-theme-dark">
  <!-- Dark mode enabled -->
</body>
```

Or toggle with JavaScript:

```javascript
document.body.classList.toggle('van-theme-dark');
```

---

## Tips for HTML Prototyping

1. **Use the CDN**: Always include Vant CSS from CDN for consistent styling
2. **Mobile viewport**: Always set proper viewport meta tag
3. **Use CSS variables**: Leverage `var(--van-*)` for consistent colors
4. **Copy icon classes**: Use `van-icon van-icon-{name}` pattern
5. **Use utility classes**: `van-ellipsis`, `van-hairline--*` for common patterns
6. **Fixed elements**: Tab bars should be `position: fixed; bottom: 0`
7. **Safe areas**: Add padding for notch devices with `env(safe-area-inset-*)`
8. **Max-width container**: Use `max-width: 414px` to simulate phone screen
