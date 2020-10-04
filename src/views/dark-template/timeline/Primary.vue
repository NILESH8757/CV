<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Life in a Nutshell' : 'My Experiences'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        detailed   : true,
        transparent: true,
        year       : '1996',
        title      : 'Born on Aug 9, 1996',
        html       : 'With a chance of %0.00000000000512.<br>I\'m completely aware of value of the life!',
        icon       : 'mdi-cake-variant',
      },
      {
        detailed   : true,
        transparent: true,
        year       : '2003',
        title      : 'Touched a Mouse',
        html       : 'ME: "Woooow!"<br><i>... Of course got slapped later!</i>',
        icon       : 'mdi-mouse-variant',
      },
      {
        detailed   : true,
        year       : '2000-2014',
        // transparent: true,
        title      : 'Finished School',
        /* eslint-disable no-useless-escape */
        html       : `
                <p>
                   Finally, free from school. Attended three different school and had lot of fun. 
                   Was an average joe in school, not a dumb not scholar. <br>Played almost all sports. Pulled many pranks on classmates as well as on teachers. Bunked classes, got in fights, had crush on senior, you name it, have done it all.
                </p>
                `,
        /* eslint-enable no-useless-escape */
        image : 'img/timeline/school.png',
        icon: 'mdi-school',
      },
      {
        year       : '2014',
        transparent: true,
        title      : 'Mission JEE',
        html       : `
          <p>
              When: <span class="orange--text lighten-1">June, 2014</span> <br>
              Where: <span class="">New Delhi</span>
          </p>
          <p>
            Like every other indian teen, with an aim to secure a good rank in JEE (Joint Entrance Examination), a test exam for admission in prestigiuos engineering colleges of India, I took admission in Akash Institue, Mayur Vihar, Delhi. <br>
            Don't know about preparation, but, exlored each and every nook and corner of Delhi and made some very cool friends. Great time in Delhi ;)
          </p>
        `,
        image    : 'img/timeline/akash.png',
        icon: 'mdi-book-open-variant',
      },
      {
        year : '2015',
        title: 'Landed in SLIET',
        html : `
          <p>
              When: <span class="orange--text lighten-1">August, 2015</span> <br>
              How: <span class="">By luck</span> 
          </p>
          <p>
             I had already taken admission in UIT Burdwan, has attended two weeks of classes. Then suddenly I got to know that I got alloted SLIET Punjab in spcial round of allocation. <br>
             My undergrad experience is one of the best experiences of my life. Too many memories!
          </p>
        `,
        image    : 'img/timeline/college.png',
        iconImage: 'img/timeline/slietlogo.png',
      },
      {
        year       : '2015',
        transparent: true,
        title      : 'Flunked basic programming course :(',
        html       : `
          <p>
              When: <span class="red--text darken-3">First Semester</span> <br>
              How: <span class="">Ignorance</span>
          </p>
          <p>
            Failed in basic programming course (C programming) in 1st sem. Had never programmed in my life and first time those syntaxes looked greek to me. I could've try harder. But general attitute in the first Semester was - party, binge-watch shows, explore campus and sleep all day after bunking classes. <br>
              Next semester, I rectified my mistake and scored B+ in the same course.
          </p>
        `,
        image    : 'img/timeline/failed.png',
        icon: 'mdi-face',
      },
      {
        year : '2016',
        title: 'Built Line-followr bot',
        html : `
          <p>
              When: <span class="green--text accent-4">2nd Semester</span> <br>
              Team: <span class="">Pandavas</span>
          </p>
          <p>
            Along with my friends, attended seminar by i3indya™ Technologies. Learnt basics of micro-controller and System programming. Got familiar with electronic circuits and devices used in such kind of robots. Again, a wonderful experience!.
          </p>
        `,
        image    : 'img/timeline/robot.png',
        iconImage: 'img/timeline/bot-icon.png',
      },
      {
        year       : '2016',
        title      : 'Entry in Web Development',
        html       : `
          <p>
          finally, learnt web development and built few simple websites. <strong>Yay!</strong>
          </p>
          <p>
          So, this was my sophomore year, I was introduced to web-dev through Web Applications course. I was pretty excited to finally, build something useful. I also tried to clone my school\'s website ;)
          </p>
          <p>
          Technically, I got familiar with and tried to be best (not yet of course!) at the following technologies:
          <ul>
          <li>HTML</li>
          <li>CSS</li>
          <li>Bootstrap</li>
          <li>JavaScript</li>
          <li>Animation</li>
          <li>version Control/CD</li>
          <li>Development best practices</li>
          <li>And more ...</li>
          </ul>
          </p>
          <p>
          So please don't underestimate this card by its height in pixels. It's worth a lot to me.
          </p>

        `,
        icon: 'mdi-code-not-equal-variant',
      },
      {
        year : '2017',
        title: 'Built a group project and participated in Techfest',
        html : `
          <p>
              Pandavas (my group) built a working prototype model of bascule bridge and took part in hackathon oraganized by our college techfest. <br> <br>
              <span class="light-blue--text lighten-3">No luck with prize had a gerat experience working on project from scratch with friends!</span>

          </p>
        `,
        image: 'img/timeline/techfest2016.png',
        icon : 'mdi-star-outline',
      },
      {
        year : '2017',
        title: 'God addicted to competitive programming :)',
        html : `
          <p>
              How: <span class="light-blue--text lighten-3">Accidently!</span> <br> <br>
              I still clearly remember the day. It was the holiday of Indian Republic day (26.01.2017), I was in my hostel room, having nothing to do, got bored and started endless fb scrolling. Stumbled upon Geeksforgeeks\'s post about \"How to start competitive programming\". Out of curiosity, clicked on it, and opened SPOJ and solved first problem. Got excited after first green AC status. And then rest is the history.
          </p>
        `,
        image: 'img/timeline/cp.png',
        icon : 'mdi-code-greater-than',
      },
      {
        year : '2018',
        title: 'Became member of college\'s programming club (SCS)',
        html : `
          <p>
            Position: <span class="light-blue--text lighten-3">Club Member</span>
          </p>
          <p>
            As a member of SLIET Computer Society, created algorithmic/mathematical challenges and oraganized a few coding contests to create programming awareness in the campus.
          </p>
        `,
        image: 'img/timeline/scs.png',
        icon : 'mdi-code-braces',
      },
      {
        year : '2019',
        title: 'Achieved my coding goals',
        html : `
          <p>
              Goals: <span class="green--text accent-4">To get in top 10%</span> <br>
              Where: <span class="">On Codechef and Codeforces</span>
          </p>
          <p>
            After facing lots of struggle, and practicing super hard, finally managed to secure yellow rating on Codechef and Expert rating on codeforces. I was aiming for these ranking/rating for quite a long time. 
          </p>
          <p>
            Profiles : <br>
            <ul>
              <li> <a href = "https://www.codechef.com/users/nilesh8757" target = "_blank">Codechef</a> </li>
              <li> <a href = "https://codeforces.com/profile/nilesh8757" target = "_blank">Codeforces</a> </li>
            </ul>
          </p>
        `,
        image    : 'img/timeline/codinggoals.png',
        icon: 'mdi-code-tags',
      },
      {
        year : '2019',
        title: 'Graduated!',
        html : `
          <p>
              Did I enjoy?: <span class="light-blue--text lighten-3">Hell Yes!</span><br>What did I learn: <span class="light-blue--text lighten-3">Life, Universe and Everything!</span>
          </p>
          <p>
             With heavy heart, had to say goodbye to a place which turned a boy and complete and responsible man in every aspects and also gave him countless memories to cherish forever. Undoubtedly, Best four years of my life!
          </p>
        `,
        image: 'img/timeline/sliet.png',
        icon : 'mdi-school',
      },
      {
        year : '2019',
        title: 'Joined Infosys as System Engineer',
        html : `
          <p>
              Current status: <span class="light-blue--text lighten-3">Now working</span><br>
          </p>
          <p>
            As a fresher, got the opporunity to work with one the best tech giant of India.The experience at the Mysore DC was full of a rollar-coster ride. Two best thing I most liked about the Mysore DC:
            <ul>
                <li>Magnificent world class infrastructure.</li>
                <li>Weekly movie shows :)</li>
            </ul>
          </p>
        `,
        image    : 'img/timeline/infosys-mysore.png',
        iconImage: 'img/timeline/firstjob.png',
      },
      {
        year : 'So far ...',
        title: 'Getting my hands dirty in the world of freelancing',
        html : `I'm the guy who loves exprementing! After my short term tenure at Infosys, I decided to give a shot to freelancing. You know, following the trend BYOB ;) I'm trying to establish myself on : 
                    <ul><li><a target="_blank" href="https://www.freelancer.in/">Freelancer</a> (First gig after lots of struggle)</li><li><a target="_blank" href="https://www.freelancer.in/">Upwork</a> (Better for Experienced)</li></ul>`,
        icon: 'mdi-fountain-pen-tip',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
