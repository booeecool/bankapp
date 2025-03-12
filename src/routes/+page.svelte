<script>
	let balance = 0;
	let transactions = [];

	let amount = '';
	let name = '';
	let reason = '';
	let accountName = '';
	let date = '';

	function addTransaction() {
		if (!amount || !name || !reason || !accountName) {
			alert('Please fill in all required fields.');
			return;
		}

		const transaction = {
			id: Date.now(),
			amount: parseFloat(amount),
			name,
			reason,
			accountName,
			date: date || new Date().toLocaleDateString() // Use current date if not provided
		};

		transactions = [transaction, ...transactions];
		balance += transaction.amount;

		// Reset form fields
		amount = '';
		name = '';
		reason = '';
		accountName = '';
		date = '';
	}

	function removeTransaction(id) {
		const transaction = transactions.find((t) => t.id === id);
		if (transaction) {
			balance -= transaction.amount;
			transactions = transactions.filter((t) => t.id !== id);
		}
	}
</script>

<div class="min-h-screen bg-gray-100 p-8">
	<div class="mx-auto max-w-2xl rounded-lg bg-white p-6 shadow-lg">
		<h1 class="mb-6 text-center text-3xl font-bold">Fake Bank App</h1>

		<!-- Balance Display -->
		<div class="mb-6 text-center">
			<h2 class="text-2xl font-semibold">Balance: ${balance.toFixed(2)}</h2>
		</div>

		<!-- Transaction Form -->
		<div class="mb-6">
			<div class="space-y-4">
				<input
					type="number"
					bind:value={amount}
					placeholder="Amount"
					class="w-full rounded border border-gray-300 p-2"
				/>
				<input
					bind:value={name}
					placeholder="Transaction Name"
					class="w-full rounded border border-gray-300 p-2"
				/>
				<input
					bind:value={reason}
					placeholder="Reason"
					class="w-full rounded border border-gray-300 p-2"
				/>
				<input
					bind:value={accountName}
					placeholder="Account Name"
					class="w-full rounded border border-gray-300 p-2"
				/>
				<input type="date" bind:value={date} class="w-full rounded border border-gray-300 p-2" />
				<button
					on:click={addTransaction}
					class="w-full rounded bg-blue-500 p-2 text-white hover:bg-blue-600"
				>
					Add Transaction
				</button>
			</div>
		</div>

		<!-- Transactions List -->
		<div>
			<h3 class="mb-4 text-xl font-semibold">Transactions</h3>
			{#if transactions.length === 0}
				<p class="text-gray-500">No transactions yet.</p>
			{:else}
				<ul class="space-y-3">
					{#each transactions as transaction (transaction.id)}
						<li class="flex items-center justify-between rounded bg-gray-50 p-3">
							<div>
								<p class="font-medium">{transaction.name}</p>
								<p class="text-sm text-gray-500">{transaction.reason}</p>
								<p class="text-sm">Account: {transaction.accountName}</p>
								<p class="text-sm">Date: {transaction.date}</p>
								<p class="text-sm">
									{transaction.amount > 0 ? '+' : ''}${transaction.amount.toFixed(2)}
								</p>
							</div>
							<button
								on:click={() => removeTransaction(transaction.id)}
								class="text-red-500 hover:text-red-700"
							>
								Remove
							</button>
						</li>
					{/each}
				</ul>
			{/if}
		</div>
	</div>
</div>