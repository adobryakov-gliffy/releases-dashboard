<template>
  <div class="grey lighten-5">

    <v-row no-gutters>
      <v-col
        md="4"
      ></v-col>
      <v-col
        md="2"
      >
        <v-card
          class="pa-2"
          outlined
          tile
        >
        <v-menu
          ref="menu"
          v-model="menu"
          :close-on-content-click="false"
          :return-value.sync="date"
          transition="scale-transition"
          offset-y
          min-width="auto"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-text-field
              v-model="date"
              label="Date from"
              prepend-icon="mdi-calendar"
              readonly
              v-bind="attrs"
              v-on="on"
            ></v-text-field>
          </template>
          <v-date-picker
            v-model="date"
            no-title
            scrollable
          >
            <v-spacer></v-spacer>
            <v-btn
              text
              color="primary"
              @click="menu = false"
            >
              Cancel
            </v-btn>
            <v-btn
              text
              color="primary"
              @click="$refs.menu.save(date)"
            >
              OK
            </v-btn>
          </v-date-picker>
        </v-menu>
        </v-card>
      </v-col>
      <v-col
        md="2"
      >
      <v-card
          class="pa-2"
          outlined
          tile
        >
        <v-menu
          ref="menu"
          v-model="menu"
          :close-on-content-click="false"
          :return-value.sync="date"
          transition="scale-transition"
          offset-y
          min-width="auto"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-text-field
              v-model="date"
              label="Date to"
              prepend-icon="mdi-calendar"
              readonly
              v-bind="attrs"
              v-on="on"
            ></v-text-field>
          </template>
          <v-date-picker
            v-model="date"
            no-title
            scrollable
          >
            <v-spacer></v-spacer>
            <v-btn
              text
              color="primary"
              @click="menu = false"
            >
              Cancel
            </v-btn>
            <v-btn
              text
              color="primary"
              @click="$refs.menu.save(date)"
            >
              OK
            </v-btn>
          </v-date-picker>
        </v-menu>
        </v-card>
      </v-col>
      <v-col
        md="4"
      ></v-col>
    </v-row>

    <v-row no-gutters v-for="project in projects" :key="project.name" class="project_row">
      <v-col
        md="1"
      >
        <v-card
          class="pa-2"
          outlined
          tile
        >
          {{project.name}}
        </v-card>
      </v-col>
      <v-col
        md="1"
      >
        <v-card
          class="pa-2 releaseBaCounter"
          outlined
          tile
        >
          ({{project.releasedBefore}})
        </v-card>
      </v-col>
      <v-col
        md="9"
      >
        <v-card
          class="pa-2"
          outlined
          tile
        >
          
          
    <v-card
      v-for="release in project.releases"
      :style="`position: absolute; top: 10px; left: ${release.shift * 1.5}px;`"
      :key="release.date"
      :class="`mx-auto release ${release.isNext ? 'next' : ''}`"
      :max-width="release.isNext ? 300 : 200"
      outlined
    >
      <v-list-item three-line>
        <v-list-item-content>
          <div class="text-overline mb-4">
            Release {{ release.isNext ? '(next)' : ''}}
          </div>
          <v-list-item-title class="text-h5 mb-1">
            {{ release.name }}
          </v-list-item-title>
          <v-list-item-subtitle>{{ release.date }}</v-list-item-subtitle>
        </v-list-item-content>
  
      </v-list-item>
    </v-card>

        </v-card>
      </v-col>
      <v-col
        md="1"
      >
        <v-card
          class="pa-2 releaseBaCounter"
          outlined
          tile
        >
          ({{project.releasedAfter}})
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
  export default {
    data: () => ({
      projects: [
        {
          name: 'GJC 6.3.0',
          releasedBefore: 6,
          releasedAfter: 1,
          releases: [
            {
              date: '2021-12-31',
              shift: 31,
              name: 'Release 5.3'
            },
            {
              date: '2022-03-01',
              shift: 400,
              isNext: true,
              name: 'Release 5.4'
            },
            {
              date: '2022-03-01',
              shift: 700,
              name: 'Release 6.0'
            },
          ]
        },
        {
          name: 'Monday',
          releasedBefore: 5,
          releasedAfter: 2,
          releases: [
            {
              date: '2021-12-31',
              shift: 90,
              name: 'Release 3.1'
            },
            {
              date: '2022-03-01',
              shift: 630,
              isNext: true,
              name: 'Release 3.2'
            },
          ]
        },
        {
          name: 'GCONF',
          releasedBefore: 10,
          releasedAfter: 0,
          releases: [
            {
              date: '2021-12-31',
              shift: 31,
              name: 'Release 3.2'
            },
            {
              date: '2022-03-01',
              shift: 440,
              isNext: true,
              name: 'Release 3.3'
            },
          ]
        },
        {
          name: 'GJIRA',
          releasedBefore: 10,
          releasedAfter: 0,
          releases: [
          ]
        },
        {
          name: 'GJC',
          releasedBefore: 10,
          releasedAfter: 0,
          releases: [
          ]
        },
        {
          name: 'GCC',
          releasedBefore: 10,
          releasedAfter: 0,
          releases: [
          ]
        },
        {
          name: 'GO',
          releasedBefore: 10,
          releasedAfter: 0,
          releases: [
          ]
        },
      ],
    }),
  }
</script>

<style scoped>
  .project_row .col .pa-2 {
    height: 170px;
  }
  .releaseBaCounter {
    font-size: 40pt;
  }
  .release {
    width: 200px;
  }
  .release.next {
    width: 400px;
  }
</style>