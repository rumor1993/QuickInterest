<script>
    import {onMount} from "svelte";

    onMount(() => {
        const ins = document.createElement('ins');
        const script = document.createElement('script');

        ins.className = 'kakao_ad_area';
        ins.style.display = 'none;';

        const winodwSize = window.innerWidth;
        if (winodwSize < 1024) {
            ins.setAttribute('data-ad-width', '320');
            ins.setAttribute('data-ad-height', '50');
            ins.setAttribute('data-ad-unit', 'DAN-biusmlMB8b29bjEK');
        } else {
            ins.setAttribute('data-ad-width', '728');
            ins.setAttribute('data-ad-height', '90');
            ins.setAttribute('data-ad-unit', '728x90 사이즈의 광고 ID');
        }

        script.async = true;
        script.type = 'text/javascript';
        script.src = '//t1.daumcdn.net/kas/static/ba.min.js';

        document.querySelector('.aside__kakaoAdFit')?.appendChild(ins);
        document.querySelector('.aside__kakaoAdFit')?.appendChild(script);
    })
</script>

<aside className="aside__kakaoAdFit"></aside>