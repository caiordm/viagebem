<script>
    import { marked } from 'marked';

    import { GoogleGenerativeAI } from "@google/generative-ai";
    let gemini_api_key = import.meta.env.VITE_GEMINI_API_KEY;

    let local = '';
    let response = ''; 
    let html = '';

    const run = async () => {
        const genAI = new GoogleGenerativeAI(gemini_api_key);
        const model = genAI.getGenerativeModel({ model: "gemini-1.5-flash" });

        let prompt = `Estou pensando em ir para ${local}, liste para mim: os principais pontos turísticos, as melhores formas de ir e algumas dicas para não passar por perrengues.`

        const result = await model.generateContent(prompt);
        console.log(result.response);
        response = result.response.text()
        let wait = false
        html = marked.parse(response);
        console.log(html)
    };
</script>



<div class="w-11/12 flex flex-col gap-1 items-center justify-center mt-4">
    <h1 class="text-fuchsia-900 text-2xl font-black">ViageBem 🧳</h1>
    <span class="text-slate-700 text-center"
        >Diga pra onde você quer ir, e receba informações valiosas sobre seu
        próximo destino! ✈️</span
    >
</div>

<div class="w-11/12 flex flex-col gap-2">
    <form
        class="w-full flex justify-between bg-slate-100 rounded-2xl p-2 gap-1 border-2 border-slate-200 border-dashed"
    >
        <input
            type="text"
            bind:value={local}
            placeholder="Para qual lugar você quer ir?"
            name="local"
            class="bg-transparent w-full text-md focus:outline-none border-none"
        />
        <button
            id="button"
            class="bg-fuchsia-900 text-white font-medium p-2 pl-4 pr-4 rounded-lg"
            type="submit"
            on:click={run}>Enviar</button
        >
    </form>
    <!-- <Readme/> -->
    <!-- {#if wait}
       <p>Carregando</p> -->
    {#if response}
        <div class="w-full flex flex-col gap-3 p-4 pl-6 pr-6 bg-slate-100 border-2 border-slate-300 border-dashed rounded-3xl">
            {@html html}
        </div>
    {/if}

    <span class="{response ? "mt-4" : "absolute bottom-0"} text-slate-400 mb-4">ViageBem é feito por <a href="github.com/caiordm" class="font-medium">caiordm</a></span>
</div>
