<script>
    import { navigate } from "$app/navigation";
  
    let items = [
      { id: 1, name: "Laptop", price: 1200, stock: 5 },
      { id: 2, name: "Phone", price: 800, stock: 10 },
      { id: 3, name: "Tablet", price: 600, stock: 7 },
    ];
  
    let cart = [];
    let paymentDetails = { cardNumber: "", expiry: "", cvv: "", email: "" };
  
    function addToCart(item) {
      if (item.stock > 0) {
        cart.push(item);
        item.stock--;
      }
    }
  
    function checkout() {
      if (cart.length === 0) {
        alert("Your cart is empty!");
        return;
      }
      alert("Payment successful! Redirecting to home page.");
      cart = [];
      navigate("/");
    }
  </script>
  
  <div class="min-h-screen bg-gray-100 p-8">
    <div class="max-w-4xl mx-auto">
      <h1 class="text-3xl font-bold mb-6">Shop</h1>
  
      <!-- Navigation Buttons -->
      <div class="flex space-x-4 mb-6">
        <button
          on:click={() => navigate("/shop/stocker")}
          class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
        >
          Stocker Panel
        </button>
        <button
          on:click={() => navigate("/bank")}
          class="bg-green-500 text-white px-4 py-2 rounded hover:bg-green-600"
        >
          Bank App
        </button>
        <button
          on:click={() => navigate("/bank/admin")}
          class="bg-purple-500 text-white px-4 py-2 rounded hover:bg-purple-600"
        >
          Admin Panel
        </button>
      </div>
  
      <!-- Items Grid -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
        {#each items as item}
          <div class="bg-white p-4 rounded-lg shadow">
            <h2 class="text-xl font-semibold">{item.name}</h2>
            <p class="text-gray-600">${item.price.toFixed(2)}</p>
            <p class="text-sm text-gray-500">Stock: {item.stock}</p>
            <button
              on:click={() => addToCart(item)}
              class="mt-2 w-full bg-blue-500 text-white p-2 rounded hover:bg-blue-600"
            >
              Add to Cart
            </button>
          </div>
        {/each}
      </div>
  
      <!-- Cart -->
      <div class="bg-white p-6 rounded-lg shadow">
        <h2 class="text-2xl font-bold mb-4">Cart</h2>
        {#if cart.length === 0}
          <p class="text-gray-500">Your cart is empty.</p>
        {:else}
          <ul class="space-y-2 mb-4">
            {#each cart as item}
              <li class="flex justify-between items-center">
                <span>{item.name} - ${item.price.toFixed(2)}</span>
              </li>
            {/each}
          </ul>
          <button
            on:click={checkout}
            class="w-full bg-green-500 text-white p-2 rounded hover:bg-green-600"
          >
            Checkout
          </button>
        {/if}
      </div>
    </div>
  </div>