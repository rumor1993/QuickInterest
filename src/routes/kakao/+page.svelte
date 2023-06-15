<script>
    import Calculator from "../../lib/utils/Calculator.svelte";
    let visible = false
    let interestRate = 0.022
    let interest = 0
    let incomeTax = 0
    let localTax = 0
</script>


<section>
    <div class="m-auto mt-5 w-full max-w-sm p-4 bg-white sm:p-6">
        <h3 class="text-2xl mb-3 text-base font-semibold text-gray-900 md:text-xl">
            카카오뱅크 (세이프박스)
        </h3>
        <p class="text-sm font-normal text-gray-500">계좌마다 하나씩 세이프박스를 만들어
            통장의 여유자금을 간편하게 관리할 수 있습니다.</p>
    </div>

    <Calculator bind:visible bind:interestRate bind:interest bind:incomeTax bind:localTax></Calculator>

    <div id="detailed-pricing" class="m-auto mt-5 max-w-sm">
        <div class="mb-2 text-sm text-gray-900">금리(2023. 06. 15. 현재, 세전)</div>

        <div class="overflow-hidden min-w-max">
            <div class="grid grid-cols-2 p-4 text-sm font-medium text-gray-900 bg-gray-100 border-t border-b border-gray-200">
                <div>금액구간</div>
                <div>1억까지 </div>
            </div>

            <div class="grid grid-cols-2 px-4 py-5 text-sm text-gray-700 border-b border-gray-200">
                <div class="text-gray-500">금리</div>
                <div class="text-gray-500">연 2.20%</div>
            </div>
        </div>

        <div class="mt-2 text-xs text-gray-500">※ 금액구간 및 금리는 시장 상황 및 회사 사정에 따라 변동될 수 있으며, 변동된 경우 변동일로부터 변경된 금액구간 및 금리를 적용합니다.</div>
    </div>

</section>