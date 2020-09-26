<template>
  <mdb-container>
    <mdb-row>
      <mdb-col col="12">
      <div>
      &nbsp;
      </div>
        <mdb-row>
        <div align="left"><div></div></div><div>&nbsp;</div><mdb-col col="12" class="text-left">
          </mdb-col>
          <mdb-col class="text-center">
          <img src="./boot.png" width="100%">
          </mdb-col>
          <mdb-col col="4">
          <h3>
          _______ ⛅<br>Cloudy</div><br>
          &nbsp;&nbsp;&nbsp;<mdb-icon icon="thermometer-three-quarters"/>&nbsp;&nbsp;21°C </h3></mdb-col></b>

        </mdb-row>
        <img src="./logo.png" width="50%">
      </h1>
      <div>
      &nbsp;
      </div><h6><b>SETS OF WORKOUT SESH THAT OUR LOVELY BEAUTIFUL COACH__ IJA.AINI ARE RUNNING TODAY AS CHAIRMEN V.P FOR BOOTY-FIT TECHNOLOGY!</b></h6>
      <div>
      &nbsp;
      </div>
        <Event
          v-for="(event, index) in events"
          :index="index"
          :time="event.time"
          :title="event.title"
          :location="event.location"
          :description="event.description"
          :key="index"
          @delete="handleDelete"
        />
        <mdb-row>
          <mdb-col xl="3" md="6" class="mx-auto text-center">
            <mdb-btn color="info" @click.native="modal = true">+ Add Activity</mdb-btn>
          </mdb-col>
        </mdb-row>
      </mdb-col>
      <mdb-col col="3">
      </mdb-col>
    </mdb-row>
    <div>
    &nbsp;
    </div>
    <div>
    &nbsp;
    </div>
    <div>
    &nbsp;
    </div>
    <mdb-modal v-if="modal" @close="modal = false">
      <mdb-modal-header>
        <mdb-modal-title tag="h4" class="w-100 text-center font-weight-bold">Add New Schedule</mdb-modal-title>
      </mdb-modal-header>
      <mdb-modal-body>
        <form class="mx-3 grey-text">
          <mdb-input
            name="time"
            label="Time"
            icon="clock"
            placeholder="12:30"
            type="text"
            @input="handleInput($event, 'time')"
          />
          <mdb-input
            name="title"
            label="Title"
            icon="edit"
            placeholder="Briefing"
            type="text"
            @input="handleInput($event, 'title')"
          />
          <mdb-input
            name="location"
            label="Location (optional)"
            icon="map"
            type="text"
            @input="handleInput($event, 'location')"
          />
          <mdb-textarea
            name="description"
            label="Description (optional)"
            icon="sticky-note"
            @input="handleInput($event, 'description')"
          />
        </form>
      </mdb-modal-body>
      <mdb-modal-footer class="justify-content-center">
        <mdb-btn color="info" @click.native="addEvent">Add</mdb-btn>
      </mdb-modal-footer>
    </mdb-modal>
  </mdb-container>
</template>
<script>
import {
  mdbContainer,
  mdbRow,
  mdbCol,
  mdbIcon,
  mdbBtn,
  mdbModal,
  mdbModalHeader,
  mdbModalTitle,
  mdbModalBody,
  mdbModalFooter,
  mdbInput,
  mdbTextarea
} from "mdbvue";
import Event from "@/components/Event";
export default {
  name: "App",
  components: {
    mdbContainer,
    mdbRow,
    mdbCol,
    mdbIcon,
    mdbBtn,
    mdbModal,
    mdbModalHeader,
    mdbModalTitle,
    mdbModalBody,
    mdbModalFooter,
    mdbInput,
    mdbTextarea,
    Event
  },
  data() {
    return {
      events: [
        {
          time: "08:00",
          title: "Nora @ Xtreme Hardcore Gym & Fitness - Balance (RM650)",
          location: "Address: Dataran, 8-2, Dataran Wangsa, Wangsa Melawati, 53300 Kuala Lumpur, Wilayah Persekutuan Kuala Lumpur",
          description: "Personal Trainer: Need a boost in your workout or still new? We have certified trainer to help you with trimming down those labs, muscles toning, workout scheduling and consultation."
        },
        {
          time: "09:00",
          title: "Lee @ Xtreme Hardcore Gym & Fitness",
          location: "Address: Dataran, 8-2, Dataran Wangsa, Wangsa Melawati, 53300 Kuala Lumpur, Wilayah Persekutuan Kuala Lumpur"
        },
        {
          time: "11:00",
          title: "Melati @ THE NEST GYM FITNESS - JALAN GENTING KLANG SETAPAK KUALA LUMPUR."
        },
        {
          time: "01:00",
          title: "Orchid @ Kajang Gym",
          location: "Celebrity Fitness - Kajang Metropoint",
          description: "In our club, you can get fit and fierce, your way. We have a cardio area, cycling studio, free weights area"
        }
      ],
      modal: false,
      newValues: []
    };
  },
  methods: {
    handleDelete(eventIndex) {
      this.events.splice(eventIndex, 1);
    },
    handleInput(val, type) {
      this.newValues[type] = val;
    },
    addEvent() {
      this.events.push({
        time: this.newValues["time"],
        title: this.newValues["title"],
        location: this.newValues["location"],
        description: this.newValues["description"]
      });
    }
  }
};
</script>

<style>
</style>
