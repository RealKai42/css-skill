<template>
  <div class="bruce flex-ct-x" data-title="iOS开关按钮">
    <input class="ios-switch" type="checkbox" />
  </div>
</template>
<style lang="scss" scoped>
.btn {
  border-radius: 31px;
  width: 102px;
  height: 62px;
  background-color: #e9e9eb;
}
.ios-switch {
  position: relative;
  /* 不显示 */
  appearance: none;
  cursor: pointer;
  transition: all 100ms;
  @extend .btn;
  &::before {
    position: absolute;
    content: "";
    transition: all 300ms cubic-bezier(0.45, 1, 0.4, 1);
    @extend .btn;
  }
  &::after {
    position: absolute;
    left: 4px;
    top: 4px;
    border-radius: 27px;
    width: 54px;
    height: 54px;
    background-color: #fff;
    box-shadow: 1px 1px 5px rgba(#000, 0.3);
    content: "";
    transition: all 300ms cubic-bezier(0.4, 0.4, 0.25, 1.35);
  }
  &:checked {
    background-color: #5eb662;
    &::before {
      /* 
      用来模拟按钮背景的缩放渐变，
      相当是一层在按钮背景上的布，
      点击按钮时这块布快速缩小，
      就实现了变换颜色 */
      transform: scale(0);
    }
    &::after {
      transform: translateX(40px);
    }
  }
}
</style>
