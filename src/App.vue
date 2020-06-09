<template>
  <v-app>
    <v-content>
      <v-container
        fluid
      >
        <v-row>
          <v-col>
            <div align="center" class="mb-2">
              <v-img
                :src="require('./assets/banner.png')"
                width="80%"
              />
              <div class="display-1">Sonic Club's Canvas Trading 2020 Event</div>
              <div class="subtitle-1">Event in progress!</div>
            </div>
            <v-card>
              <v-container fluid>
                <v-row
                  v-for="(stageGroup, stageGroupIdx) in stageGroups"
                  :key="stageGroupIdx"
                  justify="center"
                  dense
                >
                  <v-col
                    v-for="stageIndex in stageCount"
                    :key="stageIndex"
                    class="d-flex child-flex"
                  >
                    <Entry
                      :previewPath="previewPathFromStage(stageIndex, stageGroup[stageIndex - 1])"
                      :downloadPath="downloadPathFromStage(stageIndex, stageGroup[stageIndex - 1])"
                      :avatarUrl="avatarUrlFromStage(stageGroup[stageIndex - 1])"
                    />
                  </v-col>
                </v-row>
              </v-container>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Entry from './components/Entry';
export default {
  name: 'App',
  components: {
    Entry
  },

  data: () => ({
    participants: {
      '4sonicfan': {
        gallery: null,
        sns: null,
      },
      'ArmorGontier': {
        gallery: null,
        sns: null,
      },
      'AussieHobbyYeah': {
        gallery: null,
        sns: null,
      },
      'Clever The Wolf': {
        gallery: null,
        sns: null,
      },
      'Flamestream': {
        gallery: null,
        sns: null,
      },
      'Flappy': {
        gallery: null,
        sns: null,
      },
      'Goodie_Noodles (Nichan)': {
        gallery: null,
        sns: null,
      },
      'Mllermanda': {
        gallery: null,
        sns: null,
      },
      'Nini Rosé': {
        gallery: null,
        sns: null,
      },
      'NOOB': {
        gallery: null,
        sns: null,
      },
      'Rotten': {
        gallery: null,
        sns: null,
      },
      'TylerBucket': {
        gallery: null,
        sns: null,
      },
      'Wolfie': {
        gallery: null,
        sns: null,
      },
      '🌌💮𝓢𝐏ε𝓵ｌ 🔮ғ𝕋𝒽𝐞𝓓έ𝐚ｄ🌸🌆🌇🌺': {
        gallery: null,
        sns: null,
      },
    },
    stageGroups: [
      ['4sonicfan', 'Clever The Wolf'],
      ['ArmorGontier', 'ArmorGontier'],
      ['AussieHobbyYeah', 'NOOB'],
      ['Clever The Wolf', 'Nini Rosé-2'],
      ['Flamestream', 'Mllermanda'],
      ['Flamestream-2', 'Wolfie'],
      ['Flappy', '🌌💮𝓢𝐏ε𝓵ｌ 🔮ғ𝕋𝒽𝐞𝓓έ𝐚ｄ🌸🌆🌇🌺'],
      ['Goodie_Noodles (Nichan)', 'Flappy'],
      ['Goodie_Noodles (Nichan)-2', '🌌💮𝓢𝐏ε𝓵ｌ 🔮ғ𝕋𝒽𝐞𝓓έ𝐚ｄ🌸🌆🌇🌺-2'],
      ['Mllermanda', 'Flamestream'],
      ['Nini Rosé', 'AussieHobbyYeah'],
      ['Nini Rosé-2', 'Flamestream-2'],
      ['NOOB', 'TylerBucket'],
      ['Rotten', 'Nini Rosé'],
      ['TylerBucket', 'Goodie_Noodles (Nichan)'],
      ['Wolfie', 'Rotten'],
      ['🌌💮𝓢𝐏ε𝓵ｌ 🔮ғ𝕋𝒽𝐞𝓓έ𝐚ｄ🌸🌆🌇🌺', 'Goodie_Noodles (Nichan)-2'],
      ['🌌💮𝓢𝐏ε𝓵ｌ 🔮ғ𝕋𝒽𝐞𝓓έ𝐚ｄ🌸🌆🌇🌺-2', '4sonicfan'],
    ],
    stageCount: 5,
  }),

  computed: {
    displayedIds() {
      return this.maxSelected ? this.selectedIds : Object.keys(this.images);
    },
  },

  methods: {
    previewPathFromStage(stageIndex, stageName) {
      if (!stageName) return;
      return `/stage-${stageIndex}/${stageName}.png`
    },
    downloadPathFromStage(stageIndex, stageName) {
      if (stageIndex > 1) return;
      if (!stageName) return;
      return `entries/stage-${stageIndex}/${stageName}.psd`
    },
    avatarUrlFromStage(stageName) {
      if (!stageName) return;
      console.log(stageName)
      let participantName = stageName.match(/(.+?)(-\d+)?$/)[1];
      console.log(`./assets/avatars/${participantName}.png`)
      return require(`./assets/avatars/${participantName}.png`)
    },
  },

  async created () {
    this.$vuetify.theme.dark = true
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  transition: all 1s;
}
</style>
