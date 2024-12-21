<template>
    <header :class="{ 'scrolled-nav': scrolledNav }">
        <nav>
            <div class="branding">
                T E A M B L A C K
            </div>
            <ul v-show="!mobile" class="navigation">
                <li><router-link class="link" :to="{ name: 'home' }">IsaacLora</router-link></li>
                <li><router-link class="link" :to="{ name: '' }">Documentos</router-link></li>
                <li><router-link class="link" :to="{ name: '' }">Guías</router-link></li>
                <li><router-link class="link" id="button" :to="{ name: '' }">TABBY APP</router-link></li> <!-- Esto te mandará a la ruta del tabby -->
            </ul>
          <!--   <div class="icon">
                <i @click="toggleMobileNav" v-show="mobile" class="far fa-bars" :class="{'icon-active': mobileNav }"></i>
            </div> -->
            <transition name="mobile-nav">
                <ul v-show="mobileNav" class="dropdown">
                <li><router-link class="link" :to="{ name: 'home' }">IsaacLora</router-link></li>
                <li><router-link class="link" :to="{ name: '' }">Documentos</router-link></li>
                <li><router-link class="link" :to="{ name: '' }">Guías</router-link></li>
                <li><router-link class="link" id="button" :to="{ name: '' }">TABBY APP</router-link></li> <!-- Este te mandara a la app del tabby desde el mobil -->
             </ul>
            </transition>  
        </nav>
    </header>
</template>

<script>
export default {
    name: "nav",
    data() {
        return {
            scrolledNav: null,
            mobile: null,
            mobileNav: null,
            windowWidth: null,
        }
    },
    mounted () {
       window.addEventListener('scroll', this.updateScroll)
    },
    created() {
        window.addEventListener('resize', this.checkScreen);
        this.checkScreen()
    },
    methods: {
        toggleMobileNav() {
            this.mobileNav = !this.mobileNav;
        },

        updateScroll() {
            const scrollPosition = window.scrollY;
            if(scrollPosition > 50) {
                this.scrolledNav = true;
                return;
            }
            this.scrolledNav = false;
        },

        checkScreen() {
            this.windowWidth = window.innerWidth;
            if(this.windowWidth <= 830) {
                this.mobile = true;
                return;
            }
            this.mobile = false;
            this.mobileNav = false;
            return;
        }
    }
}
</script>

<style lang="css" scoped>
header {
  z-index: 99;
  width: 100%;
  position: fixed;
  transition: .5s ease all;
  color: #fff;

  nav {
  position: relative; 
  display: flex;
  flex-direction: row;
  padding: 12px;
  transition: .5s ease all;
  width: 90%;
  margin: 0 auto;
  
  @media(min-width: 1140px) {
    max-width: 1140px;
  }
  ul,
  .link {
    font-weight: 500;
    color: #fff;
    list-style: none;
    text-decoration: none;
  }

  li {
    text-transform: uppercase;
    padding: 16px;
    margin: 16px;
  }
  .link {
    font-size: 14px;
    transition: .5 ease all;
    padding-bottom: 4px;
    border-bottom: 1px solid transparent;

    &:hover {
        color: #00afea;
        border-color: #00afea;
    }
  }

  .branding {
    display: flex;
    align-items: center;
}

.navigation {
    display: flex;
    align-items: center;
    flex: 1;
    justify-content: center;
}

.icon {
    display: flex;
    align-items: center;
    position: absolute;
    top: 0;
    right: 24px;
    height: 100%;
    i {
        cursor: pointer;
        font-size: 24px;
        transition: .8 ease all;
    }
}

.icon-active {
    transform: rotate(180deg);
}


  
.dropdown {
    display: flex;
    flex-direction: column;
    position: fixed;
    width: 100%;
    max-width: 250px;
    height: 100%;
    top: 0;
    left: 0;
    backdrop-filter: blur(10px);
    background-color: black;
    li {
        margin-top: 0px;
        margin-left: 0;
        .link {
            color: #fff;
        }
    }
    .mobile-nav-enter-active, 
    .mobile-nav-enter-leaving {
        transition: 1s ease all;
    }

    .mobile-nav-enter-from, .mobile-nav-enter-leave-to {
        transform: translateX(-250px);
    }

    .mobile-nav-enter-to {
        transform: translateX(0);
    }
}
}
}

.scroll-nav {
    background-color: #000;
    box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -1px rgba(0,0,0,0.0.06);
    nav { 
        padding: 8px 0;
        .branding {
            width: 40px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -1px rgba(0,0,0,0.0.06);
        }
    }
}


</style>
