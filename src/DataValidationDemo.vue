<template>
  <div class="h-[100%] overflow-y-auto">
    <div class="text-sm text-gray-500 mb-2">Test Case Performance</div>
    <table class="min-w-full divide-y divide-gray-200">
      <thead class="bg-gray-50">
        <tr>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">
            Test Case
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">
            std-kadane.cpp
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">
            std-dp.cpp
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">
            std-kadane.py
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">
            std-dp.py
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">
            wrong-positive-only.py
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 tracking-wider">
            wrong-n-square.cpp
          </th>
        </tr>
      </thead>
      <tbody class="bg-white divide-y divide-gray-200">
        <!-- Summary row -->
        <tr>
          <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
            Summary
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500 items-center gap-1">
            <CheckCircleIcon class="w-5 h-5 text-green-600" />
            <span>AC</span>
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500 items-center gap-1">
            <CheckCircleIcon class="w-5 h-5 text-green-600" />
            <span>AC</span>
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500 items-center gap-1">
            <ExclamationCircleIcon class="w-5 h-5 text-yellow-500" />
            <span>Slow AC</span>
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500 items-center gap-1">
            <ExclamationCircleIcon class="w-5 h-5 text-yellow-500" />
            <span>Slow AC</span>
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500 items-center gap-1">
            <CheckCircleIcon class="w-5 h-5 text-green-600" />
            <span>WA</span>
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500 items-center gap-1">
            <CheckCircleIcon class="w-5 h-5 text-green-600" />
            <span>TLE</span>
          </td>
        </tr>
        <!-- 10 Test case rows -->
        <tr v-for="testCase in testCases" :key="testCase.number" class="row"
          :style="{ animationDelay: `${testCase.number * 0.05}s` }">
          <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
            {{ testCase.number }}
          </td>

          <td class="px-6 py-4 whitespace-nowrap text-sm">
            <div :class="timeClass(testCase.std_kadane_cpp.time)">
              {{ testCase.std_kadane_cpp.time }} ms
            </div>
            <div class="text-sm text-gray-500">
              {{ testCase.std_kadane_cpp.memory }} MB
            </div>
            <div v-if="testCase.std_kadane_cpp.status" :class="statusClass(testCase.std_kadane_cpp.status)">
              {{ testCase.std_kadane_cpp.status }}
            </div>
          </td>

          <td class="px-6 py-4 whitespace-nowrap text-sm">
            <div :class="timeClass(testCase.std_dp_cpp.time)">
              {{ testCase.std_dp_cpp.time }} ms
            </div>
            <div class="text-sm text-gray-500">
              {{ testCase.std_dp_cpp.memory }} MB
            </div>
            <div v-if="testCase.std_dp_cpp.status" :class="statusClass(testCase.std_dp_cpp.status)">
              {{ testCase.std_dp_cpp.status }}
            </div>
          </td>

          <td class="px-6 py-4 whitespace-nowrap text-sm">
            <div :class="timeClass(testCase.std_kadane_py.time)">
              {{ testCase.std_kadane_py.time }} ms
            </div>
            <div class="text-sm text-gray-500">
              {{ testCase.std_kadane_py.memory }} MB
            </div>
            <div v-if="testCase.std_kadane_py.status" :class="statusClass(testCase.std_kadane_py.status)">
              {{ testCase.std_kadane_py.status }}
            </div>
          </td>

          <td class="px-6 py-4 whitespace-nowrap text-sm">
            <div :class="timeClass(testCase.std_dp_py.time)">
              {{ testCase.std_dp_py.time }} ms
            </div>
            <div class="text-sm text-gray-500">
              {{ testCase.std_dp_py.memory }} MB
            </div>
            <div v-if="testCase.std_dp_py.status" :class="statusClass(testCase.std_dp_py.status)">
              {{ testCase.std_dp_py.status }}
            </div>
          </td>

          <td class="px-6 py-4 whitespace-nowrap text-sm">
            <div :class="timeClass(testCase.wrong_positive_only_py.time)">
              {{ testCase.wrong_positive_only_py.time }} ms
            </div>
            <div class="text-sm text-gray-500">
              {{ testCase.wrong_positive_only_py.memory }} MB
            </div>
            <div v-if="testCase.wrong_positive_only_py.status"
              :class="statusClass(testCase.wrong_positive_only_py.status)">
              {{ testCase.wrong_positive_only_py.status }}
            </div>
          </td>

          <td class="px-6 py-4 whitespace-nowrap text-sm">
            <div :class="timeClass(testCase.wrong_n_square_cpp.time)">
              {{ testCase.wrong_n_square_cpp.time }} ms
            </div>
            <div class="text-sm text-gray-500">
              {{ testCase.wrong_n_square_cpp.memory }} MB
            </div>
            <div v-if="testCase.wrong_n_square_cpp.status" :class="statusClass(testCase.wrong_n_square_cpp.status)">
              {{ testCase.wrong_n_square_cpp.status }}
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { CheckCircleIcon, ExclamationCircleIcon } from '@heroicons/vue/24/outline'

// Helper function to choose color class for time usage.
function timeClass(time) {
  if (time < 500) {
    return 'text-green-600'
  } else if (time < 1000) {
    return 'text-yellow-600'
  } else if (time < 2000) {
    return 'text-red-600'
  } else {
    return 'text-purple-600'
  }
}

// Helper function to set the color for the answer status.
function statusClass(status) {
  if (status === 'AC') {
    return 'text-green-600'
  } else if (status === 'WA') {
    return 'text-red-600'
  }
  return ''
}

// Generate 10 test case rows with values that align with the summary.
// - std-kadane.cpp and std-dp.cpp: fast (green) and AC.
// - std-kadane.py and std-dp.py: slower (yellow) but AC.
// - wrong-positive-only.py: fast with WA.
// - wrong-n-square.cpp: time >= 2000ms so no answer is provided.
const testCases = ref(
  Array.from({ length: 10 }, (_, i) => {
    // Use a simple pseudo-random sequence based on index
    const seed = i * 123456789;
    const rand = (min, max) => min + (seed % (max - min + 1));
    
    return {
      number: i + 1,
      std_kadane_cpp: { time: 350 + rand(0, 49), memory: "1.0", status: "AC" },
      std_dp_cpp: { time: 360 + rand(0, 49), memory: "1.0", status: "AC" },
      std_kadane_py: { time: 850 + rand(0, 49), memory: "1.0", status: "AC" },
      std_dp_py: { time: 870 + rand(0, 49), memory: "1.0", status: "AC" },
      wrong_positive_only_py: { 
        time: 320 + rand(0, 49), 
        memory: "1.0", 
        status: i >= 1 ? "WA" : "AC" 
      },
      wrong_n_square_cpp: { time: 2020 + rand(0, 49), memory: "1.0", status: "" }
    }
  })
)
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