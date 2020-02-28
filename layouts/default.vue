<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>

       
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      {{title}}
      <v-spacer />
      <span v-if="this.$auth.user">
      Welcome, <b>{{this.$auth.user.name}}</b>
      <v-btn text @click="logout">      

        {{logout_btn.label}}
        <v-icon>{{ logout_btn.icon }}</v-icon>
      </v-btn>
     </span>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
   
    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; {{year}}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      year: new Date().getFullYear(),
      clipped: false,
      drawer: true,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'User',
          to: '/user'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Role',
          to: '/role'
        },
       
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Account Management Systen',
      logout_btn:{
        icon:'mdi-logout',
        label:'Logout'
      }
    }
  },
  methods:{
  async logout() {
    await this.$auth.logout();
  },
  }
}
</script>
