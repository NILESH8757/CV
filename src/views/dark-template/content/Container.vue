<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="Who am I?"
        >
        I'm a freelance web developer, competitive programmer and an avid reader. I like solving algorithmic/mathematical puzzles who also has keen interests in solving complex programming problems. Currently, I'm looking for a full-time opportunity in SWE.
      </content-section>
      <content-section
        v-if="prouds"
        title="What am I proud of?"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    small
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon  : 'mdi-code-not-equal-variant',
        text  : 'Solved 2k+ problems!',
        source: '(Across various programmnig platforms)',
      },
      {
        icon  : 'mdi-pen',
        text  : 'Written many tech/programmnig related answers on Quora and got great responses.',
        source: '(Quora is general Q-A website)',
      },
      {
        icon  : 'mdi-book-open-variant',
        text  : 'Read 100+ books including non-fiction and fiction of all genres.',
        source: '(Favourites : Mark O’Connell, Paulo Coelho, Ruskin Bond.)',
      },
      {
        icon  : 'mdi-wallet-travel',
        text  : 'Travelled across the country and covered many beautiful destinations.',
        source: '(Next goal : to explore other countries.)',
      },
    ],
    educations: [
      {
        from       : '2015',
        to         : '2019',
        title      : 'Bachelor\'s degree, Computer Science & Engineering',
        location   : 'SLIET Punjab, India.',
        description: 'Became a member of SCS and curated many programming challenges.',
      },
    ],
    skills: [
      {
        title: 'C/C++',
        icon : 'mdi-language-cpp',
        value: 90,
      },
      {
        title: 'Python',
        icon : 'mdi-language-python',
        value: 60,
      },
      {
        title: 'HTML',
        icon : 'mdi-language-html5',
        value: 80,
      },
      {
        title: 'CSS',
        icon : 'mdi-language-css3',
        value: 70,
      },
      {
        title: 'JavaScript',
        icon : 'mdi-language-javascript',
        value: 50,
      },
      {
        title: 'Vue.js Framework',
        icon : 'mdi-vuejs',
        value: 40,
      },
      {
        title: 'Bootstrap',
        icon : 'mdi-bootstrap',
        value: 60,
      },
      {
        title: 'Node.js',
        icon : 'mdi-nodejs',
        value: 55,
      },
      {
        title: 'MongoDB',
        icon : 'mdi-database',
        value: 67,
      },
      {
        title: 'Git',
        icon : 'mdi-git',
        value: 45,
      },
      { divider: true },
      {
        title: 'Ubuntu',
        icon : 'mdi-ubuntu',
        value: 78,
      },
      {
        title: 'Test Driven Development',
        icon : 'mdi-test-tube',
        value: 40,
      },
      { divider: true },
      {
        title: 'Leadership',
        icon : 'mdi-account-group',
        value: 68,
      },
      {
        title: 'Communication Skills',
        icon : 'mdi-account-multiple',
        value: 96,
      },
      {
        title: 'Team Management',
        icon : 'mdi-face',
        value: 68,
      },
      {
        title: 'Problem Solving',
        icon : 'mdi-puzzle',
        value: 96,
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
