<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-deep-orange-10">
      <q-toolbar>
    <q-btn dense flat round @click="leftDrawerOpen = !leftDrawerOpen" icon="menu"/>
    <q-space></q-space>
    <q-btn flat round>
  <q-avatar>
          <img src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/dcf2a4a0-8fb5-45dd-8bf8-8017a35cf1d2/deeiz9c-0c9ecef0-fa47-45a4-bced-c7e28ac3ec01.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcL2RjZjJhNGEwLThmYjUtNDVkZC04YmY4LTgwMTdhMzVjZjFkMlwvZGVlaXo5Yy0wYzllY2VmMC1mYTQ3LTQ1YTQtYmNlZC1jN2UyOGFjM2VjMDEuanBnIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.Q93od_wD0-3a47q5w804wNm1IngBowqEzQ9NAJyp57g" />
        </q-avatar>
        <q-menu>
          <q-list style="min-width: 100px">
            <q-separator />
            <q-item clickable v-close-popup>
              <q-item-section>Profile</q-item-section>
            </q-item>
            <q-separator />
            <q-item clickable v-close-popup @click="logout()">
              <q-item-section>Logout</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
        </q-btn>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :breakpoint="500"
      content-class="text-white bg-primary"
    >
    <q-scroll-area class="fit">
        <q-list>
          <q-item class="justify-center text-center q-mb-md q-mt-md">
           <div>
              <q-avatar size="100px">
              <img src="https://steamuserimages-a.akamaihd.net/ugc/772865496057619242/3B80531FBB34FB2021F384AA675EE2DAF1C64D40/">
              </q-avatar>
            <div class="text-weight-bold q-mt-md">{{ $q.localStorage.getItem('dataUser').namaLengkap }}</div>
            <div class="text-yellow">Aplikasi Nonton Anime</div>
           </div>
          </q-item>

          <q-item clickable active-class="active" v-ripple exact :to="{ name: 'dashboardAdmin' }">
            <q-item-section avatar>
            <q-icon name="dashboard"/>
            </q-item-section>
            <q-item-section>
            <q-item-label>Dashboard</q-item-label>
            </q-item-section>
          </q-item>
           <q-item clickable active-class="active" v-ripple exact :to="{ name: 'dataAnime' }">
            <q-item-section avatar>
            <q-icon name="style"/>
            </q-item-section>
            <q-item-section>
            <q-item-label>Data Anime</q-item-label>
            </q-item-section>
          </q-item>
          <q-item clickable active-class="active" :to="{ name: 'inputBarang' }" v-ripple exact>
            <q-item-section avatar>
            <q-icon name="input"/>
            </q-item-section>
            <q-item-section>
            <q-item-label>Input Anime</q-item-label>
            </q-item-section>
          </q-item>
          <q-item clickable active-class="active" :to="{ name: 'dataUser' }" v-ripple exact>
            <q-item-section avatar>
            <q-icon name="supervisor_account"/>
            </q-item-section>
            <q-item-section>
            <q-item-label>Data User</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
    </q-scroll-area>
    </q-drawer>

    <q-page-container class="bg-grey-3">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
const linksData = [
]

export default {
  name: 'MainLayout',
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  },
  methods: {
    logout () {
      this.$q.localStorage.remove()
      this.$router.push({ name: 'loginPage' })
    }
  }
}
</script>
<style scoped>
.active {
  color: #000000;
  background-color : #fff;
  padding-right: 10px;
}
</style>
