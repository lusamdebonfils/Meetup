<template>
  <v-app light>
    <v-navigation-drawer v-model="sideNav" temporary>
      <v-list>
        <v-list-tile v-for="item in  menuItems" 
        :key="item.title"
        router
        :to="item.link"
        >
          <v-list-tile-action>
            <v-icon>{{ item.icon}}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            {{ item.title}}
          </v-list-tile-content>
        </v-list-tile>


      </v-list>
    </v-navigation-drawer>
    <v-toolbar>
      <v-toolbar-side-icon @click.native.stop="sideNav = !sideNav" class="hidden-sm-and-up"></v-toolbar-side-icon>
      <v-toolbar-title>
        <router-link to="/" tag="span" style="cursor:pointer">
        MeetUp
        </router-link>
        </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-xs-only">
        <v-btn flat v-for="item in  menuItems" 
        :key="item.title"
        router
        :to="item.link"
        >
          <v-icon left>{{ item.icon}}</v-icon>
          {{ item.title}}
        </v-btn>
      

      </v-toolbar-items>
    </v-toolbar>
    <main>
    <router-view></router-view>

    </main>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        sideNav: false,
        clipped: false,
        drawer: true,
        fixed: false,
        menuItems: [
          { icon: 'supervisor_account', title: 'View MeetUps', link: '/meetups' },
           { icon: 'room', title: 'Organize MeetUp', link: '/meetup/new' },
            { icon: 'person', title: 'Profile', link: '/profile' },
             { icon: 'face', title: 'Sing up', link: '/signup' },
              { icon: 'lock_open', title: 'Sign in', link: '/signin' }

        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Vuetify.js'
      }
    }
  }
</script>

<style lang="stylus">
  @import './stylus/main'
</style>
