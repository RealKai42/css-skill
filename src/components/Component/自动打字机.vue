<template>
  <div class="bruce flex-ct-x" data-title="自动打字器">
    <div class="auto-typing">
      Do You Want To Know More About CSS Development Skill
    </div>
  </div>
</template>
<style lang="scss" scoped>
@mixin typing($count: 0, $duration: 0, $delay: 0) {
  overflow: hidden;
  border-right: 1px solid transparent;
  /* ch 为一个字符的宽度 */
  width: #{$count + 1}ch;
  font-family: Consolas, Monaco, monospace;
  white-space: nowrap;
  animation: typing #{$duration}s steps($count + 1) #{$delay}s infinite
      backwards,
    caret 500ms steps(1) #{$delay}s infinite forwards;
}

.auto-typing {
  font-weight: bold;
  font-size: 30px;
  color: #09f;
  /* 引入 mixin */
  @include typing(52, 5);
}
@keyframes caret {
  /* 闪烁的右 border */
  50% {
    border-right-color: currentColor;
  }
}
@keyframes typing {
  from {
    width: 0;
  }
}
</style>
