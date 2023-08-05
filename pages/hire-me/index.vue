<template>
  <main class="container">
    <h1 class="top-heading">
      Want to work together?
    </h1>
    <p>Dat kan! Op dit moment doe ik geen freelance werk, maar ik ben wel opzoek naar een nieuwe werkgever.</p>

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

                <p>{{ item.title }}</p>
              </div>
            </div>
          </div>
        </div>
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
          <h3 style="padding-bottom: 1rem">
            {{ item.display }}
          </h3>

          <span v-if="item.wip" class="card-badge" title="Dit project is nog niet af">Work in progress</span>

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
export default {
  name: 'hire-me',
  data () {
    return {
      casesQuestion: false,
      experience: [
        {
          display: 'd-Media B.V.',
          title: 'Software developer',
          timespan: 'Januari 2023 - Present'
        },
        {
          display: 'Wabber B.V.',
          title: 'Software developer',
          timespan: 'Juni 2020 - Juli 2022'
        }
      ],
      experienceQuestion: false,
      cases: [
        {
          display: 'I hope I',
          description: "Ergens in ons hebben we allemaal wel een bucket-list. Maar waar schrijven we 'm op? Het leek mij leuk om hier iets voor te maken, zodat je je bucket-list kan opschrijven, (hopelijk!) afvinken en delen met anderen, misschien kan je samen je bucketlist afwerken?",
          link: 'https://gitlab.com/luatoss/ihi',
          wip: true
        },
        {
          display: 'Luatic',
          description: 'Deze website is eigenlijk een bijproduct van een eigen domein willen hebben, maar opgezet om mijn toetsenborden te kunnen delen. En nu voor deze pagina! Een website is eigenlijk nooit af, maar buiten al mijn toetsenborden toe te voegen heb ik er op dit moment geen plannen voor.',
          link: false,
          wip: false
        },
        {
          display: 'Laros Beauty',
          description: 'Een simpele website om een klein bedrijf op de kaart te kunnen zetten. Binnenkort kunnen we online!',
          link: 'https://larosbeauty.nl',
          wip: false
        }
      ]
    }
  },
  methods: {

  }
}
</script>

<style scoped>
@import '@/assets/styles/hire-me.css';
</style>
