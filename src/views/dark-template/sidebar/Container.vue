<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Nilesh <span class="light-blue--text text--lighten-3">Kumar</span>
        </h1>
        <span>
          Software Developer | Competitive Programmer
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template
                v-for="(item, i) in items"
              >
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'nilesh8757@gmail.com',
            },
            {
              name: 'Phone',
              icon: 'mdi-cellphone',
              text: '+91-9871226035',
            },
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: 'Aug 9, 1996',
            },
            {
              name: 'Habitation',
              icon: 'mdi-map-marker',
              text: 'Pune, India',
            },
          ],
        },
        socials: {
          title: 'SOCIALS',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/NILESH8757',
              link: 'https://github.com/NILESH8757',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/nilesh8757',
              link: 'https://www.linkedin.com/in/nilesh8757/',
            },
            {
              icon: 'mdi-twitter',
              text: 'twitter.com/nilesh8757',
              link: 'https://twitter.com/nilesh8757',
            },
            {
              icon: 'mdi-instagram',
              text: 'instagram.com/nileshfrommars',
              link: 'https://www.instagram.com/nileshfrommars/',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [
            {
              icon: 'mdi-bike',
              text: 'Cycling',
            },
            {
              icon: 'mdi-camera',
              text: 'Photography',
            },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Books',
            },
            {
              icon: 'mdi-code-not-equal-variant',
              text: 'Coding',
            },
            {
              icon: 'mdi-teach',
              text: 'Mentoring',
            },
            {
              icon: 'mdi-music',
              text: 'Music',
            },
            {
              icon: 'mdi-account-group',
              text: 'Leadership',
            },
            {
              icon: 'mdi-gamepad-variant',
              text: 'Gaming',
            },
            {
              icon: 'mdi-cube-outline',
              text: 'Rubik Cube',
            },
            {
              icon: 'mdi-chart-bubble',
              text: 'Badminton',
            },
            {
              icon: 'mdi-television',
              text: 'TV Shows',
            },
            {
              icon: 'mdi-swim',
              text: 'Swimming',
            },
            {
              icon: 'mdi-fish',
              text: 'Fishing',
            },
            {
              icon: 'mdi-run',
              text: 'Jogging',
            }
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'English',
              value: 95,
            },
            {
              text : 'Hindi',
              value: 100,
            },
            {
              text : 'Punjabi',
              value: 50,
            },
            {
              text : 'Vajjika',
              value: 90,
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar{
    background: #2e2e2e;
}
</style>
