<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: 'Jobs',
  meta: [
    {
      name: 'Job Listings',
      content: 'The number one website for finding jobs in Solar',
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle text="Jobs in Solar" class="capitalize" />
    </PageHeader>
    <PageBody>
      <ContentList v-slot="{ list }" path="/job">
        <PageSection v-for="article in list" :key="article._path">
          <div
            class="block hover:no-underline p-6 flex space-x-6 rounded border border-gray-900/10 dark:border-gray-50/[0.2]"
          >
            <div class="mt-1 text-slate-600 dark:text-gray-400 text-right">
              <div>{{ article.date }}</div>
              <Anchor
                class="text-sm flex items-center justify-end space-x-1"
                :href="`https://www.github.com/${article.author}`"
              >
                <icon-mdi:github-face class="text-xs" />
                <span>{{ article.author }}</span>
              </Anchor>
            </div>
            <div class="flex flex-col">
              <div
                class="text-xl font-semibold text-slate-800 dark:text-gray-50"
              >
                {{ article.title }}
              </div>
              <div class="text-slate-700 dark:text-gray-300 mb-1">
                {{ article.description }}
              </div>
              <div class="flex">
                <Anchor
                  class="text-sm flex space-x-1 items-center text-primary-500"
                  :to="article._path"
                >
                  <span>Learn More</span>
                  <icon:ic:baseline-arrow-right-alt class="text-sm" />
                </Anchor>
              </div>
            </div>
          </div>
        </PageSection>
      </ContentList>
    </PageBody>
  </PageWrapper>
</template>
