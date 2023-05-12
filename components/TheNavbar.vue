<template>
  <header class="header" :class="{'open': navbarExpand}">
    <div class="overlay has-fade"></div>
    <nav id="header-nav" class="flex container flex-j-c-sb flex-a-i-c">
      <a href="#" class="header__toggle" @click="navbarExpand = !navbarExpand">
        <!-- <img src="images/icon-menu.svg" alt=""> -->
        <span></span>
        <span></span>
        <span></span>
      </a>
      <div class="header__logo">
        <!--          <img src="images/logo.svg" alt="">-->
        <slot name="logo"></slot>
      </div>
      <ul class="header__links hide-for-mobile">
        <li><a href="#">Collections</a></li>
        <li><a href="#">Men</a></li>
        <li><a href="#">Women</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
      <div class="flex flex-a-i-c header__user">
        <div class="header__cart flex flex-j-c-e">
          <!--            <img src="images/icon-cart.svg" alt="">-->
        </div>
        <div class="header__avatar flex flex-a-i-c">
          <!--            <img src="images/image-avatar.png" alt="">-->
        </div>
      </div>
    </nav>
    <!--Menu for mobile-->
    <div class="header__menu">
      <a href="#">Collections</a>
      <a href="#">Men</a>
      <a href="#">Women</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </div>

  </header>
</template>

<script>
export default {
  name: "TheNavbar",
  data(){
    return{
      navbarExpand: false
    }
  }
}
</script>

<style scoped lang="scss">

.header {
  position: fixed;
  animation: fade-in;
  z-index: 6;
  width: 100%;
  background-color: white;

  .header__toggle {
    display: block;
    @media (min-width: 992px) {
      display: none;
    }
  }

  &.open {
    .header__toggle { //mobile menu toggle

      > span:nth-child(2) {
        opacity: 0;
      }

      > span:first-child {
        transform: rotate(45deg);
      }

      > span:last-child {
        transform: rotate(-45deg);
      }

    }

    .overlay {
      opacity: 1;
      visibility: visible;
    }

    .header__menu {
      left: 0;
    }
  }

  &__toggle { //mobile menu toggle
    position: relative;
    margin-right: 0.937rem;

    > span {
      display: block;
      width: 1.625rem;
      height: 0.187rem;
      background-color: #000;
      transition: all 300ms ease-in-out;
      transform-origin: 2px 2px;

      &:not(:last-child) {
        margin-bottom: 5px;
      }


    }
  }

  &__logo {
    img {
      width: 5.8125rem;
      //height: 1.375rem;
      height: 2.375rem;
    }
  }

  &__links {
    display: none;
    @media (min-width: 992px) {
      display: flex;
    }

    li {
      //color:$darkGrayishBlue;
      transition: color 200ms ease-in-out;
      position: relative;
      // min-width: 100px;

      &:not(:last-child) {
        margin-right: 2.125rem;
      }

      &:hover {
        //color:$veryDarkBlue;
      }

      &::before {
        content: "";
        position: absolute;
        top: 12px;
        left: 50%;
        width: 50px;
        height: 50px;
        //border:4px solid $black;
        transform: translateX(-50%) translateY(-50%) scale(0.5);
        border-radius: 5%;
        background: transparent;
        opacity: 0;
        transition: all 0.3s;
        z-index: -1;
      }

      &:hover::before {
        opacity: 1;
        width: 250%;
      }
    }
  }

  &__cart {
    img {
      width: 1.562rem;
      height: 1.562rem;
    }

    margin-right: 2.75rem;
  }

  &__avatar {
    img {
      width: 3.125rem;
      height: 3.125rem;
    }
  }

  nav {
    padding-top: 1.5rem;
    padding-bottom: 1.5rem;
  }

  .overlay {
    // opacity: 0;
    position: fixed;
    //background-image:linear-gradient($veryDarkBlue,transparent);
    top: 4.8rem;
    right: 0px;
    bottom: 0px;
    left: 0px;
    animation: fade-in 300ms ease-in-out;
  }

  &__menu {
    position: fixed;
    top: 4.8rem;
    margin: 0;
    width: 60%;
    left: -100%;
    background: white;
    text-align: left;
    padding-left: 1.25rem;
    padding-top: 2.312rem;
    height: 100vh;

    a {
      display: block;
      margin-bottom: 1.5rem;
      //font-size: $font-med;
      font-weight: 900;
      //color:$veryDarkBlue;
    }

    a :not(last-child) {
      margin-bottom: 1.5rem;
    }
  }
}
</style>
