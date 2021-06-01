<template>
  <div class="container mx-auto max-w-5xl items-center justify-center">
    <ul class="mt-5">
      <li
        class="flex flex-row mb-2 shadow-md"
        v-for="job in jobs"
        v-bind:key="job"
      >
        <div
          class="
            select-none
            cursor-pointer
            rounded-md
            flex flex-1
            items-center
            p-4
            transition
            duration-500
            ease-in-out
            transform
            hover:-translate-y-1
            hover:shadow-lg
          "
        >
          <div
            class="
              flex flex-col
              rounded-md
              w-10
              h-10
              bg-gray-300
              justify-center
              items-center
              mr-4
            "
          >
            <a :href="job.url" target="_blank"><img :src="job.logo" /></a>
          </div>
          <div class="flex-1 pl-1 mr-16">
            <div class="font-bold">{{ job.title }}</div>
            <div class="text-gray-600 text-sm">{{ job.company }}</div>
            <div class="text-gray-600 text-sm">{{ job.type }}</div>
          </div>
          <div class="text-green-600 medium text-xs">
            <a :href="job.listing" target="_blank">View</a>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "Looper",
  data() {
    return {
      jobs: [],
    };
  },
  created() {
    this.getJobs();
  },
  methods: {
    getJobs() {
      axios
        .get(
          "http://cors-anywhere.herokuapp.com/https://jobs.github.com/positions.json?search=remote&markdown=true"
        )
        .then((response) => {
          for (var i = 0; i < response.data.length; i++) {
            let api = response.data[i];
            let apiInfo = {
              title: api.title,
              company: api.company,
              url: api.company_url,
              logo: api.company_logo,
              apply: api.how_to_apply,
              listing: api.url,
              type: api.type,
              desc: api.description,
            };
            this.jobs.push(apiInfo);
          }
        });
    },
  },
};
</script>
<style></style>
