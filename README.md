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
