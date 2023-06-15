<script>
    import Calculator from "../../lib/utils/Calculator.svelte";
    let visible = false
    let interestRate = 0.0245
    let interest = 0
    let incomeTax = 0
    let localTax = 0
</script>


<section>
    <div class="m-auto mt-5 w-full max-w-sm p-4 bg-white sm:p-6">
        <h3 class="text-2xl mb-3 text-base font-semibold text-gray-900 md:text-xl">
            수협은행 (매일받는통장)
        </h3>
        <p class="text-sm font-normal text-gray-500">입출금통장 첫거래고객 우대 및 매일 이자를 받을 수 있는 입출금통장</p>
    </div>

    <Calculator bind:visible bind:interestRate bind:interest bind:incomeTax bind:localTax></Calculator>

    <div id="detailed-pricing" class="m-auto mt-5 max-w-sm">
        <div class="mb-2 text-sm text-gray-900">금리(2023. 06. 15. 현재, 세전)</div>

        <div class="overflow-hidden min-w-max">
            <div class="grid grid-cols-4 p-4 text-sm font-medium text-gray-900 bg-gray-100 border-t border-b border-gray-200">
                <div>금액구간</div>
                <div>1천만원이하 </div>
                <div>1천만원초과 1억원이하</div>
                <div>1억원초</div>
            </div>

            <div class="grid grid-cols-4 px-4 py-5 text-sm text-gray-700 border-b border-gray-200">
                <div class="text-gray-500">금리</div>
                <div class="text-gray-500">기본금리 1.50, 우대금리 1.0</div>
                <div class="text-gray-500">기본금리 2.00, 우대금리 1.0</div>
                <div class="text-gray-500">기본금리 0.10</div>
            </div>
        </div>

        <div class="mt-2 text-xs text-gray-500">※ 금액구간 및 금리는 시장 상황 및 회사 사정에 따라 변동될 수 있으며, 변동된 경우 변동일로부터 변경된 금액구간 및 금리를 적용합니다.</div>
    </div>

</section>