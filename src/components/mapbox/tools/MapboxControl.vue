<script>
import {mapGetters} from 'vuex'
export default {
  name: 'mapbox-control',
  render () {
    return ''
  },
  data: () => ({
    nav: null
  }),
  computed: {
    ...mapGetters(['mapboxMap'])
  },
  watch: {
    mapboxMap (newVal, oldVal) {
      if (newVal) this.reload()
    }
  },
  methods: {
    reload () {
      const {mapboxMap, mapboxgl} = global
      if (this.nav) mapboxMap.removeControl(this.nav)
      this.nav = new mapboxgl.NavigationControl()
      mapboxMap.addControl(this.nav)
    }
  }
}
</script>
