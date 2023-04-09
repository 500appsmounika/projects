<template>
  <div>
    <div>
      <div class="bg-white shadow-md rounded-md p-4">
        <table class="w-full table-auto">
          <thead>
            <tr>
              <th class="px-4 py-2 text-left">Name</th>
              <th class="px-4 py-2 text-left">listing_type_name</th>
              <th class="px-4 py-2 text-left">specifications</th>
              <th class="px-4 py-2 text-left">age_of_the_project</th>
              <th class="px-4 py-2 text-left">logo_url</th>
              <th class="px-4 py-2 text-left">default_image_url</th>
            </tr>
          </thead>

          <tbody>
            <tr
              class="bg-gray-100"
              v-for="(template, index) in templatedata"
              :key="index"
            >
              <td class="px-4 py-2">{{ template.name }}</td>
              <td class="px-4 py-2">{{ template.listing_type_name }}</td>
              <td class="px-4 py-2">{{ template.specifications }}</td>
              <td class="px-4 py-2">{{ template.age_of_the_project }}</td>
              <td class="px-4 py-2">{{ template.logo_url }}</td>
              <td class="px-4 py-2">{{ template.default_image_url }}</td>
              <td class="px-4 py-2">
                      <div class="align item-center justify-between">
                <PencilSquareIcon
                  name="iconoir:edit-pencil"
                  size="20"
                  class="h-5 w-5 flex-shrink-0 text-gray-400 group-hover:text-gray-500"
                  @click="editData(template)"
                >
                  <!-- <Edit :model="model" :comment="comment.note"></Edit> -->
                </PencilSquareIcon>
                <TrashIcon
                  name="bytesize:trash"
                  size="16"
                  class="h-5 w-5 flex-shrink-0 text-gray-400 group-hover:text-gray-500:text-red-600"
                  @click="emits('deleteData',template)"
                >
                </TrashIcon></div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
<script setup>
import { PlusIcon, PencilSquareIcon, TrashIcon } from "@heroicons/vue/20/solid";
const props = defineProps({
  templatedata: Array,
  default: () => [],
});
const emits = defineEmits(['editData','deleteData','updateData']);

const editData =(data) =>{
  console.log("here in edit",data);
  emits('editData',data)
}
</script>
