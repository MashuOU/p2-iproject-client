<script>
import { useFunctionStore } from "../stores/counter";
import { mapActions, mapState } from "pinia";
export default {
  props: ["news"],
  methods: {
    ...mapActions(useFunctionStore, ["fetchPodcast", "handlePodcastDetail"]),
  },
  computed: {
    ...mapState(useFunctionStore, ["podcastAllData"]),
  },
};
</script>

<template>
  <div
    class="
      flex-shrink
      max-w-full
      w-full
      sm:w-1/3
      px-3
      pb-3
      pt-3
      sm:pt-0
      border-b-2
      sm:border-b-0
      border-dotted border-gray-100
    "
  >
    <div class="flex flex-row sm:block hover-img">
      <a href="#" @click.prevent="handlePodcastDetail(news.link)">
        <img
          class="max-w-full w-full mx-auto"
          :src="news?.image"
          alt="alt title"
        />
      </a>

      <div class="py-0 sm:py-3 pl-3 sm:pl-0">
        <h3 class="text-lg font-bold leading-tight mb-2">
          <div class="flex">
            <a href="#">{{ news?.title }}</a>
            
          </div>
        </h3>
        <p class="font-light hidden md:block text-gray-600 leading-tight mb-1">
          duration : {{ news?.duration }}
        </p>
        <div>
          <a class="text-gray-500" href="#"
            ><span
              class="inline-block h-3 border-l-2 border-red-600 mr-2"
            ></span>
            {{ news?.published_at }}
          </a>
        </div>
      </div>
    </div>
  </div>
</template>