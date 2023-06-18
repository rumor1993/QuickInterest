<script>
    import { fade } from 'svelte/transition';

    let deposit;
    let total = 0

    export let visible = false
    export let interestRate = 0
    export let customRate = 0
    export let interest = 0
    export let incomeTax = 0
    export let localTax = 0
    let day = 0

    const getDateDiff = () => {
        const date1 = new Date(document.getElementById("startDate").value);
        const date2 = new Date(document.getElementById("endDate").value);

        const diffDate = date1.getTime() - date2.getTime();

        return Math.abs(diffDate / (1000 * 60 * 60 * 24)); // 밀리세컨 * 초 * 분 * 시 = 일
    }

    function changeDate() {
        day = getDateDiff()
        console.log(day)
        calculateInterest()
        calculateTax()
    }


    function changeDeposit() {
        interestRate = customRate / 100

        if (!isNumber(Number(deposit.replaceAll(',', '')))) {
            visible = true
            deposit = '';
        }
        addCommas()
        calculateInterest();
        calculateTax();
    }

    function addCommas() {
        deposit = Number(deposit.replaceAll(',', ''));
        deposit = deposit.toLocaleString('ko-KR');
    }

    function isNumber(value) {
        return /^\d+$/.test(value);
    }

    function init() {
        deposit = '';
        visible = false
    }

    function calculateInterest() {
        interest = Number(deposit.replaceAll(',', '')) * interestRate / 365 * day
        interest = interest.toLocaleString('ko-KR');
    }

    function calculateTax() {
        let incomeTaxNum = removeLastDigit(Number(interest.replaceAll(',', '')) * 0.14)
        incomeTax = incomeTaxNum.toLocaleString('ko-KR');

        let localTaxNum = removeLastDigit(Number(interest.replaceAll(',', '')) * 0.014)
        localTax = localTaxNum.toLocaleString('ko-KR');

        total = Math.trunc(Number(interest.replaceAll(',', '')) - (incomeTaxNum + localTaxNum))
        total = total.toLocaleString('ko-KR');
    }

    function removeLastDigit(number) {
        return Math.floor(number / 10) * 10;
    }
</script>

<div class="m-auto w-full max-w-sm p-5 bg-white border border-gray-200 rounded-lg shadow sm:p-5">
    {#if visible}
        <div transition:fade id="alert-2" class="flex p-4 mb-4 text-red-800 rounded-lg bg-red-50" role="alert">
            <svg aria-hidden="true" class="flex-shrink-0 w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z" clip-rule="evenodd"></path></svg>
            <span class="sr-only">Info</span>
            <div class="ml-3 text-sm font-medium">
                예치금액은 숫자만 입력하셔야 합니다!
            </div>
            <button on:click={init} type="button" class="ml-auto -mx-1.5 -my-1.5 bg-red-50 text-red-500 rounded-lg focus:ring-2 focus:ring-red-400 p-1.5 hover:bg-red-200 inline-flex h-8 w-8" data-dismiss-target="#alert-2" aria-label="Close">
                <span class="sr-only">Close</span>
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
            </button>
        </div>
    {/if}

    <h5 class="mb-5 text-base font-semibold text-gray-900 md:text-base">
        <div class="">📠 이자 계산기</div>
    </h5>

    <div class="grid items-end gap-6">
        <div class="relative z-0">
            <input type="text" id="default_standard" bind:value={deposit} on:keyup={changeDeposit} class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
            <label for="default_standard" class="absolute text-sm text-gray-500 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:left-0 peer-focus:text-blue-600 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">예치금액</label>
        </div>

        <div class="relative z-0">
            <input type="number" id="default_custom" bind:value={customRate} on:change={changeDeposit} on:keyup={changeDeposit} class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
            <label for="default_custom" class="absolute text-sm text-gray-500 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:left-0 peer-focus:text-blue-600 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">이자율(%)</label>
        </div>

        <div class="text-sm text-gray-500">예·적금기간</div>
        <div date-rangepicker class="flex items-center">
            <div class="relative">
                <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                    <svg aria-hidden="true" class="w-5 h-5 text-gray-500" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M6 2a1 1 0 00-1 1v1H4a2 2 0 00-2 2v10a2 2 0 002 2h12a2 2 0 002-2V6a2 2 0 00-2-2h-1V3a1 1 0 10-2 0v1H7V3a1 1 0 00-1-1zm0 5a1 1 0 000 2h8a1 1 0 100-2H6z" clip-rule="evenodd"></path></svg>
                </div>
                <input id="startDate" name="start" on:changeDate={changeDate} type="text" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5"
                       placeholder="시작일">
            </div>
            <span class="mx-4 text-gray-500">-</span>
            <div class="relative">
                <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                    <svg aria-hidden="true" class="w-5 h-5 text-gray-500" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M6 2a1 1 0 00-1 1v1H4a2 2 0 00-2 2v10a2 2 0 002 2h12a2 2 0 002-2V6a2 2 0 00-2-2h-1V3a1 1 0 10-2 0v1H7V3a1 1 0 00-1-1zm0 5a1 1 0 000 2h8a1 1 0 100-2H6z" clip-rule="evenodd"></path></svg>
                </div>
                <input id="endDate" name="end" on:changeDate={changeDate} type="text" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5" placeholder="종료일">
            </div>
        </div>
        <hr class="h-px my-2 bg-gray-200 border-0">
    </div>


    <div class="mt-2">
        <p class="text-right text-gray-500 ">{interest}</p>
        <p class="text-xs text-right text-gray-500 ">이자 (세전)</p>
    </div>
    <div class="mt-2">
        <p class="text-right text-gray-500 ">{incomeTax}</p>
        <p class="text-xs text-right text-gray-500 ">소득세</p>
    </div>
    <div class="mt-2">
        <p class="text-right text-gray-500 ">{localTax}</p>
        <p class="text-xs text-right text-gray-500">지방세</p>
    </div>

    <div class="flex justify-between mt-4">
        <sapn class="text-lg text-right font-bold">총 이자</sapn>
        <span class="text-lg text-left font-bold">{total} 원</span>
    </div>
</div>