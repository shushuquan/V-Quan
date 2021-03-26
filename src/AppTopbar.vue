<template>
	<div class="layout-topbar">
		<button class="p-link layout-menu-button" @click="onMenuToggle">
			<span class="pi pi-bars"></span>
		</button>
		<div class="layout-topbar-icons">
			<span class="layout-topbar-search">
				<InputText type="text" placeholder="Search" />
				<span class="layout-topbar-search-icon pi pi-search"></span>
			</span>
			<button class="p-link">
				<span class="layout-topbar-item-text">Events</span>
				<span class="layout-topbar-icon pi pi-bell"></span>
				<span class="layout-topbar-badge">5</span>
			</button>
			<button class="p-link">
				<span class="layout-topbar-item-text">Settings</span>
				<span class="layout-topbar-icon pi pi-cog"></span>
			</button>
			<button class="p-link" @click="toggle"  aria-haspopup="true" aria-controls="overlay_menu">
				<span class="layout-topbar-item-text">User</span>
				<Avatar image="assets/layout/images/profile.png" class="p-mr-2" shape="circle" />
			
			</button>
                  <Menu id="overlay_menu" ref="menu" :model="items" :popup="true" />
		  
		</div>


	</div>
</template>

<script>
import AppProfile from './AppProfile.vue';
export default {
    components: {
	AppProfile
    },
	data() {
		return {
			expanded: false,
            items: [
                {
                    label: '选项',
                    items: [{
                        label: '更新',
                        icon: 'pi pi-refresh',
                        command: () => {
                            this.$toast.add({severity:'success', summary:'Updated', detail:'Data Updated', life: 3000});
                        }
                    },
                    {
                        label: '删除',
                        icon: 'pi pi-times',
                        command: () => {
                            this.$toast.add({ severity: 'warn', summary: 'Delete', detail: 'Data Deleted', life: 3000});
                        }
                    }
                ]},
		    {
                   separator:true
                },
		    {
                        label: 'Vue官网',
                        icon: 'pi pi-external-link',
                        url: 'https://vuejs.org/'
                    },
				    {
                   separator:true
                },
		    {
                        label: '路由',
                        icon: 'pi pi-upload',
                        to: '/fileupload'
                },
		    {
                   separator:true
                },
                {
                    label: '导航',
                    items: [{
                        label: 'Vue官网',
                        icon: 'pi pi-external-link',
                        url: 'https://vuejs.org/'
                    },
                    {
                        label: '路由',
                        icon: 'pi pi-upload',
                        to: '/fileupload'
                    }
                ]}
            ]

		}
	},
    methods: {
        onMenuToggle(event) {
            this.$emit('menu-toggle', event);
        },
	toggle(event) {
            this.$refs.menu.toggle(event);
        },
    }
}
</script>