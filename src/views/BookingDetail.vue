<template>
  <div>
    <Navbar />
    <div>
      <b-jumbotron class="bgBODetail">
        <b-jumbotron class="fillBOPass">
          <div class="fillOne">
            <h1>Booking Pass</h1>
            <p class="h3 mb-2">
              <b-dropdown
                  variant="outline"
                  right
                  class="float-right"
                  menu-class="dropmenu"
                  no-caret
                >
                  <template v-slot:button-content>
                    <p class="h3"><b-icon icon="three-dots-vertical"></b-icon></p>
                  </template>
                  <b-dropdown-item-button @click="print">
                    Print Ticket
                  </b-dropdown-item-button>
                  <b-dropdown-item-button>
                    <router-link class="txtDecor" to="/mybooking">Back</router-link>
                  </b-dropdown-item-button>
                </b-dropdown>
            </p>
          </div>
          <div class="fillTwo">
            <b-row class="allLine">
              <b-col lg="7" class="liners">
                <div class="travel">
                  <img
                    src="../assets/img/garuda-indonesia-logo-BD82882F07-seeklogo 1.png"
                  />
                  <h1>{{getDetailBooking[0].fromalias}} <img src="../assets/img/planeGray.svg" /> {{getDetailBooking[0].toalias}}</h1>
                </div>
                <div class="Detail1">
                  <b-col>
                    <h5>Code</h5>
                    <h4>{{getDetailBooking[0].code}}</h4>
                  </b-col>
                  <b-col>
                    <h5>Class</h5>
                    <h4>{{this.classflight}}</h4>
                  </b-col>
                </div>
                <div class="Detail2">
                  <b-col>
                    <h5>Terminal</h5>
                    <h4>{{getDetailBooking[0].terminal}}</h4>
                  </b-col>
                  <b-col>
                    <h5>Gate</h5>
                    <h4>{{getDetailBooking[0].gate}}</h4>
                  </b-col>
                </div>
                <div class="Detail3">
                  <b-col>
                    <h5>Departure</h5>
                    <h4>{{getDetailBooking[0].date_departure}} - {{getDetailBooking[0].departure}}</h4>
                  </b-col>
                </div>
              </b-col>
              <b-col lg="3">
                  <div class="qrcode">
                      <img src="../assets/img/QR.svg">
                  </div>
              </b-col>
            </b-row>
          </div>
        </b-jumbotron>
      </b-jumbotron>
    </div>
    <Footer />
  </div>
</template>

<script>
// import Swal from 'sweetalert2'
import JsPDF from 'jspdf'
// import html2canvas from 'html2canvas'
import Navbar from '@/components/Navbar.vue'
import Footer from '@/components/Footer.vue'
import { mapGetters, mapActions } from 'vuex'

export default {
  title: 'Ankasa | Booking Detail',
  components: {
    Navbar,
    Footer
  },
  data () {
    return {
      classflight: null,
      ngeprint: ''
    }
  },
  computed: {
    ...mapGetters({
      getDetailBooking: 'booking/getBookingDetail'
    })
  },
  methods: {
    ...mapActions({
      actionGetBookingDetail: 'booking/getBookingDetails'
    }),
    print () {
      const doc = new JsPDF('landscape')

      doc.text(this.ngeprint, 15, 15)
      doc.save('Ankasa-Ticket.pdf')
    }
  },
  mounted () {
    this.actionGetBookingDetail().then((result) => {
      this.classflight = result[0].classflight

      if (this.classflight === 0) {
        this.classflight = 'Economy'
      } else if (this.classflight === 1) {
        this.classflight = 'Business'
      } else if (this.classflight === 2) {
        this.classflight = 'First Class'
      }
      this.ngeprint = `${
        'Code : ' + result[0].code + '\n' +
        'Class : ' + this.classflight + '\n' +
        'From : ' + result[0].fromalias + '\n' +
        'To : ' + result[0].toalias + '\n' +
        'Terminal : ' + result[0].terminal + '\n' +
        'Gate: ' + result[0].gate + '\n' +
        'Departure : ' + result[0].date_departure + ' - ' + result[0].departure}`
    })
  }
}
</script>

<style scoped>
.txtDecor {
  text-decoration: none;
  color: black;
}
.allLine{
    margin: 0px;
    border: 2px solid;
    border-radius: 7.5px;
}
.liners{
    border-right: 2px solid;
}
.qrcode{
    margin-left: 145px;
    margin-top: 115px;
}
.Detail3 {
padding-left: 13%;
    margin: 5% 0;
}
.Detail2 {
    padding-left: 13%;
    margin: 5% 0;
    display: flex;
  /* text-align: center; */
  /* justify-content: space-around; */
}
.Detail1 {
    margin: 5% 0;
    padding-left: 13%;
    display: flex;
  /* text-align: center; */
  /* justify-content: space-around; */
}
.travel {
  display: flex;
  justify-content: space-around;
    margin: 5% 0;

}
.bgBODetail {
  background: #2395ff;
}
.fillBOPass {
  background: #ffffff;
  box-shadow: 0px 8px 27px rgba(14, 63, 108, 0.19);
  border-radius: 20px;
}
.fillOne {
  display: flex;
  justify-content: space-between;
}
.fillTwo {
  background: #ffffff;
  border: 1px solid #e5e5e5;
  box-sizing: border-box;
  border-radius: 7.5px;
}
</style>
