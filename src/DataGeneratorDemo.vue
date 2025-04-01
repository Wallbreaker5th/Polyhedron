<template>
  <div class="flex flex-col h-[100%] overflow-y-auto">
    <!-- Title -->
    <div class="text-lg font-semibold mb-4">Generate Test Data</div>

    <!-- Form Section -->
    <div class="flex flex-col gap-4 mb-6">
      <div class="flex items-center gap-2">
        <span class="text-sm text-gray-500">Reference:</span>
        <Menu as="div" class="relative inline-block text-left" multiple>
          <div>
            <MenuButton
              class="inline-flex w-full justify-center gap-x-1.5 rounded-md bg-white px-3 py-2 text-sm font-medium text-gray-700 shadow-sm ring-1 ring-inset ring-gray-200 hover:bg-gray-50">
              wrong-positive-only.py
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
                <MenuItem v-slot="{ active }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm']">
                    <span class="truncate">std-dp.cpp</span>
                  </a>
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm']">
                    <span class="truncate">std-kadane.py</span>
                  </a>
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm']">
                    <span class="truncate">std-dp.py</span>
                  </a>
                </MenuItem>
                <MenuItem v-slot="{ active, selected }">
                  <a :class="[active ? 'bg-gray-100 text-gray-900' : 'text-gray-700', 'group flex items-center px-4 py-2 text-sm', 'font-semibold']">
                    <span class="mr-2 text-green-500">
                      <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                        <path fill-rule="evenodd" d="M16.704 4.153a.75.75 0 01.143 1.052l-8 10.5a.75.75 0 01-1.127.075l-4.5-4.5a.75.75 0 011.06-1.06l3.97 3.97 7.473-9.819a.75.75 0 011.05-.143z" clip-rule="evenodd" />
                      </svg>
                    </span>
                    <span class="truncate">wrong-positive-only.py</span>
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
          value="hack this code with uniform random distribution"
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
        value="gen-uniform-random.py"
        class="rounded-md border border-gray-300 px-3 py-2 text-sm text-gray-700 bg-gray-50"
        disabled
      />

      <button
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
        type="button">
        Generate Test Data
      </button>
    </div>

    <!-- Code Section -->
    <div class="flex-1 rounded-lg bg-gray-100 p-4 font-mono">
      <div class="text-sm text-gray-500 mb-2">gen-uniform-random.py</div>
      <CodeAppearAnime :tokens="tokens" :code="pythonCode" />
    </div>

    <!-- Table Section -->
    <div class="mt-6">
      <div class="text-sm text-gray-500 mb-2">New Test Cases Added</div>
      <table class="min-w-full divide-y divide-gray-200">
        <thead class="bg-gray-50">
          <tr>
            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">n</th>
            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">a_max</th>
            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">a_min</th>
          </tr>
        </thead>
        <tbody class="bg-white divide-y divide-gray-200">
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">100000</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">1e9</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">-1e9</td>
          </tr>
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">100000</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">1e9</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">-100</td>
          </tr>
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">100000</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">1e9</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">-1000</td>
          </tr>
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">100000</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">1000</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">-1000</td>
          </tr>
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">100000</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">1000</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">-1e9</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue';
import { ChevronDownIcon } from '@heroicons/vue/24/outline';
import CodeAppearAnime from './CodeAppearAnime.vue';

const pythonCode = ref(`from polyhedron_gen import *

n = get_param("n")
a_max = get_param("a_max")
a_min = get_param("a_min")
a = random_list(n, uniform_int(a_min, a_max))

write(a.len(), "\\n")
write(a)`);

const tokens = ref([
  { content: 'from', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: 'polyhedron_gen', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: 'import', type: 'keyword' }, { content: ' ', type: 'whitespace' }, { content: '*', type: 'operator' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'n', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'get_param', type: 'function' }, { content: '(', type: 'punctuation' }, { content: '"n"', type: 'string' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'a_max', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'get_param', type: 'function' }, { content: '(', type: 'punctuation' }, { content: '"a_max"', type: 'string' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'a_min', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'get_param', type: 'function' }, { content: '(', type: 'punctuation' }, { content: '"a_min"', type: 'string' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'a', type: 'variable' }, { content: ' ', type: 'whitespace' }, { content: '=', type: 'operator' }, { content: ' ', type: 'whitespace' }, { content: 'random_list', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'n', type: 'variable' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'uniform_int', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'a_min', type: 'variable' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: 'a_max', type: 'variable' }, { content: ')', type: 'punctuation' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: '\n', type: 'whitespace' },
  { content: 'write', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'a.len()', type: 'function' }, { content: ',', type: 'punctuation' }, { content: ' ', type: 'whitespace' }, { content: '"\\n"', type: 'string' }, { content: ')', type: 'punctuation' }, { content: '\n', type: 'whitespace' },
  { content: 'write', type: 'function' }, { content: '(', type: 'punctuation' }, { content: 'a', type: 'variable' }, { content: ')', type: 'punctuation' }
]);
</script>
