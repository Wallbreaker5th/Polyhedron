<template>
  <div class="min-h-screen bg-gray-50 text-gray-900">
    <!-- Navigation -->
    <div class="relative">
      <Disclosure as="nav" class="bg-white shadow-sm relative z-10" v-slot="{ open }">
        <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
          <div class="flex h-16 items-center justify-between">
            <div class="flex items-center">
              <div class="flex-shrink-0">
                <div class="text-2xl font-bold text-blue-600">Polyhedron</div>
              </div>
              <div class="hidden md:block ml-10">
                <div class="flex space-x-4">
                  <a href="#features"
                    class="text-gray-500 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium">
                    Features
                  </a>
                  <a href="#pricing" class="text-gray-500 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium">
                    Pricing
                  </a>
                  <a href="#cta" class="text-gray-500 hover:text-gray-900 px-3 py-2 rounded-md text-sm font-medium">
                    Join Waitlist
                  </a>
                </div>
              </div>
            </div>

            <!-- Mobile menu button -->
            <div class="-mr-2 flex md:hidden">
              <DisclosureButton
                class="inline-flex items-center justify-center p-2 rounded-md text-gray-500 hover:text-gray-900 hover:bg-gray-100">
                <span class="sr-only">Open main menu</span>
                <Bars3Icon v-if="!open" class="block h-6 w-6" aria-hidden="true" />
                <XMarkIcon v-else class="block h-6 w-6" aria-hidden="true" />
              </DisclosureButton>
            </div>
          </div>
        </div>

        <!-- Mobile menu panel -->
        <TransitionRoot appear :show="open" as="template">
          <DisclosurePanel class="absolute w-full md:hidden bg-white shadow-lg">
            <TransitionChild
              as="template"
              enter="transition ease-out duration-200"
              enter-from="opacity-0 -translate-y-1"
              enter-to="opacity-100 translate-y-0"
              leave="transition ease-in duration-150"
              leave-from="opacity-100 translate-y-0"
              leave-to="opacity-0 -translate-y-1"
            >
              <div class="space-y-1 px-2 pb-3 pt-2">
                <TransitionChild
                  v-for="(item, index) in [
                    { href: '#features', text: 'Features' },
                    { href: '#pricing', text: 'Pricing' },
                    { href: '#cta', text: 'Join Waitlist' }
                  ]"
                  :key="index"
                  as="template"
                  enter="transition ease-out duration-200"
                  enter-from="opacity-0 translate-x-2"
                  enter-to="opacity-100 translate-x-0"
                  leave="transition ease-in duration-150"
                  leave-from="opacity-100 translate-x-0"
                  leave-to="opacity-0 translate-x-2"
                  :style="{ transitionDelay: `${50 * index}ms` }"
                >
                  <DisclosureButton as="a" :href="item.href"
                    class="block px-3 py-2 rounded-md text-base font-medium text-gray-500 hover:text-gray-900 hover:bg-gray-50"
                  >
                    {{ item.text }}
                  </DisclosureButton>
                </TransitionChild>
              </div>
            </TransitionChild>
          </DisclosurePanel>
        </TransitionRoot>
      </Disclosure>

      <!-- Hero Section -->
      <div class="relative isolate px-6 pt-14 lg:px-8">
        <div class="mx-auto max-w-4xl pb-32 pt-8 sm:pb-40 sm:pt-14">
          <div class="text-center">
            <img src="/logo.svg" alt="Polyhedron Logo" class="w-30 h-30 mx-auto mb-8">
            <h1
              class="text-4xl font-bold tracking-tight sm:text-6xl bg-gradient-to-r from-blue-600 to-blue-600 bg-clip-text text-transparent">
              <span class="text-4xl sm:text-6xl">C</span><span class="text-2xl sm:text-4xl">ompetitive-</span><span class="text-4xl sm:text-6xl">P</span><span class="text-2xl sm:text-4xl">rogramming</span> Problem Creation Revolutionized
            </h1>
            <p class="mt-6 text-xl leading-8 text-gray-600">
              AI-powered platform for generating competition-grade programming problems with complete toolchain support.
            </p>
            <div class="mt-10 flex items-center justify-center gap-x-6">
              <a href="#cta"
                class="rounded-full bg-blue-600 px-8 py-4 text-lg font-semibold text-white hover:bg-blue-500 transition-all">
                Try Polyhedron
              </a>
              <a href="#features" class="text-sm font-semibold leading-6 text-gray-900 hover:text-blue-600">
                Learn more <span aria-hidden="true">→</span>
              </a>
            </div>
            <div class="mt-16 flex justify-center">
              <div class="grid grid-cols-2 md:grid-cols-4 gap-8 text-sm text-gray-600">
                <div class="flex items-center gap-2">
                  <span class="text-blue-600 font-bold">10+</span> Languages Supported
                </div>
                <div class="flex items-center gap-2">
                  <span class="text-blue-600 font-bold">100%</span> Open Standards
                </div>
                <div class="flex items-center gap-2">
                  <span class="text-blue-600 font-bold">95%</span> Faster Problem Creation
                </div>
                <div class="flex items-center gap-2">
                  <span class="text-blue-600 font-bold">24/7</span> AI Assistance
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- #4B82C2 #FCB911 #B12B1A from top left to bottom right -->
        <div
          class="absolute inset-x-0 top-[calc(50%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(50%-30rem)]">
          <div class="relative left-[calc(20%+3rem)] aspect-[2/3] w-[calc(10%+12rem)] -translate-x-4/5 bg-[#4B82C2] opacity-20">
          </div>
        </div>
        <div
          class="absolute inset-x-0 top-[calc(90%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(90%-30rem)]">
          <div class="relative left-[calc(60%+3rem)] aspect-[2/3] w-[calc(10%+12rem)] -translate-x-4/5 bg-[#FCB911] opacity-20">
          </div>
        </div>
        <div
          class="absolute inset-x-0 top-[calc(70%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(70%-30rem)]">
          <div class="relative left-[calc(100%+3rem)] aspect-[2/3] w-[calc(10%+12rem)] -translate-x-4/5 bg-[#B12B1A] opacity-20">
          </div>
        </div>
      </div>
    </div>

    <!-- Features Section -->
    <div id="features" class="py-22 sm:py-32 bg-white">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-2xl lg:text-center">
          <h2
            class="text-3xl font-bold tracking-tight sm:text-4xl bg-gradient-to-r from-green-600 to-blue-600 bg-clip-text text-transparent pb-1">
            Powerful Features for Problem Creators
          </h2>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            Everything you need to create world-class programming problems, from initial concept to competition-ready
            packages
          </p>
        </div>
        <div class="mx-auto mt-16 max-w-2xl sm:mt-20 lg:mt-24 lg:max-w-none">
          <TabGroup as="div" class="lg:grid lg:grid-cols-12 lg:gap-x-8">
            <!-- Feature List as Tabs -->
            <div class="lg:col-span-3">
              <TabList class="flex overflow-x-auto pb-4 lg:block lg:space-y-2 lg:pb-0">
                <Tab v-for="feature in features" :key="feature.name" v-slot="{ selected }" as="template">
                  <div :class="[
                    'group relative flex-1 lg:flex-none rounded-lg p-2 cursor-pointer transition-colors',
                    selected
                      ? 'bg-blue-50 border-2 border-blue-600'
                      : 'hover:bg-gray-50 border-2 border-transparent'
                  ]">
                    <div class="flex items-center">
                      <div class="shrink-0 p-1.5 rounded-lg" :class="selected ? 'bg-blue-600' : 'bg-gray-600'">
                        <component :is="feature.icon" class="h-4 w-4 text-white" />
                      </div>
                      <div class="ml-2">
                        <h3 class="text-xs font-semibold text-gray-900">{{ feature.name }}</h3>
                      </div>
                    </div>
                  </div>
                </Tab>
              </TabList>
            </div>

            <!-- Feature Demo Panels -->
            <div class="mt-8 lg:col-span-9 lg:mt-0">
              <TabPanels class="p-2 pt-0">
                <TabPanel v-for="(feature, _) in features" :key="feature.name" class="min-h-[400px]">
                  <div class="mb-6">
                    <h3 class="text-xl font-bold text-gray-900">{{ feature.name }}</h3>
                    <p class="mt-2 text-gray-600">{{ feature.description }}</p>
                  </div>
                  <div
                    class="rounded-lg bg-white shadow-[inset_2px_4px_6px_-1px_rgba(0,0,0,0.1),inset_0_2px_4px_-2px_rgba(0,0,0,0.1)] border-2 border-gray-100 w-full max-w-[800px] h-[400px] md:h-[500px] lg:h-[600px] p-4 sm:p-6">
                    <component :is="feature.demo" />
                  </div>
                </TabPanel>
              </TabPanels>
            </div>
          </TabGroup>
        </div>
      </div>
    </div>

    <!-- Pricing Section -->
    <div id="pricing" class="bg-gray-50 py-24 sm:py-32">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-2xl text-center">
          <h2
            class="text-3xl font-bold tracking-tight sm:text-4xl bg-gradient-to-r from-purple-600 to-blue-600 bg-clip-text text-transparent pb-1">
            Simple Pricing
          </h2>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            Choose the plan that fits your needs. Start for free, upgrade when you're ready.
          </p>
        </div>
        <div class="mt-16 flex justify-center">
          <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3">
            <div v-for="plan in pricingPlans" :key="plan.name" class="flex flex-col rounded-2xl bg-white shadow-xl"
              :class="plan.highlight ? 'ring-1 ring-blue-600' : 'ring-1 ring-gray-900/5'">
              <div class="p-8 sm:p-10">
                <h3 class="text-lg font-semibold leading-8 tracking-tight text-blue-600">{{ plan.name }}</h3>
                <div class="mt-4 flex items-baseline text-5xl font-bold tracking-tight text-gray-900">
                  {{ plan.price }}<span v-if="plan.price !== 'Custom'"
                    class="text-lg font-semibold leading-8 text-gray-600">/month</span>
                </div>
                <p class="mt-6 text-base leading-7 text-gray-600">{{ plan.tagline }}</p>
                <ul role="list" class="mt-8 space-y-3 text-sm leading-6 text-gray-600">
                  <li v-for="feature in plan.features" :key="feature" class="flex gap-x-3">
                    <CheckIcon class="h-6 w-5 flex-none text-blue-600" aria-hidden="true" />
                    {{ feature }}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- CTA Section -->
    <div id="cta" class="bg-white py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="mx-auto max-w-4xl text-center">
          <h2
            class="text-3xl font-bold tracking-tight sm:text-4xl bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent pb-1">
            Start Creating Better Problems Today
          </h2>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            Join our waitlist to experience the future of competitive-programming problem creation. Be the first to know when we
            launch.
          </p>
          <div class="mt-10 flex flex-col sm:flex-row items-center justify-center gap-4 sm:gap-x-4">
            <input type="email" placeholder="Enter your email" v-model="mail"
              class="w-full sm:w-auto rounded-full border border-gray-300 px-4 sm:px-6 py-3 sm:py-4 text-base sm:text-lg focus:outline-none focus:ring-2 focus:ring-blue-600" />
            <button
              class="w-full sm:w-auto rounded-full bg-blue-600 px-6 sm:px-8 py-3 sm:py-4 text-base sm:text-lg font-semibold text-white hover:bg-blue-500 transition-colors"
              @click="joinWaitlistOnClick">
              Join Waitlist
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer -->
    <footer class="border-t border-gray-200">
      <div class="mx-auto max-w-7xl px-6 py-12 md:flex md:items-center md:justify-between lg:px-8">
        <div class="mt-8 md:order-1 md:mt-0">
          <p class="text-center text-sm leading-5 text-gray-500">&copy; 2024 Polyhedron. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Disclosure, DisclosureButton, DisclosurePanel, TabGroup, TabList, Tab, TabPanels, TabPanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon, DocumentTextIcon, CodeBracketIcon, GlobeAltIcon, XCircleIcon, CpuChipIcon, ShieldCheckIcon, LockClosedIcon, ArrowUpOnSquareIcon, CheckIcon } from '@heroicons/vue/24/outline'
import { TransitionRoot, TransitionChild } from '@headlessui/vue'
import StatementExpansionDemo from './StatementExpansionDemo.vue'
import SolutionGenerationDemo from './SolutionGenerationDemo.vue'
import MaterialGenerationDemo from './MaterialGenerationDemo.vue'
import IncorrectSolutionsDemo from './IncorrectSolutionsDemo.vue'
import DataGeneratorDemo from './DataGeneratorDemo.vue'
import DataValidationDemo from './DataValidationDemo.vue'
import AccessControlDemo from './AccessControlDemo.vue'
import ExportDemo from './ExportDemo.vue'
import Clarity from '@microsoft/clarity'

const mail = ref('')

const features = [
  {
    name: 'Problem Statement Expansion',
    description: 'Transform brief ideas into fully formatted competition-grade problem statements. And enjoy real-time previews powered by Typst',
    icon: DocumentTextIcon,
    demo: StatementExpansionDemo,
  },
  {
    name: 'Solution Generation',
    description: 'Generate detailed solutions and ready-to-use presentation decks automatically',
    icon: CodeBracketIcon,
    demo: SolutionGenerationDemo,
  },
  {
    name: 'Material Generation in Multiple Languages',
    description: 'Produce standard solutions, checker, validator, and interactors in multiple languages',
    icon: GlobeAltIcon,
    demo: MaterialGenerationDemo,
  },
  {
    name: 'Incorrect Solutions',
    description: 'Automatically generate common incorrect approaches for comprehensive testing',
    icon: XCircleIcon,
    demo: IncorrectSolutionsDemo,
  },
  {
    name: 'Data Generator Creation',
    description: 'Build robust test data generators based on problem constraints and solutions',
    icon: CpuChipIcon,
    demo: DataGeneratorDemo,
  },
  {
    name: 'Data Validation',
    description: 'Automated verification of data correctness and strength testing for robust problem sets',
    icon: ShieldCheckIcon,
    demo: DataValidationDemo,
  },
  {
    name: 'Access Control',
    description: 'Granular permissions management for secure problem creation and collaboration',
    icon: LockClosedIcon,
    demo: AccessControlDemo,
  },
  {
    name: 'Export & Integration',
    description: 'Export problems to multiple formats and directly upload to CMS, UOJ, Polygon, and other platforms',
    icon: ArrowUpOnSquareIcon,
    demo: ExportDemo,
  },
]

const pricingPlans = [
  {
    name: 'Free',
    price: '$0',
    tagline: 'Perfect for getting started',
    features: [
      'Basic problem creation',
      'Limited AI assistance',
      'Community support',
    ],
    highlight: false
  },
  {
    name: 'Pro',
    price: '$19',
    tagline: 'For serious problem creators',
    features: [
      'Interactive and run-twice problems',
      'More AI assistance',
      'Team collaboration',
      'Larger resource limits'
    ],
    highlight: true
  },
  {
    name: 'Enterprise',
    price: 'Custom',
    tagline: 'For organizations and competitions',
    features: [
      'All Pro features',
      'The most intelligent models',
      'Customizable judgers',
      'SLA and support',
      'Local deployment'
    ],
    highlight: false
  }
]

function joinWaitlistOnClick() {
  Clarity.event('join-waitlist')

  const aprilFoolsDate = new Date('2025-04-01T14:00:00');
  const currentDate = new Date();

  if (currentDate > aprilFoolsDate) {
    alert('April Fools! 🎉\nThis was just a joke, but thanks for your interest!');
  } else {
    if (!mail.value || !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(mail.value)) {
      alert('Please enter a valid email address');
    } else {
      alert('You have joined the waitlist! 🎉\nWe will notify you when we launch.');
    }
  }
}
</script>

<style scoped>
.bg-gradient-to-r {
  background-size: 200% 200%;
  animation: gradient-shift 8s ease infinite;
}

@keyframes gradient-shift {
  0% {
    background-position: 0% 50%;
  }

  50% {
    background-position: 100% 50%;
  }

  100% {
    background-position: 0% 50%;
  }
}
</style>