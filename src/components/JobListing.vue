<script setup>
    import { defineProps , ref,computed} from 'vue';
    import { RouterLink } from 'vue-router';


    const props = defineProps({
            job: Object
        });
    const ShowFullDescription = ref(false);
    const toggleFullDescription = () => {
        ShowFullDescription.value = !ShowFullDescription.value;
    }
    const truncatedDescription = computed(() => {
        let description = props.job.description;
        if(!ShowFullDescription.value){
            description = description.substring(0,90) + '...';
        }
        return description;
    });
</script>
<template>
  <div class="bg-white rounded-xl shadow-md relative">
    <div class="p-4">
      <div class="mb-6">
        <div class="text-gray-600 my-2">{{ job.type }}</div>
        <h3 class="text-xl font-bold">{{ job.title }}</h3>
      </div>

      <div class="mb-5">
        <div >
            {{ truncatedDescription }}
        </div>
        <button @click="toggleFullDescription" class=" px-6 py-1 rounded text-green-300  hover:text-green-400 mb-5">
            {{ ShowFullDescription ? 'Read Less' : 'Read More' }}
        </button>
        <!-- We are seeking a talented Front-End Developer to join our team in
        Boston, MA. The ideal candidate will have strong skills in HTML, CSS,
        and JavaScript... -->
      </div>

      <h3 class="text-green-500 mb-2">{{ job.salary }} / year</h3>
      <!-- $70 - $80K / Year -->

      <div class="border border-gray-100 mb-5"></div>

      <div class="flex flex-col lg:flex-row justify-between mb-4">
        <div class="text-orange-700 mb-3">
          <i class="pi pi-map-marker text-orange-700 text-lg"></i>
          {{ job.location }} <!--Boston, MA-->
        </div>
        <RouterLink
          :to="'/jobs/' + job.id"
          class="h-[36px] bg-green-200 hover:bg-green-300 text-black font-semibold text-sm px-4 py-2 rounded-lg text-center"
        >
          Read More
        </RouterLink>
      </div>
    </div>
  </div>
</template>
