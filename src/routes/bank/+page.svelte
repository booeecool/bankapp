<script>
    let balance = 1000; // Starting balance
    let transactions = [];
  
    function addTransaction(amount) {
      if (isNaN(amount) || amount === 0) {
        alert("Please enter a valid amount.");
        return;
      }
      transactions.push({ id: Date.now(), amount });
      balance += amount;
    }
  </script>
  
  <div class="min-h-screen bg-gray-100 p-8">
    <div class="max-w-4xl mx-auto">
      <h1 class="text-3xl font-bold mb-6">Bank App</h1>
  
      <!-- Balance Display -->
      <div class="bg-white p-6 rounded-lg shadow mb-8">
        <h2 class="text-2xl font-bold">Balance: ${balance.toFixed(2)}</h2>
      </div>
  
      <!-- Transactions List -->
      <div class="bg-white p-6 rounded-lg shadow">
        <h2 class="text-2xl font-bold mb-4">Transactions</h2>
        {#if transactions.length === 0}
          <p class="text-gray-500">No transactions yet.</p>
        {:else}
          <ul class="space-y-3">
            {#each transactions as transaction}
              <li class="flex justify-between items-center p-3 bg-gray-50 rounded">
                <p class="font-medium">
                  {transaction.amount > 0 ? "+" : ""}${transaction.amount.toFixed(2)}
                </p>
              </li>
            {/each}
          </ul>
        {/if}
      </div>
    </div>
  </div>