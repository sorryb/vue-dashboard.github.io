<template>
  <v-container fluid grid-list-xl>
    <v-layout row wrap>
      <v-flex d-flex lg12 sm12 xs12>
      <v-card style="margin-bottom: 150px;">
        <v-toolbar color="cyan" dark>
          <v-toolbar-side-icon></v-toolbar-side-icon>

          <v-toolbar-title>Notification Inbox</v-toolbar-title>

          <v-spacer></v-spacer>

          <v-btn icon>
            <v-icon>search</v-icon>
          </v-btn>
        </v-toolbar>

        <v-list two-line>
          <template v-for="(item, index) in items">
            <v-subheader
              v-if="item.header"
              :key="item.header"
            >
              {{ item.header }}
            </v-subheader>

            <v-divider
              v-else-if="item.divider"
              :key="index"
              :inset="item.inset"
            ></v-divider>

            <v-list-tile
              v-else
              :key="item.title"
              avatar
              @click="openDetail"
            >
              <v-list-tile-avatar>
                <img :src="item.avatar">
              </v-list-tile-avatar>

              <v-list-tile-content>
                <v-list-tile-title v-html="item.title"></v-list-tile-title>
                <v-list-tile-sub-title v-html="item.subtitle"></v-list-tile-sub-title>
              </v-list-tile-content>
                <v-list-tile-action>
                  <!-- <v-list-tile-action-text>{{ formatDate(item.created_at) }}</v-list-tile-action-text> -->
                  <v-icon v-if="!item.isStarred" @click="item.isStarred = !item.isStarred" color="grey lighten-1" >star_border</v-icon>
                  <v-icon v-else @click="item.isStarred = !item.isStarred" color="yellow darken-2">star</v-icon>
                </v-list-tile-action>
            </v-list-tile>
          </template>
        </v-list>
      </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { header: 'Today' },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
          title: 'Working this weekend?',
          isStarred: false,
          subtitle: "<span class='text--primary'>Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to haresolve something?",
        },
        { divider: true, inset: true },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
          title: 'Summer Checks <span class="grey--text text--lighten-1">4</span>',
          isStarred: false,
          subtitle: "<span class='text--primary'>to Alex, Scott, Jennifer</span> &mdash; This week starts the checks for this summer.",
        },
        { divider: true, inset: true },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/3.jpg',
          title: 'Flour, milk powder or grain dusts',
          isStarred: false,
          subtitle: "<span class='text--primary'>Sandra Adams</span> &mdash; Exposure to organic dusts can result in severe health impacts, including respiratory irritation and occupational asthma.",
        },
        { divider: true, inset: true },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/4.jpg',
          title: 'Use of display screen equipment',
          isStarred: false,
          subtitle: "<span class='text--primary'>Trevor Hansen</span> &mdash; Prolonged use of poorly designed workstations can result in a range of ill-health effects",
        },
        { divider: true, inset: true },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/5.jpg',
          title: 'Workplace aggression and abuse',
          isStarred: false,
          subtitle: "<span class='text--primary'>Britta Holt</span> &mdash; Whether it’s from a colleague, client or someone else, workplace aggression and abuse can have serious effects on someone’s mental and physical health.",
        }
      ],
    }
  },

  methods: {
    openDetail() {
      const vm = this;


    }
  }
}
</script>

<style>

</style>
