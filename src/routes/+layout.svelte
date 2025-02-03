<script>
	import { navigate } from "$app/navigation";
  </script>
  
  <nav class="bg-blue-600 text-white p-4">
	<div class="container mx-auto flex justify-between items-center">
	  <h1 class="text-2xl font-bold">Fake Shop & Bank App</h1>
	  <div class="space-x-4">
		<button on:click={() => navigate("/")} class="hover:underline">Home</button>
		<button on:click={() => navigate("/shop")} class="hover:underline">Shop</button>
		<button on:click={() => navigate("/bank")} class="hover:underline">Bank</button>
	  </div>
	</div>
  </nav>
  
  <slot />