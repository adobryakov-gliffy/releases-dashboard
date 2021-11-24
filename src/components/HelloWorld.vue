<template>
  <div class="grey lighten-5">

    <v-row no-gutters>
      <v-col
        md="12"
      ></v-col>
    </v-row>

    <v-row no-gutters v-for="(project, index) in projects" :key="project.name"
        class="project_row">
      <v-col
        class="project_name_col"
        md="1"
      >
        <v-card
          class="project_name pa-2"
          outlined
          tile
        >
          {{index + 1}} {{project.name}}
        </v-card>
      </v-col>
      <v-col
        class="releaseBaCounter"
        md="1"
      >
        <v-card
          class="pa-2"
          outlined
          tile
        >
          <div class="number_round">{{project.releasedBefore}}</div>
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
          
          
    <div
      v-for="release in project.releases"
      :style="`position: absolute; top: 0px; left: ${release.shift * 1.5}px;`"
      :key="release.date"
      :class="`mx-auto release ${release.isNext ? 'next' : ''}`"
      :max-width="release.isNext ? 300 : 200"
    >
      <v-list-item
        class="release_card"
        :style="`background-color: ${project.color};`">
        <div>
          <div class="release_name">
            {{ release.name }} {{ release.isNext ? '(next)' : ''}}
          </div>
          <div class=" release_status">
            
            <span v-if="release.status === 'done'" class="status_done">DONE</span>
            <span v-if="release.status === 'in_progress'" class="status_in_progress">IN PROGRESS</span>
            <span v-if="release.status === 'planning'" class="status_planning">PLANNING</span>
          </div>
          <div style="display: none;">{{ release.date }}</div>
        </div>
  
      </v-list-item>
    </div>

        </v-card>
      </v-col>
      <v-col
        class="releaseBaCounter"
      >
        <v-card
          class="pa-2"
          outlined
          tile
        >
          <div class="number_round">{{project.releasedAfter}}</div>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
  export default {
    mounted: function() {

      this.projects = [
        {
          name: 'GJC 6.3.0',
          releasedBefore: 6,
          releasedAfter: 1,
          color: '#904CFF',
          releases: [
            {
              date: '2021-12-31',
              shift: 131,
              name: 'Release 5.3',
              status: 'done',
            },
            {
              date: '2022-03-01',
              shift: 400,
              isNext: true,
              name: 'Release 5.4',
              status: 'in_progress',
            },
            {
              date: '2022-03-01',
              shift: 700,
              name: 'Release 6.0',
              status: 'planning',
            },
          ]
        },
        {
          name: 'Monday',
          releasedBefore: 5,
          releasedAfter: 2,
          color: '#4C9AFF',
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
          color: '#00AEEF',
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
          color: '#CCF1FF',
          releases: [
          ]
        },
        {
          name: 'GJC',
          releasedBefore: 10,
          releasedAfter: 0,
          color: '#FFF4E3',
          releases: [
          ]
        },
        {
          name: 'GCC',
          releasedBefore: 10,
          releasedAfter: 0,
          color: '#DFFFFF',
          releases: [
          ]
        },
        {
          name: 'GO',
          releasedBefore: 10,
          releasedAfter: 0,
          color: '#FFF3C7',
          releases: [
          ]
        },
      ];

      const randRange = 150;
      for (let project of this.projects) {
        const majorNumber = Math.ceil(Math.random() * 7) + 1;
        const minorNumber = Math.ceil(Math.random() * 7) + 1;

        project.releasedBefore = Math.ceil(Math.random() * 7);
        project.releasedAfter = Math.ceil(Math.random() * 7);
        project.releases = [
            {
              date: '2021-12-31',
              shift: 131 + ( Math.random() * randRange - randRange/2),
              name: `Release ${majorNumber}.${minorNumber}`,
              status: 'done',
            },
            {
              date: '2022-03-01',
              shift: 400 + ( Math.random() * randRange - randRange/2),
              isNext: true,
              name: `Release ${majorNumber}.${minorNumber+1}`,
              status: 'in_progress',
            },
            {
              date: '2022-03-01',
              shift: 700 + ( Math.random() * randRange - randRange/2),
              name: `Release ${majorNumber}.${minorNumber+2}`,
              status: 'planning',
            },
          ];
      }

    },
    data: () => ({
      projects: [],
    }),
  }
</script>

<style scoped>
  body {
    font-family: Roboto;
    font-style: normal;
    font-weight: 500;
    font-size: 17px;
    line-height: 116.19%;
  }
  .project_row_head {
    background-color: #FAFBFC;
  }
  .project_row .col .pa-2 {
    background-color: #F0F2F4;
    height: 54px;
  }
  .project_row .col {
    border-top: 4px #fff solid;
  }
  .releaseBaCounter {
    width: 40px !important;
    font-size: 130%;
    text-align: center;
  }
  .release {
    width: 127px;
    height: 40px !important;
  }
  .release .text-overline {
    position: absolute;
    top: 0;
  }
  .release .v-list-item {
    /* background-color: #4C9AFF; */
  }
  .release.next {
    width: 250px;
  }

  .project_row2 {
    height: 30px !important;
  }

  .text-overline {
    font-family: Roboto;
    font-style: normal;
    font-weight: 500;
    font-size: 17px;
    line-height: 116.19%;
  }


  .status_done {
    background-color: #90C454;
  }
  .status_in_progress {
    background-color: #EF8B1F;
  }
  .status_planning {
    background-color: #42516E;
  }


  .v-card {
    border: none !important;
    top: 0 !important;
  }

  .release_card {
    border-left: #4C9AFF 4px solid;
  }



  .release_status {
    color: #fff;
    position: relative;
    top: -6px;
  }
  .release_status span {
    font-size: 10pt;
  }
  .release_card {
    height: 54px !important;
    margin: 0 !important;
  }


  .project_name {
    color: #4C4C66;
  }
  .project_name_col {
    border-right: 10px solid #F1F1F1;
  }

  .number_round {
    color: #fff;
    background: #90C454;
    border-radius: 25px;
    width: 30px;
    margin: auto;
  }


  .release_name {
    text-transform: uppercase;
    overflow: hidden;
    white-space: nowrap;
    margin-bottom: 0px;
    position: relative;
    top: 0px;
  }
</style>