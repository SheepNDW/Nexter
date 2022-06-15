# Nexter

advanced css course project #3


## Notes

### Features Section

* 讓 grid-columns 自適應改變欄位數

```scss
.features {
  // 略
  grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));
}
```

* 使用 grid 布局來製作單一 feature 元件

![](https://i.imgur.com/HMPnJAe.png)

```scss
.feature {
  display: grid;
  grid-template-columns: min-content 1fr;
  row-gap: 1.5rem;
  column-gap: 2.5rem;

  &__icon {
    fill: $color-primary;
    width: 4.5rem;
    height: 4.5rem;
    // 注意: 這邊不能用 1 / -1, 因為 -1 只適用於有顯式聲明的 row
    grid-row: 1 / span 2;
    transform: translateY(-1rem);
  }

  &__text {
    font-size: 1.7rem;
  }
}
```


### Homes Section

* 房子卡片

![](https://i.imgur.com/PK7KsYX.png)

將卡片做成兩欄 然後將名字和愛心的icon 設置跟 img 一樣的 row，再透過 z-index 去覆蓋

```scss
.home {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  row-gap: 3.5rem;

  &__img {
    width: 100%;
    grid-row: 1 / 2;
    grid-column: 1 / -1;
    z-index: 1;
  }

  &__like {
    grid-row: 1 / 2;
    grid-column: 2 / 3;
    fill: $color-primary;
    height: 2.5rem;
    width: 2.5rem;
    z-index: 2;
    justify-self: end;
    margin: 1rem;
  }

  &__name {
    grid-row: 1 / 2;
    grid-column: 1 / -1;
    justify-self: center;
    align-self: end;
    z-index: 3;
    transform: translateY(50%);

    // 略
  }
}
```

### Gallery

* 圖片牆

![](https://i.imgur.com/1NijEs3.jpg)

透過 CSS Grid 和 img 的 `object-fit` 屬性來實現圖片牆的展示

```scss
.gallery {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  // 使用 vw 單位讓 row 根據螢幕寬度去自適應
  grid-template-rows: repeat(7, 5vw);
  grid-gap: 1.5rem;
  padding: 1.5rem;

  &__item {
    &--1 {
      grid-row: 1 / span 2;
      grid-column: 1 / span 2;
    }

    &--2 {
      grid-row: 1 / span 3;
      grid-column: 3 / span 3;
    }

    &--3 {
      grid-row: 1 / span 2;
      grid-column: 6 / span 1;
    }

    // 略...
  }

  &__img {
    display: block;
    width: 100%;
    height: 100%;
    // 要同時設定寬和高才能使 object-fit 生效
    object-fit: cover;
  }
}
```
