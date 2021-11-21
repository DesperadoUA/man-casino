<template>
    <nav class="menu">
        <div :class="item | menuItemClass" v-for="(item, index) in value" :key="index">
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
        data() {
			return {
				value: [
                    {title: 'Онлайн казино',
                        permalink: '/',
                        child: [
                        	{title: 'Casino 1', 'permalink': '/casino/slotoking/'},
							{title: 'Casino 2', 'permalink': '/link-2'},
							{title: 'Casino 3', 'permalink': '/link-3'},
							{title: 'Casino 4', 'permalink': '/link-4'},
							{title: 'Casino 5', 'permalink': '/link-5'},
							{title: 'Casino 6', 'permalink': '/link-6'},
							{title: 'Casino 7', 'permalink': '/link-7'},
							{title: 'Casino 8', 'permalink': '/link-8'},
							{title: 'Casino 9', 'permalink': '/link-9'},
							{title: 'Casino 10', 'permalink': '/link-10'},
							{title: 'Casino 1', 'permalink': '/casino/slotoking/'},
							{title: 'Casino 2', 'permalink': '/link-2'},
							{title: 'Casino 3', 'permalink': '/link-3'},
							{title: 'Casino 4', 'permalink': '/link-4'},
							{title: 'Casino 5', 'permalink': '/link-5'},
							{title: 'Casino 6', 'permalink': '/link-6'},
							{title: 'Casino 7', 'permalink': '/link-7'},
							{title: 'Casino 8', 'permalink': '/link-8'},
							{title: 'Casino 9', 'permalink': '/link-9'},
							{title: 'Casino 10', 'permalink': '/link-10'}
                        ]
                    },
                    {title: 'Блог', permalink: '/blog/', child: []},
					{title: 'Бонусы',
						permalink: '/bonuses',
						child: [
							{title: 'Bonus 1', 'permalink': '/bonus-1'},
							{title: 'Bonus 2', 'permalink': '/bonus-2'},
							{title: 'Bonus 3', 'permalink': '/bonus-3'},
							{title: 'Bonus 4', 'permalink': '/bonus-4'},
							{title: 'Bonus 5', 'permalink': '/bonus-5'},
							{title: 'Bonus 6', 'permalink': '/bonus-6'},
							{title: 'Bonus 7', 'permalink': '/bonus-7'},
							{title: 'Bonus 8', 'permalink': '/bonus-8'},
							{title: 'Bonus 9', 'permalink': '/bonus-9'},
							{title: 'Bonus 10', 'permalink': '/bonus-10'}
						]
					},
                    {title: 'Производители', permalink: '/vendors/',
                        child: [
                            {title:'vendor', permalink: '/vendor/thunderkick/'}
                        ]
                    },
					{title: 'Платежные системы', permalink: '/payments/', child: [
							{title:'payment', permalink: '/payment/visa/'}
                        ]}
                ]
            }
        },
        filters: {
			menuItemClass(item){
				if(item.child.length === 0) return 'menu_item'
                else return 'menu_item dropdown'
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