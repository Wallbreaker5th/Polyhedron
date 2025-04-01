<template>
  <div class="flex flex-col space-y-8 h-[100%] overflow-y-auto">
    <!-- Members Table -->
    <div>
      <div class="flex items-center justify-between mb-4">
        <h3 class="text-lg font-semibold">Team Members</h3>
        <button class="px-4 py-2 text-sm font-medium text-white bg-blue-600 rounded-md hover:bg-blue-500">
          Add Member
        </button>
      </div>
      <div class="overflow-x-auto border border-gray-200 rounded-lg">
        <table class="min-w-full divide-y divide-gray-200">
          <thead class="bg-gray-50">
            <tr>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Name
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Email
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Role
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Actions
              </th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr v-for="(member, index) in members" :key="member.email" class="row"
              :style="{ animationDelay: `${index * 0.05}s` }">
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                {{ member.name }}
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                {{ member.email }}
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                {{ member.role }}
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                <button class="text-blue-600 hover:text-blue-900">Edit</button>
                <span class="mx-2 text-gray-300">|</span>
                <button class="text-red-600 hover:text-red-900">Remove</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <!-- Roles and Permissions Table -->
    <div>
      <div class="flex items-center justify-between mb-4">
        <h3 class="text-lg font-semibold">Roles and Permissions</h3>
        <button class="px-4 py-2 text-sm font-medium text-white bg-blue-600 rounded-md hover:bg-blue-500">
          Add Role
        </button>
      </div>
      <div class="overflow-hidden border border-gray-200 rounded-lg">
        <table class="min-w-full divide-y divide-gray-200">
          <thead class="bg-gray-50">
            <tr>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Role
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Permissions
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Actions
              </th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr class="row" :style="{ animationDelay: `0.05s` }">
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                Problem Setter
              </td>
              <td class="px-6 py-4 text-sm text-gray-500">
                <ul class="list-disc list-inside">
                  <li>Read/Write problem statements</li>
                  <li>Submit code for judging</li>
                  <li>Create test data</li>
                </ul>
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                <button class="text-blue-600 hover:text-blue-900">Edit</button>
                <span class="mx-2 text-gray-300">|</span>
                <button class="text-red-600 hover:text-red-900">Remove</button>
              </td>
            </tr>
            <tr class="row" :style="{ animationDelay: `0.1s` }">
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                Tester
              </td>
              <td class="px-6 py-4 text-sm text-gray-500">
                <ul class="list-disc list-inside">
                  <li>Read problem statements</li>
                  <li>Submit code for judging</li>
                  <li>View test results</li>
                </ul>
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                <button class="text-blue-600 hover:text-blue-900">Edit</button>
                <span class="mx-2 text-gray-300">|</span>
                <button class="text-red-600 hover:text-red-900">Remove</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const members = ref([
  { name: 'John Doe', email: 'john@example.com', role: 'Admin' },
  { name: 'Jane Doe', email: 'jane@example.com', role: 'Problem Setter' },
  { name: 'Alice Doe', email: 'alice@example.com', role: 'Tester' },
  { name: 'Bob Doe', email: 'bob@example.com', role: 'Tester' },
]);

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
