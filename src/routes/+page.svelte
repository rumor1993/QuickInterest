<script>
	import calculator from '$lib/images/calculator.png';
	import Adfit from "./custom/Adfit.svelte";
</script>

<section>
	<div class="m-auto mt-5 w-full max-w-sm p-4 bg-white border border-gray-200 rounded-lg shadow sm:p-6">
		<h1 class="mb-3 text-xl font-semibold text-gray-900">
			이자 계산기
		</h1>
		<p class="text-sm font-normal text-gray-500">쉽고 빠른 계산으로 예금이자를 확인할 수 있습니다.</p>
		<ul class="my-4 space-y-3">
			<li>
				<a on:click={() => location.href="/custom/day"} class="flex items-center p-3 text-base font-bold text-gray-900 rounded-lg bg-gray-50 hover:bg-gray-100 group hover:shadow">
					<img class="w-5" src="{calculator}">
					<span class="flex-1 ml-3 whitespace-nowrap">이자 계산기 <span class="text-sm text-blue-600">(일)</span></span>
					<span class="inline-flex items-center justify-center px-2 py-0.5 ml-3 text-xs font-medium text-gray-500 bg-gray-200 rounded">Popular</span>
				</a>
			</li>

			<li>
				<a on:click={() => location.href="/custom/month"} class="flex items-center p-3 text-base font-bold text-gray-900 rounded-lg bg-gray-50 hover:bg-gray-100 group hover:shadow">
					<img class="w-5" src="{calculator}">
					<span class="flex-1 ml-3 whitespace-nowrap">이자 계산기 <span class="text-sm text-blue-600">(월)</span></span>
					<span class="inline-flex items-center justify-center px-2 py-0.5 ml-3 text-xs font-medium text-gray-500 bg-gray-200 rounded">Popular</span>
				</a>
			</li>
		</ul>

		<hr class="h-px my-8 bg-gray-200 border-0">

      	<Adfit></Adfit>

		<hr class="h-px my-8 bg-gray-200 border-0">

		<h3 class="mb-3 text-base font-semibold text-gray-900">
			파킹 통장
		</h3>
		<p class="text-xs font-normal text-gray-500">‘파킹통장’은 Parking(주차)와 통장의 합성어로, 차를 잠시 주차하듯 언제든지 돈을 넣었다 뺄 수 있는 통장이다.</p>
		<ul class="my-4 space-y-3">
			<li>
				<a on:click={() => location.href="/toss"} class="flex items-center p-3 text-base font-bold text-gray-900 rounded-lg bg-gray-50 hover:bg-gray-100 group hover:shadow">
					<img class="w-5" src="https://play-lh.googleusercontent.com/Yoaqip2U7E9EKghfvnZW1OeanfbjaL3Qqn5TGVDYAqkbXsL3TDNyEp_oBPH5vAPro38">
					<span class="flex-1 ml-3 whitespace-nowrap">토스뱅크</span>
				</a>
			</li>
			<li>
				<a on:click={() => location.href="/kakao"} class="flex items-center p-3 text-base font-bold text-gray-900 rounded-lg bg-gray-50 hover:bg-gray-100 group hover:shadow">
					<img class="w-5" src="https://t1.daumcdn.net/cfile/tistory/997BD7335D089C3023">
					<span class="flex-1 ml-3 whitespace-nowrap">카카오뱅크</span>
				</a>
			</li>
			<li>
				<a on:click={() => location.href="/kbank"} class="flex items-center p-3 text-base font-bold text-gray-900 rounded-lg bg-gray-50 hover:bg-gray-100 group hover:shadow">
					<img class="w-5" src="https://play-lh.googleusercontent.com/nfphbnXEbNaL_BqRrU97IWCEnuHz6rBE5VHztahXk4cDE3Ag8MxRImhfF9plwrtylLg=w240-h480-rw">
					<span class="flex-1 ml-3 whitespace-nowrap">케이뱅크</span>
				</a>
			</li>
		</ul>
		<div>
			<a href="#" class="inline-flex items-center text-xs font-normal text-gray-500 hover:underline">
				<svg class="w-3 h-3 mr-2" aria-hidden="true" focusable="false" data-prefix="far" data-icon="question-circle" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M256 8C119.043 8 8 119.083 8 256c0 136.997 111.043 248 248 248s248-111.003 248-248C504 119.083 392.957 8 256 8zm0 448c-110.532 0-200-89.431-200-200 0-110.495 89.472-200 200-200 110.491 0 200 89.471 200 200 0 110.53-89.431 200-200 200zm107.244-255.2c0 67.052-72.421 68.084-72.421 92.863V300c0 6.627-5.373 12-12 12h-45.647c-6.627 0-12-5.373-12-12v-8.659c0-35.745 27.1-50.034 47.579-61.516 17.561-9.845 28.324-16.541 28.324-29.579 0-17.246-21.999-28.693-39.784-28.693-23.189 0-33.894 10.977-48.942 29.969-4.057 5.12-11.46 6.071-16.666 2.124l-27.824-21.098c-5.107-3.872-6.251-11.066-2.644-16.363C184.846 131.491 214.94 112 261.794 112c49.071 0 101.45 38.304 101.45 88.8zM298 368c0 23.159-18.841 42-42 42s-42-18.841-42-42 18.841-42 42-42 42 18.841 42 42z"></path></svg>
				본 계산기는 참고용으로만 활용하시길 바랍니다.</a>
		</div>
	</div>
</section>


<style lang="postcss">
	:global(html) {
		background-color: theme(colors.white);
	}
</style>