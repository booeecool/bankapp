<script>
    let items = [];
    let newItem = { name: "", price: 0, stock: 0 };
  
    function addItem() {
      if (!newItem.name || newItem.price <= 0 || newItem.stock <= 0) {
        alert("Please fill in all fields correctly.");
        return;
      }
      items.push({ ...newItem, id: Date.now() });
      newItem = { name: "", price: 0, stock: 0 };
    }
  
    function startAuction(item) {
      alert(`Auction started for ${item.name}!`);
    }
  </script>
  
  <div class="min-h-screen bg-gray-100 p-8">
    <div class="max-w-4xl mx-auto">
      <h1 class="text-3xl font-bold mb-6">Stocker Panel</h1>
  
      <!-- Add Item Form -->
      <div class="bg-white p-6 rounded-lg shadow mb-8">
        <h2 class="text-2xl font-bold mb-4">Add Item</h2>
        <div class="space-y-4">
          <input
            bind:value={newItem.name}
            placeholder="Item Name"
            class="w-full p-2 border border-gray-300 rounded"
          />
          <input
            type="number"
            bind:value={newItem.price}
            placeholder="Price"
            class="w-full p-2 border border-gray-300 rounded"
          />
          <input
            type="number"
            bind:value={newItem.stock}
            placeholder="Stock"
            class="w-full p-2 border border-gray-300 rounded"
          />
          <button
            on:click={addItem}
            class="w-full bg-blue-500 text-white p-2 rounded hover:bg-blue-600"
          >
            Add Item
          </button>
        </div>
      </div>
  
      <!-- Items List -->
      <div class="bg-white p-6 rounded-lg shadow">
        <h2 class="text-2xl font-bold mb-4">Items</h2>
        {#if items.length === 0}
          <p class="text-gray-500">No items in stock.</p>
        {:else}
          <ul class="space-y-3">
            {#each items as item}
              <li class="flex justify-between items-center p-3 bg-gray-50 rounded">
                <div>
                  <p class="font-medium">{item.name}</p>
                  <p class="text-sm text-gray-500">${item.price.toFixed(2)}</p>
                  <p class="text-sm text-gray-500">Stock: {item.stock}</p>
                </div>
                <button
                  on:click={() => startAuction(item)}
                  class="bg-green-500 text-white p-2 rounded hover:bg-green-600"
                >
                  Start Auction
                </button>
              </li>
            {/each}
          </ul>
        {/if}
      </div>
    </div>
  </div>