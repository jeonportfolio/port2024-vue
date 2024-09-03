<script setup>
import { headerNav } from "../constants";
</script>

<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__logo">
                <h1>
                    <a href="#">portfolio<em>vue.js(DARK MODE)</em></a>
                </h1>
            </div>
            <nav 
                class="header__nav"
                :class="{ show: isNavVisible }"
                role="navigation" 
                aria-label="메인 메뉴"
            >
                <ul>
                    <li v-for="(nav, key) in headerNav" :key="key">
                        <a :href="nav.url" @click="scrollLink($event)">{{ nav.title }}</a>
                        <!-- 클릭하면 event값을 가져온다. -->
                    </li>
                </ul>
            </nav>
            <div 
                class="header__nav__mobile" 
                id="headerToggle" 
                aria-controls="primary-menu" 
                :aria-expanded="isNavVisible.toString()"

                role="button"
                tabindex="0"
                @click="toggleMobileMenu"
            >
            <!-- aria expended에서  toString은 ture와 false의 값으로 받기때문에 문자열 취급해준다. -->
                <span></span>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    data(){
        return {
            isNavVisible: false,
        }
    },
    methods: {
        toggleMobileMenu(){
            this.isNavVisible = !this.isNavVisible;
        },
        scrollLink(event){
            event.preventDefault();

            const targetId = event.target.getAttribute("href");
            const targetElement = document.querySelector(targetId);

            if(targetElement){
                targetElement.scrollIntoView({ behavior: "smooth" });
            }
        }
    }
}
</script>

<style lang="scss">
@import "@/assets/scss/mixin";

#header {
    @include position-fixed;
    z-index: 10000;
}

.header__inner {
    @include flex-between;
    background-color:  rgba(10, 10, 10, 0.825);
    backdrop-filter: blur(15px);
    
    .header__logo {
        font-size: 1.5rem; //1rem은 16px기준 root기준으로 바뀐다.rem은 미세하게 바뀌는 것 
        text-align: center;
        text-transform: uppercase;
        line-height: 1;
        color: #fff;

        @media (max-width: 830px){
            font-size: 1.3rem;
        }   
        
        em {
            font-size: 17px;
            display: block;
            color: #d9d9d9;
        }
    }
    .header__nav {
        @media (max-width: 830px){
            display: none;

            &.show { //show가 생겼을때 메뉴창이 나오게 하는 설정 
                display: block;

                ul {
                    display: block;
                    position: absolute;
                    right: 0;
                    top: 52px;
                    background-color: #434040;
                    opacity: 90%;
                    backdrop-filter: blur(15px);
                    z-index: 10000;
                    min-width: 150px;
                    padding: 20px 0;
                
                    li {
                        display: block;
                        text-align: right;
                        
                        a {
                            display: inline-block;
                            padding: 10px;
                            color: #fff;
                        }
                    }
                }
               
            }
            &.show + .header__nav__mobile span::before {
                width: 20px;
            }
            &.show + .header__nav__mobile span::after {
                width: 20px;
            }
        } 
        
        li {
            display: inline;
    
            a {
                text-transform: uppercase;
                font-size: 20px;
                padding: 14px;
                position: relative;
                color:#fff;
    
                &::before {       //메뉴명에 밑줄생김
                    content: '';
                    width: calc(100% - 28px);
                    height: 1px;
                    background-color:#fff;
                    position: absolute;
                    left: 14px;
                    bottom: 10px;
                    transform: scaleX(0); //가로의 크기가 0이여서 보이지 않게됨 
                    transition: all 0.3s;
                }
    
                &:hover::before {
                    transform: scaleX(1);  //scale을 0에서 1로 주게되면 없어졌다가 다시 나타남
                }
            }
        }
    }
    .header__nav__mobile {
        display: none;
        width: 40px;
        height: 40px;
        cursor: pointer;
        position: relative;

        @media (max-width: 830px){
            display: block;
        }
        
        span {
            display: block;
            width: 40px;
            height: 2px;
            background-color: var(--black);
            margin-top: 19px;
            position: relative;
        }

        &::before {
            content: "";   
            width: 40px;
            height: 2px;
            background-color: var(--black);
            position: absolute;
            right: 0;
            top: 6px;
            transition: width 0.3s;
        }
        &::after {
            content: "";
            width: 40px;
            height: 2px;
            background-color: var(--black);
            position: absolute;
            left: 0;
            bottom: 6px;
            transition: width 0.3s;
        }
    }

    // 자식관계이면 그 안에 써도 된다. 
}

</style>

