<template>
  <div class="flex flex-col h-[100%] overflow-y-auto">
    <!-- Title -->
    <div class="text-lg font-semibold mb-4">Generate Incorrect Solution</div>

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
                <MenuItem v-slot="{ active }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm']">
                    <span class="truncate">solution.typ - Kadane's Algorithm</span>
                  </a>
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm']">
                    <span class="truncate">solution.typ - Dynamic Programming</span>
                  </a>
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm']">
                    <span class="truncate">std-kadane.cpp</span>
                  </a>
                </MenuItem>
              </div>
            </MenuItems>
          </transition>
        </Menu>
      </div>

      <div class="flex items-center gap-2">
        <input
          type="text"
          value="only consider subsequences containing only positive elements"
          class="flex-1 rounded-md border border-gray-300 px-3 py-2 text-sm text-gray-700 bg-gray-50"
          disabled
        />
        <button class="p-2 text-gray-500 hover:text-gray-700">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path d="M11 3a1 1 0 10-2 0v1a1 1 0 102 0V3zM15.657 5.757a1 1 0 00-1.414-1.414l-.707.707a1 1 0 001.414 1.414l.707-.707zM18 10a1 1 0 01-1 1h-1a1 1 0 110-2h1a1 1 0 011 1zM5.05 6.464A1 1 0 106.464 5.05l-.707-.707a1 1 0 00-1.414 1.414l.707.707zM5 10a1 1 0 01-1 1H3a1 1 0 110-2h1a1 1 0 011 1zM8 16v-1h4v1a2 2 0 11-4 0zM12 14c.015-.34.208-.646.477-.859a4 4 0 10-4.954 0c.27.213.462.519.476.859h4.002z" />
          </svg>
        </button>
      </div>

      <input
        type="text"
        value="wrong-positive-only.py"
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
      <div class="text-sm text-gray-500 mb-2">wrong-positive-only.py</div>
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
    max_sum = 0
    current_sum = 0
    for num in arr:
        if num > 0:
            current_sum += num
            max_sum = max(max_sum, current_sum)
        else:
            current_sum = 0
    return max_sum

# Input handling
n = int(input())
arr = list(map(int, input().split()))
print(max_subarray_sum(arr))`);

const tokens = ref([
  { content: 'def', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'max_subarray_sum', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'arr', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: ':', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '    ', type: 'whitespace' }, { content: 'max_sum', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: '0', type: 'number' }, { content: '\n', type: 'whitespace' },
  { content: '    ', type: 'whitespace' }, { content: 'current_sum', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: '0', type: 'number' }, { content: '\n', type: 'whitespace' },
  { content: '    ', type: 'whitespace' }, { content: 'for', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'num', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: 'in', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'arr', type: 'variable' }, { content: ':', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '        ', type: 'whitespace' }, { content: 'if', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'num', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '>', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: '0', type: 'number' }, { content: ':', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '            ', type: 'whitespace' }, { content: 'current_sum', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '+=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'num', type: 'variable' }, { content: '\n', type: 'whitespace' },
  { content: '            ', type: 'whitespace' }, { content: 'max_sum', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'max', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'max_sum', type: 'variable' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'current_sum', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '        ', type: 'whitespace' }, { content: 'else', type: 'keyword' }, { content: ':', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '            ', type: 'whitespace' }, { content: 'current_sum', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: '0', type: 'number' }, { content: '\n', type: 'whitespace' },
  { content: '    ', type: 'whitespace' }, { content: 'return', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'max_sum', type: 'variable' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: '# Input handling', type: 'comment' }, { content: '\n', type: 'whitespace' },
  { content: 'n', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'int', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'input', type: 'function' }, { content: '(', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'arr', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'list', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'map', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'int', type: 'function' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'input', type: 'function' }, { content: '(', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '.', type: 'punctuation' }, { content: 'split', type: 'function' }, { content: '(', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'print', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'max_subarray_sum', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'arr', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }
]);
</script>


