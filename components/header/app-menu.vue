<template>
    <nav class="menu">
        <div :class="item | menuItemClass" v-for="(item, index) in menu" :key="index">
            <NuxtLink :to="item.permalink" class="menu_item_link">{{item.title}}</NuxtLink>
            <div class="dropdown_menu" v-if="item.child.length !== 0">
                <nav class="menu_box">
                    <ul>
                        <li class="menu_box_item"
                            v-for="(itemChild, indexChild) in item.child"
                            :key="indexChild">
                            <NuxtLink no-prefetch :to="itemChild.permalink" >
                                {{itemChild.title}}
                            </NuxtLink>
                        </li>
                    </ul>
                </nav>
            </div>
        </div>
    </nav>
</template>

<script>
	export default {
		name: "app-menu",
        filters: {
			menuItemClass(item){
				if(item.child.length === 0) return 'menu_item'
                else return 'menu_item dropdown'
            }
        },
		data(){
			return {
				value: []
			}
		},
		computed:{
			menu() {
				const options = this.$store.getters['options/getOptions']
				if(options) {
					this.value = options.menu
				}
				return this.value

			}
		}
	}
</script>

<style scoped>
    .menu {
        display: flex;
        padding: 5px;
    }
    .menu_item {
        padding: 5px 15px;
        position: relative;
    }
    .menu_item:hover .dropdown_menu{
        display: block;
    }
    .menu_item_link {
        font-family: var(--font-semi);
        color: var(--white);
        text-decoration: none;
        font-size: 19px;
    }
    .menu_box {
        height: 430px;
        overflow-y: scroll;
    }
    .menu_box_item {
        padding: 5px 25px;
    }
    .menu_box_item a {
        text-decoration: none;
        font-family: var(--font);
        font-style: normal;
        font-weight: 600;
        font-size: 14px;
        line-height: 19px;
        color: var(--light-blue);
        transition: 0.7s;
    }
    .menu_box_item:hover {
        background: var(--strong-blue);
        border-radius: 4px;
    }
    .menu_box_item:hover a {
        color: var(--white);
    }
    .dropdown_menu {
        padding: 20px 10px 20px 0px;
        display: none;
        position: absolute;
        bottom:-470px;
        left:-10px;
        height: 470px;
        width: 220px;
        overflow-y:scroll;
        background: var(--blue-opacity);
        border: 1px solid var(--gray);
        box-sizing: border-box;
        box-shadow: 0px 2px 10px rgba(77, 92, 129, 0.25);
        border-radius: 8px;
    }
    ::-webkit-scrollbar {
        width:2px;
    }
    ::-webkit-scrollbar-thumb {
        border-width:1px 1px 1px 2px;
        border-color:#777;
        background-color:#9FA7B4;
    }
    ::-webkit-scrollbar-thumb:hover {
        background-color:#9FA7B4;
    }
    ::-webkit-scrollbar-track-piece {
        background-color:#2a3950
    }
    @media (min-width: 320px) and (max-width: 767px) {
        .menu {
            display: block;
            margin-top: 20px;
        }
        .menu_item {
            position: relative;
        }
        .dropdown:after {
            content: "";
            width: 10px;
            height: 6px;
            position: absolute;
            background: url("/img/triangle.png") no-repeat;
            right: -10px;
            top:15px;
        }
        .dropdown_menu {
            position: static;
            height: 270px;
            z-index: 11;
            overflow-y: scroll;
            width: 200px;
            margin-top: 10px;
        }
        .menu_box {
            overflow-y: initial;
        }
    }
    @media (min-width: 768px) and (max-width: 1200px) {
        .menu {
            display: block;
            margin-top: 20px;
        }
        .menu_item {
            position: relative;
        }
        .dropdown:after {
            content: "";
            width: 10px;
            height: 6px;
            position: absolute;
            background: url("/img/triangle.png") no-repeat;
            right: -10px;
            top:15px;
        }
        .dropdown_menu {
            position: static;
            height: 270px;
            z-index: 11;
            overflow-y: scroll;
            width: 200px;
            margin-top: 10px;
        }
        .menu_box {
            overflow-y: initial;
        }
    }
</style>