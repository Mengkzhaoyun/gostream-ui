<template>
  <v-container fluid>
    <v-slide-y-transition mode="out-in">
      <v-layout column align-center>
        <img src="@/assets/logo.png" alt="Vuetify.js" class="mb-5">
        <blockquote>
          &#8220;SSE Client.&#8221;
          <footer>
            <small>
              <em>&mdash;Mengkzhaoyun</em>
            </small>
          </footer>
        </blockquote>
      </v-layout>
    </v-slide-y-transition>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    stockData: null
  }),
  props: {
    source: String
  },
  created() {
    this.setupStream();
  },
  methods: {
        setupStream() {
            // Not a real URL, just using for demo purposes
            let es = new EventSource('http://localhost:8090/gostream/stream/events');

            es.addEventListener('message', event => {
                let data = JSON.parse(event.data);
                this.stockData = data.stockData;
            }, false);

            es.addEventListener('error', event => {
                if (event.readyState == EventSource.CLOSED) {
                    console.log('Event was closed');
                    console.log(EventSource);
                }
            }, false);
        }
    }
};
</script>