<script>
    import { goto } from "$app/navigation"; // Use `goto()` instead of `navigate`
</script>

<nav class="bg-blue-600 text-white p-4">
    <div class="container mx-auto flex justify-between items-center">
        <h1 class="text-2xl font-bold">Fake Shop & Bank App</h1>
        <div class="space-x-4">
            <button on:click={() => goto("/")} class="hover:underline">Home</button>
            <button on:click={() => goto("/shop")} class="hover:underline">Shop</button>
            <button on:click={() => goto("/bank")} class="hover:underline">Bank</button>
        </div>
    </div>
</nav>

<slot />
