<script>
import { toast } from 'vue3-toastify'

export default {
  name: 'Dashboard',

  data() {
    return {
      burgers: null,
      burger_id: null,
      status: [],
    }
  },
  methods: {
    async getBurgers() {

      try {
        const req = await fetch('http://localhost:3000/burgers')
        const data = await req.json()

        this.burgers = data

        this.getStatus()

      } catch (error) {
        console.log(error.message)
      }

    },

    async getStatus() {

      try {
        const req = await fetch('http://localhost:3000/status')
        const data = await req.json()

        this.status = data
        console.log(this.status)
      } catch (error) {
        console.log(error.message)
      }

    },

    async deletBurger(id) {
      try {
        const req = await fetch(`http://localhost:3000/burgers/${id}`, {
          method: 'DELETE',

        })

        const res = await req.json()
        this.getBurgers()
        toast.success('Pedido deletado com sucesso!')
      } catch (error) {
        console.log(error.message)
      }
    },

    async updateBurg(event, id) {
      const option = event.target.value
      const dataJson = JSON.stringify({ status: option })

      try {
        const req = await fetch(`http://localhost:3000/burgers/${id}`, {
          method: 'PATCH',
          body: dataJson,
          headers: {

            "Content-Type": "application/json"
          }
        })
        toast.success('Status alterado com sucesso!')
      } catch (error) {
        console.log(error.message)
      }

    }
  },

  mounted() {
    this.getBurgers()
  }
}
</script>

<template>
  <div class="burger-table">
    <div>
      <div class="burger-table-heading">

      </div>

      <div class="burger-table-rows">
        <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
          <div class="order-number">
            <h4>Id</h4>
            <p>{{ burger.id }}</p>
          </div>
          <div>
            <h4>Nome</h4>
            <p>{{ burger.name }}</p>
          </div>
          <div>
            <h4>Pão</h4>
            <p>{{ burger.bread }}</p>
          </div>
          <div>
            <h4>carnes</h4>
            <p>{{ burger.meat.tipo }}</p>
          </div>
          <div>
            <h4>opcionais</h4>
            <ul v-for="(opt, index) in burger.optional" :key="index">
              <li>{{ opt }}</li>
            </ul>
          </div>
          <div>
            <div class="select-container">
              <select name="status" class="status" @change="updateBurg($event, burger.id)">
                <option value="">Selecione</option>
                <option :value="statusItem.tipo" v-for="statusItem in status" :key="statusItem.id"
                  :selected="burger.status === statusItem.tipo">{{ statusItem.tipo }}
                </option>
              </select>
              <button class="delete-btn" @click='deletBurger(burger.id)'>Cancelar</button>
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