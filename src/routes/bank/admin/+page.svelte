<script>
    import { navigate } from "$app/navigation";
  
    let balance = 1000; // Starting balance
    let amount = 0;
  
    function updateBalance() {
      if (isNaN(amount) || amount === 0) {
        alert("Please enter a valid amount.");
        return;
      }
      balance += amount;
      amount = 0;
      alert("Balance updated!");
    }
  </script>
  
  <div class="min-h-screen bg-gray-100 p-8">
    <div class="max-w-4xl mx-auto">
      <h1 class="text-3xl font-bold mb-6">Admin Panel</h1>
  
      <!-- Balance Display -->
      <div class="bg-white p-6 rounded-lg shadow mb-8">
        <h2 class="text-2xl font-bold">Balance: ${balance.toFixed(2)}</h2>
      </div>
  
      <!-- Update Balance Form -->
      <div class="bg-white p-6 rounded-lg shadow">
        <h2 class="text-2xl font-bold mb-4">Update Balance</h2>
        <input
          type="number"
          bind:value={amount}
          placeholder="Amount"
          class="w-full p-2 border border-gray-300 rounded mb-4"
        />
        <button
          on:click={updateBalance}
          class="w-full bg-blue-500 text-white p-2 rounded hover:bg-blue-600"
        >
          Update Balance
        </button>
      </div>
    </div>
  </div>