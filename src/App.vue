<template>
  <div id="app">
    <div id="title">
      <span class="shine time1">T</span
      ><span class="shine time2">i</span
      ><span class="shine time3">t</span
      ><span class="shine time4">e</span
      ><span class="shine time5">e</span
      ><span class="shine time6">n</span
      ><span class="shine time7">i</span
      ><span class="shine time8">e</span
      ><span class="shine time9">n</span>
      <span class="shine time10">T</span
      ><span class="shine time11">a</span
      ><span class="shine time12">i</span
      ><span class="shine time13">s</span
      ><span class="shine time14">t</span
      ><span class="shine time15">o</span
      ><span class="shine time16">t</span>
      <span class="shine time17">2</span
      ><span class="shine time18">0</span
      ><span class="shine time19">1</span
      ><span class="shine time20">9</span
    ></div>
        
    <a v-on:click="setState('landing')">
      <b v-if="state === 'landing'">Etusivu</b>
      <u v-else>Etusivu</u>
    </a>
    <a v-on:click="setState('info')">
      <b v-if="state === 'info'">Infoo</b>
      <u v-else>Infoo</u>
    </a>
    <a v-on:click="setState('score')">
      <b v-if="state === 'score'">Lajit</b>
      <u v-else>Lajit</u>
    </a>

    <div v-if="state === 'landing'" class="flex row items-center mb-4">
      <div class="col-sm-2 pt-1"></div>
      <div class="col-sm-8 pt-1">
        <div>
          Jälleen on aika Titeenien Taistoille! Titeenit pidetään tänä vuonna Otaniemessä 15.3. - 17.3. 
        </div>
        <div>
          Titeenien Taistot on Suomen tietoteekkareiden välinen kilpailu, jossa taistellaan viidessä huikeassa lajissa mestaruudesta. 
        </div>
        <div>
          Titeenit alkavat perjantaina 15.3. sodanjulistussitseillä klo 18:30 Smökissä ja jatkuu seuraavana päivänä varsinaisilla lajeilla. Mikäli ei ole ilmoittautunut sitseille, Gorsussa on vaihtoehtoista ohjelmaa illan ajan.
        </div>
      </div>
    </div>
    <div v-if="state === 'info'" class="flex row justify-between items-center mb-4">
      <div class="col-sm-2 pt-1"></div>
        <div class="col-sm-8 pt-1">
          Perjantain aikataulu:<br>
          Majoitus aukeaa: 15.00 <br>
          Sodanjulistussitsit: 18.30 @ Smökki (Jämeräntaival 4)<br>
          Vaihtoehtoinen ohjelma: 18.00 @ Gorsu (Jämeräntaival 5)<br>
          <br><br>
          Lauantain aikataulu:<br>
          Suihkut aukeaa: 8.00 @ Rantasauna & Otakaari 20<br>
          Aamupala: 9.30 @ Smökki<br>
          1. laji: 11.xx @ Alvarin aukio<br>
          2. laji: 12.xx @ Alvarin aukio<br>
          Tauko<br>
          3. laji: 16.00 @ Smökki<br>
          4. laji: 17.xx @ Smökki<br>
          5. laji: 20.00 @ Smökki<br>
          <br>
          Majoituspaikat:<br>
          Oulu: Jämeräntaival 5, tatamisali<br>
          Muut: Otakaari 20<br>
          <br>
          <br>
          Yhteystiedot kun tulee yleistä kysyttävää:<br>
          Jussi Impiö, @titeenitirehtoori<br>
          <br>
          Majoitukseen liittyen:<br>
          Launtaina klo 00-09 @ablecable<br>
          Sunnuntaina klo 00-09 @ulkosuhdevastaava<br>
        </div>
      <div class="col-sm-2 pt-1"></div>
      <div class="col-sm-4 pt-1"></div>
      <div class="col-sm-4 pt-1">
        <iframe src="https://www.google.com/maps/d/u/1/embed?mid=1NkjfA4u5ZwNl3ST90Pb-gWgvwnbCQERw" width="640" height="480"></iframe>
      </div>
      <div class="col-sm-4 pt-1"></div>

    </div>
    <div v-if="state === 'score'" class="flex justify-between items-center mb-4">
      <div v-for="(value, propertyName) in teams" v-bind:key="propertyName" class="row mb-1">
        <div class="col-sm-2">{{ propertyName }}:</div>
        <div class="col-sm-8 pt-1">
          <b-progress :value="value['value']" :max="max_score" :variant="value['color']" :key="value.variant" />
        </div>
        <div class="col-sm-2"></div>
      </div>

      <div v-for="e in events" v-bind:key="e.number" class="row mb-12">
        <div class="col-sm-12" style="text-align: left; padding-bottom: 1em">
          <h2 class="col-sm-6" >{{ e.number }}. Laji: {{ e.name }}</h2>
          <div class="col-sm-12 col-md-6">
            <span>{{ e.desc }}</span>
          </div>
        </div>
        <div class="col-sm-12">
        
          <div v-for="(p, index) in e.points" v-bind:key="index" class="row mb-12">
            <div class="col-sm-12" style="text-align: left">
              <span class="col-sm-2" style="padding-left: 10em">- {{ p.kilta }} ansaitsee {{ p.pisteet }} pistettä sillä {{ p.syy }}! Upeaa!</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <img width="400em" src="https://svgshare.com/i/Bkt.svg" onerror="this.onerror=null; this.src='./image.png'">
    <div id="sponssi">
      YHTEISTYÖSSÄ
    </div>
    <img style="margin: 0 5em" width="200em" src="https://www.siili.com/themes/siili_2017/logo.svg" onerror="this.onerror=null; this.src='./image.png'">
    <img style="margin: 0 5em" width="200em" src="https://startuplifers.org/wp-content/uploads/2018/11/compressed_Startuplifers_Logo_Red_RGB_medium.png" onerror="this.onerror=null; this.src='./image.png'">


  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      state: 'landing',
      info: null,
      max_score: 0,
      teams: {
        'TIK': { color: 'dark', value: 0, logo: "./assets/virallinen_logo_musta.png"},
        'TITE': { color: 'dark', value: 0, logo: "./assets/tite_logo.png" },
        'CLUSTER': { color: 'dark', value: 0, logo: "./assets/cluster_logo.png" },
        'DIGIT': { color: 'dark', value: 0, logo: "./assets/digit.png" },
        'OTIT': { color: 'dark', value: 0, logo: "./assets/photo_2019-03-06_16-12-47.png" }
      },
      events: [
        { number: 0, name: 'titeeni.city', location: 'Web', desc: 'Rakenna titeenihahmosi! Oletko level 1 fuksi vai level 85 Mouho? Täällä otetaan tietoteekkarista mittaa. Esineitä hahmollesi löydät mystisitä qr-koodeista.', points: [] },
        { number: 1, name: 'Esterata', location: 'Alvari', desc: 'Esteradalla killat pääsevät tekemään fyysista tuttavuutta erinäisiin tietoliikenneprotokolliin.', points: [] },
        { number: 2, name: 'Kuutiopallo & Kumikanaultimate', location: 'Alvari', desc: 'Kuutiopallo sekä kumikanaultimate ovat Tietokillan perinteisimpiä ulkopelejä. Nyt kaikki killat pääsevät tutustumaan niihin raikkaassa kevätsäässä', points: [] },
        { number: 3, name: 'Puolikäsismäsh', location: 'Smökki', desc:'Tämä kommunik- ja koordinaatiotaitoja vaativa videopeli pistää dynaamisimmatkin ryhmäpelaajat koetukselle', points: [] },
        { number: 4, name: 'Roombapongi', location: 'Smökki', desc:'Tässä tarkkuuslajissa tietoteekkarit pääsevät oppimaan tärkeitä taitoja tulevaan singulariteetin-jälkeiseen ihmisten ja robottien väliseen loppusotaan.', points: [] },
        { number: 5, name: 'Otaniemipeli', location: 'Smökki', desc: 'Titeenit huipentuvat tähän mitä perinteikkäimpään ja ikävuosissa jopa Tietokiltaa vanhempaan kaikkien tietoteekkarilautapelien kanta-äitiin. Jokaisen killan tulee lähettää peliin 3 hengen edustusjoukkue.', points: [] }
      ] 
    }
  },
  methods: {
    setState: function (s) {
      this.state = s
    }
  },
  mounted () {
    axios
      .get('http://13.53.217.34:5000/result')
      .then(request => {

        var t_sum = {};
        var e_dec = {}
        request.data.forEach(function(item) {
          if(t_sum[item.kilta] === undefined) {
            t_sum[item.kilta] = 0;
          }
          t_sum[item.kilta] += parseInt(item.pisteet)

          if(e_dec[item.laji] === undefined) {
            e_dec[item.laji] = [{"kilta": item.kilta, "syy": item.syy, "pisteet": item.pisteet}]
          }
          else{
            e_dec[item.laji].push({"kilta": item.kilta, "syy": item.syy, "pisteet": item.pisteet})
          }
        })

        for (var key in e_dec) {
          this.events[key].points = e_dec[key]
        }
        for (var key in t_sum) {
          if (t_sum[key] > this.max_score){
            this.max_score = t_sum[key]
          }
          this.teams[key].value = t_sum[key]
        }
        this.info = request.data
      })
  }
}
console.log("SE ON VÄÄRIN PÄIN")
</script>
