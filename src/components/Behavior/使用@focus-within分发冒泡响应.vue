<template>
  <div class="bruce flex-ct-x" data-title="使用:focus-within分发冒泡响应">
    <form class="bubble-distribution">
      <h3>注册</h3>
      <div class="account">
        <input
          type="text"
          placeholder="请输入手机或邮箱"
          pattern="^1[3456789]\d{9}$|^[\w-]+(\.[\w-]+)*@[\w-]+(\.[\w-]+)+$"
          required
        />
        <img
          src="https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-assets/v3/static/img/greeting.1415c1c.png~tplv-t2oaga2asx-image.image"
        />
      </div>
      <div class="password">
        <input
          type="password"
          placeholder="请输入密码(6到20位字符)"
          pattern="^[\dA-Za-z_]{6,20}$"
          required
        />
        <img
          src="https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-assets/v3/static/img/blindfold.58ce423.png~tplv-t2oaga2asx-image.image"
        />
      </div>
      <div class="code">
        <input
          type="text"
          placeholder="请输入邀请码(6位数字)"
          pattern="^[\d]{6}$"
          maxLength="6"
          required
        />
        <button type="button">查询</button>
        <img
          src="https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-assets/v3/static/img/greeting.1415c1c.png~tplv-t2oaga2asx-image.image"
        />
      </div>
      <img
        src="https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-assets/v3/static/img/normal.0447fe9.png~tplv-t2oaga2asx-image.image"
      />
      <ul>
        <li>
          <input id="male" type="radio" name="sex" />
          <label for="male">Boy</label>
        </li>
        <li>
          <input id="female" type="radio" name="sex" />
          <label for="female">Girl</label>
        </li>
      </ul>
      <button type="button">注册</button>
    </form>
  </div>
</template>
<style lang="scss" scoped>
.bruce {
  background-color: #999;
}
.bubble-distribution {
  position: relative;
  margin-top: 50px;
  padding: 25px;
  border-radius: 2px;
  width: 320px;
  background-color: #fff;
  h3 {
    font-size: 16px;
    color: #333;
  }
  div {
    margin-top: 10px;
  }
  img {
    position: absolute;
    /*
    这里先用绝对定位 left: 50%
    定位到中心，然后再用偏移让图片居中
    */
    left: 50%;
    bottom: 100%;
    margin: 0 0 -20px -60px;
    width: 120px;
  }
  ul {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 10px;
    height: 30px;
    line-height: 30px;
  }
  li {
    position: relative;
    width: 45%;
    transition: all 300ms;
    &:focus-within {
      background: linear-gradient(90deg, #09f 50%, transparent 0) repeat-x,
        linear-gradient(90deg, #09f 50%, transparent 0) repeat-x,
        linear-gradient(0deg, #09f 50%, transparent 0) repeat-y,
        linear-gradient(0deg, #09f 50%, transparent 0) repeat-y;
      background-position: 0 0, 0 100%, 0 0, 100% 0;
      background-size: 8px 1px, 8px 1px, 1px 8px, 1px 8px;
      animation: move 500ms infinite linear;
    }
  }
  input[type="text"],
  input[type="password"] {
    padding: 10px;
    border: 1px solid #e9e9e9;
    border-radius: 2px;
    width: 100%;
    height: 40px;
    outline: none;
    transition: all 300ms;
    &:focus:valid {
      border-color: #09f;
    }
    &:focus:invalid {
      border-color: #f66;
    }
  }

  input[type="radio"] {
    position: absolute;
    width: 0;
    height: 0;
    &:checked + label {
      border: 3px solid transparent;
      background-color: #09f;
      color: #fff;
    }
  }
  label {
    display: block;
    border-bottom: 1px solid #ccc;
    width: 100%;
    background-clip: padding-box;
    cursor: pointer;
    text-align: center;
    transition: all 300ms;
  }
  button {
    margin-top: 10px;
    border: none;
    border-radius: 2px;
    width: 100%;
    height: 40px;
    outline: none;
    background-color: #09f;
    cursor: pointer;
    color: #fff;
    transition: all 300ms;
  }
  /* 这里接受到的 focus-within 是冒泡自己的自元素 */
  .account,
  .password,
  .code {
    img {
      display: none;
      margin-bottom: -27px;
    }
    &:focus-within {
      /* 当 focus 时，把自己 div 下的 img 设置为 block */
      img {
        display: block;
      }
      /* 把跟自己同级的通用 img 设置为 none */
      & ~ img {
        display: none;
      }
    }
  }
  .code {
    display: flex;
    justify-content: space-between;
    button {
      margin-top: 0;
    }
    input {
      &:not(:placeholder-shown) {
        width: 70%;
        & + button {
          width: 25%;
        }
      }
      &:placeholder-shown {
        width: 100%;
        & + button {
          width: 0;
          opacity: 0;
        }
      }
    }
  }
}
@keyframes move {
  to {
    background-position: 6% 0, -6% 100%, 0 -6%, 100% 6%;
  }
}
</style>
