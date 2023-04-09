<template>
    <!-- <TransitionRoot as="template" :show="edit">
        --{{ editdata }}
      <Dialog as="div" class="relative z-10" @close="edit = false">

        <div class="fixed inset-0 overflow-hidden">
          <div class="absolute inset-0 overflow-hidden">
            <div
              class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10"
            >
              <TransitionChild
              as="template"
                enter="transform transition ease-in-out duration-500 sm:duration-700"
                enter-from="translate-x-full"
                enter-to="translate-x-0"
                leave="transform transition ease-in-out duration-500 sm:duration-700"
                leave-from="translate-x-0"
                leave-to="translate-x-full"
              >
                <DialogPanel class="pointer-events-auto w-screen max-w-md">
                  <div
                    class="flex h-full flex-col overflow-y-scroll bg-white py-6 shadow-xl"
                  >
                    <div class="px-4 sm:px-6">
                      <div class="flex align-center rounded-xl justify-between">
                        <DialogTitle
                          class="text-base font-semibold leading-6 text-gray-900"
                          >project</DialogTitle
                        >
                        <div class="space-y-6 lg:col-span-2 lg:col-start-1">
                          <div class="ml-3 flex h-7 items-center">
                            <button
                              type="button"
                              class="rounded-md bg-white text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                              @click="edit = false"
                            >
                              <span class="sr-only">Close panel</span>
                              <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                            </button>
                          </div>
                        </div>
                      </div>
                   <form>
                      <div class="mt-2">
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Name</label
                        >
                        <input
                          type="text"
                          v-model="editdata.name"
                          name="email"
                          id="email"
                          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        />
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Project Details</label
                        >
                        <div class="mt-2">
                          <textarea
                            rows="4"
                            name="comment"
                            id="comment"
                            v-model="editdata.details"
                            class="block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:py-1.5 sm:text-sm sm:leading-6"
                          />
                        </div>
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Project Specifications</label
                        >
                        <div class="mt-2">
                          <textarea
                            rows="4"
                            name="comment"
                            id="comment"
                            v-model="editdata.specifications"
                            class="block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:py-1.5 sm:text-sm sm:leading-6"
                          />
                        </div>
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >logo_url</label
                        >
                        <input
                          type="text"
                          v-model="editdata.logo_url"
                          name="email"
                          id="email"
                          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        />
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >default_image_url</label
                        >
                        <input
                          type="text"
                          v-model="editdata.default_image_url"
                          name="email"
                          id="email"
                          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        />
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >listing_type_name</label
                        >
                        <input
                          type="text"
                          v-model="editdata.listing_type_name"
                          name="email"
                          id="email"
                          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        />
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >default_image_url</label
                        >
                        <input
                          type="text"
                          v-model="editdata.age_of_the_project"
                          name="email"
                          id="email"
                          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        />
                      </div>
                    </form>
                      <div class="flex justify-center m-10">
                        <button
                          type="button"
                          class="rounded-full bg-white px-2.5 py-1 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50"
                          @click="edit = false"
                        >
                          Cancel
                        </button>
                        <div  @click="edit = false">
                        <button
                          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full"
                          @click="savedata"
                        >
                          Add
                        </button></div>
                      </div>
                    </div>
                  </div>
                </DialogPanel>
              </TransitionChild>
            </div>
          </div>
        </div>
      </Dialog>
    </TransitionRoot> -->

    <TransitionRoot as="template" :show="edit">
      <Dialog as="div" class="relative z-10" @close="edit = false">
        <div class="fixed inset-0 overflow-hidden">
          <div class="absolute inset-0 overflow-hidden">
            <div
              class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10"
            >
              <TransitionChild
                as="template"
                enter="transform transition ease-in-out duration-500 sm:duration-700"
                enter-from="translate-x-full"
                enter-to="translate-x-0"
                leave="transform transition ease-in-out duration-500 sm:duration-700"
                leave-from="translate-x-0"
                leave-to="translate-x-full"
              >
                <DialogPanel class="pointer-events-auto w-screen max-w-md">
                  <div
                    class="flex h-full flex-col overflow-y-scroll bg-white py-6 shadow-xl"
                  >
                    <div class="px-4 sm:px-6">
                      <div class="flex items-start justify-between">
                        <DialogTitle
                          class="text-base font-semibold leading-6 text-gray-900"
                          >project</DialogTitle
                        >
                        <div class="ml-3 flex h-7 items-center">
                          <button
                            type="button"
                            class="rounded-md bg-white text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                            @click="edit = false"
                          >
                            <span class="sr-only">Close panel</span>
                            <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                          </button>
                        </div>
                      </div>
                    </div>
                    <!-- Data is prefilled in input fields -->
                    <form @submit.prevent="saveFormData" @reset.prevent="cancel">
                    <div
                      class="relative mt-6 flex-1 px-4 sm:px-6 border ml-2 mr-2"
                    >
                      <div class="mt-2">
                        <label
                          for="name"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Name</label
                        >
                        <div class="mt-2">
                          <input
                            id="name"
                            v-model="editdata.name"
                            class="pl-2 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            placeholder="Enter Name"
                          />
                        </div>
                      </div>
                      <div class="mt-2">
                        <label
                          for="details"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Details</label
                        >
                        <div class="mt-2">
                          <input
                            id="details"
                            v-model="editdata.details"
                            class="pl-2 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            placeholder="Enter Details"
                          />
                        </div>
                      </div>
                      <div class="mt-2">
                        <label
                          for="total_project_area"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >specifications</label
                        >
                        <div class="mt-2">
                          <input
                            id="total_project_area"
                            v-model="editdata.specifications"
                            class="pl-2 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            placeholder="Enter Total Project Area"
                          />
                        </div>
                      </div>
                      <div class="mt-2">
                        <label
                          for="listing_type_name"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Listing Type Name</label
                        >
                        <div class="mt-2">
                          <input
                            id="listing_type_name"
                            v-model="editdata.listing_type_name"
                            class="pl-2 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            placeholder="Enter Listing Type Name"
                          />
                        </div>
                      </div>
                      <div class="mt-2">
                        <label
                          for="listing_type_name"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >age of the project</label
                        >
                        <div class="mt-2">
                          <input
                            id="listing_type_name"
                            v-model="editdata.age_of_the_project"
                            class="pl-2 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            placeholder="Enter Listing Type Name"
                          />
                        </div>
                      </div>
                      <div class="mt-2">
                        <div class="mt-2 mb-2 ml-[15.25rem] flex">
                          <div>
                            <button
                              type="reset"
                              class="mr-1 rounded bg-white px-2 py-1 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50"
                            >
                              Cancel
                            </button>
                          </div>
                          <div>
                            <button
                              type="submit"
                              class="rounded bg-indigo-600 px-2 py-1 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                            >
                            Save
                            </button>
                          </div>
                        </div>
                      </div>
                    </div>
                  </form>
                  </div>
                </DialogPanel>
              </TransitionChild>
            </div>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
</template>

<script setup >

import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import {
  XMarkIcon,
  PencilSquareIcon,
  TrashIcon,
} from "@heroicons/vue/24/outline";
const form = ref({});
const emit = defineEmits(["savedata","cancel"]);
const props = defineProps({
    edit: Boolean,
    editdata:Object
  });
const saveFormData = () => {
  emit("savedata", props.editdata);
  props.editdata = {};
};
const cancel = () => {
    emit("cancel");
  };
</script>