<template>
  <div class="flex h-[100%]">
    <!-- Left Part: Problem Selection -->
    <div class="w-2/5 pr-4 flex flex-col">
      <div class="flex-1 overflow-hidden">
        <div class="rounded-lg bg-gray-50 border border-gray-300 p-4 h-full overflow-y-auto">
          <div class="whitespace-pre-wrap break-words text-gray-700 font-normal mb-4">Select Problems to Export</div>
          <div class="space-y-2">
            <div v-for="problem in problems" :key="problem.id" class="flex items-center row" :style="{ animationDelay: `${problem.id * 0.05}s` }">
              <input 
                :id="`problem-${problem.id}`" 
                type="checkbox" 
                checked
                class="h-4 w-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500"
              >
              <label :for="`problem-${problem.id}`" class="ml-3 text-sm text-gray-700">{{ problem.name }}</label>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Right Part: Export Options -->
    <div class="w-3/5 pl-4 flex flex-col">
      <div class="rounded-lg bg-gray-100 p-4 h-full overflow-y-auto">
        <div class="text-sm text-gray-500 mb-4">Export Options</div>
        <div class="space-y-4">
          <div>
            <label class="block text-sm font-medium text-gray-700 mb-2">Export Format</label>
            <Menu as="div" class="relative inline-block text-left w-full">
              <div>
                <MenuButton
                  class="inline-flex w-full justify-between rounded-md bg-white px-3 py-2 text-sm font-medium text-gray-700 shadow-sm ring-1 ring-inset ring-gray-200 hover:bg-gray-50">
                  Codeforces
                  <ChevronDownIcon class="-mr-1 h-5 w-5 text-gray-400" aria-hidden="true" />
                </MenuButton>
              </div>

              <transition enter-active-class="transition ease-out duration-100"
                enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100"
                leave-active-class="transition ease-in duration-75" leave-from-class="transform opacity-100 scale-100"
                leave-to-class="transform opacity-0 scale-95">
                <MenuItems
                  class="absolute left-0 z-10 mt-2 w-full origin-top-right rounded-md bg-white shadow-lg ring-1 ring-black/5 focus:outline-none">
                  <div class="py-1">
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">PDF (Statement only)</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Typst source code (Statement only)</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Markdown source code (Statement only)</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">LaTeX source code (Statement only)</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">UOJ</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Lemonlime</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">CMS</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Arbiter</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Codeforces</a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Luogu</a>
                    </MenuItem>
                  </div>
                </MenuItems>
              </transition>
            </Menu>
          </div>

          <div class="pt-4">
            <button 
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline w-full"
              @click="exportProblems"
            >
              Export Selected
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue';
import { ChevronDownIcon } from '@heroicons/vue/24/outline';

const problems = ref([
  { id: 1, name: 'A. Airline Planning' },
  { id: 2, name: 'B. Binary String' },
  { id: 3, name: 'C. Colorful Graph' },
  { id: 4, name: 'D. Double Palindrome' },
  { id: 5, name: 'E. Easy Problem' },
]);

const exportProblems = () => {
  console.log('Exporting problems in', selectedFormat.value);
};

</script>

<style scoped>
@keyframes appear {
  from {
    opacity: 0;
    transform: translateX(-10px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.row {
  opacity: 0;
  animation: appear 0.1s forwards;
}
</style>
