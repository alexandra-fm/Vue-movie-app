<template>
  <div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "Notification",
  data() {
      return {
        count: 0
      }
    },
  computed: {
    ...mapGetters(["messagePool"])
  },
  watch: {
    messagePool: "showNotification"
  },
  methods: {
    showNotification({ variant, msg, title }) {
      this.$bvToast.toast(msg, {
        title,
        variant,
        solid: true,
        autoHideDelay: "5000"
      });
    },
     showToast() {
        // Use a shorter name for `this.$createElement`
        const h = this.$createElement
        // Create a ID with a incremented count
        const id = `my-toast-${this.count++}`

        // Create the custom close button
        const $closeButton = h(
          'b-button',
          {
            on: { click: () => this.$bvToast.hide(id) }
          },
          'Close'
        )

        // Create the toast
        this.$bvToast.toast([$closeButton], {
          id: id,
          title: `Toast ${this.count}`,
          noCloseButton: true
        })
      }
  }
};
</script>

<style scoped>
.notif {
  z-index: 999
}
</style>
