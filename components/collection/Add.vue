<template>
  <!-- v-else-if="open" -->
  <div>
    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10" @close="open = false">
        <div class="fixed inset-0" />
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
                              @click="open = false"
                            >
                              <span class="sr-only">Close panel</span>
                              <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                            </button>
                          </div>
                          <div class="py-90px"></div>
                        </div>
                      </div>
                      <div class="relative mt-6 flex-1 px-4 sm:px-6"></div>
                      <div class="mt-2">
                        <label
                          for="email"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Name</label
                        >
                        <input
                          type="text"
                          v-model="formdata.name"
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
                            v-model="formdata.details"
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
                            v-model="formdata.specification"
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
                          v-model="formdata.logo_url"
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
                          v-model="formdata.default_image_url"
                          name="email"
                          id="email"
                          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        />
                      </div>

                      <div class="flex justify-center m-10">
                        <button
                          type="button"
                          class="rounded-full bg-white px-2.5 py-1 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50"
                          @click="open = false"
                        >
                          Cancel
                        </button>
                        <button
                          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full"
                          @click="postData(), open=false"
                        >
                          Add
                        </button>
                      </div>
                    </div>
                  </div>
                </DialogPanel>
              </TransitionChild>
            </div>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
  </div>
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

const props = defineProps({
  open: Boolean,
  formdata: Object,
  default: () => [],
});
const emits=defineEmits(["post-data"])
const postData = async () => {
  console.log("hello")
  let form={
  name:props.formdata.name,
  details:props.formdata.details,
  specification:props.formdata.specification,
  logo_url:propsformdata.logo_url,
  default_image_url:props.formdata.default_image_url,
  category: "Residential",
  sub_category: "Apartment",
  status: "Fully Constructed",
  rera_approved: true,
  approve_status: "Active"

 }
   emits("post-data", form);
  
};
</script>
