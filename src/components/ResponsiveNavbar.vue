<template>
    <nav>
        <BurgerBtn
        @change = "menu = $event"
        />
        <div class="logo">
            <img src="../assets/logo.png" alt="">
        </div>
        <ul
        :class="[menu ? 'active' : false]"
        >
            <li
            v-for="(link, index) in navLinks"
            :key="index"
            @click="linkToggle(index)"
            :class="linkActive == index ? 'active' : ''"
            >
            <i :class="link.icon"></i>
                <a href=#!>
                    {{link.text}}
                <i 
                v-if="link.children"
                class="ion-ios-arrow-down"
                >
                </i>    
                </a>
            
                <div
                class="children-links"
                v-show="link.children"
                >
                <a
                v-for="(linkChildren,index) in link.children"
                @mouseenter="
                $event.currentTarget.style.background = 'green'
                $event.currentTarget.style.color = 'white'
                "
                @mouseleave="
                $event.currentTarget.style.background = ''
                $event.currentTarget.style.color = ''
                "
                :key="index"
                >
                    {{linkChildren.text}}
                </a>    
                </div>
            </li>
        </ul>
    </nav>
    
</template>

<script>
import BurgerBtn from '@/components/BurgerBtn'

    export default {
        data: () => ({
            menu: false,
            linkActive: '',
            navLinks: [
                {
                    text: "Офисы",
                    icon: "ion-ios-briefcase",
                },
                {
                    text: "Оборудование",
                    icon: "ion-ios-desktop",
                },
                {
                    text: "Phones",
                    icon: "ion-ios-phone-portrait",
                    children: [
                        {
                            text: "Телефоны Инфо"
                        },
                        {
                            text: "Телефоны по ФИО"
                        },
                        {
                            text: "Телефон с переадресацией"
                        },
                    ]
                },
                {
                    text: "IP Planning",
                    icon: "ion-ios-clipboard",
                    children: [
                        {
                            text: "IPAM"
                        }
                    ]
                },
                {
                    text: "Reports",
                    icon: "ion-ios-alert"
                },
                {
                    text: "Phone Reports",
                    icon: "ion-ios-browsers",
                    children: [
                        {
                            text: "По моделям"
                        },
                        {
                            text: "По кластерам"
                        },
                        {
                            text: "По не используемым"
                        },
                        {
                            text: "По Agent Licenses"
                        }
                    ]
                },
                {
                    text: "Tools",
                    icon: "ion-ios-hammer",
                    children: [
                        {
                            text: "Поиск незарегистрированных телефонов"
                        },
                        {
                            text: "CUCM маршрутизация"
                        },
                        {
                            text: "Testing CORS Requests"
                        }
                    ]
                },
                {
                    text: "Справочники",
                    icon: "ion-ios-information-circle-outline",
                    children: [
                        {
                            text: "Рег. центры (mapping)"
                        },
                        {
                            text: "Регионы"
                        },
                        {
                            text: "Города"
                        },
                        {
                            text: "Статусы офисов"
                        },
                        {
                            text: "Оборудование"
                        },
                        {
                            text: "Типы портов"
                        },
                        {
                            text: "VRF"
                        },
                        {
                            text: "Networks(Table)"
                        },
                        {
                            text: "Networks(Tree)"
                        },
                        {
                            text: "Логи HardWare"
                        },
                        {
                            text: "Логи Phones"
                        }
                    ]
                }
            ]
        }),
        methods: {
            linkToggle (index) {
                if (this.linkActive === index) {
                    this.linkActive = null
                } else {
                    this.linkActive = index
                }
            }
        },
        components: {BurgerBtn}
    }
</script>

<style scoped>
.logo {
    padding: 10px;
}
nav {
    display: flex;
    align-items: center;
    background-color: #f7f9f9;
    height: 70px;
    box-shadow: 0px 3px 4px rgb(0 0 0 / 25%);
}
ul {
    padding-left: 0px;
    display: flex;
    align-items: center;
    flex-basis: 100%;
    list-style: none;
    margin: 0px;
    position: absolute;
    flex-direction: column;
    width: 250px;
    height: 100%;
    top: 70px;
    background-color: #f7f9f9;
    left: -190px;
    transition: 300ms ease all;
}
li {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    flex: 0 1 15%;
    cursor: pointer;
    font-size: 18px;
    font-weight: 500;
    position: relative;
    padding: 0px 20px;
}
li.active > .children-links{
    opacity: 1;
    visibility: visible;
}
li a {
    text-decoration: none;
    color: black;
    padding: 10px 10px;
    white-space: nowrap;
}
li:not(:first-child) {
    margin-left: 20px;
}
.children-links {
    display: flex;
    min-width: 100%;
    position: absolute;
    background: #fff;
    flex-direction: column;
    top: 100%;
    left: 0;
    text-align: left;
    box-shadow: 2px 2px 4px 4px rgb(0 0 0 / 25%);
    opacity: 0;
    transition: all 0.4s;
    visibility: hidden;
    max-height: 300px;
    overflow: hidden;
    overflow-y: auto;
}
li:hover {
    background: #1212;
}
li.active .ion-ios-arrow-down::before {
    transition: 300ms ease all;
    transform: scaleY(-1);
}
.outside {
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0px;
    left: 0px;
}
ul.active {
    left: 0px;
}
li {
    flex: none;
    height: 50px !important;
    margin-left: 0px !important;
    flex-direction: row-reverse;
    width: 100%;
    justify-content: space-between;
}
.logo {
    width: 100%;
    text-align: center;
}
#burger {
    display: block;
    margin-left: 15px;
}
.children-links {
    background-color: #f7f9f9;
    z-index: 99;
}
ul:not(.active) li.active .children-links{
    opacity: 0;
    visibility: hidden;
}
</style>