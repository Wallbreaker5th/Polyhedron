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
                ICPC
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
                    :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">ICPC</a>
                  </MenuItem>
                  <MenuItem v-slot="{ active }">
                  <a
                    :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">NOI</a>
                  </MenuItem>
                  <MenuItem v-slot="{ active }">
                  <a
                    :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'block px-4 py-2 text-sm']">Codeforces</a>
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
    <div class="w-full md:w-3/5 pl-0 md:pl-4 mt-4 md:mt-0">
      <div class="rounded-lg bg-gray-100 p-4 h-full overflow-y-auto font-mono">
        <div class="text-sm text-gray-500 mb-2">statement.typ</div>
        <CodeAppearAnime :tokens="tokens" :code="typstCode" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue';
import { ChevronDownIcon } from '@heroicons/vue/24/outline';
import CodeAppearAnime from './CodeAppearAnime.vue';

const ideaText = ref(`Problem: Maximum Subarray Sum
Constraints:
- Array size n: 1 to 10^5
- Element range: -10^9 to 10^9
Task: Find the maximum sum of a contiguous subarray.`);
const typstCode = ref(`#import "./polyhedron-statement.typ": *;
#show: ph-init

= Maximal Subarrays Sum

#ph-resource-limits()

== Description

Given an array of integers $a_1, a_2, ..., a_n$, we want to find the maximum sum of a subarray of the array. A subarray is a contiguous sequence of elements within the array. A subarray can be empty, in which case the sum is 0.

== Input

The input consists of two lines. The first line contains an integer $n$ $(1 <= n <= 10^5)$, the number of elements in the array. The second line contains $n$ integers $a_1, a_2, ..., a_n$ $(-10^9 <= a_i <= 10^9)$, the elements of the array.

== Output

Output a single integer, the maximum sum of a subarray of the array.

== Example

#ph-samples()
`);
const tokens = ref([ // Manually defined tokens and types for highlighting and animation
  { content: '#import', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: '"./polyhedron-statement.typ"', type: 'string' }, { content: ':', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: '*', type: 'operator' }, { content: ';', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '#show', type: 'keyword' }, { content: ':', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'ph-init', type: 'function' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '= Maximal Subarrays Sum', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '#ph-resource-limits', type: 'function' }, { content: '()', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '== Description', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'Given an array of integers ', type: 'text' }, { content: '$a_1, a_2, ..., a_n$', type: 'formula' }, { content: ', we want to find the maximum sum of a subarray of the array. A subarray is a contiguous sequence of elements within the array. A subarray can be empty, in which case the sum is 0.', type: 'text' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '== Input', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'The input consists of two lines. The first line contains an integer ', type: 'text' }, { content: '$n$', type: 'formula' }, { content: ' ', type: 'whitespace' }, { content: '$(1 <= n <= 10^5)$', type: 'formula' }, { content: ', the number of elements in the array. The second line contains ', type: 'text' }, { content: '$n$', type: 'formula' }, { content: ' integers ', type: 'text' }, { content: '$a_1, a_2, ..., a_n$', type: 'formula' }, { content: ' ', type: 'whitespace' }, { content: '$(-10^9 <= a_i <= 10^9)$', type: 'formula' }, { content: ', the elements of the array.', type: 'text' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '== Output', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'Output a single integer, the maximum sum of a subarray of the array.', type: 'text' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '== Example', type: 'heading' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '#ph-samples', type: 'function' }, { content: '()', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
]);
</script>
