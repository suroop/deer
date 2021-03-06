<template>
    <div id="pic" ref="pic" :style="{clip: 'rect(auto,auto,auto,'+clip_left+')'}">
        <nav>
            <div class="logo">
                <img src="../assets/deer_orange.png" alt="logo" id="logo">
                <p class="txt">Orange Theme</p>
            </div>
            <ul>
                <li><strong>THEMES</strong></li>
                <li><strong>SHOWCASE</strong></li>
                <li><strong>BLOG</strong></li>
                <li><strong>HELP</strong></li>
                <li><button class="btn"><strong>Login</strong></button></li>
            </ul>
        </nav>
        <div class="content content-left">
            <p>Our work combines</p>
            <p>design and development</p>
            <button @click="gettingStart" :style="{animation:isClick?'getting_start 3s ease-in-out forwards':'none'}">Getting Start&nbsp;&nbsp;&nbsp;<i class="fa fa-arrow-right"></i></button>
        </div>
        <img alt="deer_color" src="../assets/deer_color.png" id="deer">
        <div class="shadow"></div>
        <div class="content content-right">
            <img src="../assets/moon.jpg" alt="moon" class="moon">
            <p>We make</p>
            <p><span>sleek and modern</span> design</p>
            <p>for you business</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "PIC",
        data(){
          return {
              startX:0,
              isClick:false
          }
        },
        props:{
            clip_left:{
                type:String
            }
        },
        methods:{
            gettingStart:function () {
                this.isClick = !this.isClick;
            }
        },

    }
</script>

<style lang="scss" rel="stylesheet/scss">
    @import "src/common/scss/mixins";
    @media (max-width: 600px){
        #code{
            nav{
                ul{
                    li{
                        margin: 0 4px !important;
                    }
                }
            }
            .content{
                opacity: 0 !important;
            }
        }
    }
    @media (max-width: 1200px){
        #code{
            .content{
                opacity: 0.5;
            }
        }
    }
    #pic{
        user-select: none;
        background-color: white;
        z-index: 99;
        width: 80vw;
        height: 100vh;
        position: absolute;
        right: 10vw;
        top: 0;
        overflow: hidden;
        nav{
            width: 100%;
            height: 50px;
            display: flex;
            flex-direction: row;
            align-items: center;
            justify-content: space-between;
            .logo{
                width: 50px;
                height: 50px;
                margin: 0 10px;
                position: relative;
                .txt{
                    width: 150px;
                    position: absolute;
                    top: 50%;
                    left: 25%;
                    opacity: 0;
                    transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
                    @include flexBox(center,center);
                    color: orange;
                    font-weight: 600;
                    font-family: 'Microsoft JhengHei',serif;
                }
                #logo{
                    cursor: pointer;
                    position: relative;
                    height: 50px;
                    width: auto;
                    &:hover ~ .txt{
                        left: 50%;
                        opacity: 1;
                    }
                }
            }
            ul{
                display: flex;
                flex-direction: row;
                align-items: center;
                li{
                    width: auto;
                    height: 35px;
                    user-select: none;
                    margin: auto 10px;
                    line-height: 35px;
                    font-family: 'Microsoft Yahei',serif;
                    cursor: pointer;
                    font-size: 12px;
                    strong{
                        transition: 1s ease-in-out;
                        &:hover{
                            font-size: 14px;
                        }
                    }
                    &:hover{
                        height: 33px;
                        border-bottom: 2px solid #c2c2c2;
                    }

                    &:last-child{
                        .btn{
                            width: 80px;
                            height: 35px;
                            border-radius: 20px;
                            color: orange;
                            background-color: black;
                            border: none;
                            cursor: pointer;
                        }
                    }
                }
            }
        }
        #deer{
            user-select: none;
            position: absolute;
            left: 50%;
            top: 45%;
            transform: translate(-50%,-50%);
            height: 500px;
            width: auto;
            animation: pic_float infinite forwards 3s;
        }
        .shadow{
            position: absolute;
            left: 50%;
            top: 85%;
            transform: translate(-50%,-50%);
            width: 180px;
            height: 10px;
            border-radius: 70%;
            background-color: rgba(0, 0, 0, 0.8);
            box-shadow:0 4px 4px rgba(0, 0, 0, 0.4);
            filter: blur(4px);
            animation: shadow_float infinite forwards 3s;
        }
        .content{
            width: 350px;
            height: 400px;
            position: absolute;
            transform: translateY(-50%);
            transition: opacity 2s;
            p{
                text-align: center;
                font-family: 'Microsoft JhengHei',serif;
                font-size: 25px;
                font-weight: 400;
                color: orange;
                line-height: 50px;
                &:first-child{
                    margin-top: 5px;
                }
                span{
                    color: orange;
                }
            }
        }
        .content-left{
            top: 60%;
            left: 5%;
            button{
                width: 200px;
                height: 60px;
                border: 4px solid orange;
                background-color: transparent;
                cursor: pointer;
                border-radius: 25px;
                font-size: 18px;
                font-weight: 600;
                color: orange;
                margin: 35px 75px;

                font-family: 'Microsoft JhengHei',serif;
            }
        }
        .content-right{
            user-select: none;
            top: 60%;
            right: 5%;
            p{
                color: black;
                span{
                    color: orange;
                }
            }

            .moon{
                width: 50px;
                height: 50px;
                margin: 20px 150px;
                border-radius: 50%;
                border: none;
            }
        }
    }
</style>