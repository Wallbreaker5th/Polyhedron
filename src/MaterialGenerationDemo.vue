<template>
  <div class="flex flex-col h-[100%] overflow-y-auto">
    <!-- Title -->
    <div class="text-lg font-semibold mb-4">Generate Standard Solution</div>

    <!-- Form Section -->
    <div class="flex flex-col gap-4 mb-6">
      <div class="flex items-center gap-2">
        <span class="text-sm text-gray-500">Reference:</span>
        <Menu as="div" class="relative inline-block text-left" multiple>
          <div>
            <MenuButton
              class="inline-flex w-full justify-center gap-x-1.5 rounded-md bg-white px-3 py-2 text-sm font-medium text-gray-700 shadow-sm ring-1 ring-inset ring-gray-200 hover:bg-gray-50">
              solution.typ - Kadane's Algorithm, std-kadane.cpp
              <ChevronDownIcon class="-mr-1 h-5 w-5 text-gray-400" aria-hidden="true" />
            </MenuButton>
          </div>

          <transition enter-active-class="transition ease-out duration-100"
            enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100"
            leave-active-class="transition ease-in duration-75" leave-from-class="transform opacity-100 scale-100"
            leave-to-class="transform opacity-0 scale-95">
            <MenuItems
              class="absolute left-0 z-10 mt-2 origin-top-right rounded-md bg-white shadow-lg ring-1 ring-black/5 focus:outline-none">
              <div class="py-1">
                <MenuItem v-slot="{ active, }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm', 'font-semibold']">
                    <span class="mr-2 text-green-500">
                      <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                        <path fill-rule="evenodd" d="M16.704 4.153a.75.75 0 01.143 1.052l-8 10.5a.75.75 0 01-1.127.075l-4.5-4.5a.75.75 0 011.06-1.06l3.97 3.97 7.473-9.819a.75.75 0 011.05-.143z" clip-rule="evenodd" />
                      </svg>
                    </span>
                    <span class="truncate">solution.typ - Kadane's Algorithm</span>
                  </a>
                </MenuItem>
                <MenuItem v-slot="{ active, selected }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm', selected ? 'font-semibold' : 'font-normal']">
                    <span v-if="selected" class="mr-2 text-green-500">
                      <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                        <path fill-rule="evenodd" d="M16.704 4.153a.75.75 0 01.143 1.052l-8 10.5a.75.75 0 01-1.127.075l-4.5-4.5a.75.75 0 011.06-1.06l3.97 3.97 7.473-9.819a.75.75 0 011.05-.143z" clip-rule="evenodd" />
                      </svg>
                    </span>
                    <span class="truncate">solution.typ - Dynamic Programming</span>
                  </a>
                </MenuItem>
                <MenuItem v-slot="{ active, }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm', 'font-semibold']">
                    <span class="mr-2 text-green-500">
                      <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                        <path fill-rule="evenodd" d="M16.704 4.153a.75.75 0 01.143 1.052l-8 10.5a.75.75 0 01-1.127.075l-4.5-4.5a.75.75 0 011.06-1.06l3.97 3.97 7.473-9.819a.75.75 0 011.05-.143z" clip-rule="evenodd" />
                      </svg>
                    </span>
                    <span class="truncate">std-kadane.cpp</span>
                  </a>
                </MenuItem>
              </div>
            </MenuItems>
          </transition>
        </Menu>
      </div>

      <input
        type="text"
        placeholder="Enter more instructions here"
        class="rounded-md border border-gray-300 px-3 py-2 text-sm text-gray-500 bg-gray-50"
        disabled
      />

      <input
        type="text"
        value="std-kadane.py"
        class="rounded-md border border-gray-300 px-3 py-2 text-sm text-gray-700 bg-gray-50"
        disabled
      />

      <button
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
        type="button">
        Generate Solution
      </button>
    </div>

    <!-- Code Section -->
    <div class="flex-1 rounded-lg bg-gray-100 p-4 font-mono">
      <div class="text-sm text-gray-500 mb-2">std-kadane.py</div>
      <CodeAppearAnime :tokens="tokens" :code="pythonCode" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue';
import { ChevronDownIcon } from '@heroicons/vue/24/outline';
import CodeAppearAnime from './CodeAppearAnime.vue';

const pythonCode = ref(`def max_subarray_sum(arr):
    max_current = max_global = arr[0]
    for i in range(1, len(arr)):
        max_current = max(arr[i], max_current + arr[i])
        max_global = max(max_global, max_current)
    return max(0, max_global)

# Input handling
n = int(input())
arr = list(map(int, input().split()))
print(max_subarray_sum(arr))`);

const tokens = ref([
  { content: 'def', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'max_subarray_sum', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'arr', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: ':', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '    ', type: 'whitespace' }, { content: 'max_current', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'max_global', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'arr', type: 'variable' }, { content: '[', type: 'punctuation' }, { content: '0', type: 'number' }, { content: ']', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '    ', type: 'whitespace' }, { content: 'for', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'i', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: 'in', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'range', type: 'function' }, { content: '(', type: 'punctuation' }, { content: '1', type: 'number' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'len', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'arr', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: ':', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '        ', type: 'whitespace' }, { content: 'max_current', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'max', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'arr', type: 'variable' }, { content: '[', type: 'punctuation' }, { content: 'i', type: 'variable' }, { content: ']', type: 'punctuation' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'max_current', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '+', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'arr', type: 'variable' }, { content: '[', type: 'punctuation' }, { content: 'i', type: 'variable' }, { content: ']', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '        ', type: 'whitespace' }, { content: 'max_global', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'max', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'max_global', type: 'variable' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'max_current', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '    ', type: 'whitespace' }, { content: 'return', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'max', type: 'function' }, { content: '(', type: 'punctuation' }, { content: '0', type: 'number' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'max_global', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '# Input handling', type: 'comment' }, { content: '\n', type: 'whitespace' },
  { content: 'n', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'int', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'input', type: 'function' }, { content: '(', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'arr', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'list', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'map', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'int', type: 'function' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'input', type: 'function' }, { content: '(', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '.', type: 'punctuation' }, { content: 'split', type: 'function' }, { content: '(', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'print', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'max_subarray_sum', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'arr', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }
]);
</script>
