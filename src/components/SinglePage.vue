<template>
    <header :class="{ 'scrolled-nav' : scrollPosition }">
        <nav>
            <div class="name-logo">
                videonly
            </div>
            <div v-show="!mobile" class="button-leftside">
                <ul v-show="!mobile" class="navigation" style="">
                    <li><a href="#" class="link1" style="background-color: transparent">LOGIN</a></li>
                    <li><a href="#" class="link2">SIGNIN</a></li>
                </ul>
            </div>
            <div class="icon-nav">
                <i @click="toggleMobileNav" v-show="mobile" class="far fa-bars" :class="{ 'fas fa-times' : mobileNav }"></i>
            </div>
            <transition name="mobile-nav">
                <ul v-show="mobileNav" class="dropdown-nav">
                    <li><a href="#" class="link">LOGIN</a></li>
                    <li><a href="#" class="link">SIGNIN</a></li>
                </ul>         
            </transition>
        </nav>
    </header>
</template>

<script>
export default {
    name: 'SinglePage',
    data() {
        return {
            scrollPosition: null,
            mobile: null,
            mobileNav: null,
            windowWidth: null,
        }
    },

    created() {
        window.addEventListener('resize', this.checkScreen);
        this.checkScreen();
    },

    methods: {
        toggleMobileNav() {
            this.mobileNav = !this.mobileNav;
        },

        checkScreen() {
            this.windowWidth = window.innerWidth;
            if (this.windowWidth <= 759) {
                this.mobile = true;
                return;
            }
            this.mobile = false;
            this.mobileNav = false;
            return;
        },
    },
};
</script>

<style lang="postcss">
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@500&display=swap');


header {
    font-family: 'Noto Sans KR', sans-serif;
    background-color: transparent;
    z-index: 99;
    width: 100%;
    position: fixed;
    transition: .5s ease all;
    color: #fff;
}

.name-logo {
    display: flex;
    align-items: center;
}

nav {
    position: relative;
    display: flex;
    flex-direction: row;
    padding: 12px 0;
    transition: .5s ease all;
    width: 90%;
    margin: 0 auto;
}

.navigation {
    position: absolute;
    width: 95%;
    display: flex;
    flex: 1;
    justify-content: flex-end;
}

li {
    text-transform: uppercase;
    margin-left: 16px;
}

.navigation li a {
    font-size: 12px;
    background-color: #f44336;
    color: white;
    padding: 5px 25px;
    text-decoration: none;
}

.link1 {
    background-color: transparent;
    border: 1px solid white;
    border-radius: 5px;
}

.link1:hover {
    --tw-bg-opacity: 0.2;
    background-color: rgba(254, 242, 242, var(--tw-bg-opacity));
}

.link2 {
    border-radius: 5px;
}

.link2:hover {
    --tw-bg-opacity: 1;
    background-color: rgba(254, 202, 202, var(--tw-bg-opacity));
    color: black;
}

.icon-nav {
    display: flex;
    align-items: center;
    position: absolute;
    top: 0;
    right: 24px;
    height: 100%;
}

.icon-nav i {
    cursor: pointer;
    font-size: 20px;
    transition: .8 ease all;
}


.dropdown-nav {
    display: flex;
    flex-direction: column;
    position: fixed;
    width: 100%;
    max-width: 250px;
    height: 100%;
    background-color: rgb(255, 255, 255);
    top: 0;
    left: 0;
}

.dropdown-nav li {
    margin-left: 10px;
}

.dropdown-nav>li>a {
    color: black;
}

.mobile-nav-enter-active,
.mobile-nav-leave-active {  
    transition: 1s ease all;
}

.mobile-nav-enter-active,
.mobile-nav-leave-to {
    transform: translateX(-250px);
}

.mobile-nav-enter-to {
    transform: translateX(0);
}

@media {min-width: 1140px} {
    nav {
        max-width: 1140px;
    }
}



</style>