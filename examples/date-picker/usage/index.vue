<!-- 该脚本为自动生成，如有需要请在 /script/generate-usage/index.js 中调整 -->
<template>
  <base-usage :code="usageCode" :config-list="configList" :panel-list="panelList" @PanelChange="onPanelChange">
    <template #datePicker="{ configProps }"><t-date-picker v-bind="configProps" /></template>
    <template #dateRangePicker="{ configProps }"><t-date-range-picker v-bind="configProps" /></template>
  </base-usage>
</template>

<script setup lang="jsx">
/* eslint-disable */
import { ref, onMounted } from 'vue';
import datePickerConfigJson from './date-picker-props.json';

import dateRangePickerConfigJson from './date-range-picker-props.json';

const configList = ref(datePickerConfigJson);
const panelList = [
  { label: 'datePicker', value: 'datePicker', config: datePickerConfigJson },
  { label: 'dateRangePicker', value: 'dateRangePicker', config: dateRangePickerConfigJson },
];

const usageCodeMap = {
  datePicker: '<t-date-picker v-bind="configProps" />',
  dateRangePicker: '<t-date-range-picker v-bind="configProps" />',
};
const usageCode = ref(`<template>${usageCodeMap[panelList[0].value].trim()}</template>`);

function onPanelChange(panel) {
  configList.value = panelList.find((item) => item.value === panel).config;
  usageCode.value = `<template>${usageCodeMap[panel].trim()}</template>`;
}
</script>
