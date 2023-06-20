<script>
  let itemName = '';
  let price = '';
  let expenseList = [];

  function addExpense() {
    if (itemName == '') {
      document.getElementById('item-name').focus();
    } else if (price == ''){
      document.getElementById('item-price').focus();
    } else {
      expenseList = [
        ...expenseList,
        {
          name: itemName,
          price: price,
        },
      ];
      itemName = '';
      price = '';
    }
  }

  function deleteExpense(index) {
    expenseList.splice(index,1);
    expenseList = expenseList;
  }
</script>
<h1>Учет расходов</h1>
<main>
  <form on:submit|preventDefault={addExpense}>
    <p>Название:</p>
    <input bind:value={itemName} id="item-name"/>
    <p>Сумма:</p>
    <input bind:value={price} id="item-price"/>
    <button class="add-expense" on:click={addExpense}><span>Добавить</span></button>
  </form>
  <table cellpadding="8" align="left">
    <tr>
      <th>Название</th>
      <th>Сумма</th>
      <th>Действия</th>
    </tr>
    {#each expenseList as item, index}
      <tr>
        <td>{item.name}</td>
        <td>{item.price}</td>
        <td><button class="delete-expense" on:click={() => deleteExpense(index)}>Удалить</button></td>
      </tr>
    {/each}
  </table>
</main>
<style>
  h1 {
    text-align: center;
    font-size: 1.5rem;
    margin: 2em 0;
  }

  table {
    width: 100%;
    margin: 2em 0;
  }

  th {
    background-color: #e4e4e4;
  }

  table, th, td {
    border: 2px solid #d4d4d4;
    border-collapse: collapse;

    text-align: left;
  }

  .add-expense {
    background-color: #00b400;
    color: white;
    
    border: 1px solid #02a002;
    border-radius: 5px;

    width: 90px;
    height: 25px;
  }

  .delete-expense {
    background-color: #e90000;
    color: white;
    
    border: 1px solid #d80000;
    border-radius: 5px;

    width: 90px;
    height: 25px;
  }
</style>