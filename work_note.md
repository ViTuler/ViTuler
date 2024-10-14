CSS Part:
  [Navbar Effect](https://element-plus.org/zh-CN/guide/namespace.html#%E8%AE%BE%E7%BD%AE-elconfigprovider)

  ```scss
  .navbar-wrapper {
    position: relative;
    border-bottom: 1px solid var(--border-color);
    height: var(--header-height);
    padding: 0 12px 0 24px;
    background-image: radial-gradient(transparent 1px,var(--bg-color) 1px);
    background-size: 4px 4px;
    backdrop-filter: saturate(50%) blur(4px);
    -webkit-backdrop-filter: saturate(50%) blur(4px);
    top: 0
  }
  ```
  
  最主要的有三个:
  1. background-image 的 径向渐变
  2. background-size 限制单元的大小
  3. backdrop-filter 的毛玻璃

  Blog: [V2](https://www.v2ex.com/t/1079493)
