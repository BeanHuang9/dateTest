<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import FormPicker from '@/components/FormPicker.vue';
import FormTime from '@/components/FormTime.vue';
import HandleTable from '@/components/HandleTable.vue';
import NormalTable from '@/components/NormalTable.vue';
// import AgencyCalendar from '@/components/AgencyCalendar.vue';

import DateParts from '@/components/DateParts.vue';

const areaList: Ref<string[]> = ref(['特殊設定', '常態設定']);
const currentArea: Ref<string> = ref('特殊設定');

const eventTabs: Ref<string[]> = ref(['診次調整', '特殊項目', '指定企業']);
const selectedTab: Ref<string> = ref('診次調整');

// const normalTabs: Ref<string[]> = ref(['一般檢查', '特殊檢查', '價格時段']);

const isOpen = ref(false);
const isOpen1 = ref(false);
const isOpenSpecial = ref(false);
const searchTerm = ref('');
const items = ref([
	'英屬維京群島商華敦國際有限公司台灣分公司',
	'康美包紙盒包裝股份有限公司',
	'艾比斯馬特國際股份有限公司',
	'優志旺股份有限公司',
	'台灣山葉音樂股份有限公司',
]);

const planItems = ref(['方案A', '方案B', '方案C-腸胃道', '方案C-心血管', '方案D', '方案E']);
const specialItems = ref([
	'心電心音檢查 ( )',
	'無痛胃鏡檢查(70歲以上需事前評估) ( Panendoscopy exam )',
	'心臟超音波檢查 ( Cardiac sonogram exam )',
	'無痛內視鏡CO2充氣系統 ( CO2 inflatable system for painless endoscope )',
	'心臟冠狀動脈鈣化指數分析 ( 心臟冠狀動脈鈣化指數分析 )',
	'攝護腺磁振造影檢查 ( 攝護腺腫瘤核磁共振篩檢 )',
	'血液重金屬檢測 ( heavy metal blood test )',
]);

const filteredItems = ref(items.value);

const toggleDropdown = () => {
	isOpen.value = !isOpen.value;
};

const planDropdown = () => {
	isOpen1.value = !isOpen1.value;
};

const specialDropdown = () => {
	isOpenSpecial.value = !isOpenSpecial.value;
};

const filterItems = () => {
	const lowerCaseSearchTerm = searchTerm.value.toLowerCase();

	filteredItems.value = items.value.filter((item) => item.toLowerCase().includes(lowerCaseSearchTerm));
};

onMounted(() => {
	filterItems();
});
</script>
<template>
	<div class="py-28">
		<div class="w-2/3 m-auto flex justify-start font-semibold tracking-2.25 text-lg">
			<button
				v-for="(item, idx) in areaList"
				:key="idx"
				:class="{ 'bg-[#ECF4F7]': currentArea === item }"
				class="rounded-t-2xl px-6 py-3 border-2 border-b-0 border-[#cccccc] shadow mr-1 text-[#313131] text-base"
				@click="currentArea = item"
			>
				{{ item }}
			</button>
		</div>
		<!-- py-4 w-2/3 m-auto flex justify-center items-center bg-[#ECF4F7] -->

		<div class="m-auto flex justify-center items-center">
			<div class="h-5/6 w-full text-4xl">
				<div class="tab-content">
					<div v-if="currentArea === '特殊設定'" class="tab-pane">
						<div class="w-2/3 m-auto bg-[#ECF4F7] border-2 border-b-0 border-solid border-[#cccccc]">
							<div class="px-8 py-6">
								<div class="set-content leading-normal">
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">事件</div>
										<!-- <div class="flex items-center me-4">
										<input
											id="radio-1"
											checked
											type="radio"
											value=""
											name="colored-radio"
											class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
										/>
										<label for="radio-1" class="ms-2 text-sm font-medium dark:text-gray-300">診次調整</label>
									</div>
									<div class="flex items-center me-4">
										<input
											id="radio-2"
											type="radio"
											value=""
											name="colored-radio"
											class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
										/>
										<label for="radio-2" class="ms-2 text-sm font-medium dark:text-gray-300">特殊項目</label>
									</div>
									<div class="flex items-center me-4">
										<input
											id="radio-3"
											type="radio"
											value=""
											name="colored-radio"
											class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
										/>
										<label for="radio-3" class="ms-2 text-sm font-medium dark:text-gray-300">指定企業</label>
									</div> -->
										<div class="flex items-center me-4">
											<div v-for="(tab, index) in eventTabs" :key="index" class="flex items-center me-4">
												<input
													:id="'radio-' + (index + 1)"
													type="radio"
													:value="tab"
													v-model="selectedTab"
													name="colored-radio"
													class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
												/>
												<label :for="'radio-' + (index + 1)" class="ms-2 text-sm font-medium dark:text-gray-300">{{ tab }}</label>
											</div>
										</div>
										<div class="w-full ml-[90px]">
											<!-- <div v-if="selectedTab === '診次調整'">Content for 診次調整</div> -->
											<div v-if="selectedTab === '特殊項目'">
												<div class="relative group w-full">
													<button
														class="inline-flex w-full px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-blue-500"
														@click="specialDropdown"
													>
														<span class="mr-2">無痛胃鏡檢查(70歲以上需事前評估) ( Panendoscopy exam )</span>
														<svg
															xmlns="http://www.w3.org/2000/svg"
															class="w-5 h-5 ml-2 -mr-1 absolute right-2"
															viewBox="0 0 20 20"
															fill="currentColor"
															aria-hidden="true"
														>
															<path
																fill-rule="evenodd"
																d="M6.293 9.293a1 1 0 011.414 0L10 11.586l2.293-2.293a1 1 0 111.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z"
																clip-rule="evenodd"
															/>
														</svg>
													</button>
													<div
														v-show="isOpenSpecial"
														class="absolute w-full z-10 right-0 mt-2 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 p-1 space-y-1"
													>
														<!-- Search input -->
														<div class="relative">
															<input
																v-model="searchTerm"
																class="flex items-center justify-between w-full px-2 py-2 text-gray-600 border-b border-gray-300 focus:outline-none text-sm"
																type="text"
																placeholder=""
																autocomplete="off"
															/>
															<svg
																class="w-4 h-4 text-gray-600 dark:text-white absolute top-4 right-4"
																aria-hidden="true"
																xmlns="http://www.w3.org/2000/svg"
																fill="none"
																viewBox="0 0 20 20"
															>
																<path
																	stroke="currentColor"
																	stroke-linecap="round"
																	stroke-linejoin="round"
																	stroke-width="2"
																	d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"
																/>
															</svg>
														</div>

														<ul class="p-3 space-y-3 text-sm text-gray-700 dark:text-gray-200" aria-labelledby="dropdownCheckboxButton">
															<li v-for="(item, i) in specialItems" :key="item">
																<div class="flex items-center">
																	<input
																		:id="i"
																		type="checkbox"
																		value=""
																		class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
																	/>
																	<label :for="i" class="ms-2 text-gray-700 text-sm font-medium dark:text-gray-300">{{ item }}</label>
																</div>
															</li>
														</ul>
													</div>
												</div>
											</div>
											<div v-if="selectedTab === '指定企業'">
												<div class="flex items-center justify-between">
													<div class="relative group w-[70%]">
														<button
															class="inline-flex w-full px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-blue-500"
															@click="toggleDropdown"
														>
															<span class="mr-2">英屬維京群島商華敦國際有限公司台灣分公司</span>
															<svg
																xmlns="http://www.w3.org/2000/svg"
																class="w-5 h-5 ml-2 -mr-1 absolute right-2"
																viewBox="0 0 20 20"
																fill="currentColor"
																aria-hidden="true"
															>
																<path
																	fill-rule="evenodd"
																	d="M6.293 9.293a1 1 0 011.414 0L10 11.586l2.293-2.293a1 1 0 111.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z"
																	clip-rule="evenodd"
																/>
															</svg>
														</button>
														<div
															v-show="isOpen"
															class="absolute w-full z-10 right-0 mt-2 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 p-1 space-y-1"
														>
															<!-- Search input -->
															<div class="relative">
																<input
																	v-model="searchTerm"
																	class="flex items-center justify-between w-[90%] px-2 py-2 text-gray-600 border-b border-gray-300 focus:outline-none text-sm"
																	type="text"
																	placeholder=""
																	autocomplete="off"
																/>
																<svg
																	class="w-4 h-4 text-gray-600 dark:text-white absolute top-4 right-4"
																	aria-hidden="true"
																	xmlns="http://www.w3.org/2000/svg"
																	fill="none"
																	viewBox="0 0 20 20"
																>
																	<path
																		stroke="currentColor"
																		stroke-linecap="round"
																		stroke-linejoin="round"
																		stroke-width="2"
																		d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"
																	/>
																</svg>
															</div>

															<!-- Dropdown content goes here -->
															<a
																v-for="item in filteredItems"
																:key="item"
																class="block px-4 py-2 text-gray-700 hover:bg-gray-100 active:bg-blue-100 cursor-pointer rounded-md text-sm"
																>{{ item }}</a
															>
														</div>
													</div>
													<div class="relative group w-[29%]">
														<button
															class="inline-flex w-full px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-blue-500"
															@click="planDropdown"
														>
															<span class="mr-2">方案A</span>
															<svg
																xmlns="http://www.w3.org/2000/svg"
																class="w-5 h-5 ml-2 -mr-1 absolute right-2"
																viewBox="0 0 20 20"
																fill="currentColor"
																aria-hidden="true"
															>
																<path
																	fill-rule="evenodd"
																	d="M6.293 9.293a1 1 0 011.414 0L10 11.586l2.293-2.293a1 1 0 111.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z"
																	clip-rule="evenodd"
																/>
															</svg>
														</button>
														<div
															v-show="isOpen1"
															class="absolute w-full z-10 right-0 mt-2 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 p-1 space-y-1"
														>
															<a
																v-for="item in planItems"
																:key="item"
																class="block px-4 py-2 text-gray-700 hover:bg-gray-100 active:bg-blue-100 cursor-pointer rounded-md text-sm"
																>{{ item }}</a
															>
														</div>
													</div>
												</div>
											</div>
										</div>
									</div>
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">日期</div>
										<span><FormPicker /></span>
										<span class="flex items-center ml-8 text-base"> 時段 </span>
										<span class="ml-4"><FormTime /></span>
									</div>
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">重複</div>
										<div id="checkboxDay" class="flex items-center">
											<label
												><input type="checkbox" name="variety" value="每日" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>每日</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週一" checked="checked" /><span
													class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週一</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週二" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週二</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週三" checked="checked" /><span
													class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週三</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週四" checked="checked" /><span
													class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週四</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週五" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週五</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週六" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週六</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週日" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週日</span
												></label
											>
										</div>
									</div>
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">名額</div>
										<div class="flex items-center me-4">
											<input
												id="radio-closed"
												checked
												type="radio"
												value=""
												name="closed"
												class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
											/>
											<label for="radio-closed" class="ms-2 text-sm font-medium dark:text-gray-300">休診</label>
										</div>
										<div class="flex items-center me-4">
											<input
												id="radio-people"
												checked
												type="radio"
												value=""
												name="radio-people"
												class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
											/>
											<label for="radio-people" class="ms-2 text-sm font-medium dark:text-gray-300"
												>調整名額為 <input type="number" class="placeCenter ml-1 mr-1 h-7 w-16 text-center" placeholder="15" /> 位
											</label>
										</div>
									</div>
								</div>

								<!-- btn -->
								<div class="text-center">
									<button
										type="button"
										class="w-full drop-shadow-lg border border-slate-300 text-[#313131] bg-[#FFF] hover:bg-[#ccc]/80 focus:ring-2 focus:outline-none focus:ring-[#ccc]/50 font-medium text-sm px-5 py-2.5 text-center dark:hover:bg-[#ccc]/80 dark:focus:ring-[#ccc]/40 me-2 mb-2"
									>
										新增條件
									</button>
								</div>
							</div>
						</div>

						<!-- table -->
						<div class="relative w-2/3 m-auto bg-[#ECF4F7]">
							<table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
								<!-- uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400 -->
								<!-- <thead class="text-base bg-transparent text-[#313131]">
									<tr>
										<th scope="col" class="align-middle text-center py-1 border-l-0 border-2 border-solid border-[#cccccc]" width="5%">
											優先<br />順序
										</th>
										<th scope="col" class="align-middle text-center py-1 border-2 border-solid border-[#cccccc]" width="15%">時間</th>
										<th scope="col" class="align-middle text-center py-1 border-2 border-solid border-[#cccccc]" width="15%">時段</th>
										<th scope="col" class="align-middle text-center py-1 border-2 border-solid border-[#cccccc]" width="15%">重複</th>
										<th scope="col" class="align-middle text-center py-1 border-r-0 border-2 border-solid border-[#cccccc]" width="50%">事件</th>
									</tr>
								</thead> -->
								<!-- <tbody>
									沒有資料顯示
									<tr class="border-b bg-transparent text-center">
										<td class="px-6 py-4" colspan="5">尚無設定</td>
									</tr>

									有資料顯示 
									<tr class="border-b bg-transparent text-center text-[#313131]">
										<td class="px-3 py-2 align-middle text-center border-l-0 border-2 border-solid border-[#cccccc]">Move</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">2023-11-1<br />至<br />2023-11-1</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">13:00<br />至<br />13:40</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">週一 週二<br />週三 週四<br />週五 週六</td>
										<td class="px-3 py-2 text-left align-middle border-r-0 border-2 border-solid border-[#cccccc]">
											<span>指定企業名額：九乘九 E , F 方案, 3位</span>
											<a href="#" class="float-right align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75">
												<img alt="Edit" src="@/assets/edit.svg" width="20" height="20" />
											</a>
										</td>
									</tr>
									<tr class="border-b bg-transparent text-center text-[#313131]">
										<td class="px-3 py-2 align-middle text-center border-l-0 border-2 border-solid border-[#cccccc]">Move</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">2023-11-15<br />至<br />2023-11-30</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">13:00<br />至<br />13:40</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">週一 週三</td>
										<td class="px-3 py-2 text-left align-middle border-r-0 border-2 border-solid border-[#cccccc]">
											<span>診次調整：5位</span>
											<a href="#" class="float-right align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75">
												<img alt="Edit" src="@/assets/edit.svg" width="20" height="20" />
											</a>
										</td>
									</tr>
								</tbody>-->
							</table>
							<HandleTable />
						</div>

						<div class="w-2/3 m-auto bg-[#fff] border-0">
							<p class="leading-normal text-base pt-3">
								備註說明：文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文字文文字文字文字文字文字文字文字文字文字文字
							</p>
						</div>

						<div class="w-11/12 m-auto mt-6">
							<DateParts />
							<!-- <AgencyCalendar /> -->
						</div>
					</div>
					<div v-else class="tab-pane">
						<div class="w-2/3 m-auto bg-[#ECF4F7] border-2 border-b-0 border-solid border-[#cccccc]">
							<div class="px-8 py-6">
								<div class="set-content leading-normal">
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">事件</div>

										<div class="flex items-center me-4">
											<input
												id="normalRadio-1"
												checked
												type="radio"
												value=""
												name="normal-radio"
												class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
											/>
											<label for="normalRadio-1" class="ms-2 text-sm font-medium dark:text-gray-300">一般檢查</label>
										</div>
										<div class="flex items-center me-4">
											<input
												id="normalRadio-2"
												type="radio"
												value=""
												name="normal-radio"
												class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
											/>
											<label for="normalRadio-2" class="ms-2 text-sm font-medium dark:text-gray-300">特殊檢查</label>
										</div>
										<div class="flex items-center me-4">
											<input
												id="normalRadio-3"
												type="radio"
												value=""
												name="normal-radio"
												class="w-4 h-4 bg-gray-100 border-gray-300 dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600"
											/>
											<label for="normalRadio-3" class="ms-2 text-sm font-medium dark:text-gray-300">價格時段</label>
										</div>
									</div>
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">時段</div>
										<span><FormTime /></span>
									</div>
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">重複</div>
										<div id="checkboxDay" class="flex items-center">
											<label
												><input type="checkbox" name="variety" value="每日" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>每日</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週一" checked="checked" /><span
													class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週一</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週二" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週二</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週三" checked="checked" /><span
													class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週三</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週四" checked="checked" /><span
													class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週四</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週五" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週五</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週六" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週六</span
												></label
											>
											<label
												><input type="checkbox" name="variety" value="週日" /><span class="rounded-md button text-sm py-0.5 px-4 mr-3"
													>週日</span
												></label
											>
										</div>
									</div>
									<div class="flex flex-wrap text-[#313131] mb-8">
										<div class="flex items-center me-4 w-20 text-base">名額</div>

										<div class="flex items-center me-4">
											<label for="radio-people" class="text-sm font-medium dark:text-gray-300"
												><input type="number" class="placeCenter ml-1 mr-1 h-7 w-16 text-center" placeholder="15" /> 位
											</label>
										</div>
									</div>
								</div>

								<!-- btn -->
								<div class="text-center">
									<button
										type="button"
										class="w-full drop-shadow-lg border border-slate-300 text-[#313131] bg-[#FFF] hover:bg-[#ccc]/80 focus:ring-2 focus:outline-none focus:ring-[#ccc]/50 font-medium text-sm px-5 py-2.5 text-center dark:hover:bg-[#ccc]/80 dark:focus:ring-[#ccc]/40 me-2 mb-2"
									>
										新增條件
									</button>
								</div>
							</div>
						</div>

						<!-- table -->
						<div class="relative w-2/3 m-auto bg-[#ECF4F7]">
							<table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
								<!-- uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400 -->
								<!-- <thead class="text-base bg-transparent text-[#313131]">
									<tr>
										<th scope="col" class="align-middle text-center py-1 border-l-0 border-2 border-solid border-[#cccccc]" width="5%">
											優先<br />順序
										</th>
										<th scope="col" class="align-middle text-center py-1 border-2 border-solid border-[#cccccc]" width="15%">時間</th>
										<th scope="col" class="align-middle text-center py-1 border-2 border-solid border-[#cccccc]" width="15%">時段</th>
										<th scope="col" class="align-middle text-center py-1 border-2 border-solid border-[#cccccc]" width="15%">重複</th>
										<th scope="col" class="align-middle text-center py-1 border-r-0 border-2 border-solid border-[#cccccc]" width="50%">事件</th>
									</tr>
								</thead> -->
								<!-- <tbody>
									沒有資料顯示
									<tr class="border-b bg-transparent text-center">
										<td class="px-6 py-4" colspan="5">尚無設定</td>
									</tr>

									有資料顯示 
									<tr class="border-b bg-transparent text-center text-[#313131]">
										<td class="px-3 py-2 align-middle text-center border-l-0 border-2 border-solid border-[#cccccc]">Move</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">2023-11-1<br />至<br />2023-11-1</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">13:00<br />至<br />13:40</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">週一 週二<br />週三 週四<br />週五 週六</td>
										<td class="px-3 py-2 text-left align-middle border-r-0 border-2 border-solid border-[#cccccc]">
											<span>指定企業名額：九乘九 E , F 方案, 3位</span>
											<a href="#" class="float-right align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75">
												<img alt="Edit" src="@/assets/edit.svg" width="20" height="20" />
											</a>
										</td>
									</tr>
									<tr class="border-b bg-transparent text-center text-[#313131]">
										<td class="px-3 py-2 align-middle text-center border-l-0 border-2 border-solid border-[#cccccc]">Move</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">2023-11-15<br />至<br />2023-11-30</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">13:00<br />至<br />13:40</td>
										<td class="px-3 py-2 align-middle text-center border-2 border-solid border-[#cccccc]">週一 週三</td>
										<td class="px-3 py-2 text-left align-middle border-r-0 border-2 border-solid border-[#cccccc]">
											<span>診次調整：5位</span>
											<a href="#" class="float-right align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75">
												<img alt="Edit" src="@/assets/edit.svg" width="20" height="20" />
											</a>
										</td>
									</tr>
								</tbody>-->
							</table>
							<NormalTable />
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
#checkboxDay input[type='checkbox'] {
	display: none;
}
#checkboxDay input:checked + .button {
	background: #0087e0;
	color: #fff;
}
#checkboxDay {
	.button {
		display: flex;
		background: #d9d9d9;
		color: #313131;
		cursor: pointer;

		&:hover {
			background: #0087e0;
			color: #fff;
		}
	}
}
</style>
