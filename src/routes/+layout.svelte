<script>
    import { dev } from "$app/environment";
    import { inject } from "@vercel/analytics";

    inject({ mode: dev ? "development" : "production" });
    
    import "../app.css";
</script>

<main class="w-full flex flex-col gap-4 items-center justify-center mb-4">
    <slot />
</main>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

    :global(html) {
        background-color: #ffffff;
        opacity: 0.8;
        background-image: linear-gradient(#f7f7f7 2px, transparent 2px),
            linear-gradient(90deg, #f7f7f7 2px, transparent 2px),
            linear-gradient(#f7f7f7 1px, transparent 1px),
            linear-gradient(90deg, #f7f7f7 1px, #ffffff 1px);
        background-size:
            50px 50px,
            50px 50px,
            10px 10px,
            10px 10px;
        background-position:
            -2px -2px,
            -2px -2px,
            -1px -1px,
            -1px -1px;
    }

    :global(h2) {
        font-size: 14pt;
        font-weight: 700;
        color: #701a75
    }

    :global(ul) {
        display: flex;
        flex-direction: column;
        gap: 0.4rem;
    }

    :global(li) {
        list-style: disc;
    }

    :global(strong) {
        font-weight: 600;
    }
</style>
