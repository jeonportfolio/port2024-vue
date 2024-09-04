<script setup>
import { skillText } from "@/constants/index";
</script>

<template>
    <section id="skill">
        <div class="skill__inner">
            <h2 class="skill__title">
                Challenge <em>나의 도전</em>
            </h2>
            <div class="skill__desc">
                <div v-for="(text, key) in skillText" :key="key">
                    <span>{{ key + 1 }}.</span>
                    <h3>{{ text.title }}</h3>
                    <p>{{ text.desc }}</p>
                </div>
                <div>
                            <span>3.</span> 
                            <h3>학력 및 자격사항</h3>
                            <p > ▶한국공학대학교(IT경영학과)(2019.03 ~ 2025.02(졸업예정))<br/>
                                 ▶웹디자인 기능사<br/>
                                 ▶머니스테이션(인턴과정(실습 및 파트) 2024.01.02 ~ 2024.10.05)(마케팅부서) <br/>
                                 ▶OPIC IH등급<br/>
                                 ▶SQLD<br/>
                                 ▶컴퓨터활용능력2급<br/>
                                 ▶교내 공모전 -팀 프로젝트 APP 기획- 우수상<br/>
                                 ▶운전면허 보통 2종 <br/>
                                 ▶바리스타 2급 <br/>
                            </p>
                        </div>
            </div>            
        </div>
    </section>
</template> 

<style  lang="scss">
.skill__inner {
    padding: 30px;
    display: flex;
    justify-content: space-between;

    @media (max-width: 800px){
        flex-direction: column;
    }

    .skill__title {
        
        position: sticky;
        top: 65px;
        left: 0;
        height: 5vw;
        font-size: 4vw;
        font-weight: 900;
        line-height: 1.6;
        font-family: var(--mainKor-font);
        text-transform: uppercase;
        border-bottom: 0.4vw solid #fff;

        @media (max-width: 800px){
            width: 100%;
            margin-bottom: 10vw;
            font-size: 30px;
            height: auto;
            top: 53px;
            background-color: var(--mainBg-color);
        }
    

        em {
            font-size: 1.25rem;
            font-weight: 400;
            line-height: 2;
        }
    

     
    }
    .skill__desc {
        width: 50%;
        
        @media (max-width: 800px){
           width: 100%;
        }
    

        span {
            font-size: 5vw;
            line-height: 1;
            font-weight: 900;
            line-height: 1.3;
            font-family: var(--mainNum-font);
            @media (max-width: 800px){
               font-size: 20vw;
             }
        }
        h3 {
            font-size: 1.5rem;
            text-decoration: underline;
            text-underline-position: under;
            margin-bottom: 1vw;
        }
        p {
            margin-bottom: 30vh;
            font-size: 1.1rem;
        }
    }

}
</style>