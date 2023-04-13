<script>
export default {
  name: 'Dashboard'
}
</script>

<template>
  <div class="burger-table">
    <div>
      <div class="burger-table-heading">

      </div>

      <div class="burger-table-rows">
        <div class="burger-table-row">
          <div class="order-number">
            <h4>Id</h4>
            1
          </div>
          <div>
            <h4>Nome</h4>
            <p>Ramon</p>
          </div>
          <div>
            <h4>Pão</h4>
            <p>4 queijos</p>
          </div>
          <div>
            <h4>carnes</h4>
            <p>Picanha</p>
          </div>
          <div>
            <h4>opcionais</h4>
            <ul>
              <li>salame</li>
              <li>tomate</li>
            </ul>
          </div>
          <div>
            <h4>carnes</h4>
            <div class="select-container">
              <select name="status" class="status">
                <option value="">Selecione</option>
              </select>
              <button class="delete-btn">Cancelar</button>
            </div>

          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<style scoped>
.burger-table {
  max-width: 1200px;
  margin: 0 auto;
}


.burger-table-rows,
.burger-table-row {
  display: flex;
  flex-wrap: wrap;
}

h4 {
  margin-bottom: 5px;
}

.burger-table-heading {
  border-bottom: 3px solid #333;
}

.burger-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #CCC;

}

.burger-table-heading div,
.burger-table-row div {
  width: 19%;
}

.burger-table-heading .order-id,
.burger-table-row .order-number {
  width: 5%;
}

select {
  padding: 12px 6px;
  margin-right: 12px;
}

.delete-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: .5s;
}

.select-container {
  display: flex;
}

.delete-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>