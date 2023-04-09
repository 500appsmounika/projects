<template>
  <!--add projects button-->
  <button
    type="button"
    class="rounded bg-indigo-50 px-2 py-1 text-sm font-semibold text-indigo-600 shadow-sm hover:bg-indigo-100"
    @click="opensidebar()"
  >
    Add Project
  </button>
  <CollectionList :templatedata="templateData" @deleteData="deleteData" @editData="updatetemplateData"></CollectionList>

  <CollectionAdd
    v-if="open"
    :open="open"
    :formdata="formdata"
    @post-data="postData"
  ></CollectionAdd>
  <CollectionEdit :editdata="editdata" :edit="edit"  @savedata="postData"></CollectionEdit>
</template>
<script setup lang="ts">
import { ref } from "vue";
//define the props
const open = ref(false);
const edit=ref(false)
const templateData=ref([])
const editdata=ref({})
 const formdata={
  name:"",
  details:"",
  specifications:"",
  logo_url:"",
  default_image_url:"",
  age_of_the_project:"",
  listing_type_name:""

 }

//post and edit
 const postData = async (form: any) => {
  if(form.uid){
    console.log("meesa",form)
    const editoptions={ body: form};
    await useAuthLazyFetchPut(`https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${form.uid}`,editoptions);
    edit.value=false;
    const { data: response } = await useAuthLazyFetch(
      "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/?offset=0&limit=100&sort_column=id&sort_direction=desc", "" );
      templateData.value = response.value;

  }else{
  let options = {
    
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
      Authorization:
        "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYmZlOTY3MDc0YzJhNGVlNDhiODFlYWU1ZmU5ZThhMjkiLCJkIjoiMTY4MDA4MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzkyNzB9._HklK6rl9AWu3mp4kRdrOIsxyEP-jNpG7kgF3K-5GlA",
    },
    body:form
    
  };
  const data = await useAuthLazyFetchPost(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/",
    options
  );
  templateData.value=data.data._rawValue
  console.log("templateData",templateData)
}}
//Prefill
const updatetemplateData = (data: any) => {
  console.log("here in main",data);
  
  edit.value = true;
  editdata.value = data;
  console.log("here in main",editdata.value);

};
//Get
const getData = useLazyFetch(
  "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/?offset=0&limit=100&sort_column=id&sort_direction=desc"
);
templateData.value = getData.data._rawValue;

//Delete
const deleteData = async (data: any) => {
  const doption={body: data};
  await useAuthLazyFetchDelete(`https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${data.uid}`,
  doption);
  const { data: response } = await useAuthLazyFetch(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/?offset=0&limit=100&sort_column=id&sort_direction=desc",
    ""
  );
  templateData.value = response.value;
 
};
function opensidebar() {
  open.value = !open.value;
 
}
</script>
