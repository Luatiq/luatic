<template>
  <main class="container">
    <h1 class="top-heading">
      Let's work together!
    </h1>
    <p>Op dit moment zoek ik geen freelance werk, maar ik ben wel opzoek naar een nieuwe werkgever.</p>

    <section>
      <h2>Experience</h2>

      <button type="button" title="Wat heb je gedaan?" class="subbutton" @click="experienceQuestion = !experienceQuestion">
        Wat heb je gedaan?
      </button>

      <section v-if="experienceQuestion" class="card">
        <p>
          Als je wil weten wat mijn werkzaamheden zijn (geweest) bij deze bedrijven, mail me voor mijn volledige CV!
        </p>
      </section>
      <br>

      <section class="card card-timeline">
        <div class="timeline">
          <div v-for="item in experience" :key="item.display" class="timeline-container">
            <div class="timeline-content">
              <div class="card">
                <h2>{{ item.display }}</h2>
                <span class="card-badge timeline-badge">{{ item.timespan }}</span>

                <p class="text-highlight">
                  {{ item.title }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>
    </section>

    <section>
      <h2>Skill set</h2>
      <section class="card-wrapper">
        <section class="card card-half skill-list">
          <ul>
            <li v-for="item in skillset.highlighted" :key="item.display" class="skill-card">
              <span class="skill-icon">
                <component :is="`Brand${item.icon !== undefined ? item.icon : item.display}Icon`" v-if="item.iconFile === undefined" />
                <!--suppress HtmlRequiredAltAttribute -->
                <img v-else :src="getImage(item.iconFile)" class="select-none">
              </span>

              {{ item.display }}

              <span :title="`Sinds ${item.since}`">
                <calendar-icon class="subtext skill-card-icon" />
              </span>

              <span v-if="item.enjoyment !== undefined" :title="getIconForSkillEnjoyment(item.enjoyment).title">
                <component
                  :is="`mood-${getIconForSkillEnjoyment(item.enjoyment).iconName}-icon`"
                  :class="getIconForSkillEnjoyment(item.enjoyment).className"
                  class="subtext skill-card-icon"
                />
              </span>
            </li>
          </ul>

          <h3>Good to know?</h3>
          <ul>
            <li v-for="item in skillset.extra" :key="item.display" class="skill-card">
              <span class="skill-icon">
                <component :is="`Brand${item.icon !== undefined ? item.icon : item.display}Icon`" v-if="item.iconFile === undefined" />
                <!--suppress HtmlRequiredAltAttribute -->
                <img v-else :src="getImage(item.iconFile)" class="select-none">
              </span>

              {{ item.display }}

              <span :title="`Sinds ${item.since}`">
                <calendar-icon class="subtext skill-card-icon" />
              </span>

              <span v-if="item.enjoyment !== undefined" :title="getIconForSkillEnjoyment(item.enjoyment).title">
                <component
                  :is="`mood-${getIconForSkillEnjoyment(item.enjoyment).iconName}-icon`"
                  :class="getIconForSkillEnjoyment(item.enjoyment).className"
                  class="subtext skill-card-icon"
                />
              </span>
            </li>
          </ul>
        </section>

        <section class="card card-half skill-list">
          <h3>Duh, natuurlijk kan & ken ik</h3>
          <ul>
            <li v-for="item in skillset.obvious" :key="item.display" class="skill-card">
              <span class="skill-icon">
                <component :is="`Brand${item.icon !== undefined ? item.icon : item.display}Icon`" v-if="item.iconFile === undefined" />
                <!--suppress HtmlRequiredAltAttribute -->
                <img v-else :src="getImage(item.iconFile)" class="select-none">
              </span>

              {{ item.display }}

              <span :title="`Sinds ${item.since}`">
                <calendar-icon class="subtext skill-card-icon" />
              </span>

              <span v-if="item.enjoyment !== undefined" :title="getIconForSkillEnjoyment(item.enjoyment).title">
                <component
                  :is="`mood-${getIconForSkillEnjoyment(item.enjoyment).iconName}-icon`"
                  :class="getIconForSkillEnjoyment(item.enjoyment).className"
                  class="subtext skill-card-icon"
                />
              </span>
            </li>
          </ul>
        </section>
      </section>
    </section>

    <section>
      <h2>My work</h2>

      <button type="button" title="Waarom zo weinig?" class="subbutton" @click="casesQuestion = !casesQuestion">
        Is dat alles?
      </button>

      <section v-if="casesQuestion" class="card">
        <p>
          Dit zijn alleen mijn eigen projecten.
          <br>
          Buiten dat de meeste werkgevers niet zullen staan te springen om hun (klanten-)projecten hiertussen te zien staan, kan je
          als (voornamelijk) back-end developer de projecten enof werkzaamheden die je doet eigenlijk niet laten zien.
          <br>
          Nu hoor ik je denken; "Waarom heb je niet meer 'side projects'?"
          <br>
          Ik wil niet het wiel opnieuw uitvinden.
          Dus iets bedenken wat ik nuttig vind om mijn tijd in te steken, vind ik lastig. Dan ben ik liever bezig met servers, distro-hoppen, of (andere) hobbies.
        </p>
      </section>

      <p>Hier een aantal dingen die ik heb gemaakt;</p>

      <section class="card-wrapper">
        <div v-for="item in cases" :key="item.display" class="card card-half">
          <h3 class="case-title text-highlight">
            {{ item.display }}
            <!-- @TODO upgrade tablericons (so Vue 3) for Symfony icon -->
            <component :is="`Brand${item.icon}Icon`" v-if="item.iconFile === undefined" />
            <!--suppress HtmlRequiredAltAttribute -->
            <img v-else :src="getImage(item.iconFile)" class="select-none" style="height: 24px">
          </h3>

          <span v-if="item.wip" class="card-badge badge-wip badge-help" title="Dit project is nog niet af">
            <alert-triangle-icon />
          </span>

          <p>{{ item.description }}</p>

          <a :href="item.link" target="_blank">
            <button v-if="item.link" :title="'Bekijk ' + item.display">Bekijk project</button>
            <button v-else disabled title="Hier zit je al :)">Hier zit je al :)</button>
          </a>
        </div>
      </section>
    </section>
  </main>
</template>

<script>
import {
  CalendarIcon,
  AlertTriangleIcon,
  MoodHappyIcon,
  MoodAnnoyedIcon,
  MoodAngryIcon,
  BrandVueIcon,
  BrandBootstrapIcon,
  BrandLaravelIcon,
  BrandDrupalIcon,
  BrandPhpIcon,
  BrandHtml5Icon,
  BrandCss3Icon,
  BrandJavascriptIcon,
  // BrandJqueryIcon,
  BrandGitIcon
  // BrandPhotoshopIcon
} from 'vue-tabler-icons'

export default {
  name: 'hire-me',
  components: {
    CalendarIcon,
    AlertTriangleIcon,
    MoodHappyIcon,
    MoodAnnoyedIcon,
    MoodAngryIcon,
    BrandVueIcon,
    BrandBootstrapIcon,
    BrandLaravelIcon,
    BrandDrupalIcon,
    BrandPhpIcon,
    BrandHtml5Icon,
    BrandCss3Icon,
    BrandJavascriptIcon,
    // BrandJqueryIcon,
    BrandGitIcon
    // BrandPhotoshopIcon
  },
  data () {
    return {
      experience: [
        {
          display: 'd-Media web professionals',
          title: 'Software developer',
          timespan: 'Januari 2023 - Februari 2024'
        },
        {
          display: 'Wabber B.V.',
          title: 'Software developer',
          timespan: 'Juni 2020 - Juli 2022'
        }
      ],
      experienceQuestion: false,
      skillset: {
        highlighted: [
          {
            display: 'Symfony',
            enjoyment: 'most',
            since: 'Januari 2020',
            iconFile: 'brand-symfony.svg'
          },
          {
            display: 'Vue',
            since: 'Maart 2021'
          },
          {
            display: 'Bootstrap',
            since: '2019'
          },
          {
            display: 'Laravel',
            since: 'Februari 2023'
          },
          {
            display: 'Drupal',
            enjoyment: 'least',
            since: 'Januari 2023'
          }
        ],
        obvious: [
          {
            display: 'PHP',
            icon: 'Php',
            since: 'December 2019'
          },
          {
            display: 'Git',
            since: 'Januari 2020'
          },
          {
            display: 'HTML',
            icon: 'Html5',
            since: '2018'
          },
          {
            display: 'CSS',
            icon: 'Css3',
            since: '2018'
          },
          {
            display: 'JavaScript',
            icon: 'Javascript',
            since: '2018'
          },
          {
            display: 'Jquery',
            enjoyment: 'little',
            since: 'Januari 2020',
            iconFile: 'brand-jquery.svg'
          }
        ],
        extra: [
          {
            display: 'Photoshop',
            since: '2016',
            iconFile: 'brand-photoshop.svg'
          }
        ]
      },
      cases: [
        {
          display: 'I hope I',
          icon: 'Symfony',
          iconFile: 'brand-symfony-case.svg',
          description: "Ergens in ons hebben we allemaal wel een bucket-list. Maar waar schrijven we 'm op? Het leek mij leuk om hier iets voor te maken, zodat je je bucket-list kan opschrijven, (hopelijk!) afvinken en delen met anderen, misschien kan je samen je bucketlist afwerken?",
          link: 'https://gitlab.com/luatoss/ihi',
          wip: true
        },
        {
          display: 'Luatic',
          icon: 'Vue',
          description: 'Deze website is eigenlijk een bijproduct van een eigen domein willen hebben, maar opgezet om mijn toetsenborden te kunnen delen. En nu voor deze pagina! Een website is eigenlijk nooit af, maar buiten al mijn toetsenborden toe te voegen heb ik er op dit moment geen plannen voor.',
          link: false,
          wip: false
        },
        {
          display: 'Laros Beauty',
          icon: 'Bootstrap',
          description: 'Een simpele website om een klein bedrijf op de kaart te kunnen zetten. Binnenkort kunnen we online!',
          link: 'https://larosbeauty.nl',
          wip: false
        }
      ],
      casesQuestion: false
    }
  },
  methods: {
    getIconForSkillEnjoyment (enjoymentLevel) {
      switch (enjoymentLevel) {
        case 'most':
          return {
            title: 'Dit vind ik het leukst om mee te werken',
            iconName: 'happy',
            className: 'text-good'
          }
        case 'little':
          return {
            title: 'Hier werk ik liever niet mee',
            iconName: 'annoyed',
            className: 'text-bleh'
          }
        case 'least':
          return {
            title: 'Hier blijf ik liever van weg',
            iconName: 'angry',
            className: 'text-bad'
          }
      }
    },
    getImage (filename) {
      return require('../../assets/images/' + filename)
    }
  }
}
</script>

<style scoped>
@import '@/assets/styles/hire-me.css';
</style>
