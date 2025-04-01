<template>
  <div class="flex h-[100%]">
    <!-- Left Part: Input Box -->
    <div class="w-2/5 pr-4 flex flex-col">
      <div class="flex-1 overflow-hidden">
        <div class="rounded-lg bg-gray-50 border border-gray-300 p-4 h-full overflow-y-auto">
          <div class="whitespace-pre-wrap break-words text-gray-700 font-normal">
            {{ ideaText }}
          </div>
        </div>
      </div>
      <div class="mt-4 flex flex-col md:flex-row items-center justify-between gap-4">
        <div class="flex items-center gap-2 w-full md:w-auto">
          <span class="text-sm text-gray-500">Style:</span>
          <Menu as="div" class="relative inline-block text-left w-full md:w-auto">
            <div>
              <MenuButton
                class="inline-flex w-full justify-center gap-x-1.5 rounded-md bg-white px-3 py-2 text-sm font-medium text-gray-700 shadow-sm ring-1 ring-inset ring-gray-200 hover:bg-gray-50">
                Document
                <ChevronDownIcon class="-mr-1 h-5 w-5 text-gray-400" aria-hidden="true" />
              </MenuButton>
            </div>

            <transition enter-active-class="transition ease-out duration-100"
              enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100"
              leave-active-class="transition ease-in duration-75" leave-from-class="transform opacity-100 scale-100"
              leave-to-class="transform opacity-0 scale-95">
              <MenuItems
                class="absolute left-0 z-10 mt-2 w-56 origin-top-right rounded-md bg-white shadow-lg ring-1 ring-black/5 focus:outline-none">
                <div class="py-1">
                  <MenuItem v-slot="{ active }">
                  <a
                    :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Document</a>
                  </MenuItem>
                  <MenuItem v-slot="{ active }">
                  <a
                    :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Slide</a>
                  </MenuItem>
                </div>
              </MenuItems>
            </transition>
          </Menu>
        </div>

        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline w-full md:w-auto"
          type="button">
          Convert
        </button>
      </div>
    </div>

    <!-- Right Part: Animated Typst Code -->
    <div class="w-3/5 pl-4">
      <div class="rounded-lg bg-gray-100 p-4 h-full overflow-y-auto font-mono">
        <div class="text-sm text-gray-500 mb-2">solution.typ</div>
        <CodeAppearAnime :tokens="tokens" :code="typstCode" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue';
import { ChevronDownIcon } from '@heroicons/vue/24/outline';
import CodeAppearAnime from './CodeAppearAnime.vue';

const ideaText = ref(`Keep track of the partial sum and the minimal historical partial sum`);
const typstCode = ref(`#import "./polyhedron-solution.typ": *;
#show: ph-init

= Solution for Maximum Subarray Sum

== Algorithm

We can solve this problem using Kadane's Algorithm. The idea is to iterate through the array, maintaining a current maximum sum ending at the current position and a global maximum sum.

== Time Complexity

The time complexity of Kadane's Algorithm is $O(n)$, as we iterate through the array once.

== Space Complexity

The space complexity is $O(1)$, as we only use a few variables to keep track of the sums.
`);
const tokens = ref([ // Manually defined tokens and types for highlighting and animation
  { content: '#import', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: '"./polyhedron-solution.typ"', type: 'string' }, { content: ':', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: '*', type: 'operator' }, { content: ';', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '#show', type: 'keyword' }, { content: ':', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'ph-init', type: 'function' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '= Solution for Maximum Subarray Sum', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '== Algorithm', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'We can solve this problem using Kadane\'s Algorithm. The idea is to iterate through the array, maintaining a current maximum sum ending at the current position and a global maximum sum.', type: 'text' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '== Time Complexity', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'The time complexity of Kadane\'s Algorithm is ', type: 'text' }, { content: '$O(n)$', type: 'formula' }, { content: ', as we iterate through the array once.', type: 'text' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '== Space Complexity', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'The space complexity is ', type: 'text' }, { content: '$O(1)$', type: 'formula' }, { content: ', as we only use a few variables to keep track of the sums.', type: 'text' }, { content: '\n', type: 'whitespace' },
]);
</script>
