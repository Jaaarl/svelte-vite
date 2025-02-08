<script>
  const fetchData = (async () => {
    const response = await fetch(
      "https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@latest/v1/currencies.json"
    );
    const data = await response.json();
    return data;
  })();
</script>

{#await fetchData}
  <p>...waiting</p>
{:then data}
  {#each Object.entries(data) as [code, name]}
    <li>{code}: {name}</li>
  {/each}
{:catch error}
  <p>An error occurred!</p>
{/await}
