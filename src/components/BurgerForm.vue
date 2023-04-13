<script>
import { toast } from 'vue3-toastify'
export default {
  name: 'BurguerForm',

  data() {
    return {
      breadData: null,
      meatData: null,
      optionalData: null,
      name: null,
      bread: null,
      meat: null,
      optional: [],
      msg: null
    }
  },
  methods: {
    async getIngredients() {
      const req = await fetch('http://localhost:3000/ingredientes')
      const data = await req.json()

      this.breadData = data.paes
      this.meatData = data.carnes
      this.optionalData = data.opcionais
    },
    async createBurger(event) {
      event.preventDefault()

      if (!this.optional) {
        this.optional = {}
      }

      const data = {
        name: this.name,
        meat: this.meat,
        bread: this.bread,
        optional: Object.keys(this.optional),
        status: 'Solicitado'
      }

      if (this.name === null || this.meat === null || this.bread === null) {
        return toast.error('Preencha todos os dados do pedido')
      }


      const dataJson = JSON.stringify(data)

      try {
        const req = await fetch('http://localhost:3000/burgers', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: dataJson
        })

        this.name = null
        this.meat = null
        this.bread = null
        this.optional = []

        const res = await req.json()

        toast.success(`Pedido nº ${res.id} realizado com sucesso!`)
      } catch (error) {
        console.log(error.message)
        toast.error('Algo deu errado!')
      }


    }
  },
  mounted() {
    this.getIngredients()
  }
}
</script>

<template>
  <div>
    <div class="form">
      <form @submit="createBurger">
        <div class="input-container">
          <label for="name">Nome do cliente: </label>
          <input type="text" id="name" placeholder="Digite seu nome" v-model="name" />
        </div>

        <div class="input-container">
          <label for="bread">Escolha o pão: </label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option :value="bread.tipo" v-for="bread in breadData" :key="bread.id">
              {{ bread.tipo }}
            </option>
          </select>
        </div>

        <div class="input-container">
          <label for="meat">Escolha a carne do seu Burger </label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Selecione o tipo de carne</option>
            <option v-for="meat in meatData" :value="meat" :key="meat.id">{{ meat.tipo }}</option>
          </select>
        </div>

        <div class="input-container">
          <label for="optional" id="optional-title">Selecione os opcionais: </label>

          <div class="checkbox">
            <div class="checkbox-cointainer" v-for="optionalItem in optionalData" :key="optionalItem.id">
              <input type="checkbox" :name="'optional-' + optionalItem.tipo" id="optional"
                v-model="optional[optionalItem.tipo]" />
              <span>{{ optionalItem.tipo }}</span>
            </div>
          </div>
        </div>

        <div class="input-container">
          <input type="submit" value="Criar meu Burger" class="submit-btn" />
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
form {
  max-width: 400px;
  margin: 0 auto;
}

form .input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#optional {
  flex-direction: row;
  flex-wrap: wrap;
}

#optional-title {
  width: 100%;
}

.checkbox {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  max-width: 300px;
  justify-content: space-between;
}

.checkbox-cointainer {
  display: flex;
  flex-wrap: wrap;
}

.checkbox-cointainer input {
  width: auto;
  margin-right: 5px;
  margin-bottom: 15px;
}

.checkbox-cointainer span {
  font-weight: bold;
  margin-right: 30px;
}

.submit-btn {
  margin-bottom: 100px;
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
  transition: 0.5s;
}

.submit-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>
