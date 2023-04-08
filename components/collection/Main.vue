<template>

      <button 
        type="button"
        class="rounded bg-indigo-50 px-2 py-1 text-sm font-semibold text-indigo-600 shadow-sm hover:bg-indigo-100" @click="opensidebar()"
      >
        Add Project
      </button>
      <CollectionList :templateData="templateData"></CollectionList>
      <CollectionAdd v-if="open" :open="open" :formdata="formdata" @post-data="postData"></CollectionAdd>
</template>
<script setup>
import { ref } from "vue";
import {
XMarkIcon,
PencilSquareIcon,
TrashIcon,
} from "@heroicons/vue/24/outline";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
const open = ref(false);
const name =ref('');
const details=ref('')
const specifications=ref('')
const logo_url=ref('')
const default_image_url=ref('')
 const formdata={
  name:"",
  details:"",
  specification:"",
  logo_url:"",
  default_image_url:""

 }
 const postData = async (form) => {
// console.log("updateTemplate(form);>>>>>>>",templateData)
  // if (form.uid) return updateTemplate(form)
  const { data: templateData } = await useAuthLazyFetch(
  "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/?offset=0&limit=100&sort_column=id&sort_direction=desc"
);
  let options = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
      Authorization:
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYmZlOTY3MDc0YzJhNGVlNDhiODFlYWU1ZmU5ZThhMjkiLCJkIjoiMTY4MDA4MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzkyNzB9._HklK6rl9AWu3mp4kRdrOIsxyEP-jNpG7kgF3K-5GlA",
    },
    body: form,
  };
  const { data: addTemplateData } = await useAuthLazyFetchPost(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/",
    options
  );
  templateData.value.unshift(form);
  formsData.value = {};
};
function opensidebar() {
  open.value = !open.value;
}
</script>