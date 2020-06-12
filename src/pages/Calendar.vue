<template>
  <div id="calendar">
    <!-- detail event -->
    <v-dialog
      v-model="dialog"
      max-width="340">
      <v-card v-if="selectedEvent">
        <v-card-title class="headline">{{ selectedEvent.title }}</v-card-title>

        <v-card-text>
          Hazard Reported At: {{ selectedEvent.start + ' 15:25' }}
        </v-card-text>
        <v-card-text>
          Hazard Resolved At: {{ selectedEvent.end + ' 18:05'}}
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1"
            flat="flat"
            @click="dialog = false">
            Ok
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <!-- creating new event -->
    <v-dialog
      v-model="dialogCreateEvent"
      max-width="525">
      <v-card v-if="dialogCreateEvent">
        <v-card-title class="headline">Do you want to create new hazard on {{ createEventDate.toLocaleDateString() }} ?</v-card-title>

        <v-card-text>
          <v-text-field
            v-model="newEventTitle"
            label="Hazard Description"
            hint="Type hazard name and choose category" />
        </v-card-text>

        <v-card-text>
          <v-radio-group v-model="selectedEventClass" row>
            <v-radio
              label="Danger"
              color="blue"
              value=""/>
            <v-radio
              label="Easy"
              color="red"
              value="event-item-caution"/>
            <v-radio
              label="Facilities"
              color="green"
              value="event-item-meeting"/>
            <v-radio
              label="Food"
              color="yellow"
              value="event-item-warning"/>
            <v-radio
              label="For ITS"
              color="purple"
              value="event-item-trip"/>
          </v-radio-group>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1"
            flat="flat"
            @click="dialogCreateEvent = false">
            Disagree
          </v-btn>

          <v-btn
            color="green darken-1"
            flat="flat"
            @click="createEvent()">
            Agree
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <full-calendar
      :events="events"
      locale="en"
      @eventClick="eventClick($event)"
      @dayClick="dayClick($event)"/>
  </div>
</template>

<script>
export default {
  data() {
    var d = new Date();

    return {
      dialog: false,
      dialogCreateEvent: false,
      newEventTitle: null,
      createEventDate: null,
      selectedEventClass: null,
      selectedEvent: null,
      events: [
        {
          title : 'A brocken glass',
          start : `${d.getFullYear()}-${d.getMonth()+1}-01`,
          end : `${d.getFullYear()}-${d.getMonth()+1}-03`,
          cssClass : 'event-item-caution',
        },
        {
          title : 'Meeting Room  Issues',
          start : `${d.getFullYear()}-${d.getMonth()+1}-05`,
          end : `${d.getFullYear()}-${d.getMonth()+1}-07`,
          cssClass : 'event-item-trip'
        },
        {
          title : 'Elevator Trip with sounds',
          start : `${d.getFullYear()}-${d.getMonth()+1}-03`,
          end : `${d.getFullYear()}-${d.getMonth()+1}-07`,
          cssClass : 'event-item-warning'
        },
        {
          title : 'Dangerous Event on balcony',
          start : `${d.getFullYear()}-${d.getMonth()+1}-02`,
          cssClass : 'event-item-meeting'
        },
        {
          title : 'Some troubleshoot',
          start : `${d.getFullYear()}-${d.getMonth()+1}-04`,
          cssClass : 'event-item-meeting'
        },
        {
          title : 'Issues with water',
          start : `${d.getFullYear()}-${d.getMonth()+1}-05`,
          end : `${d.getFullYear()}-${d.getMonth()+1}-05`,
          cssClass : 'event-item-caution'
        },

        {
          title : 'Desk issue on floor 2',
          start : `${d.getFullYear()}-${d.getMonth()+1}-05`,
          cssClass : 'event-item-caution'
        },
        {
          title : 'Some inadvertance in meeting room Everest',
          start : `${d.getFullYear()}-${d.getMonth()+1}-09`,
          end : `${d.getFullYear()}-${d.getMonth()+1}-09`,
          cssClass : 'event-item-meeting'
        },
        {
          title : 'Dangerous floor',
          start : `${d.getFullYear()}-${d.getMonth()+1}-10`,
          end : `${d.getFullYear()}-${d.getMonth()+1}-10`,
          cssClass : 'event-item-trip'
        },
        {
          title : 'Hazard example 1',
          start : `${d.getFullYear()}-${d.getMonth()+1}-08`,
          cssClass : 'event-item-meeting'
        },
        {
          title : 'Hazard example 2',
          start : `${d.getFullYear()}-${d.getMonth()+1}-11`,
          cssClass : 'event-item-meeting'
        },
        //----last month
        {
          title : 'Issues with milk',
          start : `${d.getFullYear()}-${d.getMonth()}-20`,
          end : `${d.getFullYear()}-${d.getMonth()}-23`,
          cssClass : 'event-item-caution'
        },
        {
          title : 'Some problems in meeting room Floor4',
          start : `${d.getFullYear()}-${d.getMonth()}-27`,
          end : `${d.getFullYear()}-${d.getMonth()}-28`,
          cssClass : 'event-item-meeting'
        },
		{
          title : 'Dangerous floor in bathroom',
          start : `${d.getFullYear()}-${d.getMonth()}-17`,
          end : `${d.getFullYear()}-${d.getMonth()}-19`,
          cssClass : 'event-item-trip'
        },
        {
          title : 'Fail to start printer',
          start : `${d.getFullYear()}-${d.getMonth()}-08`,
          cssClass : 'event-item-meeting'
        },
        {
          title : 'Room with smoke',
          start : `${d.getFullYear()}-${d.getMonth()}-16`,
          cssClass : 'event-item-meeting'
        }
      ]
    }
  },

  methods: {
    eventClick($event) {
      const vm = this;

      vm.dialog = true;

      vm.selectedEvent = $event;
    },

    dayClick($event) {
      const vm = this;

      vm.dialogCreateEvent = true;

      vm.createEventDate = $event;
    },

    createEvent() {
      const vm = this;

      vm.events.push({
        title: vm.newEventTitle ? vm.newEventTitle : 'New Hazards',
        start: vm.createEventDate,
        cssClass: vm.selectedEventClass ? vm.selectedEventClass : null
      });

      vm.createEventDate = null;
      vm.newEventTitle = '';
      vm.dialogCreateEvent = false;
    }
  }
}
</script>

<style>
  #calendar {
    height: 100%;
  }

  .prev-month {
    font-size: 16px !important;
    font-weight: bold;
  }

  .next-month {
    font-size: 16px !important;
    font-weight: bold;
  }

  .event-item {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif !important;
    font-size: 14px !important;
  }

  .event-item-caution {
    background-color: #e89a9a !important;
  }

  .event-item-warning {
    background-color: #ffffa5 !important;
  }

  .event-item-meeting {
    background-color: #71d48e !important;
  }

  .event-item-trip {
    background-color: #8d78e6 !important;
  }

</style>
