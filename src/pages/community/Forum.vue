<template>
  <div class="flex h-screen overflow-hidden">

    <!-- Sidebar -->
    <Sidebar :sidebarOpen="sidebarOpen" @close-sidebar="sidebarOpen = false" />

    <!-- Content area -->
    <div class="relative flex flex-col flex-1 overflow-y-auto overflow-x-hidden">
      
      <!-- Site header -->
      <Header :sidebarOpen="sidebarOpen" @toggle-sidebar="sidebarOpen = !sidebarOpen" />

      <main>
        <div class="px-4 sm:px-6 lg:px-8 py-8 md:py-0 w-full max-w-9xl mx-auto">

          <div class="xl:flex">

            <!-- Left + Middle content -->
            <div class="md:flex flex-1">

              <!-- Left content -->
              <ForumLeftContent />

              <!-- Middle content -->
              <div class="flex-1 md:ml-8 xl:mx-4 2xl:mx-8">
                <div class="md:py-8">

                  <!-- Buttons group -->
                  <div class="mb-4">
                    <div class="w-full flex flex-wrap -space-x-px">
                        <button class="btn grow bg-white border-slate-200 text-indigo-500 rounded-none first:rounded-l last:rounded-r">Popular</button>
                        <button class="btn grow bg-white border-slate-200 hover:bg-slate-50 text-slate-600 rounded-none first:rounded-l last:rounded-r">Newest</button>
                        <button class="btn grow bg-white border-slate-200 hover:bg-slate-50 text-slate-600 rounded-none first:rounded-l last:rounded-r">Following</button>
                    </div>
                  </div>

                  <!-- Forum entries -->
                  <div class="space-y-2">
                    <ForumEntries />
                  </div>

                  <!-- Pagination -->
                  <div class="mt-6 text-right">
                    <nav class="inline-flex" role="navigation" aria-label="Navigation">
                      <ul class="flex justify-center">
                        <li class="ml-3 first:ml-0">
                          <a class="btn bg-white border-slate-200 text-slate-300 cursor-not-allowed" href="#0" disabled>&lt;- Previous</a>
                        </li>
                        <li class="ml-3 first:ml-0">
                          <a class="btn bg-white border-slate-200 hover:border-slate-300 text-indigo-500" href="#0">Next -&gt;</a>
                        </li>
                      </ul>
                    </nav>
                  </div>

                </div>
              </div>

            </div>

            <!-- Right content -->
            <ForumRightContent />

          </div>
          
        </div>
      </main>

    </div> 

  </div>
</template>

<script>
import { ref } from 'vue'
import Sidebar from '../../partials/Sidebar.vue'
import Header from '../../partials/Header.vue'
import ForumLeftContent from '../../partials/community/ForumLeftContent.vue'
import ForumEntries from '../../partials/community/ForumEntries.vue'
import ForumRightContent from '../../partials/community/ForumRightContent.vue'

export default {
  name: 'Forum',
  components: {
    Sidebar,
    Header,
    ForumLeftContent,
    ForumEntries,
    ForumRightContent,
  }, 
  setup() {

    const sidebarOpen = ref(false)

    return {
      sidebarOpen,
    }  
  }
}
</script>