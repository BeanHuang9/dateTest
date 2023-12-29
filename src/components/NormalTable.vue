<script setup lang="ts">
import { ref } from 'vue';
const days = ['週一', '週二', '週三', '週四', '週五', '週六', '週日'];

const data = ref([
	{
		title: '無痛胃鏡檢查(70歲以上需事前評估)',
	},
]);
</script>

<template>
	<table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
		<thead class="text-base bg-transparent text-[#313131] border-2 border-solid border-[#cccccc]">
			<tr>
				<th scope="col" class="align-middle text-center py-1 border-r-2 border-solid border-[#cccccc]">項目</th>
				<th scope="col" v-for="day in days" :key="day" class="align-middle text-center py-1">{{ day }}</th>
			</tr>
		</thead>
		<!-- v-for="(item, index) in data" :key="index" -->
		<tbody>
			<tr v-if="data.length === 0" class="border-b bg-transparent text-center">
				<td class="px-6 py-4" :colspan="days.length + 1">尚無設定</td>
			</tr>
			<tr class="border-2 border-solid border-[#cccccc] bg-transparent text-[#313131]">
				<td class="px-3 py-2 align-middle w-[25%]">
					<span class="inline-block align-middle w-[26%]"
						><button type="button" class="px-2 py-1 mb-1 text-xs font-medium text-center bg-[#D9D9D9] rounded-lg hover:bg-[#D1D5DB] text-[#313131]">
							刪除
						</button>
						<button type="button" class="px-2 py-1 text-xs font-medium text-center text-white bg-[#0087E0] rounded-lg hover:bg-[#3F83F8]">
							確認
						</button>
					</span>
					<span class="inline-block align-middle w-[73%]">無痛胃鏡檢查(70歲以上需事前評估)</span>
				</td>
				<!-- <td class="px-3 py-2 align-middle text-center">
					<label for="radio-people" class="text-sm font-medium dark:text-gray-300">
						<input type="number" class="placeCenter ml-1 mr-1 h-7 w-9 text-center" :placeholder="item.Mon" /> 位
					</label>
				</td> -->
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">0</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">0</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">2</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">3</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
			</tr>
			<tr class="border-2 border-solid border-[#cccccc] bg-transparent text-[#313131]">
				<td class="px-3 py-2 align-middle w-[25%]">
					<span class="inline-block align-middle w-[26%]"
						><a data-v-2b6fddf7="" href="#" class="align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75"
							><img data-v-2b6fddf7="" alt="Edit" src="/src/assets/edit.svg" width="20" height="20"
						/></a>
					</span>
					<span class="inline-block align-middle w-[73%]">血液重金屬檢測</span>
				</td>
				<!-- <td class="px-3 py-2 align-middle text-center">
					<label for="radio-people" class="text-sm font-medium dark:text-gray-300">
						<input type="number" class="placeCenter ml-1 mr-1 h-7 w-9 text-center" :placeholder="item.Mon" /> 位
					</label>
				</td> -->
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">2</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
			</tr>
			<tr class="border-2 border-solid border-[#cccccc] bg-transparent text-[#313131]">
				<td class="px-3 py-2 align-middle w-[25%]">
					<span class="inline-block align-middle w-[26%]"
						><a data-v-2b6fddf7="" href="#" class="align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75"
							><img data-v-2b6fddf7="" alt="Edit" src="/src/assets/edit.svg" width="20" height="20"
						/></a>
					</span>
					<span class="inline-block align-middle w-[73%]"
						>方案價<br />
						$ 0 - 3,000</span
					>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">12:00<br />|<br />12:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">12:00<br />|<br />12:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">12:00<br />|<br />12:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">12:00<br />|<br />12:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">12:00<br />|<br />12:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">12:00<br />|<br />12:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">12:00<br />|<br />12:20</div>
				</td>
			</tr>
			<tr class="border-2 border-solid border-[#cccccc] bg-transparent text-[#313131]">
				<td class="px-3 py-2 align-middle w-[25%]">
					<span class="inline-block align-middle w-[26%]"
						><a data-v-2b6fddf7="" href="#" class="align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75"
							><img data-v-2b6fddf7="" alt="Edit" src="/src/assets/edit.svg" width="20" height="20"
						/></a>
					</span>
					<span class="inline-block align-middle w-[73%]"
						>方案價<br />
						$ 3,001 - 12,000</span
					>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">10:00<br />|<br />10:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">10:00<br />|<br />10:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">10:00<br />|<br />10:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">10:00<br />|<br />10:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">10:00<br />|<br />10:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">10:00<br />|<br />10:20</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow">10:00<br />|<br />10:20</div>
				</td>
			</tr>
			<tr class="border-2 border-solid border-[#cccccc] bg-transparent text-[#313131]">
				<td class="px-3 py-2 align-middle w-[25%]">
					<span class="inline-block align-middle w-[26%]"
						><button type="button" class="px-2 py-1 mb-1 text-xs font-medium text-center bg-[#D9D9D9] rounded-lg hover:bg-[#D1D5DB] text-[#313131]">
							刪除
						</button>
						<button type="button" class="px-2 py-1 text-xs font-medium text-center text-white bg-[#0087E0] rounded-lg hover:bg-[#3F83F8]">
							確認
						</button>
					</span>
					<span class="inline-block align-middle w-[73%]">
						<div class="px-3 py-2 bg-white shadow inline-block align-middle numBorder">
							<span>13:00</span>
						</div>
						-
						<div class="px-3 py-2 bg-white shadow inline-block align-middle numBorder">
							<span>13:30</span>
						</div>
					</span>
				</td>
				<!-- <td class="px-3 py-2 align-middle text-center">
					<label for="radio-people" class="text-sm font-medium dark:text-gray-300">
						<input type="number" class="placeCenter ml-1 mr-1 h-7 w-9 text-center" :placeholder="item.Mon" /> 位
					</label>
				</td> -->
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">2</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">20</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">15</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">0</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">0</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">0</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">2</span>位</div>
				</td>
			</tr>
			<tr class="border-2 border-solid border-[#cccccc] bg-transparent text-[#313131]">
				<td class="px-3 py-2 align-middle w-[25%]">
					<span class="inline-block align-middle w-[26%]"
						><a data-v-2b6fddf7="" href="#" class="align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75"
							><img data-v-2b6fddf7="" alt="Edit" src="/src/assets/edit.svg" width="20" height="20"
						/></a>
					</span>
					<span class="inline-block align-middle w-[73%]">10:20 - 10:40</span>
				</td>

				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">2</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
			</tr>
			<tr class="border-2 border-solid border-[#cccccc] bg-transparent text-[#313131]">
				<td class="px-3 py-2 align-middle w-[25%]">
					<span class="inline-block align-middle w-[26%]"
						><a data-v-2b6fddf7="" href="#" class="align-middle font-medium text-blue-600 dark:text-blue-500 hover:opacity-75"
							><img data-v-2b6fddf7="" alt="Edit" src="/src/assets/edit.svg" width="20" height="20"
						/></a>
					</span>
					<span class="inline-block align-middle w-[73%]">10:40 - 11:40</span>
				</td>

				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">2</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">20</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">15</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
				<td class="px-3 py-4 align-middle text-center numBorder">
					<div class="px-3 py-2 bg-white shadow"><span class="pr-3 mr-1">-</span>位</div>
				</td>
			</tr>
		</tbody>
	</table>
</template>

<style lang="scss" scoped>
.numBorder span {
	border-bottom: 1px solid #000;
}
</style>
