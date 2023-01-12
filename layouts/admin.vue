<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <div style="display: flex; flex-direction: column; align-items: center; margin-top: 10px; margin-bottom: 20px">
        <div style="display: flex; gap: 5px; width: 75%; align-items: center;">
          <div class="w-25">
            <v-img src="/icon.png"/>
          </div>
          <span class="font-weight-bold text-h4">LOGO</span>
        </div>
        <span class="text-grey">Lorem ipsum dolor asit mer</span>
      </div>

      <div style="height: 80vh">
        <div class="px-3" style="display: flex; flex-direction: column; justify-content: space-between; height: 100%">
          <v-list nav density="compact">
            <v-divider/>
            <v-list-item
                v-for="(item, i) in items"
                :key="i"
                :value="item"
                active-color="primary"
                rounded="shaped">
              <template v-slot:prepend>
                <v-icon :icon="item.icon"></v-icon>
              </template>

              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item>
            <v-divider/>
            <v-list-group value="Users">
              <template v-slot:activator="{ props }">
                <v-list-item
                    v-bind="props"
                    prepend-icon="mdi-account-circle"
                    title="Users"
                ></v-list-item>
              </template>

              <v-list-item
                  v-for="i in 3"
                  title="Admin"
                  prepend-icon="mdi-account-circle"
              ></v-list-item>
            </v-list-group>
            <v-list-group value="Users1">
              <template v-slot:activator="{ props }">
                <v-list-item
                    v-bind="props"
                    prepend-icon="mdi-account-circle"
                    title="Users"
                ></v-list-item>
              </template>

              <v-list-item
                  v-for="i in 3"
                  title="Admin"
                  prepend-icon="mdi-account-circle"
              ></v-list-item>
            </v-list-group>
            <v-divider/>
          </v-list>

          <v-card
              color="secondary"
              dark
              class="mx-auto"
              width="100%">
            <div class="d-flex py-3 justify-space-between">
              <v-list-item
                  density="compact"
                  prepend-icon="mdi-cog"
              >
                <v-list-item-subtitle>Paramètres</v-list-item-subtitle>
              </v-list-item>
            </div>

          </v-card>
        </div>
      </div>
    </v-navigation-drawer>

    <v-app-bar app elevation="1" color="primary">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Application</v-toolbar-title>
      <v-toolbar-items style="height: fit-content; margin-right: 25px">
        <v-menu width="250px" >
          <template v-slot:activator="{ props }">
            <v-avatar style="cursor: pointer;" v-bind="props" color="white" >sk</v-avatar>
          </template>
          <v-list style="margin-top: 5px;">
            <v-list-item>
              <v-list-item-title>Profil</v-list-item-title>
            </v-list-item>
            <v-divider/>
            <v-list-item prepend-icon="mdi-logout">
              <v-list-item-title>Déconnexion</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-toolbar-items>
    </v-app-bar>

    <v-main style="background-color: #f6f6f6">
      <slot/>
    </v-main>
  </v-app>
</template>

<script setup>
const drawer = ref(null)

const selectedItem = ref(null)
const items = [
  {text: 'Real-Time', icon: 'mdi-clock'},
  {text: 'Audience', icon: 'mdi-account'},
  {text: 'Conversions', icon: 'mdi-flag'},
]
</script>
