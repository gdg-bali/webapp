<template>
  <v-list class="listContainer">
    <v-list-tile>
      <v-list-tile-action>
        <v-icon left class="mr-2">location_on</v-icon>
      </v-list-tile-action>
      <v-list-tile-content>
        <v-list-tile-title>
          {{ (event.venue || {}).name || 'TBA' }}
        </v-list-tile-title>
      </v-list-tile-content>
    </v-list-tile>
    <v-list-tile>
      <v-list-tile-action>
        <v-icon left class="mr-2">event</v-icon>
      </v-list-tile-action>
      <v-list-tile-content>
        <v-list-tile-title>
          <FormatDate :starts-at="event.startsAt" :with-time="true" />
        </v-list-tile-title>
      </v-list-tile-content>
    </v-list-tile>
  </v-list>
</template>

<script>
const FormatDate = () =>
  import(/* webpackChunkName: "format-date" */ '@components/shared/FormatDate');

export default {
  props: {
    event: {
      type: Object,
      default: () => ({
        venue: {},
      }),
    },
  },
  components: {
    FormatDate,
  },
};
</script>

<style lang="stylus" scoped>
.listContainer {
  background: transparent;
}
</style>
