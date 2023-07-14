<script>
    import {onMount} from "svelte";

    onMount(() => {
        (window.adsbygoogle = window.adsbygoogle || []).push({});

        const ins = document.createElement('ins');
        const script = document.createElement('script');

        ins.className = 'kakao_ad_area';
        ins.style.display = 'none;';

        ins.setAttribute('data-ad-width', '320');
        ins.setAttribute('data-ad-height', '250');
        ins.setAttribute('data-ad-unit', 'DAN-9mgXNeFER8WqmiE7');

        script.async = true;
        script.type = 'text/javascript';
        script.src = '//t1.daumcdn.net/kas/static/ba.min.js';

        document.querySelector('.aside__kakaoAdFit_big')?.appendChild(ins);
        document.querySelector('.aside__kakaoAdFit_big')?.appendChild(script);
    })
</script>

<aside class="aside__kakaoAdFit_big" style="text-align: center"></aside>