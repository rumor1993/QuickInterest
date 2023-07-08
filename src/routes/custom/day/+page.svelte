<script>
    import calculator from '$lib/images/calculator.png';
    import CustomCalculator from "../../../lib/utils/CustomCalculator.svelte";

    let visible = false
    let interestRate = 0
    let interest = 0
    let incomeTax = 0
    let localTax = 0
</script>


<section>
    <div class="m-auto mt-5 w-full max-w-sm p-4 bg-white">
        <h3 class="text-xl mb-3 font-semibold text-gray-900">
            <img class="inline w-5" src="{calculator}">
            커스텀 이자 계산기
        </h3>
        <p class="text-sm font-normal text-gray-500">예치금, 이자, 금리구간등을 설정하여서 간편하게 이자와 세금을 제외한 이자 또한 손쉽게 확인 할 수 있습니다.</p>
    </div>

    <CustomCalculator bind:visible bind:interestRate bind:interest bind:incomeTax bind:localTax></CustomCalculator>

        <ins class="kakao_ad_area" style="display:none;"
        data-ad-unit = "DAN-biusmlMB8b29bjEK"
        data-ad-width = "320"
        data-ad-height = "50"></ins>
        <script type="text/javascript" src="//t1.daumcdn.net/kas/static/ba.min.js" async></script>

</section>