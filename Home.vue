<template>
  <div class="home-component">
    <div class="page">
      <v-container fluid>
        <v-row no-gutters>
          <v-col>
            <page-headers :pageTitle="titleText"></page-headers>
          </v-col>
        </v-row>

        <v-row>
          <v-col>
            <page-date :dateInput="date"></page-date>
          </v-col>
        </v-row>

        <v-row>
          <v-col>
            <tab-header :items="tabHeaders"></tab-header>
          </v-col>
        </v-row>

        <v-row>
          <v-col>
            <Stepper
              :stepItem="steps"
              :stepItemMobile="stepsMobile"
              :pagewindowWidth="windowWidth"
              :pageWindowHeight="windowHeight"
            ></Stepper>
          </v-col>
        </v-row>

        <v-row>
          <v-col>
            <table-content :content="tableData"></table-content>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </div>
</template>

<script>
import PageHeaders from "../Molecule/PageHeaders/PageHeaders.vue";
import Stepper from "../Molecule/Stepper/Stepper.vue";
import TabHeader from "../Pages/TabHeader.vue";
import PageDate from "../Atom/Date/PageDate.vue";
import TableContent from "../Molecule/TableContent/TableContent.vue";
export default {
  components: {
    TabHeader,
    Stepper,
    PageDate,
    TableContent,
    PageHeaders
  },
  mounted() {
    this.$nextTick(function() {
      window.addEventListener("resize", this.getWindowWidth);
      window.addEventListener("resize", this.getWindowHeight);
      this.getWindowWidth();
      this.getWindowHeight();
    });
  },
  data: () => ({
    windowWidth: 0,
    windowHeight: 0,
    titleText: "INTRANET C&MB Bedrijven",
    tabHeaders: "Registeren klant via Kvk",
    steps: [
      "Stap 1. Uittreksel(s) selecteren",
      "Stap 2. UBOs and Bestuurders",
      "Stap 3. Nieuwe BC",
      "Stap 4. Archieveren"
    ],
    stepsMobile: ["1", "2", "3", "4"],
    date: "29June 2020",
    tableData: {
      headers: ["", "Naam", "KvK nr.", "Plaats", "Archiveringsdoel"],
      tableValues: [
        [
          {
            type: "checkbox",
            value: ""
          },
          {
            type: "text",
            value: "Landbouwbedrijf Koolen B.V."
          },
          {
            type: "text",
            value: "17027364"
          },
          {
            type: "text",
            value: "Berjeik"
          },
          {
            type: "dropDown",
            value: ["Landbouwbedrijf Koolen B.V.", "item2", "item3"]
          }
        ]
      ]
    }
  }),

  methods: {
    getWindowWidth(event) {
      this.windowWidth = document.documentElement.clientWidth;
    },

    getWindowHeight(event) {
      this.windowHeight = document.documentElement.clientHeight;
    }
  }
};
</script>

<style>
</style>
