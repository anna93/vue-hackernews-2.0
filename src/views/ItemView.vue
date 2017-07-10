<template>
  <div>
    
  </div>
</template>

<script>

export default {
  name: 'item-view',

  computed: {
    item () {
      return this.$store.state.items[this.$route.params.id]
    }
  },

  // We only fetch the item itself before entering the view, because
  // it might take a long time to load threads with hundreds of comments
  // due to how the HN Firebase API works.
  asyncData ({ store, route: { params: { id }}}) {
    return store.dispatch('FETCH_ITEMS', { ids: [id] })
  },

  title () {
    return this.item.title
  },

  methods: {
  }
}
</script>