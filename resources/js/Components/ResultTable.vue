<script setup>

const props = defineProps({
  'data' : Object
})

</script>

<template>
  <div v-if="data.type === 'perDay' || data.type === 'perMonth' || data.type === 'perYear'" class="mt-4 lg:w-2/3 w-full mx-auto overflow-auto">
    <table class="table-auto w-full text-left whitespace-no-wrap">
      <thead>
        <tr>
          <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100 rounded-tl rounded-bl">年月日</th>
          <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">金額</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data.data" :key="item.date">
          <td class="px-4 py-3 border-b-2 border-gray-200">{{ item.date }}</td>
          <td class="px-4 py-3 border-b-2 border-gray-200">{{ item.total }}</td>
        </tr>
      </tbody>
    </table>
  </div>

  <div v-if="data.type === 'decile'" class="mt-4 lg:w-2/3 w-full mx-auto overflow-auto">
    <table class="table-auto w-full text-left whitespace-no-wrap">
      <thead>
        <tr>
          <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100 rounded-tl rounded-bl">グループ</th>
          <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">平均</th>
          <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">合計金額</th>
          <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">構成比</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data.data" :key="item.date">
          <td class="px-4 py-3 border-b-2 border-gray-200">{{ item.decile }}</td>
          <td class="px-4 py-3 border-b-2 border-gray-200">{{ item.average }}</td>
          <td class="px-4 py-3 border-b-2 border-gray-200">{{ item.totalPerGroup }}</td>
          <td class="px-4 py-3 border-b-2 border-gray-200">{{ item.totalRatio }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>