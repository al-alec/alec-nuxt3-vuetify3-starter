<template>
  <NuxtLayout name="admin">
    <v-container>
      <v-row justify="center" class="space">
        <v-col cols="9">
          <v-row>
            <v-col v-for="i in 3">
              <v-card
                  class="d-flex align-center rounded-xl"
                  dark
                  height="200"
              >
                <v-row>
                  <v-col cols="12" sm="12">
                    <v-list-item three-line class="mt-4">
                      <div class="mb-4">
                        <v-icon size="50px" color="primary">mdi-user</v-icon>
                      </div>
                      <v-list-item-subtitle class="text-h6 mb-2">
                        Team velocity
                      </v-list-item-subtitle>
                      <v-list-item-title class="headline mb-1">
                        <strong style="font-size: 25px;">52</strong>
                      </v-list-item-title>
                    </v-list-item>
                  </v-col>
                </v-row>

              </v-card>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="8">
              <client-only>
                <v-card>
                  <GChart
                      type="ColumnChart"
                      :data="ColumnChartchartData"
                      :options="ColumnChartchartOptions"
                  />
                </v-card>
              </client-only>
            </v-col>
            <v-col cols="4">
              <client-only>
                <v-card>
                  <GChart
                      type="PieChart"
                      :data="PieChartchartData"
                      :options="PieChartchartOptions"
                  />
                </v-card>
              </client-only>
            </v-col>
          </v-row>
        </v-col>
        <v-col cols="3">
          <v-card height="80vh" style="overflow-y: auto">
            <v-card-title style="position: sticky; top: 0px; z-index: 100; background-color: white">
              Activités récents
            </v-card-title>
            <v-card-text>
              <v-list lines="one">
                <v-list-item
                    v-for="item in 36"
                    :rounded="true"
                    :key="item"
                    :title="'Lorem ipsum'"
                    subtitle="lorem ipsum asit dolor set amer"
                    :border="true"
                    :prepend-avatar="'https://images.unsplash.com/photo-1671725501830-71073ba7eafc?ixlib=rb-4.0.3&ixid=MnwxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHw%3D&auto=format&fit=crop&w=500&q=60'"
                ></v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </NuxtLayout>
</template>
<script setup lang="ts">
 import {GChart} from 'vue-google-charts'

const ColumnChartchartData = ref([
  ['Year', 'Sales', 'Expenses', 'Profit'],
  ['2014', 1000, 400, 200],
  ['2015', 1170, 460, 250],
  ['2016', 660, 1120, 300],
  ['2017', 1030, 540, 350]
])
const ColumnChartchartOptions = ref({
  title: 'Résumé des crédits, collectes & dépots',
  subtitle: 'Sales, Expenses, and Profit: 2014-2017',
  height: '400',
})


 const PieChartdata = ref([
   ['Task', 'Hours per Day'],
   ['Work', 11],
   ['Eat', 2],
   ['Commute', 2],
   ['Watch TV', 2],
   ['Sleep', 7],
 ]);

 const PieChartoptions = ref({
   title: 'My Daily Activities',
   width: 800,
   height: 600,
 });
</script>
