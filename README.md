# vt-pagination

## Installation

```bash
yarn add vt-paginate
```

## Usage

```vue
<template>
  <div>
    <VTPagination
      v-slot="{
        start,
        end,
        totalItems,
        nextPage,
        prevPage,
        pages,
        isActivePage,
        isEllipsis,
      }"
      :totalItems="121"
      :maxVisiblePages="4"
      :itemsPerPage="5"
      v-model="myPage"
      @change-page="fetchPage"
    >
      <div
        class="bg-white px-4 py-3 flex items-center justify-between border-t border-gray-200 sm:px-6"
      >
        <div class="flex-1 flex items-center justify-between">
          <div>
            <p class="text-sm leading-5 text-gray-700">
              Showing
              <span class="font-medium">{{ start }}</span>
              to
              <span class="font-medium">{{ end }}</span>
              of
              <span class="font-medium">{{ totalItems }}</span>
              results
            </p>
          </div>
          <div>
            <nav class="relative z-0 inline-flex shadow-sm">
              <a
                href="#"
                @click="prevPage"
                class="relative inline-flex items-center px-2 py-2 rounded-l-md border border-gray-300 bg-white text-sm leading-5 font-medium text-gray-500 hover:text-gray-400 focus:z-10 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-100 active:text-gray-500 transition ease-in-out duration-150"
                aria-label="Previous"
              >
                <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                  <path
                    fill-rule="evenodd"
                    d="M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z"
                    clip-rule="evenodd"
                  />
                </svg>
              </a>
              <span
                v-show="isEllipsis.start"
                class="-ml-px relative inline-flex items-center px-4 py-2 border border-gray-300 bg-white text-sm leading-5 font-medium text-gray-700"
                >...</span
              >
              <VTPage
                v-for="page in pages"
                :key="page"
                :page="page"
                :class="
                  isActivePage(page)
                    ? 'bg-gray-100 text-gray-700 transition ease-in-out duration-150'
                    : ''
                "
                class="-ml-px relative inline-flex items-center px-4 py-2 border border-gray-300 bg-white text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:z-10 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-100 active:text-gray-700 transition ease-in-out duration-150"
                >{{ page }}</VTPage
              >
              <span
                v-show="isEllipsis.end"
                class="-ml-px relative inline-flex items-center px-4 py-2 border border-gray-300 bg-white text-sm leading-5 font-medium text-gray-700"
                >...</span
              >
              <a
                href="#"
                @click="nextPage"
                class="-ml-px relative inline-flex items-center px-2 py-2 rounded-r-md border border-gray-300 bg-white text-sm leading-5 font-medium text-gray-500 hover:text-gray-400 focus:z-10 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-100 active:text-gray-500 transition ease-in-out duration-150"
                aria-label="Next"
              >
                <svg class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                  <path
                    fill-rule="evenodd"
                    d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
                    clip-rule="evenodd"
                  />
                </svg>
              </a>
            </nav>
          </div>
        </div>
      </div>
    </VTPagination>
  </div>
</template>

<script>
import { VTPage, VTPagination } from "vt-pagination";
export default {
  components: {
    VTPagination,
    VTPage,
  },
  data() {
    return {
      myPage: 1,
    };
  },
  methods: {
    async fetchPage(p) {
      // fetch page from api
    },
  },
};
</script>
```
