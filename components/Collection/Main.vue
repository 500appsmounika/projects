<template>
  <header>
    <div
      class="mt-2 justify-between mt-5 sm:mt-6 sm:grid sm:grid-flow-row-dense sm:grid-cols-2 sm:gap-3"
    >
      <h2>Vue</h2>
      <input
        type="text"
        name="name"
        id="name"
        class="block rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        placeholder="Login Name:Mounika"
      />
    </div>
  </header>
  <div class="justify-between mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
    <input
      type="search"
      name="name"
      id="name"
      class="block rounded-full border-0 px-4 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
      placeholder="Search"
    />

    <button
      type="button"
      @click="opensidebar()"
      class="block rounded-md align item-center bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
    >
      Add Student
    </button>
  </div>
  <CollectionAdd v-if="open" :open="open" @postData="postData"></CollectionAdd>
  <CollectionList
    :templateData="templateData"
    @deleteData="deleteData"
    :edit="edit"
    @editData="updatetemplateData"
   
  ></CollectionList>
  <CollectionEdit v-if="edit"
    :editdata="editdata"
    :edit="edit"
    @savedata="postData"
  ></CollectionEdit>
<CollectionDelete v-if="deletedata" :deletedata="deletedata"></CollectionDelete>
</template>


<script setup>
// import { useChannelsStore } from '~~/stores/Channels'
//define ref
const open = ref(false);
const templateData = ref([]);
const edit = ref(true);
const deletedata =ref(false);
const editdata = ref({});

onMounted(() => {
    const items = localStorage.getItem("List"); 
    templateData.value=JSON.parse(items)
});
const postData = (form) => {
//   console.log("dataaaaaaa", form);
//   if(!templateData.value) templateData.value =[]
  templateData.value.push(form);
  localStorage.setItem("List", JSON.stringify(templateData.value));
  
  
  getUserData()
};
const getUserData = () => {
let userList = localStorage.getItem("List");
  templateData.value = JSON.parse(userList);
  console.log("mouni",templateData.value)
}
  

const opensidebar = () => {
  open.value = !open.value;
};


//prefill
// const updatetemplateData = () => {};
//delete
// const deleteData = () => { 
//     deletedata.value=!deletedata.value
// };
//open sidebar

</script>
